# yamdb_final

![example workflow](https://github.com/AndrejGurtovoj/yamdb_final/actions/workflows/yamdb_workflow.yml/badge.svg)
## Описание проекта
 Приложение YaMDb состоит из нескольких сервисов
 запущеные в разных, связанных контейнерах:
База Данных PostgreSQL Nginx и Gunicorn 
### Для реализации проекта используются: 
* Python 3.7 
* Django 2.2.16 
* Django REST Framework 3.12.4 
* gunicorn 20.0.4 
* psycopg2-binary==2.8.6 
* docker docker-compose 
### Запуск проекта:
Клонировать репозиторий 
* https://github.com/AndrejGurtovoj/yamdb_final.git 
* Для работы с Базой Данных в (yamdb_final/infra) создайте файл .env с переменными:
* DB_ENGINE=django.db.backends.<указываем, с какой БД работаем>
* DB_NAME=<Имя базы данных>
* POSTGRES_USER=<логин для подключения к базе данных>
* POSTGRES_PASSWORD=<пароль для подключения к БД>
* DB_HOST=<название сервиса (контейнера)>
* DB_PORT=<порт для подключения к БД> 
### Запустите контейнеры:
* docker-compose up -d
* Выполните миграции: docker-compose exec web python manage.py migrate
* Создайте суперюзера: docker-compose exec web python manage.py createsuperuser
* Подгрузите статику: docker-compose exec web python manage.py collectstatic --no-input
* Заполните базу данными: docker-compose exec web python manage.py loaddata fixtures.json