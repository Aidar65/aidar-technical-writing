# Changelog

Все ключевые изменения в проекте портфолио документируются в этом файле.
Формат основан на [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
проект придерживается [Conventional Commits](https://www.conventionalcommits.org/).

## [1.1.0] — 2026-08-10

### Added
- Добавлен раздел интерактивной консоли Swagger UI для Valve API.
- В спецификацию OpenAPI `valve-control.yaml` добавлена схема ошибок RFC 7807 (`400 Bad Request`).

### Fixed
- Переведены все диаграммы Mermaid на чистый синтаксис без костылей PyYAML.
- Исправлена кодировка UTF-8 и окончания строк (CRLF -> LF) в файле `asyncapi.yaml`.
- Настроена автовалидация через `pre-commit` с флагом `--unsafe` для `check-yaml`.

## [1.0.0] — 2026-08-01

### Added
- Базовый разворот портфолио Docs-as-Code на MkDocs Material.
- Описание архитектуры локального AI-контура (NDA / ЗОКИИ).
- ГОСТ-спецификации (ГОСТ 34.602, ГОСТ 19.201).
