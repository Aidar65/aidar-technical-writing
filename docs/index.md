# Welcome to Docs-as-Code Portfolio | Айдар Ярмаков

Данная платформа — демонстрационный стенд по документированию сложных инженерных и IT-систем в парадигме **Docs-as-Code**.

---

## 📂 Ключевые разделы портфолио

* **[REST API Telemetry Service](api/openapi.md)** — Спецификация OpenAPI 3.0 для приема метрик с электроприводов ТПА (JSON, HMAC-SHA256, коды ошибок).
* **[Архитектура C4](docs-code/architecture.md)** — Sequence diagram взаимодействия ПЛК, IoT Gateway и TimeSeries DB (Mermaid.js).
* **[ТЗ ГОСТ 19.201-78](docs-code/tz-gost19.md)** — Техническое задание на модуль шифрования телеметрии по требованиям ЗОКИИ (187-ФЗ, ГОСТ Р 34.12-2015).
* **[ПМИ ГОСТ 19.301-79](docs-code/pmi-gost19.md)** — Программа и методика испытаний с негативными тестами на эмуляцию MITM-атак.
* **[Промкейс АСУТП](industrial/valve-asutp.md)** — Интеграция дискового затвора DN100 PN25 и карта регистров Modbus RTU.

---

## 🛠 Технологический стек
* **Source Control & CI/CD:** Git (GitHub Actions)
* **Markup & SSG:** Markdown, MkDocs Material Theme
* **API Notation:** OpenAPI 3.0 (Swagger YAML)
* **Diagrams-as-Code:** Mermaid.js
