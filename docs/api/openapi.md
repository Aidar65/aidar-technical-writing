# Спецификация REST API: Управление ТПА и Телеметрия

Интерактивная документация REST API для интеграции электроприводов и датчиков положения затвора в верхний уровень АСУ ТП.

---

## 🔌 Спецификация OpenAPI (Swagger)

Спецификация разработана по стандарту OpenAPI 3.0. Исходный файл контракта: [valve-control.yaml](v1/valve-control.yaml).

### Базовый URL
`https://api.factory.int/api/v1`

### Основные эндпоинты

| Метод | Эндпоинт | Описание |
| :--- | :--- | :--- |
| **GET** | `/valves/{id}/status` | Запрос текущего положения и телеметрии |
| **POST** | `/valves/telemetry` | Прием телеметрии с IoT-шлюза |
| **POST** | `/valves/{id}/emergency-close` | Экстренное закрытие затвора (Fail-Safe) |

---

### Пример запроса статуса (cURL)

```bash
curl -X GET "https://api.factory.int/api/v1/valves/VALVE-DN100-PN16-01/status" \
  -H "Authorization: Bearer <token>" \
  -H "Accept: application/json"
```
