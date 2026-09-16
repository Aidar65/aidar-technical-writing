# mTLS-аутентификация и выпустить JWT

В данном документе описана архитектура двухсторонней TLS-аутентификации (mTLS) и взаимодействия клиентского агента с сервисом аутентификации для получения JWT-токена.

## Архитектурное описание

В процессе установления доверенного соединения клиент (`Client / Edge Agent`) предоставляет свой клиентский сертификат шлюзу (`API Gateway / NGINX`). Шлюз проверяет действительность сертификата через Удостоверяющий центр (`Cert Authority / PKI`), используя списки отзыва (CRL) или протокол OCSP. После успешной проверки сертификата клиент запрашивает выпуск токена у сервиса аутентификации (`Auth Service`), который генерирует подписанный JWT для последующих запросов.

## Диаграмма последовательности (Sequence Diagram)

```mermaid
sequenceDiagram
    autonumber
    actor Client as Client / Edge Agent
    participant Gateway as API Gateway / NGINX
    participant Auth as Auth Service
    participant PKI as Cert Authority / PKI

    Client->>Gateway: TLS Handshake with Client Cert (mTLS)
    Gateway->>PKI: Verify Client Certificate against CRL/OCSP
    PKI-->>Gateway: Certificate Valid Response
    Gateway->>Auth: POST /api/v1/auth/token (client_id, secret)
    Auth->>Auth: Authenticate Credentials & Issue JWT
    Auth-->>Gateway: 200 OK (access_token, expires_in)
    Gateway-->>Client: JWT Bearer Token Response
```

---

## Исходный кодPlantUML

Исходную PlantUML-диаграмму можно найти в файле: [`auth-flow.puml`](auth-flow.puml).
