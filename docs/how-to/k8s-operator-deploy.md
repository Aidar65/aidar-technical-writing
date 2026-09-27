# Развёртывание и управление оператором acm-operator-demo в Kubernetes

> Примечание о конфиденциальности: это синтетический учебный кейс по мотивам открытых стандартов. Все наименования сервисов, пространств имён и сетевые адреса вымышлены.

Руководство даёт пошаговые инструкции: подготовить среду, развернуть оператор `acm-operator-demo` через Helm 3 и проверить работоспособность в кластере Kubernetes. По фреймворку Diátaxis это категория How-To.

---

## Требования к окружению

Чтобы установить оператор, подготовьте окружение:

- Запущенный кластер Kubernetes `prod-cluster-1` версии `1.26` и выше.
- Утилита `kubectl` с правами администратора кластера `cluster-admin`.
- Пакетный менеджер **Helm v3** версии `3.10` и выше.
- Доступ к конфигурационным сервисам `acm-config-1.example.ru` и `acm-config-2.example.ru`.

---

## Пошаговое развёртывание оператора через Helm 3

### Шаг 1. Создайте пространство имён

Чтобы изолировать ресурсы оператора от других приложений, создайте отдельное пространство имён:

```bash
kubectl create namespace acm-system
```

### Шаг 2. Подключите Helm-репозиторий

Чтобы Helm нашёл чарт оператора, добавьте репозиторий и обновите индекс чартов:

```bash
helm repo add acm https://charts.acm-demo.io
helm repo update
```

### Шаг 3. Установите Helm-чарт оператора

Чтобы развернуть оператор `acm-operator-demo` в пространстве имён `acm-system`, установите чарт:

```bash
helm install acm-operator-demo acm/acm-operator-demo-operator \
  --namespace acm-system \
  --set operator.replicaCount=2 \
  --set resources.requests.cpu=100m \
  --set resources.requests.memory=128Mi
```

Чтобы изменить другие параметры, добавьте флаги `--set` из таблицы ниже.

---

## Таблица параметров конфигурации

| Параметр | Описание | Значение по умолчанию |
| :--- | :--- | :--- |
| `operator.replicaCount` | Количество реплик контроллера оператора | `2` |
| `resources.requests.cpu` | Запрошенные ресурсы CPU | `100m` |
| `resources.requests.memory` | Запрошенная оперативная память | `128Mi` |
| `resources.limits.cpu` | Максимальный лимит CPU | `500m` |
| `resources.limits.memory` | Максимальный лимит памяти | `512Mi` |
| `metrics.enabled` | Включает экспорт метрик в Prometheus | `true` |

---

## Проверка работоспособности и статуса

Чтобы проверить статус подов оператора, выполните команду:

```bash
kubectl get pods -n acm-system -l app.kubernetes.io/name=acm-operator-demo-operator
```

Чтобы посмотреть события пода и результаты liveness- и readiness-проб, выполните команду:

```bash
kubectl describe pod -n acm-system -l app.kubernetes.io/name=acm-operator-demo-operator
```

Ожидаемый результат: все поды в статусе `Running`, readiness-проба возвращает `HTTP 200 OK`.

---

## Процедура отката

Чтобы вернуть предыдущую версию оператора после неудачного обновления, сначала найдите номер нужной ревизии релиза:

```bash
helm history acm-operator-demo -n acm-system
```

Затем выполните откат к этой ревизии. В примере — к ревизии `1`:

```bash
helm rollback acm-operator-demo 1 -n acm-system
```
