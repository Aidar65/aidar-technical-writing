# 🚀 Technical Writing & Docs-as-Code Portfolio | Айдар Ярмаков

[![Deploy MkDocs](https://github.com/Aidar65/aidar-technical-writing/actions/workflows/deploy.yml/badge.svg)](https://github.com/Aidar65/aidar-technical-writing/actions/workflows/deploy.yml)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

Публичный репозиторий с примерами системной и API-документации в подходе **Docs-as-Code**.

🌐 **Live Demo:** [aidar65.github.io/aidar-technical-writing](https://aidar65.github.io/aidar-technical-writing)

---

## 👤 Обо мне

**Technical Engineer** с 5+ годами опыта в документации для сложных программно-аппаратных комплексов и АСУТП.

- **Масштаб:** 300+ процедур нормоконтроля в год, конфигурация данных на 3240 позиций (KKS-кодирование).
- **Регуляторы:** Росатом (АЭС, класс безопасности 4), Минпромторг (ПП РФ №719/1875, СТ-1).
- **Результат:** 100% прохождение аудитов без штрафов и замечаний. Экономия 800 тыс. ₽ на процедуре за счёт самостоятельной адаптации КД вместо аутсорса.
- **Стек:** Git, Markdown, MkDocs (Material), OpenAPI 3.0, Mermaid.js, Pandoc, GitHub Actions.

**Специализация:** Мостик между инженерным доменом (АСУТП, ТПА, IoT) и IT-документацией (REST API, ГОСТ 19/34, docs-as-code).

---

## 📂 Структура портфолио

| Раздел | Формат | Описание кейса |
| :--- | :--- | :--- |
| **[REST API Spec](docs/03-rest-api/openapi.yaml)** | OpenAPI 3.0 / YAML | Спецификация IoT-платформы: приём телеметрии с датчиков ТПА, управление положением затвора, вебхуки аварий |
| **[Архитектура C4](docs/02-gost-34/architecture.md)** | Mermaid.js | Sequence diagram: ПЛК → IoT Gateway → TimeSeries DB → Grafana. Показать, как данные с поля попадают в дашборд |
| **[ТЗ ГОСТ 19.201](docs/01-gost-19/TZ.md)** | Markdown / ЕСПД | ТЗ на модуль шифрования и проверки УКЭП по требованиям ЗОКИИ (187-ФЗ). Показать структуру ЕСПД на реальном кейсе |
| **[Промкейс АСУТП](docs/04-industrial/asutp-valve.md)** | Markdown | Спецификация дискового затвора DN100 PN25 + карта регистров Modbus RTU. Показать, как я описываю железо |

---

## 🛠 Локальный запуск

```bash
# Клонировать репозиторий
git clone https://github.com/Aidar65/aidar-technical-writing.git
cd aidar-technical-writing

# Установить зависимости и запустить локальный сервер
pip install mkdocs-material
mkdocs serve

# Открыть в браузере: http://127.0.0.1:80000
