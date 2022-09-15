![yamdb_final event parameter](https://github.com/whodef/yamdb_final/actions/workflows/yamdb_workflow.yml/badge.svg?event=push)

# Проект YaMDb

Сервис YaMDb — база отзывов о фильмах, книгах и музыке.

Это совместный проект и настоящая командная работа трёх студентов на Яндекс.Практикум, с применением Docker и DockerHub.

### Настроен CI/CD

Запуск Flake8 и тестов, обновление образа DockerHub, деплой на сервер.

Address: `159.223.208.222`

## Описание проекта

API для сервиса YaMDb.

**Отзывы**: получить список всех отзывов, создать новый отзыв, получить отзыв по id, частично обновить отзыв по id, удалить отзыв по id.

**Комментарии к отзывам**: получить список всех комментариев к отзыву по id, создать новый комментарий для отзыва, получить комментарий для отзыва по id, частично обновить комментарий к отзыву по id, удалить комментарий к отзыву по id.

**JWT-токен**: отправить confirmation_code на переданный email, получение JWT-токена в обмен на email и confirmation_code.

**Пользователи**: получить список всех пользователей, создание пользователя, получить пользователя по username, изменить данные пользователя по username, удалить пользователя по username, получить данные своей учетной записи, изменить данные своей учетной записи.

**Категории (типы) произведений**: получить список всех категорий, создать категорию, удалить категорию.

**Категории жанров**: получить список всех жанров, создать жанр, удалить жанр.

**Произведения, к которым пишут отзывы**: получить список всех объектов, создать произведение для отзывов, информация об объекте, обновить информацию об объекте, удалить произведение.


### Полная документация API по эндпоинту `/redoc/`


## Как запустить проект

Клонировать репозиторий и перейти в него в командной строке:

```
git clone https://github.com/whodef/api_yamdb.git

```

```
cd api_yamdb
```

Создать в директории infra_sp2\infra файл `.env` с параметрами:

```
DB_ENGINE=django.db.backends.postgresql
DB_NAME=postgres
POSTGRES_USER=postgres
POSTGRES_PASSWORD=postgres
DB_HOST=db
DB_PORT=5432

ALLOWED_HOSTS=localhost, 127.0.0.1, web, 127.0.0.1:8000, localhost:8000, web:8000
SECRET_KEY=<KEY>
```

Создать и активировать виртуальное окружение:

```
python3 -m venv env
```

```
source env/bin/activate
```

Установить зависимости из файла requirements.txt:

```
python3 -m pip install --upgrade pip
```

```
pip install -r requirements.txt
```

Выполнить миграции:

```
python3 manage.py migrate
```

Запустить проект:

```
python3 manage.py runserver
```


## Запуск проекта в Doker

Запустите docker-compose:

```
docker-compose up -d --build
```

Соберите файлы статики, и запустите миграции командами:

```
docker-compose exec web python manage.py makemigrations
docker-compose exec web python manage.py migrate
docker-compose exec web python manage.py collectstatic --no-input
```

Создайте суперпользователя командой:

```
docker-compose exec web python manage.py createsuperuser
```

Команда по загрузке файла fixtures в БД
```
docker-compose exec web python manage.py dumpdata > fixtures.json
```

Остановить можно командой:

```
docker-compose down -v
```

Также вместе с проектом лежат предварительно созданные фикстуры с тестовыми данными Загрузить фикстуры можно командой:

```
docker-compose exec web python manage.py loaddata fixtures.json
```

## Авторы

[Татьяна Селюк](https://github.com/whodef) - управление пользователями (Auth и Users): система регистрации и аутентификации, права доступа, работа с токеном, система подтверждения e-mail, поля.

### Над проектом так же трудились на прошлом спринте:

[Максим Чен](https://github.com/on1y4fun) - категории (Categories), жанры (Genres) и произведения (Titles): модели, view и эндпойнты для них.

[Сергей Волков](https://github.com/Svolkov-nsk) - отзывы (Review) и комментарии (Comments): модели и view, эндпойнты, права доступа для запросов. Рейтинги произведений.
