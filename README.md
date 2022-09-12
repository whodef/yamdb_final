# Проект YaMDb

##### yamdb_final

![yamdb_final workflow](https://github.com/github/docs/actions/workflows/main.yml/badge.svg?event=push)

Сервис YaMDb — база отзывов о фильмах, книгах и музыке.

Это совместный проект и настоящая командная работа трёх студентов на Яндекс.Практикум


## Описание проекта

API для сервиса YaMDb.

**Отзывы**: получить список всех отзывов, создать новый отзыв, получить отзыв по id, частично обновить отзыв по id, удалить отзыв по id.

**Комментарии к отзывам**: получить список всех комментариев к отзыву по id, создать новый комментарий для отзыва, получить комментарий для отзыва по id, частично обновить комментарий к отзыву по id, удалить комментарий к отзыву по id.

**JWT-токен**: отправить confirmation_code на переданный email, получение JWT-токена в обмен на email и confirmation_code.

**Пользователи**: получить список всех пользователей, создание пользователя, получить пользователя по username, изменить данные пользователя по username, удалить пользователя по username, получить данные своей учетной записи, изменить данные своей учетной записи.

**Категории (типы) произведений**: получить список всех категорий, создать категорию, удалить категорию.

**Категории жанров**: получить список всех жанров, создать жанр, удалить жанр.

**Произведения, к которым пишут отзывы**: получить список всех объектов, создать произведение для отзывов, информация об объекте, обновить информацию об объекте, удалить произведение.


### Полная документация API 

по адресу `http://127.0.0.1:8000/redoc/`


## Как запустить проект

Клонировать репозиторий и перейти в него в командной строке:

```
git clone https://github.com/whodef/api_yamdb.git

```

```
cd api_yamdb
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

## Запуск тестов

Из корня проекта:

```
pytest
```


## Авторы

[Татьяна Селюк](https://github.com/whodef) - управление пользователями (Auth и Users): система регистрации и аутентификации, права доступа, работа с токеном, система подтверждения e-mail, поля.

[Максим Чен](https://github.com/on1y4fun) - категории (Categories), жанры (Genres) и произведения (Titles): модели, view и эндпойнты для них.

[Сергей Волков](https://github.com/Svolkov-nsk) - отзывы (Review) и комментарии (Comments): модели и view, эндпойнты, права доступа для запросов. Рейтинги произведений.


### Лицензия [MIT](https://opensource.org/licenses/MIT)