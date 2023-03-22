![example workflow](https://github.com/SofiyaBochina/yamdb_final/actions/workflows/yamdb_workflow.yml/badge.svg)
# YaMDB API в контейнере
Учебный  проект "YaMDB API в контейнере".

## Шаблон наполнения env-файла
```
SECRET_KEY =
DEBUG =
DB_ENGINE=
DB_NAME=
POSTGRES_USER=
POSTGRES_PASSWORD=
DB_HOST=
DB_PORT=
```
## Как запустить проект:

В командной строке клонируйте проект в нужную папку:
```
git clone https://github.com/SofiyaBochina/yamdb_final
```
Перейдите в директорию infra в проекте:
```
cd yamdb_final
cd infra
```
Запустите docker-compose:
```
docker-compose up -d
```
Выполните миграции:
```
docker-compose exec web python manage.py migrate auth
docker-compose exec web python manage.py migrate —fake-initial —run-syncdb
```
Соберите статические файлы:
```
docker-compose exec web python manage.py collectstatic --no-input
```
## Как заполнить базу данными
Создайте суперпользователя:
```
docker-compose exec web python manage.py createsuperuser
```
После этого вы сможете добавлять новые объекты в базу данных через админку проекта по адресу http://localhost/admin.

## Документация
Проект в данный момент доступен по айпи 51.250.105.18. Документацию можно просмотреть по адресу http://51.250.105.18/redoc.
