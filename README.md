# 🚀 Technical Writing & Docs-as-Code Portfolio | Айдар Ярмаков

[![ci](https://github.com/Aidar65/aidar-technical-writing/actions/workflows/deploy.yml/badge.svg)](https://github.com/Aidar65/aidar-technical-writing/actions/workflows/deploy.yml)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

🌐 **Live Demo:** [aidar65.github.io/aidar-technical-writing](https://aidar65.github.io/aidar-technical-writing/)

---

## 👤 Обо мне

**Technical Content Engineer** с 5+ годами опыта в документировании сложных программно-аппаратных комплексов (АСУТП, ТПА, ИСУЗ).

- **Масштаб:** 300+ процедур нормоконтроля в год, конфигурация данных на **3240 позиций** (KKS-кодирование для Курской АЭС-2).
- **Регуляторы:** Росатом (АЭС, класс безопасности 4), Минпромторг (ПП РФ №719/1875, СТ-1), ФСТЭК (ЗОКИИ / 187-ФЗ).
- **Результат:** 100% прохождение аудитов без штрафов и замечаний. Экономия **800 тыс. руб. на процедуру** за счёт самостоятельной адаптации КД вместо аутсорса.

**Специализация:** мостик между инженерным доменом (АСУТП, ТПА, IoT) и IT-документацией (REST API, ГОСТ 19/34, docs-as-code).

---

!!! note "NDA & Sandbox Disclaimer"
    Данный репозиторий — публичный sandbox-полигон для отработки подходов **Docs-as-Code**.
    
    Основная рабочая документация (300+ ТУ, регламентов и паспортов в год для объектов АЭС, Росатома и Минпромторга) ведётся в закрытых корпоративных контурах под NDA. Представленные кейсы обезличены и адаптированы для демонстрации ИТ-стека.

---

## 📂 Структура портфолио

| Раздел | Формат | Описание |
| :--- | :--- | :--- |
| **[REST API Spec](docs/api/swagger.yaml)** | OpenAPI 3.0 / YAML | Спецификация телеметрии с HMAC-SHA256, 6 эндпоинтами и кодами ошибок RFC 7807 |
| **[C4 Architecture](docs/docs-code/architecture.md)** | Mermaid.js | Sequence-диаграмма взаимодействия ПЛК, IoT Gateway и TimeSeries DB |
| **[ТЗ ГОСТ 19.201](docs/docs-code/tz-gost19.md)** | Markdown / ЕСПД | Техническое задание на модуль сбора данных в парадигме Docs-as-Code |
| **[ПМИ ГОСТ 19.301](docs/docs-code/pmi-gost19.md)** | Markdown / ЕСПД | Программа и методика испытаний с негативными тест-кейсами |
| **[Промкейс АСУТП](docs/industrial/valve-asutp.md)** | Markdown / Tables | Спецификация дискового затвора DN100 PN25 и карта регистров Modbus RTU |

---

## 🛠 Быстрый запуск локально

```bash
git clone https://github.com/Aidar65/aidar-technical-writing.git
cd aidar-technical-writing
pip install -r requirements.txt
mkdocs serve
# Открыть в браузере: http://127.0.0.1:8000
