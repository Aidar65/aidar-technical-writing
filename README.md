# Технический писатель / Content Engineer (Docs-as-Code)

[![DocOps Quality Gate](https://github.com/Aidar65/aidar-technical-writing/actions/workflows/quality-gate.yml/badge.svg)](https://github.com/Aidar65/aidar-technical-writing/actions)

> **Enterprise & Production Context:**
> 5+ years of engineering and documentation management experience across closed-circuit enterprise systems (Nuclear Power, Critical Infrastructure, GovTech) under strict NDA. Real-world workflows utilized enterprise configuration management (CMDB / KKS) and internal VCS with digital signatures (УКЭП).
> This public repository serves as an open Docs-as-Code & DocOps sandbox demonstrating modern specification standards, automated quality gates, and architecture-as-code practices.

> Инженерный подход: Системный анализ для меня — внутренний инструмент качественного документирования. Я самостоятельно разбираю архитектуру, контракты REST/AsyncAPI и требования по ГОСТ 34/19, снимая нагрузку с разработчиков.

Двухтрековое инженерное портфолио, демонстрирующее компетенции на стыке **системного анализа** (System Analyst) и **технического писательства** (Technical Writer) с применением методологии **Docs-as-Code**.

---

## 📊 Ключевые показатели

| Метрика | Значение |
| :--- | :--- |
| Контракты под управлением | **70+ млн ₽** (Росатом: Курская АЭС-2, БРЕСТ-ОД-300) |
| Позиций в конфигурации данных | **3 240** (KKS, ЕОС-Качество, ЕОНКОМ) |
| Процедур нормоконтроля в год | **300+** (ТУ, ТЗ, ПМИ, РЭ по ГОСТ 19/34, ЕСКД, СТО Росатома) |
| Экономия на локализации КД | **до 800 000 ₽** за процедуру (КНР → ЕСКД/РФ без внешнего КБ) |
| Регуляторные проверки | **100%** без замечаний (ПДК ВК, Минпромторг ПП РФ № 719/1875) |

---

## Инженерный профиль

Инженер АСУ ТП / робототехника (КНИТУ-КАИ), 5+ лет в критической инфраструктуре (Росатом, КИИ 187-ФЗ, ГОСТ 34/19), стек Docs-as-Code.

### Ключевые предметные области

- **Системный анализ и проектирование (SA)**: Сбор и систематизация требований, разработка Технических заданий (ТЗ/ЧТЗ по ГОСТ 34.602-89), проектирование REST/gRPC API (OpenAPI 3.0), моделирование процессов и архитектуры (PlantUML, UML Sequence Diagrams).
- **Техническое писательство (TW)**: Разработка пользовательской и эксплуатационной документации по фреймворку Diátaxis, подготовка руководств по развертыванию в Kubernetes, документация пайплайнов автоматизации.
- **Docs-as-Code Ecosystem**: Хранение документации в Git, непрерывная интеграция в CI/CD (Quality Gates, markdownlint), автоматизация проверок.

---

## Единая матрица навигации по артефактам

| Категория | Название артефакта / Документа | Технологический стек / Формат | Ссылка на файл |
| :--- | :--- | :--- | :--- |
| **System Analysis** | ЧТЗ на подсистему промышленной телеметрии (ГОСТ 34.602) | ГОСТ 34, Markdown, КИИ 187-ФЗ | [`docs/reference/chtz-telemetry.md`](docs/reference/chtz-telemetry.md) |
| **System Analysis** | OpenAPI 3.0 спецификация сервиса аутентификации | OpenAPI 3.0, YAML, REST API | [`docs/system-analysis/integrations/openapi-spec.yaml`](docs/system-analysis/integrations/openapi-spec.yaml) |
| **System Analysis** | Диаграмма последовательности аутентификации и mTLS | PlantUML, UML Sequence Diagram | [`docs/system-analysis/models/auth-flow.puml`](docs/system-analysis/models/auth-flow.puml) |
| **Technical Writing** | Руководство по развертыванию оператора acm-operator-demo в K8s | Diátaxis (How-To), Helm 3, K8s | [`docs/how-to/k8s-operator-deploy.md`](docs/how-to/k8s-operator-deploy.md) |
| **Technical Writing** | Архитектура AI-пайплайна документации (Ollama + Qwen2.5) | Diátaxis (Explanation), Air-Gapped LLM | [`docs/explanation/ai-doc-pipeline.md`](docs/explanation/ai-doc-pipeline.md) |

---

## CI/CD Quality Gates

В репозитории настроен автоматический контроль качества документации через GitHub Actions (`.github/workflows/lint.yml`):

- **Линтинг**: Автоматический запуск `markdownlint` при каждом push и pull request.
- **Конфигурация**: `.markdownlint.json` с оптимальной настройкой правил форматирования.

Локальный запуск линтера:

```bash
npx markdownlint-cli "**/*.md"
```

---

## Контактная информация

- **Автор**: Айдар Ярмаков
- **GitHub**: [https://github.com/aidar65/aidar-technical-writing](https://github.com/aidar65/aidar-technical-writing)
- **Telegram**: [@Ambassador_ru](https://t.me/Ambassador_ru)
- **Email**: [jaarmakov@bk.ru](mailto:jaarmakov@bk.ru)
