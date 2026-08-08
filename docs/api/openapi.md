# Спецификация REST API: Сервис Телеметрии ТПА

Полное описание интерфейсов взаимодействия с блоком управления электроприводов запорно-регулирующей арматуры (DN100 PN25).

---

```yaml
openapi: 3.0.3
info:
  title: Valve Telemetry & Control API
  version: 1.2.0
  description: REST API сервиса сбора метрик и аварийного управления запорной арматурой.

servers:
  - url: [https://api.valves.telemetry/v1](https://api.valves.telemetry/v1)
    description: Production Cluster (Cloud Layer)

paths:
  /valves:
    get:
      summary: Получение списка запорной арматуры
      description: Возвращает массив ТПА с возможностью фильтрации по номинальному давлению (PN).
      parameters:
        - name: pn
          in: query
          required: false
          description: Фильтр по номинальному давлению в барах (кгс/см²)
          schema:
            type: integer
            enum: [16, 25, 40, 63, 100]
            example: 25
      responses:
        '200':
          description: Успешный возврат списка ТПА
          content:
            application/json:
              schema:
                type: array
                items:
                  type: object
                  properties:
                    kks_code:
                      type: string
                      example: "10LAA10AA001"
                    dn:
                      type: integer
                      example: 100
                    pn:
                      type: integer
                      example: 25
                    status:
                      type: string
                      example: "OPEN"
        '400':
          description: Некорректное значение параметра PN

  /valves/{id}/telemetry:
    post:
      summary: Передача телеметрии с электропривода
      parameters:
        - name: id
          in: path
          required: true
          description: KKS-код арматуры
          schema:
            type: string
            example: "10LAA10AA001"
      requestBody:
        required: true
        content:
          application/json:
            schema:
              type: object
              required:
                - timestamp
                - position_percent
                - torque_nm
              properties:
                timestamp:
                  type: string
                  format: date-time
                  example: "2026-08-08T12:00:00Z"
                position_percent:
                  type: number
                  example: 45.5
                torque_nm:
                  type: number
                  example: 120.4
      responses:
        '201':
          description: Метрики успешно записаны в TimeSeries DB
        '400':
          description: Ошибка валидации параметров (RFC 7807)
          content:
            application/json:
              schema:
                type: object
                properties:
                  type:
                    type: string
                    example: "[https://api.valves.telemetry/errors/invalid-kks-format](https://api.valves.telemetry/errors/invalid-kks-format)"
                  title:
                    type: string
                    example: "Invalid Parameter Format"
                  status:
                    type: integer
                    example: 400
                  detail:
                    type: string
                    example: "Значение KKS не соответствует стандарту."
        '500':
          description: Критическая аппаратная ошибка (Авария привода)
          content:
            application/json:
              schema:
                type: object
                properties:
                  type:
                    type: string
                    example: "[https://api.valves.telemetry/errors/hardware-fault](https://api.valves.telemetry/errors/hardware-fault)"
                  title:
                    type: string
                    example: "Motor Overheat Detected"
                  status:
                    type: integer
                    example: 500
                  detail:
                    type: string
                    example: "Температура обмотки электродвигателя превысила предел 120°C."

  /valves/{id}/emergency-close:
    post:
      summary: Аварийное перекрытие затвора (Emergency Cut-Off)
      parameters:
        - name: id
          in: path
          required: true
          schema:
            type: string
            example: "10LAA10AA001"
      requestBody:
        required: true
        content:
          application/json:
            schema:
              type: object
              required:
                - reason
                - operator_id
              properties:
                reason:
                  type: string
                  example: "Превышение момента Torque Fault > 250 Нм"
                operator_id:
                  type: string
                  example: "USER-9921"
      responses:
        '200':
          description: Команда на закрытие успешно отправлена в ПЛК
        '409':
          description: Привод заблокирован механически
