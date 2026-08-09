# Архитектурный паспорт ТПА (DN100 PN16)

Паспорт и архитектурная модель дискового затвора атомного исполнения (Класс безопасности 4 по НП-001-15).

---

## 📋 Технические характеристики

| Параметр | Значение | Стандарт / Норматив |
| :--- | :--- | :--- |
| **Номинальный диаметр (DN)** | 100 мм | ГОСТ 28338 |
| **Номинальное давление (PN)** | 16 бар (1.6 МПа) | ГОСТ 26349 |
| **Материал корпуса** | Сталь 13ХФА | ГОСТ 5632 |
| **Класс герметичности** | Класс А | ГОСТ 9544 |
| **Строительная длина** | 190 мм | ГОСТ 33260 |

---

## 🔄 Схема передачи сигналов (Sequence Diagram)

```mermaid
sequenceDiagram
    autonumber
    participant Valve as Электропривод (DN100)
    participant Controller as ПЛК (Modbus RTU)
    participant Gateway as IoT Gateway (MQTT)
    participant API as Backend API (REST)
    participant DB as TimescaleDB

    Valve->>Controller: Аналоговый сигнал (4-20 мА / Положение 100%)
    Controller->>Gateway: Modbus Register 40001 (Status: OPEN)
    Gateway->>API: POST /api/v1/valves/10LAA10AA001/telemetry (JSON)
    Note over API: Валидация схемы JSON и HMAC
    API->>DB: INSERT INTO valve_metrics
    API-->>Gateway: 201 Created
    
