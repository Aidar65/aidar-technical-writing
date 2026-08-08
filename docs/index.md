# 🚀 Technical Writing & Docs-as-Code Portfolio | Айдар Ярмаков

[![Deploy MkDocs](https://github.com/Aidar65/aidar-technical-writing/actions/workflows/deploy.yml/badge.svg)](https://github.com/Aidar65/aidar-technical-writing/actions/workflows/deploy.yml)

🌐 **Live Demo:** [aidar65.github.io/aidar-technical-writing](https://aidar65.github.io/aidar-technical-writing)

---

## 👤 Обо мне

**Technical Content Engineer** с 5+ годами опыта в документации для сложных программно-аппаратных комплексов и АСУТП.

- **Масштаб:** 300+ процедур нормоконтроля в год, конфигурация данных на **3240 позиций** (KKS-кодирование для Курской АЭС-2).
- **Регуляторы:** Росатом (АЭС, класс безопасности 4), Минпромторг (ПП РФ №719/1875, СТ-1) **.
- **Результат:** 100% прохождение аудитов без штрафов и замечаний. Экономия **800 тыс. ₽ на процедуру** за счёт самостоятельной адаптации КД вместо аутсорса.
- **Стек:** Git, Markdown, MkDocs (Material), OpenAPI 3.0, Mermaid.js, Pandoc, GitHub Actions.

**Специализация:** Мостик между инженерным доменом (АСУТП, ТПА, IoT) и IT-документацией (REST API, ГОСТ 19/34, docs-as-code).

---

!!! note "NDA & Sandbox Disclaimer"
    Данный репозиторий является публичным sandbox-полигоном для отработки подходов **Docs-as-Code**.
    
    Основная рабочая документация (300+ ТУ, регламентов и паспортов в год для объектов АЭС, Росатома и Минпромторга) ведётся в закрытых корпоративных контурах под NDA. Представленные кейсы обезличены и адаптированы для демонстрации ИТ-стека.

---

## 📂 Разделы портфолио

### 🔌 [REST API: IoT Telemetry Service](api/openapi.yaml)
Спецификация OpenAPI 3.0 для сервиса приёма телеметрии с датчиков ТПА. 6 эндпоинтов, примеры JSON, HMAC-SHA256 аутентификация, коды ошибок.

### 🏗 [Архитектура: C4 Model](architecture/c4-diagram.md)
Sequence diagram взаимодействия ПЛК → IoT Gateway → TimeSeries DB. Показать, как данные с поля попадают в дашборд Grafana.

### 📋 [ТЗ ГОСТ 19.201: Модуль УКЭП](gost-19/tz-module-ukip.md)
Техническое задание на модуль шифрования и проверки УКЭП по требованиям ЗОКИИ (187-ФЗ, ГОСТ Р 34.12-2015). Полная структура ЕСПД.

### ✅ [ПМИ ГОСТ 19.301: Тестирование](gost-19/pmi-ukip.md)
Программа и методика испытаний с негативными тестами на эмуляцию MITM-атак, replay-атак и проверку валидности сертификатов.

### ⚙️ [Промкейс: АСУТП затвора](industrial/asutp-valve.md)
Спецификация дискового затвора DN100 PN25 + карта регистров Modbus RTU + пример интеграции с Python.

---

## 🛠 Технологический стек

| Категория | Инструменты |
| :--- | :--- |
| **Source Control & CI/CD** | Git, GitHub Actions |
| **Markup & SSG** | Markdown, MkDocs Material Theme |
| **API Notation** | OpenAPI 3.0 (Swagger YAML) |
| **Diagrams-as-Code** | Mermaid.js |
| **Conversion** | Pandoc (MD → DOCX/PDF по ГОСТ) |

---

## 🎯 Как это использовать на собеседовании

1. **Откройте Live Demo** — там собранная документация с навигацией.
2. **Покажите коммит-хистори** — я версионирую документацию как код (ветки, PR, ревью).
3. **Спросите про стек** — я могу объяснить, почему выбрал MkDocs, а не Confluence; почему OpenAPI 3.0, а не 2.0.

---

## 📞 Контакты

- **Email:** jaarmakov@bk.ru
- **Telegram:** [@Ambassador_ru](https://t.me/Ambassador_ru)
- **GitHub:** [Aidar65](https://github.com/Aidar65)

---

*Made with ❤️ and docs-as-code approach*
