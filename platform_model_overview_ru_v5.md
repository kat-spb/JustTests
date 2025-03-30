# 📘 Обзор моделей платформы (v5)

## 🧱 Сущности платформы

| Сущность         | Тип            | Описание                                                                  | Пример                             | Шаблонизируемая |
|------------------|----------------|---------------------------------------------------------------------------|------------------------------------|------------------|
| type             | мета           | Типы, назначаемые сущностям                                               | template, script, test_plan        | ✔                |
| object           | мета           | Категория сущностей                                                       | frontend, docs, ci                 | ✔                |
| item (в object)  | экземпляр      | Элемент в категории                                                       | init_app.sh в backend              | ✔                |
| template         | мета           | Шаблон генерации сущностей                                                | base_template.zip                  | ✔                |
| project          | экземпляр      | Созданный по шаблону проект                                               | client-portal                      | ✔                |
| script           | экземпляр      | Скрипт (sh, py, docker, c++) в шаблоне или пайплайне                      | build.sh, generate_docs.py         | ✔                |
| pipeline         | процесс / мета | Пайплайн сборки и деплоя                                                  | build-deploy.yml                   | ✔                |
| environment      | экземпляр      | Окружение выполнения                                                      | docker-node, venv3.11              | ✔                |
| resource         | экземпляр      | Вычислительный ресурс                                                     | vm-a1, k8s-node                     | ✔                |
| storage          | экземпляр      | Хранилище: workspace, storage, downloads                                  | /workspace/client-portal           | ✔                |
| test_plan        | мета / процесс | План интеграционного тестирования                                         | pipeline_test_plan.yaml            | ✔                |
| builder          | процесс        | Механизм сборки                                                           | docker, make                       | ✔                |
| vcs              | системный      | Git-интеграция                                                            | GitLab, Gitea                      | ✔                |
| ci               | системный      | CI/CD-система                                                              | GitLab CI, Jenkins                 | ✔                |
| bus              | системный      | Шина данных / событий                                                     | RabbitMQ, Kafka                    | ✔ (мета)         |
| knowledge_base   | системный      | База знаний: in-memory, FS, SQL (PostgreSQL+TS)                           | postgresql+timescale               | ✔                |

---

## 🧩 Методы для сущностей

| Сущность     | CRUD | Валидация | Импорт | Экспорт | Выбор (select) | Проверка (health_check) |
|--------------|------|-----------|--------|---------|----------------|--------------------------|
| type         | ✔    | —         | —      | —       | ✔              | —                        |
| object       | ✔    | —         | ✔      | ✔       | ✔              | —                        |
| item         | ✔    | ✔         | ✔      | ✔       | ✔              | —                        |
| template     | ✔    | ✔         | ✔      | ✔       | ✔              | ✔                        |
| project      | ✔    | ✔         | ✔      | ✔       | ✔              | ✔                        |
| script       | ✔    | ✔         | ✔      | ✔       | ✔              | ✔                        |
| pipeline     | ✔    | ✔         | ✔      | ✔       | ✔              | ✔                        |
| environment  | ✔    | —         | ✔      | ✔       | ✔              | ✔                        |
| resource     | ✔    | —         | ✔      | ✔       | ✔              | ✔                        |
| storage      | ✔    | —         | —      | —       | ✔              | —                        |
| test_plan    | ✔    | ✔         | ✔      | ✔       | ✔              | ✔                        |
| knowledge_base | —  | —         | ✔ (dump) | ✔ (dump) | —            | —                        |
| bus          | —    | —         | —      | —       | —              | ✔                        |

---

## 🔁 Универсальные методы

| Метод                     | Назначение                                                       |
|---------------------------|------------------------------------------------------------------|
| POST /validate/{type}     | Проверка архива по типу                                          |
| POST /import/{type}       | Импорт сущности                                                  |
| GET /export/{type}        | Экспорт сущности                                                 |
| GET /select               | Универсальный выбор                                              |
| GET /health/{type}        | Проверка доступности сущности                                    |
| POST /kb/dump             | Сохранение базы знаний в архив                                   |
| POST /kb/restore          | Восстановление БЗ из архива                                      |
| GET /config/bus           | Получение конфигурации шины данных                               |
| GET /config/kb            | Получение конфигурации базы знаний                               |

---

## 🔄 Процессы платформы

| Процесс           | Входные параметры               | Назначение                                                  | Применимо к               |
|-------------------|----------------------------------|-------------------------------------------------------------|----------------------------|
| init              | template_id, scripts, options    | Инициализация сущности                                      | template, project          |
| build             | entity_id, type, resource_id     | Сборка сущности                                             | template, project, script  |
| ci_setup          | project_id, env_id               | Настройка CI                                                | project, pipeline          |
| ci_run            | project_id                       | Запуск пайплайна                                            | project                    |
| deploy            | artifact, resource_id            | Деплой проекта                                              | project, pipeline          |
| validate_schema   | type, file                       | Валидация по схеме                                          | template, project          |
| validate_logic    | entity_id, template_id?          | Проверка соответствия шаблону                               | project, script, pipeline  |
| test_unit         | entity_id                        | Модульные тесты                                             | script, builder            |
| test_integration  | context_id, test_plan_id         | Интеграционное тестирование                                 | pipeline, project          |
| doc_generate      | entity_id, format                | Генерация документации                                      | template, project, script  |