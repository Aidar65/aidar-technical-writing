# Развертывание и управление оператором acm-operator-demo в Kubernetes

> Примечание о конфиденциальности: Настоящий документ представляет собой синтетический учебный кейс по мотивам открытых стандартов; все наименования сервисов, пространств имен и сетевые адреса вымышлены.

Настоящее руководство предоставляет пошаговые инструкции по подготовке среды, развертыванию через Helm 3 и проверке работоспособности оператора `acm-operator-demo` в кластере Kubernetes согласно принципам фреймворка **Diátaxis** (категория **How-To**).

---

## Требования к окружению (Prerequisites)

Перед началом установки убедитесь, что соблюдены следующие условия:

- Запущенный кластер Kubernetes (`prod-cluster-1`, версия `1.26` и выше).
- Утилита `kubectl` с правами администратора кластера (`cluster-admin`).
- Установленный пакетный менеджер **Helm v3** (версия `3.10+`).
- Доступ к конфигурационным сервисам `acm-config-1.example.ru` и `acm-config-2.example.ru`.

---

## Пошаговое развертывание оператора через Helm 3

### Шаг 1: Подготовка пространства имен

Создайте изолированное пространство имен для оператора:

```bash
kubectl create namespace acm-system
```

### Шаг 2: Добавление и обновление Helm-репозитория

```bash
helm repo add acm https://charts.acm-demo.io
helm repo update
```

### Шаг 3: Установка Helm-чарта оператора

Выполните развертывание оператора `acm-operator-demo` в созданном пространстве имен:

```bash
helm install acm-operator-demo acm/acm-operator-demo-operator \
  --namespace acm-system \
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

## Проверка работоспособности и статуса (Health Check)

Для проверки текущего состояния установки и статуса подов оператора в пространстве имен `acm-system` сначала выполните базовую проверку:

```bash
kubectl get pods -n acm-system -l app.kubernetes.io/name=acm-operator-demo-operator
```

Затем выполните детальный анализ событий и статуса доступности Health Probe (Liveness & Readiness):

```bash
kubectl describe pod -n acm-system -l app.kubernetes.io/name=acm-operator-demo-operator
```

Ожидаемый результат: Статус всех подов `Running`, Readiness probe возвращает `HTTP 200 OK`.

---

## Процедура отката

В случае возникновения ошибок при обновлении или некорректной работы оператора выполните откат к предыдущей версии релиза с помощью Helm:

```bash
helm rollback acm-operator-demo 1 -n acm-system
```
