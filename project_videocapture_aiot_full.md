# 🎯 Проект: Фреймворк видеозахвата AIoT (ТЗ 23.08)

## 🧠 Цель
Создание промышленного фреймворка видеозахвата, фильтрации и наблюдения потоков с разных источников с интеграцией в платформу AIoT.

## 👥 Команда
- Инженер потоковой обработки — 0.5 ставки
- ML-специалист — 0.5 ставки
- Тестировщик — 0.5 ставки

## 🔧 Программные компоненты

| Компонент | Назначение |
|-----------|------------|
| Программный компонент: «Конфигуратор источников данных» | Настройка и управление источниками видеопотока |
| Программный компонент: «Валидатор данных» | Проверка корректности описания и состояния источников |
| Программный компонент: «Общая память» | Организация буферизации данных для параллельного доступа |
| Программный компонент: «API-шлюз» | Валидация запросов и асинхронное взаимодействие через брокер сообщений |
| Программный компонент: «Сервер обработки запросов по API» | Работа с источниками, доставка данных, логика API |
| Программный компонент: «Библиотека алгоритмов видеозахвата» | Захват потоков GenICam / UDP / RTSP, синхронизация |
| Программный компонент: «Библиотека детекции объектов» | Онлайн-фильтрация и обнаружение объектов |
| Программный компонент: «Примеры использования» | Скрипты и демо применения API и фильтров |
| Программный компонент: «Инструмент тестирования и оценки» | Модульное тестирование API и библиотек |
| Программный компонент: «База данных» | Хранение метаданных, конфигураций, логов |

## 📅 Этапы и сроки (2024–2026)

| Год | Этап | Период | Содержание |
|-----|------|--------|------------|
| 2024 | ТЗ | апрель–июль | Цели, структура, требования |
| 2024 | Эскизный проект | август–декабрь | Архитектура, патенты, API |
| 2025 | Технический проект | январь–декабрь | Интерфейсы, логика, тесты |
| 2026 | Рабочий проект | январь–август | Реализация, приёмка, ПМИ |

## 📌 Контрольные точки и демонстрации

| Дата | Событие |
|------|---------|
| 15.01.2025 | 🎯 API-прототип |
| 15.04.2025 | 📸 Захват и фильтрация |
| 15.07.2025 | 📦 Интеграция и конфигурации |
| 15.10.2025 | 🧪 Финальные тесты |

## 🗂️ Полная декомпозиция: эпик → артефакт → задача (40–80 ч)

| Эпик | Артефакт | Задача | Роль | Трудоёмкость (ч) |
|------|-----------|--------|------|------------------|
| Настройка источников | Конфигуратор источников данных | Реализовать интерфейс ввода параметров источников | streaming | 20 |
| Настройка источников | Конфигуратор источников данных | Сделать поддержку 3 типов камер: RTSP, UDP, GenICam | streaming | 20 |
| Настройка источников | Конфигуратор источников данных | Интегрировать проверку доступности источников | streaming | 16 |
| Валидация данных | Валидатор данных | Разработать схему описания источников | ml | 16 |
| Валидация данных | Валидатор данных | Реализовать проверку структуры и типов данных | ml | 20 |
| Валидация данных | Валидатор данных | Добавить отчёт об ошибках валидации | ml | 12 |
| Организация памяти | Общая память | Разработать структуру буфера для хранения кадров | streaming | 20 |
| Организация памяти | Общая память | Добавить механизмы блокировок и синхронизации | streaming | 16 |
| Организация памяти | Общая память | Реализовать тестовый прототип параллельного чтения | test | 16 |
| Сетевое взаимодействие | API-шлюз | Реализовать REST-интерфейс регистрации источников | streaming | 16 |
| Сетевое взаимодействие | API-шлюз | Добавить поддержку WebSocket для мониторинга | streaming | 20 |
| Обработка запросов | Сервер обработки запросов по API | Организовать очередь сообщений через брокер | streaming | 16 |
| Обработка запросов | Сервер обработки запросов по API | Интегрировать API-шлюз с логикой видеозахвата | streaming | 20 |
| Захват видео | Библиотека алгоритмов видеозахвата | Имплементация RTSP-захвата | streaming | 16 |
| Захват видео | Библиотека алгоритмов видеозахвата | Имплементация GenICam-потока | streaming | 20 |
| Захват видео | Библиотека алгоритмов видеозахвата | Тестовая запись потока в память | test | 16 |
| Обнаружение объектов | Библиотека детекции объектов | Добавиление онлайн-фильтр движения | ml | 20 |
| Обнаружение объектов | Библиотека детекции объектов | Интеграция YOLOv11/RT модель | ml | 24 |
| Обнаружение объектов | Библиотека детекции объектов | Тестирование стабильность фильтра | test | 12 |
| Демонстрация работы | Примеры использования | Написать 3 демонстрационных скрипта запуска | test | 12 |
| Тестирование | Инструмент тестирования и оценки | Подготовить модульные тесты API | test | 16 |
| Тестирование | Инструмент тестирования и оценки | Проверка работоспособности потоков | test | 16 |
| Работа с конфигурациями | База данных | Схема хранения: источники, сессии, ошибки | ml | 16 |
| Работа с конфигурациями | База данных | Настроить PostgreSQL + SQLAlchemy модели | ml | 20 |

## 📊 Диаграмма: задачи по ролям (2025)

```mermaid
gantt
    title Распределение задач по ролям (2025)
    dateFormat  YYYY-MM-DD
    axisFormat  %b %Y
    section STREAMING
    Реализовать интерфейс ввода параметров источн :task0, 2025-01-13, 2025-01-18
    Сделать поддержку 3 типов камер RTSP, UDP, G :task1, 2025-01-19, 2025-01-24
    Интегрировать проверку доступности источников :task2, 2025-01-25, 2025-01-29
    Разработать структуру буфера для хранения кад :task6, 2025-02-14, 2025-02-19
    Добавить механизмы блокировок и синхронизации :task7, 2025-02-20, 2025-02-24
    Реализовать REST-интерфейс регистрации источн :task9, 2025-03-02, 2025-03-06
    Добавить поддержку WebSocket для мониторинга :task10, 2025-03-07, 2025-03-12
    Организовать очередь сообщений через брокер :task11, 2025-03-13, 2025-03-17
    Интегрировать API-шлюз с логикой видеозахвата :task12, 2025-03-18, 2025-03-23
    Имплементировать RTSP-захват :task13, 2025-03-24, 2025-03-28
    Имплементировать GenICam-поток :task14, 2025-03-29, 2025-04-03
    section ML
    Разработать схему описания источников :task3, 2025-01-30, 2025-02-03
    Реализовать проверку структуры и типов данных :task4, 2025-02-04, 2025-02-09
    Добавить отчёт об ошибках валидации :task5, 2025-02-10, 2025-02-13
    Добавить онлайн-фильтр движения :task16, 2025-04-09, 2025-04-14
    Интеграция YOLOv5/RT модель :task17, 2025-04-15, 2025-04-21
    Схема хранения источники, сессии, ошибки :task22, 2025-05-10, 2025-05-14
    Настроить PostgreSQL + SQLAlchemy модели :task23, 2025-05-15, 2025-05-20
    section TEST
    Реализовать тестовый прототип параллельного ч :task8, 2025-02-25, 2025-03-01
    Тестовая запись потока в память :task15, 2025-04-04, 2025-04-08
    Тестировать стабильность фильтра :task18, 2025-04-22, 2025-04-25
    Написать 3 демонстрационных скрипта запуска :task19, 2025-04-26, 2025-04-29
    Подготовить модульные тесты API :task20, 2025-04-30, 2025-05-04
    Проверка работоспособности потоков :task21, 2025-05-05, 2025-05-09
    section КОНТРОЛЬ
    API-прототип :milestone0, 2025-01-15, 0d
    section КОНТРОЛЬ
    Захват и фильтрация :milestone1, 2025-04-15, 0d
    section КОНТРОЛЬ
    Интеграция и конфигурации :milestone2, 2025-07-15, 0d
    section КОНТРОЛЬ
    Финальные тесты :milestone3, 2025-10-15, 0d
```
