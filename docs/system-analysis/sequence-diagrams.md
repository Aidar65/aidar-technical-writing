# Sequence-диаграммы: mTLS и аутентификация

В данном документе представлена диаграмма последовательности (Sequence Diagram), описывающая процесс взаимной TLS-аутентификации (mTLS) и последующего получения JWT-токена доступа.

## Сценарий аутентификации и выпуска JWT

1. **Клиент (Edge Agent)** инициирует TLS-соединение с предоставлением клиентского сертификата.
2. **API Gateway (NGINX)** запрашивает у **Удостоверяющего центра (PKI)** валидацию сертификата по спискам CRL / OCSP.
3. После подтверждения валидности сертификата шлюз перенаправляет запрос аутентификации в **Auth Service**.
4. **Auth Service** проверяет учетные данные, генерирует JWT-токен и возвращает его клиенту.

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
