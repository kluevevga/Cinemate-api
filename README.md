# Cinemate-api

<br/>

## Стек проекта

[![Python](https://img.shields.io/badge/python-3.10-blue.svg?style=for-the-badge&logo=python)](https://www.python.org/)
[![Django](https://img.shields.io/badge/django-4.2.3-blue.svg?style=for-the-badge&logo=django)](https://www.djangoproject.com/)
[![Django REST framework](https://img.shields.io/badge/django_rest_framework-3.14.0-blue.svg?style=for-the-badge&logo=django)](https://www.django-rest-framework.org/)
[![Pillow](https://img.shields.io/badge/Pillow-10.0.0-blue.svg?style=for-the-badge)](https://pypi.org/project/Pillow/)
[![django-ckeditor](https://img.shields.io/badge/django--ckeditor-6.1.1-blue.svg?style=for-the-badge)](https://pypi.org/project/django-ckeditor/)
[![psycopg2-binary](https://img.shields.io/badge/psycopg2--binary-2.9.6-blue.svg?style=for-the-badge)](https://pypi.org/project/psycopg2-binary/)
[![django-filter](https://img.shields.io/badge/django--filter-23.2-blue.svg?style=for-the-badge)](https://pypi.org/project/django-filter/)
[![djoser](https://img.shields.io/badge/djoser-2.2.0-blue.svg?style=for-the-badge)](https://pypi.org/project/djoser/)
[![djangorestframework-simplejwt](https://img.shields.io/badge/djangorestframework--simplejwt-5.2.2-blue.svg?style=for-the-badge)](https://pypi.org/project/djangorestframework-simplejwt/)
[![drf-yasg](https://img.shields.io/badge/drf--yasg-1.21.6-blue.svg?style=for-the-badge)](https://pypi.org/project/drf-yasg/)
[![django-rest-framework-social-oauth2](https://img.shields.io/badge/django--rest--framework--social--oauth2-1.1.0-blue.svg?style=for-the-badge)](https://pypi.org/project/django-rest-framework-social-oauth2/)
[![django-cors-headers](https://img.shields.io/badge/django--cors--headers-4.2.0-blue.svg?style=for-the-badge)](https://pypi.org/project/django-cors-headers/)
[![Лицензия](https://img.shields.io/github/license/kluevevga/Cinemate-api?color=blue&style=for-the-badge&logo=github)](https://github.com/kluevevga/Cinemate-api/blob/master/LICENSE)
[![Размер кода](https://img.shields.io/github/languages/code-size/kluevevga/Cinemate-api?style=for-the-badge&logo=github)](https://github.com/kluevevga/Cinemate-api)

## О проекте

REST API backend сервис для управления фильмами и отзывами. Этот проект является частью приложения "movies" и расширяет
его функциональность.

Основные особенности проекта:

- Использует базу данных PostgreSQL для хранения данных.
- Разработан с использованием фреймворка Django REST framework.
- Реализована аутентификация с использованием JWT токенов для обеспечения безопасности.
- Поддерживает рекурсивное отображение отзывов, что позволяет удобно структурировать обратные связи.
- Система сохраняет IP-адреса отправителей отзывов, что полезно для отслеживания и анализа активности пользователей.

Также в репозитории проекта находится копия тестовой базы данных в файле "movies.postgres.bak", что упрощает
развертывание и восстановление данных при необходимости.

## Установка

Для начала, склонируйте проект на свой компьютер:

```shell
git clone https://github.com/kluevevga/Cinemate-api.git
```

Перейдите в папку с проектом:

```shell
cd Cinemate-api
```

После этого, создайте виртуальное окружение:

```shell
python3 -m venv env
```

Активируйте виртуальное окружение:

Для Windows(power shell):

```shell
.\venv\Scripts\activate
```

Для macOS и Linux и windows(git bash):

```shell
source env/bin/activate
```

Установите зависимости, необходимые для проекта:

```shell
pip install -r requirements.txt
```

## Запуск development сервера

Выполните миграции для базы данных:

```shell
python manage.py migrate
```

Запустите сервер:

```shell
python manage.py runserver
```

## End-points documentation

После установки сервера документация доступна по адресу:

```
swagger/
```

```
redoc/
```

## База Данных

1. Категории

```
1. имя - Char
2. описание - Text
3. url - Slug
```

2. Фильмы

```
1. название - Char
2. слоган - Char
3. описание - Text
4. постер - Image
5. год - Date
6. страна - Char
7. режиссер - M2M
8. актеры - M2M
9. жанр - M2M
10. премьера в мире - Char
11. бюджет - Char
12. сборы в США - Char
13. сборы в мире - Char
14. категория - FK 
15. url - Slug
16. черновик - Bool
```

3. Кадры из фильма

```
1. название - Char
2. описание - Text
3. изображение - Image
4. фильм - FK
```

4. Режиссеры\\Актеры

```
1. имя - Char
2. возраст - Int
3. описание - Text
4. изображение - Image
```

5. Звезды рейтинга

```
1. значение - Int
```

6. рейтинг

```
1. ip - IP
2. звезда - FK
3. фильм - FK
```

7. отзывы

```
1. email - Email
2. name - Char
3. text - Text
4. родитель (кому ответили)
5. фильм - FK

```

8. Жанры

```
1. имя - Char
2. описание - Text
3. url - Slug
```

## Схемма базы данных

![Scheme](database-scheme.png)

## Лицензия 📜

Этот проект распространяется под лицензией `MIT`. Дополнительную информацию можно найти
в [LICENSE](https://github.com/kluevevga/Cinemate-api/blob/master/LICENSE).