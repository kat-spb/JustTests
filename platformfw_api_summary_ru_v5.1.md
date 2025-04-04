# 🔧 Сводка API платформы (v5.1)

## 🌐 Глобальные маршруты

| Метод | Путь              | Назначение                         |
|--------|-------------------|------------------------------------|
| GET    | /server_version   | Версия сервера                     |
| GET    | /alive            | Проверка доступности платформы     |

---

## 🔁 Универсальные действия

| Метод | Путь                   | Параметры              | Назначение                           |
|--------|------------------------|-------------------------|--------------------------------------|
| GET    | /select                | type, filter            | Универсальный выбор                 |
| GET    | /health/{type}         | type                    | Проверка доступности сущности       |
| POST   | /validate/{type}       | type, file              | Валидация архива по типу            |
| POST   | /import/{type}         | type, file              | Импорт по типу                      |
| GET    | /export/{type}         | type, ids               | Экспорт по типу                     |

---

## ⚙️ Управление категориями и элементами

| Метод | Путь               | Назначение                         |
|--------|--------------------|------------------------------------|
| GET    | /objects           | Список категорий                   |
| POST   | /objects           | Создать категорию                  |
| PUT    | /objects/{id}      | Обновить категорию                 |
| DELETE | /objects/{id}      | Удалить категорию                  |

| Метод | Путь               | Назначение                         |
|--------|--------------------|------------------------------------|
| GET    | /items             | Получить элементы по object и type|
| POST   | /items             | Добавить элемент в категорию       |
| PUT    | /items/{id}        | Обновить элемент                   |
| DELETE | /items/{id}        | Удалить элемент                    |

---

## 🧱 Управление типами

| Метод | Путь               | Назначение                         |
|--------|--------------------|------------------------------------|
| GET    | /types             | Получить список типов              |
| POST   | /types             | Добавить новый тип                 |
| DELETE | /types/{name}      | Удалить тип                        |

---

## 🧩 CRUD-алиасы по типам (на основе item/type)

- /templates
- /projects
- /scripts
- /pipelines
- /environments
- /resources
- /test_plans

(для всех: GET, POST, PUT, DELETE)

---

## 🔄 Процессы

| Метод | Путь           | Назначение                         |
|--------|----------------|------------------------------------|
| POST   | /init          | Инициализация по шаблону           |
| POST   | /build         | Сборка сущности                    |
| POST   | /ci/setup      | Настройка CI                       |
| POST   | /ci/run        | Запуск пайплайна                   |
| POST   | /deploy        | Деплой проекта/шаблона             |

---

## 🧪 Валидация, тесты, документация

| Метод | Путь                | Назначение                         |
|--------|---------------------|------------------------------------|
| POST   | /validate/schema    | Валидация структуры шаблона/проекта|
| POST   | /validate/logic     | Проверка логики проекта            |
| POST   | /test/unit          | Модульные тесты                    |
| POST   | /test/integration   | Интеграционные тесты               |
| POST   | /doc/generate       | Генерация документации             |

---

## 🧠 База знаний и шина

| Метод | Путь           | Назначение                         |
|--------|----------------|------------------------------------|
| POST   | /kb/dump       | Сохранение базы знаний             |
| POST   | /kb/restore    | Восстановление БЗ                  |
| GET    | /config/bus    | Конфигурация шины                  |
| GET    | /config/kb     | Конфигурация базы знаний           |