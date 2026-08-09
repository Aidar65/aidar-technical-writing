# РђСЂС…РёС‚РµРєС‚СѓСЂР° РїРµСЂРµРґР°С‡Рё С‚РµР»РµРјРµС‚СЂРёРё СЃ СЌР»РµРєС‚СЂРѕРїСЂРёРІРѕРґР°

РњРѕРґСѓР»СЊ СЃР±РѕСЂР° РјРµС‚СЂРёРє РїРѕР·РёС†РёРѕРЅРёСЂРѕРІР°РЅРёСЏ Рё СЃРѕСЃС‚РѕСЏРЅРёСЏ Р·Р°РїРѕСЂРЅРѕР№ Р°СЂРјР°С‚СѓСЂС‹ (DN100, PN25).

## Sequence Diagram (Р’Р·Р°РёРјРѕРґРµР№СЃС‚РІРёРµ)

```mermaid
sequenceDiagram
    autonumber
    participant Valve as Р­Р»РµРєС‚СЂРѕРїСЂРёРІРѕРґ (DN100)
    participant Controller as РџР›Рљ (Modbus RTU)
    participant Gateway as IoT Gateway (MQTT)
    participant API as Backend API (REST)
    participant DB as TimescaleDB

    Valve->>Controller: РђРЅР°Р»РѕРіРѕРІС‹Р№ СЃРёРіРЅР°Р» (4-20 РјРђ / РџРѕР»РѕР¶РµРЅРёРµ 100%)
    Controller->>Gateway: Modbus Register 40001 (Status: OPEN)
    Gateway->>API: POST /api/v1/valves/10LAA10AA001/telemetry (JSON)
    Note over API: Р’Р°Р»РёРґР°С†РёСЏ СЃС…РµРјС‹ JSON Рё HMAC
    API->>DB: INSERT INTO valve_metrics
    API-->>Gateway: 201 Created
