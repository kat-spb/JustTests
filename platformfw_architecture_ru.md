# 🏛 Архитектура платформы (TOGAF-ориентированная модель)

## 📐 Архитектурные уровни по TOGAF

Платформа построена по многоуровневой архитектуре, соответствующей рекомендациям TOGAF и включающей:

---

## 1. 📈 Business Architecture — Бизнес-архитектура

Определяет **цели**, **роли пользователей**, **основные функции** и **ценностные сценарии использования платформы**.

- Роли:
  - Интегратор
  - Разработчик
  - ML-инженер / Data Scientist
  - Оператор / DevOps
- Ценности:
  - Снижение порога вхождения в проектирование решений с AI
  - Ускорение генерации и проверки решений
  - Унификация подхода ко всем этапам: от идеи до развёртывания
- Основные функции:
  - Поиск и генерация шаблонов под задачу
  - Валидация входных данных и структуры
  - Автоматизированная сборка решений (backend, UI, edge, dataflow)
  - Интерпретация, документирование, сравнение
  - Развёртывание и доставка результатов

---

## 2. 📦 Application Architecture — Прикладная архитектура

Определяет программные компоненты и их взаимодействия.

### Компоненты:
- **API-ядро (`platformfw`)** — FastAPI + OpenAPI, универсальные методы `/item`, `/build`, `/validate` и т.д.
- **Генератор (`generator`)** — логика трансформации шаблонов в готовые решения
- **Интерпретатор (`explain`)** — пояснение логики выбора решений
- **Интегратор (`builder`)** — сборка и упаковка проектов
- **Тестовая подсистема** — валидация, unit/integration/robustness-тесты
- **Документатор (`doc`)** — генерация описаний, схем, отчётов
- **Шина данных** — соединение между компонентами через событийную модель

---

## 3. 🧠 Data Architecture — Архитектура данных

Определяет:
- Единый тип данных `item`, описываемый через `type`, `object`, `metadata`, `params`, `generator`
- Унифицированную модель хранения в БЗ и на файловой системе
- Использование схем валидации (`schema.json`, `example.json`)
- Связи между сущностями (`template` ← `generator` → `project`)
- Поддержка версии, логов, тестов, артефактов

---

## 4. ⚙️ Technology Architecture — Технологическая архитектура

Используемые технологии и компоненты развертывания:

- Backend:
  - FastAPI (Python)
  - Bash/C/C++/Go backend-агенты (в systemd или docker)
- Storage:
  - Файловая структура: `/uploads`, `/workspace`, `/storage`, `/downloads`
  - Версионирование и UID-идентификация
- Execution:
  - `docker-compose`, `systemd`, `dstack`, `slurm`
- CI/CD:
  - GitLab CI, Jenkins, интеграция с внешними runner-ами
- DataBus:
  - Поддержка Kafka и RabbitMQ для событийной интеграции

---

## 5. 🔒 Security & IAM Architecture (по расширению)

- Поддержка ролей `user`, `dev`, `admin`
- Возможность подключения внешнего IAM (например, Keycloak)
- Поддержка bearer-token, Basic Auth, `client_id`/`secret_key`
- Авторизация на уровне API и сущностей (в перспективе)

---

## 💡 Предложение: архитектурные диаграммы

Дополнительно планируется построение архитектурных диаграмм в следующих нотациях:

- **Business Process Flow (BPMN)** — пользовательские сценарии
- **Motivation Model (ArchiMate)** — цели, драйверы, ограничения
- **Data Entity Model (ER)** — связи между типами item
- **Data Flow Platform (DFD)** — обработка и передача данных
- **Application Components (ArchiMate)** — логика и API-шлюзы
- **Component Details (UML)** — внутренние модули
- **Technology Stack (ArchiMate)** — технологии, зависимости
- **Deployment View (UML)** — среды, окружения, деплой
- **Traceability Matrix (TOGAF)** — соответствие целей и реализации
- **Roadmap Phases (ArchiMate)** — итерации внедрения
