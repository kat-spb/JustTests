
# 📋 Пользовательские сценарии и соответствие API

## 🧑‍💻 Общая схема взаимодействия с API
Платформа реализует 12 унифицированных методов, работающих с абстракциями `object`, `item`, `type` и `params`. Эти методы позволяют решать весь спектр задач.

---

## ✅ Таблица: Сценарии и покрытие API

| №  | Название сценария                                                | Методы API                                                | Типы (`type`)                               | Полное покрытие |
|----|-------------------------------------------------------------------|------------------------------------------------------------|---------------------------------------------|-----------------|
| 1  | Разработчик хочет решение по 4 вопросам                          | `/query`, `/item`, `/select`, `/build`, `/doc`            | `template_query`, `template`, `project`     | ✅              |
| 2  | Разработчик хочет создать новый шаблон                           | `/item`, `/validate`, `/test`, `/doc`                      | `template`, `config`, `example`             | ✅              |
| 3  | Интегратор хочет серверное решение (без обучения)                | `/item`, `/select`, `/validate`, `/build`, `/doc`, `/download` | `data`, `template`, `project`, `resource` | ✅              |
| 4  | Интегратор хочет веб-фронт на своих данных                       | `/item`, `/select`, `/build`, `/doc`, `/download`         | `data`, `template`, `project`, `ui`         | ✅              |
| 5  | Интегратор хочет встроить шаблон в своё решение                 | `/item`, `/validate`, `/select`, `/explain`, `/build`     | `project`, `script`, `structure`            | ✅              |
| 6  | Пользователь хочет обучить модель по своим данным                | `/item`, `/query`, `/select`, `/build`, `/test`, `/doc`   | `data`, `model`, `template`, `pipeline`     | ✅              |
| 7  | Пользователь проверяет совместимость модели и данных            | `/item`, `/validate`, `/explain`, `/doc`                  | `model`, `data`, `template`, `config`       | ✅              |
| 8  | Развёртывание проекта в прод                                    | `/build`, `/deploy`, `/item`, `/doc`                      | `project`, `environment`, `resource`        | ✅              |
| 9  | Добавление шаблона в базу знаний                                | `/item`, `/validate`, `/doc`, `/test`                     | `template`, `schema`, `example`             | ✅              |
| 10 | Сравнение двух моделей                                          | `/item`, `/test`, `/explain`, `/doc`                      | `model`, `test_plan`, `log`                 | ✅              |
| 11 | AutoML с ограничениями                                          | `/query`, `/build`, `/test`, `/doc`                       | `template_query`, `project`, `test_plan`    | ✅              |
| 12 | Пайплайн через визуальный редактор                              | `/item`, `/build`, `/doc`, `/test`                        | `pipeline`, `config`, `data`, `project`     | ✅              |
| 13 | Выгрузка модели в ONNX/PMML для SCADA                           | `/deploy`, `/item`, `/build`                              | `model`, `artifact`, `resource`             | ✅              |
| 14 | Интерпретация и анализ ошибок                                   | `/test`, `/doc`, `/explain`                               | `model`, `test_plan`, `artifact`            | ✅              |

---

## 📘 Примеры user story в формате API (спецификация)

### Пример: «Хочу получить решение для сбора данных с Modbus»
**Шаги:**
1. `POST /query` — формулируется задача (Modbus, микроконтроллер, измерение тока/напряжения)
2. `GET /item?type=template_query` — выбираются подходящие шаблоны
3. `POST /build` с параметрами (resource: `esp32`, protocol: `Modbus`, UI: `simple`)
4. `GET /doc` — генерируется описание, интерфейс управления
5. `GET /download` — получаем архив прошивки и UI

### Пример: «Хочу обучить модель на своих IoT-данных»
1. `POST /item` — загрузка CSV с данными (`type=data`)
2. `POST /query` — описывается задача: классификация по сенсорам
3. `GET /item?type=template_query` — предлагается `LSTM`, `RandomForest`, `AutoML`
4. `POST /build` — создается `pipeline`
5. `POST /test` — тестируем модель на hold-out
6. `GET /doc` — описание, ROC-кривая
7. `POST /deploy` — экспорт модели в ONNX
