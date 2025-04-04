# 🧪 Пример шаблонного пайплайна (обучение / инференс)

---

## 📊 Диаграмма (mermaid)

```mermaid
flowchart TD
  input[📥 Input - uploads / API / user] --> filter[🔍 Filter - selector]
  filter --> q1[🎯 Цель]
  q1 --> q2[📚 Задача]
  q2 --> q3[🔁 Сравнение]
  q3 --> q4[✅ Критерий]
  q4 --> selector[🧩 Selector - template or project]
  selector --> kb[🧠 Knowledge Base - template]
  kb --> test[🧪 Validate and Test]
  test --> generator[⚙️ Generator - builder]
  generator --> workspace[📂 Workspace - runtime]
  generator --> storage[🗄 Storage - permanent]
  generator --> bus[🔔 Bus - events]
  workspace --> ci[🚀 CI or CD]
  ci --> monitor[📊 Monitoring]
  ci --> downloads[📤 Output - download or git]
```
flowchart TD
  input[📥 Input (uploads, API, user)] --> filter[🔍 Filter / Selector]
  filter --> q1{🎯 Цель?}
  q1 --> q2{📚 Задача?}
  q2 --> q3{🔁 Сравнение с чем?}
  q3 --> q4{✅ Критерий оценки?}
  q4 --> selector[🧩 Selector (Template/Project)]
  selector --> kb[🧠 Knowledge Base (template)]
  kb --> test[🧪 Validate/Test template]
  test --> generator[⚙️ Generator: Project Builder]
  generator --> workspace[📂 Workspace (runtime)]
  generator --> storage[🗄 Storage (long-term)]
  generator --> bus[🔔 Bus (events)]
  workspace --> ci[🚀 CI/CD]
  ci --> monitor[📊 Мониторинг]
  ci --> downloads[📤 Downloads / Git / Artifact]
```

---

## 🗺️ Легенда к диаграмме

- **📥 Input** — точка входа данных (загрузки, API, пользовательские формы)
- **🔍 Filter** — выбор области применения и фильтрация по задаче
- **🎯 Цель, 📚 Задача, 🔁 Сравнение, ✅ Критерий** — четыре вопроса, определяющие мета-шаблон
- **🧩 Selector** — выбор шаблона / проекта на основе ответов
- **🧠 Knowledge Base** — база знаний, где хранятся шаблоны пайплайнов
- **🧪 Validate/Test** — проверка шаблона перед генерацией
- **⚙️ Generator** — сборка проекта по шаблону
- **📂 Workspace / 🗄 Storage** — временное и постоянное хранилище
- **🔔 Bus** — уведомления об изменениях / событиях
- **🚀 CI/CD** — автоматическая сборка / деплой
- **📊 Мониторинг** — отслеживание процесса
- **📤 Downloads / Git / Artifact** — точки выгрузки результата

---

## 🧾 Meta User Story

**Как пользователь**,  
я хочу **задать 4 ключевых вопроса**  
(цель, задача, сравнение, критерий),  
чтобы **найти и адаптировать подходящий шаблон пайплайна**,  
сохранить его в базе знаний как `template`,  
протестировать и использовать для **генерации проектов**.

---

## 📌 Конкретная реализация (пример)

**Как ML-разработчик**,  
я хочу создать пайплайн для **обучения модели классификации изображений**,  
сравнивая её с предыдущей версией на метрике `accuracy`,  
чтобы обеспечить **улучшение точности** в продакшене.

### Ответы пользователя:
- 🎯 Цель: обучить новую модель
- 📚 Задача: классификация изображений
- 🔁 Сравнение: предыдущая версия модели v1.2
- ✅ Критерий: accuracy > 0.92

### Действия платформы:
- предлагает шаблон пайплайна `ml_image_classifier_pipeline`
- сохраняет его в `knowledge_base` как `template`
- проводит валидацию шаблона
- генерирует кастомный проект с учётом параметров
- запускает CI/CD
- выгружает артефакт модели в `/downloads`

---
