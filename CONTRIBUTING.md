# Процесс командной разработки документации (CONTRIBUTING)

Данный документ описывает процесс совместной работы над документацией проекта в рамках концепции Multi-Author и стандартов качества.

---

## 1. Процесс ветвления (Branching Strategy)

- Все изменения вносятся через создание отдельной ветки от ветки `main`.
- Наименование веток должно следовать шаблону `feature/<название-задачи>` или `fix/<название-задачи>`.

---

## 2. Стандарт коммитов (Conventional Commits)

Формат сообщений коммитов должен соответствовать спецификации [Conventional Commits](https://www.conventionalcommits.org/):

```text
<type>(<scope>): <short description>
```

Основные типы (`type`):

- `feat`: добавление нового документа или раздела
- `fix`: исправление ошибок, опечаток или форматирования
- `docs`: изменения, касающиеся только документации
- `chore`: технические задачи, обновление конфигураций и CI/CD
- `style`: исправление форматирования без изменения смысла

Пример:

```text
fix(docs): align mkdocs nav with restructured artifacts and update positioning
```

---

## 3. Чек-лист перед Merge (Quality Gates)

Перед отправкой Pull Request и слиянием в ветку `main` обязательна локальная проверка следующих шагов:

- [ ] **Markdown Lint**: Проверка форматирования файлов Markdown без ошибок:
  ```bash
  npx markdownlint-cli "**/*.md"
  ```
- [ ] **OpenAPI / Spectral Lint**: Проверка спецификации OpenAPI линтером Spectral:
  ```bash
  npx @stoplight/spectral-cli lint docs/system-analysis/integrations/openapi-spec.yaml
  ```
- [ ] **Сборка MkDocs**: Проверка корректности сборки сайта документации:
  ```bash
  mkdocs build
  ```
