# Kittygram

![GitHub Actions](https://github.com/tvoeinferno/kittygram_final/actions/workflows/main.yml/badge.svg)

## Описание проекта

**Kittygram** — веб-приложение для публикации информации о котиках.

Пользователи могут:

* зарегистрироваться и авторизоваться;
* добавлять карточки своих питомцев;
* загружать фотографии котов;
* указывать достижения питомца;
* просматривать список опубликованных котиков.

Проект разделён на frontend и backend, работает в Docker-контейнерах и автоматически разворачивается на сервере с помощью GitHub Actions.

---

## Стек технологий

### Backend

* Python 3.12
* Django
* Django REST Framework
* Gunicorn
* PostgreSQL

### Frontend

* React

### Инфраструктура

* Docker
* Docker Compose
* Nginx
* GitHub Actions
* Docker Hub

---

## Структура проекта

```
backend/        Django REST API
frontend/       React-приложение
nginx/          Конфигурация Nginx
.github/        GitHub Actions
```

---

## Запуск проекта

### 1. Клонировать репозиторий

```bash
git clone https://github.com/tvoeinferno/kittygram_final.git

cd kittygram_final
```

---

### 2. Создать файл `.env`

Пример содержимого:

```env
POSTGRES_DB=kittygram
POSTGRES_USER=kittygram_user
POSTGRES_PASSWORD=kittygram_password

DB_HOST=db
DB_PORT=5432

SECRET_KEY=your_secret_key

DEBUG=False

ALLOWED_HOSTS=localhost,127.0.0.1,example.com
```

Описание переменных:

| Переменная        | Назначение                              |
| ----------------- | --------------------------------------- |
| POSTGRES_DB       | имя базы данных                         |
| POSTGRES_USER     | пользователь PostgreSQL                 |
| POSTGRES_PASSWORD | пароль PostgreSQL                       |
| DB_HOST           | адрес БД                                |
| DB_PORT           | порт PostgreSQL                         |
| SECRET_KEY        | секретный ключ Django                   |
| DEBUG             | режим разработки                        |
| ALLOWED_HOSTS     | список разрешённых хостов через запятую |

---

### 3. Запустить контейнеры

```bash
docker compose up -d
```

---

### 4. Выполнить миграции

```bash
docker compose exec backend python manage.py migrate
```

---

### 5. Собрать статические файлы

```bash
docker compose exec backend python manage.py collectstatic --noinput
```

---

После запуска приложение будет доступно по адресу:

```
http://localhost:9000
```

---

## CI/CD

При каждом push в ветку **main** автоматически выполняются:

* проверка кода flake8;
* запуск backend-тестов;
* запуск frontend-тестов;
* сборка Docker-образов;
* публикация образов в Docker Hub;
* деплой на сервер;
* выполнение миграций;
* сборка статических файлов;
* отправка уведомления в Telegram.

---

## Автор

Олег Евгеньевич

GitHub: https://github.com/tvoeinferno

