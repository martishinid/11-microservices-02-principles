# Домашнее задание к занятию «Микросервисы: принципы»

Вы работаете в крупной компании, которая строит систему на основе микросервисной архитектуры.
Вам как DevOps-специалисту необходимо выдвинуть предложение по организации инфраструктуры для разработки и эксплуатации.

## Задача 1: API Gateway 

Предложите решение для обеспечения реализации API Gateway. Составьте сравнительную таблицу возможностей различных программных решений. На основе таблицы сделайте выбор решения.

Решение должно соответствовать следующим требованиям:
- маршрутизация запросов к нужному сервису на основе конфигурации,
- возможность проверки аутентификационной информации в запросах,
- обеспечение терминации HTTPS.

Обоснуйте свой выбор.

## Задача 2: Брокер сообщений

Составьте таблицу возможностей различных брокеров сообщений. На основе таблицы сделайте обоснованный выбор решения.

Решение должно соответствовать следующим требованиям:
- поддержка кластеризации для обеспечения надёжности,
- хранение сообщений на диске в процессе доставки,
- высокая скорость работы,
- поддержка различных форматов сообщений,
- разделение прав доступа к различным потокам сообщений,
- простота эксплуатации.

Обоснуйте свой выбор.


# Ответ:

# Задача 1: API Gateway
Рассматриваемые решения:
- NGINX (с модулем NGINX Plus)
- Kong
- AWS API Gateway
- Traefik
- APISIX

| **Критерий**                                   | **NGINX**                     | **Kong**                        | **AWS API Gateway**             | **Traefik**                     | **APISIX**                     |
|------------------------------------------------|--------------------------------|----------------------------------|----------------------------------|----------------------------------|---------------------------------|
| **Маршрутизация запросов на основе конфигурации** | ✅ Поддерживает сложные правила маршрутизации | ✅ Поддерживает маршрутизацию через плагины | ✅ Поддерживает сложную маршрутизацию | ✅ Поддерживает динамическую маршрутизацию | ✅ Поддерживает сложные правила |
| **Проверка аутентификационной информации**      | ✅ С помощью сторонних модулей | ✅ Встроенная поддержка          | ✅ Интеграция с IAM               | ✅ С помощью плагинов            | ✅ Поддерживает JWT, OAuth2 и др. |
| **Терминация HTTPS**                           | ✅ Поддерживает                | ✅ Поддерживает                  | ✅ Полностью поддерживается       | ✅ Поддерживает                  | ✅ Поддерживает                 |
| **Масштабируемость**                           | ✅ Требует настройки           | ✅ Хорошая                       | ✅ Автоматическая                 | ✅ Поддерживает                  | ✅ Отличная                     |
| **Мониторинг и логирование**                   | ⚠️ Ограниченная в базовой версии | ✅ Встроенные плагины для логов  | ✅ Поддерживает CloudWatch        | ✅ Поддержка через плагины       | ✅ Встроенная поддержка         |
| **Поддержка плагинов и расширяемость**         | ⚠️ Ограниченная                | ✅ Широкий выбор плагинов        | ⚠️ Ограничена                    | ✅ Гибкая система плагинов       | ✅ Отличная поддержка           |
| **Лицензирование**                             | ⚠️ Платная версия (NGINX Plus) | ✅ Open Source + Enterprise      | ⚠️ Платная                        | ✅ Open Source                   | ✅ Open Source                  |
| **Удобство настройки**                         | ⚠️ Требует опыта               | ✅ Простая                       | ✅ Управляется через веб-консоль | ✅ Простая                       | ✅ Удобная                      |

Выбор решения:
- Если необходима простота настройки, масштабируемость и проверка аутентификации: Рекомендуется использовать Kong, так как он предоставляет встроенные возможности для аутентификации, мониторинга, логирования, и поддерживает плагинную систему.
-   - используется такими компаниями как Nasdaq, Honeywell, Cisco, FAB, Expedia, Samsung, Siemens и Yahoo Japan.
- Если требуется облачная инфраструктура: Выбор AWS API Gateway подойдет для тесной интеграции с сервисами AWS и автоматического масштабирования.
- Если важна гибкость маршрутизации и использование Open Source решений: Traefik или APISIX являются отличным выбором.

Так как задача для крупной компании **Kong**  будет оптимален для большинства случаев:
- Простая настройка.
- Богатый выбор плагинов.
- Встроенная поддержка терминации HTTPS, маршрутизации и проверки аутентификации.

  # Задача 2: Брокер сообщений

## Сравнительная таблица брокеров сообщений
| **Критерий**                                    | **RabbitMQ**                 | **Apache Kafka**              | **ActiveMQ Artemis**          | **Redis Streams**             | **NATS JetStream**            |
|-------------------------------------------------|------------------------------|--------------------------------|--------------------------------|--------------------------------|--------------------------------|
| **Кластеризация для обеспечения надёжности**    | ✅ Поддерживается (кластер и HA режим) | ✅ Поддерживается (репликация и разделы) | ✅ Поддерживается (мастер-слейв и HA) | ⚠️ Ограниченная поддержка (Redis Sentinel) | ✅ Поддерживается (кластер JetStream) |
| **Хранение сообщений на диске**                 | ✅ Поддерживается            | ✅ Поддерживается              | ✅ Поддерживается              | ✅ Поддерживается              | ✅ Поддерживается              |
| **Высокая скорость работы**                     | ✅ Высокая для стандартных задач | ✅ Отличная (особенно для больших данных) | ✅ Хорошая                     | ✅ Высокая (в памяти)          | ✅ Высокая                    |
| **Поддержка различных форматов сообщений**      | ✅ Любые форматы             | ✅ Любые форматы               | ✅ Любые форматы               | ✅ Любые форматы               | ✅ Любые форматы              |
| **Разделение прав доступа к потокам**           | ✅ Поддерживается (RBAC)     | ✅ Поддерживается (ACL)        | ✅ Поддерживается              | ⚠️ Ограниченная поддержка      | ✅ Поддерживается (ACL)       |
| **Простота эксплуатации**                       | ✅ Удобный интерфейс и документация | ⚠️ Сложная конфигурация       | ✅ Умеренная сложность         | ✅ Простота настройки          | ✅ Умеренная сложность        |
| **Используемая архитектура**                    | Традиционный брокер          | Лог событий (Event Log)       | Традиционный брокер            | In-Memory Streams             | Pub/Sub с устойчивыми потоками |
| **Масштабируемость**                            | ✅ Хорошая                   | ✅ Отличная                    | ⚠️ Ограниченная                | ⚠️ Ограниченная (на уровне Redis кластера) | ✅ Отличная                  |
| **Поддержка трансакций**                        | ✅ Поддерживается            | ✅ Поддерживается              | ✅ Поддерживается              | ⚠️ Ограниченная                | ✅ Ограниченная               |
| **Лицензирование**                              | ✅ Open Source               | ✅ Open Source                 | ✅ Open Source                 | ✅ Open Source                 | ✅ Open Source                |

Рекомендуемое решение: **Apache Kafka**
Apache Kafka удовлетворяет всем заявленным требованиям:

- Кластеризация: Надёжная поддержка кластеров, масштабируемость за счёт разделов (partitions) и репликации.
- Хранение сообщений на диске: Сообщения хранятся в логах на диске с поддержкой длительного хранения.
- Высокая скорость: Спроектирован для работы с большими объёмами данных в реальном времени.
- Форматы сообщений: Поддерживает любые форматы (JSON, Avro, Protobuf и др.).
- Разделение прав доступа: Интеграция с ACL для гибкого управления доступом.
- Простота эксплуатации: Требует немного опыта, но существует множество инструментов для мониторинга и автоматизации (Kafka Manager, Confluent Control Center).

Но следует учесть, что для крупномасштабных и критичных задач оптимальным выбором будет **Apache Kafka**, обеспечивающий надёжность, производительность и гибкость. Если важна простота и меньшие требования к масштабируемости, то стоит рассмотреть *RabbitMQ* (Масштабируемость RabbitMQ хуже, потому что его архитектура ориентирована на традиционные брокерские задачи, а не на обработку огромных потоков данных, как Kafka. RabbitMQ удобен для небольших систем, но для масштабируемых и высоконагруженных систем Kafka остаётся лидером).
