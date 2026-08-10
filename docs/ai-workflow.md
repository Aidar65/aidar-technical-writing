# Локальный AI-контур для документации (NDA / ЗОКИИ)

Схема безопасной работы с черновиками документации в закрытом периметре компании без утечки данных.

```mermaid
graph TD
    A[SME / Разработчик] -->|Фактура / Код| B[Локальная модель Qwen2.5-Coder]
    B -->|Черновик MD| C[Aider / VS Code]
    C -->|Ревью и Нормоконтроль| D[Technical Writer]
    D -->|Pull Request| E[Git Repository / CI Pipeline]
