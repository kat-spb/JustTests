# 🧱 Обзор сущностей платформы (v6)

---

## 📚 Типы сущностей, уровни и шаблонизация

| Тип                | Назначение                                           | Уровень         | Может быть шаблоном | Пример                              |
|--------------------|------------------------------------------------------|------------------|----------------------|--------------------------------------|
| `template_query`   | Формализованный запрос для подбора шаблона           | Мета             | ❌                   | запрос на обучение модели            |
| `template`         | Шаблон генерации сущности (project/pipeline)         | Мета             | ✅                   | `ml_classifier_template`             |
| `project`          | Сгенерированный проект на основе шаблона             | Экземпляр        | ✅                   | `backend_v2_project`                 |
| `script`           | Скрипт генерации или исполнения                      | Мета             | ✅                   | `train.py`, `deploy.sh`              |
| `pipeline`         | Шаблон или реализация процесса                       | Мета + Экземпляр | ✅                   | `train_pipeline`, `mlflow_pipeline`  |
| `test_plan`        | План тестов, валидаторов, метрик                     | Мета             | ✅                   | `unit_test_plan`, `smoke_suite`      |
| `environment`      | Описание среды выполнения                            | Мета             | ✅                   | `docker`, `venv`, `slurm_cluster`    |
| `resource`         | Конкретный вычислительный ресурс                     | Экземпляр        | ❌                   | `gpu_node01`, `docker_runner`        |
| `storage`          | Пространство хранения                                | Экземпляр        | ❌                   | `workspace`, `s3://bucket/model`     |

---

## 📂 Категоризация и иерархия

| Сущность  | Назначение                             | Примеры                             |
|-----------|-----------------------------------------|--------------------------------------|
| `object`  | Категория или группа                    | `ml`, `frontend`, `tests`, `docs`    |
| `item`    | Элемент внутри object с типом           | `ml/train.py`, `docker_env.yaml`     |
| `type`    | Описание типа сущности                  | `project`, `pipeline`, `script`      |

---

## 🧪 Применимость универсальных методов

| Тип              | CRUD | select | validate | import | export | health |
|------------------|------|--------|----------|--------|--------|--------|
| `template_query` | ✅   | ✅     | ✅       | ✅     | ✅     | ❌     |
| `template`       | ✅   | ✅     | ✅       | ✅     | ✅     | ✅     |
| `project`        | ✅   | ✅     | ✅       | ✅     | ✅     | ✅     |
| `script`         | ✅   | ✅     | ✅       | ✅     | ✅     | ✅     |
| `pipeline`       | ✅   | ✅     | ✅       | ✅     | ✅     | ✅     |
| `test_plan`      | ✅   | ✅     | ✅       | ✅     | ✅     | ✅     |
| `environment`    | ✅   | ✅     | ✅       | ✅     | ✅     | ✅     |
| `resource`       | ✅   | ✅     | ✅       | ✅     | ✅     | ✅     |
| `storage`        | ✅   | ✅     | ❌       | ✅     | ✅     | ✅     |

---

## 🔗 Связи между сущностями

| Источник         | Целевой элемент        | Связь                                      |
|------------------|------------------------|---------------------------------------------|
| `template_query` | `template`             | Подбор подходящего шаблона по критериям     |
| `template`       | `project`, `pipeline`  | Генерация экземпляра по шаблону             |
| `project`        | `resource`, `env`      | Выполняется в определённой среде            |
| `pipeline`       | `script`, `test_plan`  | Использует компоненты                       |
| `test_plan`      | `project`, `pipeline`  | Проверяет корректность результата           |
| `environment`    | `resource`             | Разворачивается на ресурсе                  |
| `storage`        | `project`, `artifact`  | Место хранения результата                   |
| `item`           | `object`               | Элемент категории                           |