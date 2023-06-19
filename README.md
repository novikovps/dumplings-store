# Dumpling store (Учебный проект)
Dumpling-store - это онлайн-сервис для заказа пельменей.
> `Обращаю внимание, что CI/CD написан для Gitlab.`

Демо-версия сервиса доступна, развёрнутого по инструкции из [инфраструктурного репозитория] доступна по ссылке: [пельменная]


## Технологический стек

| Name          |  Version  |
| ----          |  -------  |
|CI/CD| Gitlab Enterprise Edition 15.3.1-ee |
| **Backend**       |           |
| Language      | go 1.17   |
| Build image   |golang:1.20.3-alpine|
| Prod image   |gcr.io/distroless/base-debian11:latest|
| **Frontend**       |           |
| Language      | js (vue)   |
| Build image   |node:16.0-alpine|
| Prod image   |nginx:1.21.3-alpine|
|           |           |
| **Tests**         | sonarcube CE 8.9.2  |


## Репозиторий
Репозиторий делится на две основных ветки: main и dev.
Вся разработка ведётся в ветке dev, изменения вливаются в main.
Тегирование образа меткой latest и последующий deploy происходит только после ручного запуска job в pipeline.

## Сборка
### Backend
```
CGO_ENABLED=0 GOOS=linux go build ./cmd/api
```
### Frontend
```
npm install
npm run build
```
## Инфраструктура проекта
Информацию по инфраструктурным компонентам и инструкции по развёртыванию можно найти в [инфраструктурном репозитории]


[инфраструктурном репозитории]: <https://github.com/novikovps/ds-infra>
[инфраструктурного репозитория]: <https://github.com/novikovps/ds-infra>
[пельменная]: <https://dumplings-store.notforprod.ru/>