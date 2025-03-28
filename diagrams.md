# Диаграммы AI-платформы (Mermaid)

## 1. Контекстная диаграмма
**Показывает основные взаимодействия между пользователями, внешними сервисами и AI-платформой.**
```mermaid
graph TD
    Users[Пользователи]
    Devs[Разработчики]
    DataScientists[Data Scientists]
    BusinessUsers[Бизнес-пользователи]

    ExternalServices[Внешние сервисы]
    MLModels[ML-модели]
    Datasets[Датасеты]
    Cloud[Облачные провайдеры]

    Integration[Интеграционные системы]
    CICD[CI/CD]
    Monitoring[Мониторинг]
    APIManagement[Управление API]

    Platform[AI-платформа]

    Users -->|взаимодействие| Platform
    Devs --> Platform
    DataScientists --> Platform
    BusinessUsers --> Platform

    Platform --> MLModels
    Platform --> Datasets
    Platform --> Cloud

    Platform --> CICD
    Platform --> Monitoring
    Platform --> APIManagement
```
## 2. Функциональная схема
**Структура платформы по ключевым функциям.**
```mermaid
graph TD
    Platform[AI-платформа]
    ModelMgmt[Управление моделями]
    ServiceBuilder[Конструктор сервисов]
    Orchestration[Orchestration & Execution]
    APIGateway[API Gateway]
    Monitoring[Мониторинг и аналитика]

    Platform --> ModelMgmt
    Platform --> ServiceBuilder
    Platform --> Orchestration
    Platform --> APIGateway
    Platform --> Monitoring
```
## 3. Компонентная диаграмма
**Подсистемы платформы и их взаимодействие.**
```mermaid
graph TD
    Core[Core Platform Services]
    Auth[Аутентификация]
    ConfigMgmt[Управление конфигурацией]

    AIRuntime[AI Runtime]
    Containerization[Контейнеризация моделей]
    Inference[Инференс]

    DataMgmt[Data Management]
    Datasets[Доступ к датасетам]
    FeatureStore[Feature Store]

    Integration[Integration Layer]
    REST[REST/gRPC]
    Kafka[Kafka/Event Bus]

    Core --> Auth
    Core --> ConfigMgmt

    AIRuntime --> Containerization
    AIRuntime --> Inference

    DataMgmt --> Datasets
    DataMgmt --> FeatureStore

    Integration --> REST
    Integration --> Kafka
```
## 4. Диаграмма потоков данных
**Показывает путь данных от загрузки до инференса.**
```mermaid
graph LR
    Ingestion[Загрузка данных]
    Preprocessing[Предобработка]
    Training[Обучение]
    Deployment[Деплой]
    Inference[Инференс]

    Logs[Метрики и логи]
    Monitoring[Система мониторинга]

    Ingestion --> Preprocessing --> Training --> Deployment --> Inference
    Inference --> Logs --> Monitoring
```
## 5. Диаграмма развертывания
**Физическая и облачная инфраструктура.**
```mermaid
graph TD
    Kubernetes[Kubernetes-кластеры]
    GPU[GPU-ноды]
    DB[Базы данных]
    PostgreSQL[PostgreSQL]
    VectorDB[Vector DB]

    Cloud[AWS / Azure]
    S3[AWS S3]
    AzureML[Azure ML]

    Kubernetes --> GPU
    Kubernetes --> DB
    DB --> PostgreSQL
    DB --> VectorDB

    Cloud --> S3
    Cloud --> AzureML
    Kubernetes --> Cloud
```
## 6. Sequence-диаграммы
### a. Создание нового AI-сервиса
```mermaid
sequenceDiagram
    participant User
    participant UI
    participant API
    participant Registry as Model Registry
    participant Training as Training Service
    participant Deployment

    User->>UI: Создание сервиса
    UI->>API: Отправка запроса
    API->>Registry: Регистрация модели
    API->>Training: Запуск обучения
    Training->>Deployment: Развёртывание
```
### b. Запрос к AI-сервису
```mermaid
sequenceDiagram
    participant Client
    participant Gateway as API Gateway
    participant Engine as Inference Engine
    participant Model
    participant Response

    Client->>Gateway: Отправка запроса
    Gateway->>Engine: Перенаправление
    Engine->>Model: Выполнение инференса
    Model-->>Engine: Результат
    Engine-->>Gateway: Ответ
    Gateway-->>Client: Ответ
```
## 7. Схема безопасности
**Роли, шифрование и аудит.**
```mermaid
graph TD
    IAM\[Управление доступом \(IAM\)\]
    Admin\[Админ\]
    Dev\[Разработчик\]
    User\[Конечный пользователь\]

    Encryption[Шифрование]
    Transit[In Transit]
    AtRest[At Rest]

    Audit[Аудит доступа]

    IAM --> Admin
    IAM --> Dev
    IAM --> User

    Encryption --> Transit
    Encryption --> AtRest

    Security[Безопасность] --> IAM
    Security --> Encryption
    Security --> Audit
```
## 8. Модель доменных данных
**ER-модель сущностей платформы.**
```mermaid
erDiagram
    AISERVICE ||--o{ MODEL : includes
    AISERVICE ||--o{ PIPELINE : used
    MODEL ||--o{ DATASET : training on
    PIPELINE ||--o{ MODEL : consists of

    AISERVICE {
        string id
        string name
        string status
    }

    MODEL {
        string id
        string version
        string framework
    }

    DATASET {
        string id
        string source
        string format
    }

    PIPELINE {
        string id
        string type
        string config
    }
```
