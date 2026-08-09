# Регламент передачи телеметрии ТПА

Документ описывает сквозной процесс опроса датчиков положения затвора и крутящего момента электропривода арматуры со стороны АСУ ТП Верхнего Уровня.

## Последовательность взаимодействия (Sequence Diagram)

```mermaid
sequenceDiagram
    autonumber
    participant SCADA as АСУ ТП (SCADA)
    participant API as Valve Control API
    participant PLC as ПЛК (CODESYS)
    participant Actuator as Электропривод (БКВ/ДТ)

    SCADA->>API: GET /api/v1/valves/valve-dn100-01/status
    Note over API: Валидация JWT-токена доступа
    API->>PLC: Запрос Modbus RTU (Read Holding Registers)
    PLC->>Actuator: Считывание сигналов 4-20 мА / концевиков
    Actuator-->>PLC: Данные положения (45%) и момента (120.5 Нм)
    PLC-->>API: Ответ Modbus (сырые регистры)
    API-->>SCADA: 200 OK (JSON с параметрами ТПА)
    