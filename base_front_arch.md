# Архитектура: Базовое Angular-приложение с Docker и CI

## 🧭 TOGAF – Контекст архитектуры

```mermaid
graph TD
    user[User]
    fastapi[FastAPI API]
    docker_host[Docker Host]
    ci_cd[GitLab CI/CD]
    browser[Browser (Test Server)]
    repo[Git Repository]

    user --> fastapi
    fastapi --> docker_host
    docker_host --> repo
    repo --> ci_cd
    ci_cd --> docker_host
    docker_host --> browser
```

---

## 🏗 ODA – Структурная архитектура приложения

```mermaid
graph TD
    subgraph Application
        A1[Angular CLI Project Generator]
        A2[Custom Angular Base App]
        A3[Dockerfile + Compose]
        A4[Nginx Server]
    end

    subgraph Platform
        P1[Node.js Builder]
        P2[Docker Engine]
        P3[GitLab Runner]
    end

    subgraph Orchestration
        O1[GitLab Pipeline]
        O2[FastAPI Trigger]
    end

    O2 --> A1
    A1 --> A2
    A2 --> A3 --> A4
    A3 --> P1
    P1 --> P2
    P3 --> O1 --> P2
```

---

## 🔄 BPMN – Процесс создания, сборки и деплоя

```mermaid
graph TD
    start([Start]) --> gen[Generate Angular Project]
    gen --> cust[Customize App (Hello World)]
    cust --> build[NPM Install + Build]
    build --> docker[Build Docker Image]
    docker --> test[Test App]
    test --> deploy[Deploy with GitLab CI]
    deploy --> end([End])
```
