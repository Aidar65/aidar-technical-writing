# Развертывание и управление оператором itcacmistio в Kubernetes

Настоящее руководство предоставляет пошаговые инструкции по подготовке среды, развертыванию через Helm 3 и проверке работоспособности оператора `itcacmistio` в кластере Kubernetes согласно принципам фреймворка **Diátaxis** (категория **How-To**).

---

## Требования к окружению (Prerequisites)

Перед началом установки убедитесь, что соблюдены следующие условия:

- Запущенный кластер Kubernetes (версия `1.26` и выше).
- Утилита `kubectl` с правами администратора кластера (`cluster-admin`).
- Установленный пакетный менеджер **Helm v3** (версия `3.10+`).

---

## Пошаговое развертывание оператора через Helm 3

### Шаг 1: Подготовка пространства имен

Создайте изолированное пространство имен для оператора:

```bash
kubectl create namespace itcacm-system
```

### Шаг 2: Добавление и обновление Helm-репозитория

```bash
helm repo add itcacm https://charts.itcacm.io
helm repo update
```

### Шаг 3: Установка Helm-чарта оператора

Выполните развертывание оператора `itcacmistio` в созданном пространстве имен:

```bash
helm install itcacmistio itcacm/itcacmistio-operator \
  --namespace itcacm-system \
  --set operator.replicaCount=2 \
  --set resources.requests.cpu=100m \
  --set resources.requests.memory=128Mi
```

---

## Таблица параметров конфигурации (Values Reference)

| Параметр | Описание | Значение по умолчанию |
| :--- | :--- | :--- |
| `operator.replicaCount` | Количество реплик контроллера оператора | `2` |
| `resources.requests.cpu` | Запрошенные ресурсы CPU | `100m` |
| `resources.requests.memory` | Запрошенная оперативная память | `128Mi` |
| `resources.limits.cpu` | Максимальный лимит CPU | `500m` |
| `resources.limits.memory` | Максимальный лимит памяти | `512Mi` |
| `metrics.enabled` | Включение экспорта метрик Prometheus | `true` |

---

## Проверка работоспособности (Health Check)

Убедитесь, что поды оператора успешно запущены и находятся в состоянии `Running`:

```bash
kubectl get pods -n itcacm-system -l app.kubernetes.io/name=itcacmistio-operator
```

Проверьте статус доступности Health Probe (Liveness & Readiness):

```bash
kubectl describe pod -n itcacm-system -l app.kubernetes.io/name=itcacmistio-operator
```

Ожидаемый результат: Статус всех подов `Running`, Readiness probe возвращает `HTTP 200 OK`.
