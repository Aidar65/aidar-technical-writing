# История изменений (Changelog)

Все заметные изменения в проекте портфолио зафиксированы в этом файле.
Формат основан на [Keep a Changelog](https://keepachangelog.com/ru/1.0.0/),
и этот проект придерживается [Семантического версионирования](https://semver.org/lang/ru/).

---

## [1.2.0] - 2026-08-09

### Added
- **ГОСТ 34.602:** ТЗ на модуль управления электроприводом ТПА в Markdown (docs/reference/tz-gost34.md).
- **ГОСТ 19.201:** ТЗ на сервисную утилиту калибровки концевых выключателей (docs/reference/tz-gost19.md).
- **AsyncAPI 2.6:** Спецификация MQTT-потока телеметрии вибрации и температуры привода (docs/reference/asyncapi.yaml).
- **DocOps Quality Gate:** Настроен .vscode/settings.json для линтинга русской и английской орфографии (Code Spell Checker).

### Fixed
- Исправлен деплой в GitHub Actions: переключен нативный экшен ctions/deploy-pages@v4 с поддержкой equirements.txt.
- Приведены к строгому кодированию UTF-8 все файлы Markdown и YAML.

---

## [1.1.0] - 2026-08-09

### Added
- Интегрирована методология навигации **Diátaxis** (Tutorials, How-to, Reference, Explanation) в mkdocs.yml.
- Добавлены контакты Telegram (@Ambassador_ru) в шапку landing-страницы.

### Changed
- Обновлено каноничное имя автора на Aidar Yarmakov в конфигурации MkDocs.

---

## [1.0.0] - 2026-08-08

### Added
- Базовая сборка MkDocs Material с поддержкой OpenAPI 3.0 и Mermaid.js diagrams.