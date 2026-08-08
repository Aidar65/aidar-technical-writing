# Changelog

Все существенные изменения в этом проекте будут документироваться в этом файле.

Формат основан на [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
и проект придерживается [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

---

## [1.1.0] — 2026-08-08

### Added
- `ci`: Добавлен шаг валидации YAML-конфигураций (`yamllint`) в GitHub Actions workflow.
- `docs`: Добавлен RFC 7807 JSON-сценарий ошибки 500 для аварии электродвигателя.
- `docs`: Добавлен NDA & Sandbox Disclaimer на главную страницу (`docs/index.md`).

### Fixed
- `docs`: Исправлена относительная адресация ссылок в навигационном меню и `index.md`.

---

## [1.0.0] — 2026-08-07

### Added
- Первоначальный релиз Docs-as-Code портфолио.
- Добавлена спецификация OpenAPI 3.0 для сервиса телеметрии (`docs/api/openapi.md`).
- Добавлена C4 Sequence Diagram на Mermaid.js (`docs/docs-code/architecture.md`).
- Добавлено ТЗ по ГОСТ 19.201-78 (`docs/docs-code/tz-gost19.md`).
- Добавлена ПМИ по ГОСТ 19.301-79 (`docs/docs-code/pmi-gost19.md`).
- Добавлен промкейс АСУТП затвора DN100 PN25 (`docs/industrial/valve-asutp.md`).
- Настроен автоматический деплой через MkDocs Material и GitHub Actions.
