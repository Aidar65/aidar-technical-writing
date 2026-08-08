# 🚀 Technical Writing & Docs-as-Code Portfolio | Айдар Ярмаков

[![ci](https://github.com/Aidar65/aidar-technical-writing/actions/workflows/deploy.yml/badge.svg)](https://github.com/Aidar65/aidar-technical-writing/actions/workflows/deploy.yml)
[![Documentation Pages](https://img.shields.io/badge/docs-GitHub%20Pages-blue)](https://aidar65.github.io/aidar-technical-writing/)

Публичный репозиторий с примерами системной и API-документации в подходе **Docs-as-Code**. 

🌐 **Опубликованная платформа:** [aidar65.github.io/aidar-technical-writing](https://aidar65.github.io/aidar-technical-writing/)

---

## 👤 Профиль кандидата
* **Позиция:** Technical Content Engineer / Technical Writer (ГОСТ 19, ГОСТ 34, REST API).
* **Специализация:** Документирование сложных инженерных и IT-систем, регуляторная дисциплина (ЗОКИИ / 187-ФЗ, Росатом, Минпромторг).
* **Стек:** Git (GitHub/GitLab), Markdown, MkDocs (Material), OpenAPI 3.0 (Swagger), Mermaid.js, Pandoc, GitHub Actions CI/CD.

---

## 📂 Структура портфолио

| Раздел | Формат / Стек | Описание кейса |
| :--- | :--- | :--- |
| **[REST API Spec](https://aidar65.github.io/aidar-technical-writing/api/openapi/)** | OpenAPI 3.0 / YAML | Спецификация приема телеметрии и управления положением ТПА |
| **[Архитектура C4](https://aidar65.github.io/aidar-technical-writing/docs-code/architecture/)** | Mermaid.js | Sequence diagram взаимодействия ПЛК, IoT Gateway и TimeSeries DB |
| **[ТЗ ГОСТ 19.201](https://aidar65.github.io/aidar-technical-writing/docs-code/tz-gost19/)** | Markdown / ЕСПД | ТЗ на модуль шифрования и проверки УКЭП по требованиям ЗОКИИ (187-ФЗ) |
| **[Промкейс АСУТП](https://aidar65.github.io/aidar-technical-writing/industrial/valve-asutp/)** | Markdown | Спецификация затвора DN100 PN25 и карта регистров Modbus RTU |

---

## 🛠 Локальный запуск
```bash
# Клонировать репозиторий
git clone [https://github.com/Aidar65/aidar-technical-writing.git](https://github.com/Aidar65/aidar-technical-writing.git)

# Установить зависимости и запустить локальный сервер
pip install mkdocs-material
mkdocs serve
# Открыть в браузере: [http://127.0.0.1:8000](http://127.0.0.1:8000)
