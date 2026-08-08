# REST API Спецификация. Управление телеметрией ТПА

```yaml
openapi: 3.0.3
info:
  title: Valve Telemetry Service API
  description: API для приема телеметрии и управления положением запорной арматуры (DN/PN)
  version: 1.0.0
paths:
  /api/v1/valves/{id}/telemetry:
    post:
      summary: Передача пакета телеметрии с ПЛК / Gateway
      operationId: sendTelemetry
      parameters:
        - name: id
          in: path
          required: true
          description: Уникальный идентификатор арматуры (KKS код)
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
                - status
              properties:
                timestamp:
                  type: string
                  format: date-time
                  example: "2026-08-08T05:20:00Z"
                position_percent:
                  type: number
                  format: float
                  minimum: 0
                  maximum: 100
                  example: 100.0
                torque_nm:
                  type: number
                  example: 240.5
                status:
                  type: string
                  enum: [OPEN, CLOSED, OPENING, CLOSING, FAULT]
                  example: "OPEN"
      responses:
        '201':
          description: Пакет успешно записан в TimeSeries DB
        '400':
          description: Невалидный JSON или нарушены границы параметров
        '401':
          description: Ошибка проверки HMAC подписи пакета
