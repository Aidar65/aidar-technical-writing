# История изменений (Changelog)

Все заметные изменения в проекте портфолио зафиксированы в этом файле.
Формат основан на [Keep a Changelog](https://keepachangelog.com/ru/1.0.0/),
и этот проект придерживается [Семантического версионирования](https://semver.org/lang/ru/).

---

## [1.2.0] - 2026-08-09

### Added
- **ГОСТ 34.602:** ТЗ на подсистему промышленной телеметрии в Markdown (`docs/reference/chtz-telemetry.md`).
- **OpenAPI 3.0:** Спецификация сервиса аутентификации (`docs/system-analysis/integrations/openapi-spec.yaml`).
- **PlantUML / Mermaid:** Диаграммы последовательности mTLS аутентификации (`docs/system-analysis/sequence-diagrams.md`).
- **DocOps Quality Gate:** Настроен `.github/workflows/quality-gate.yml` (markdownlint, Vale, Lychee link checker).

### Fixed
- Приведены к строгому кодированию UTF-8 все файлы Markdown и YAML.
- Анонимизированы вендорные наименования и домены.

### Changed
- Навигация и структура документации реорганизована по методологии Diátaxis (`tutorials/`, `how-to/`, `reference/`, `explanation/`).
- Telegram-контакт актуализирован: [`@Ambassador_ru`](https://t.me/Ambassador_ru).

---

## [1.1.0] - 2026-08-09

### Added
- Интегрирована методология навигации **Diátaxis** (Tutorials, How-to, Reference, Explanation) в `mkdocs.yml`.
- Добавлены контакты Telegram в шапку landing-страницы.

### Changed
- Обновлено каноничное имя автора на Aidar Yarmakov в конфигурации MkDocs.

---

## [1.0.0] - 2026-08-08

### Added
- Базовая сборка MkDocs Material с поддержкой OpenAPI 3.0 и Mermaid.js diagrams.
