# 📘 OpenAPI спецификация платформы (v5.1)

## 📄 openapi-base.yaml

Базовая спецификация, подключается ко всем частям.

### Разделы:

- `openapi: 3.0.3`
- `info`: Название API, описание, версия
- `servers`: `http://localhost:8000`
- `components`:
  - `schemas`: общие сущности (`EntityId`, `BuildRequest`, и др.)
  - `parameters`: общие параметры (`type`, `filter`, `id`)
  - `responses`: стандартные ответы (`200`, `400`, `404`)
- `paths`:
  - `GET /server_version`
  - `GET /alive`
  - `POST /kb/dump`
  - `POST /kb/restore`
  - `GET /config/bus`
  - `GET /config/kb`

---

## 🧩 entity-api.yaml

### Назначение:

Работа с сущностями, типами, категориями и универсальными методами.

### Содержит:

- `$ref`: подключение к openapi-base.yaml
- `paths`:
  - `/select`
  - `/health/{type}`
  - `/validate/{type}`
  - `/import/{type}`
  - `/export/{type}`
  - `/objects`, `/objects/{id}`
  - `/items`, `/items/{id}`
  - `/types`, `/types/{name}`
  - Алиасы:
    - `/templates`, `/projects`, `/scripts`, `/pipelines`
    - `/environments`, `/resources`, `/test_plans`

---

## ⚙️ process-api.yaml

### Назначение:

Описывает все процессы жизненного цикла сущностей.

### Содержит:

- `$ref`: подключение к openapi-base.yaml
- `paths`:
  - `/init`
  - `/build`
  - `/ci/setup`
  - `/ci/run`
  - `/deploy`
  - `/validate/schema`
  - `/validate/logic`
  - `/test/unit`
  - `/test/integration`
  - `/doc/generate`