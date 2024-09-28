---
title: API Reference

language_tabs: # must be one of https://github.com/rouge-ruby/rouge/wiki/List-of-supported-languages-and-lexers
  - shell

includes:

search: true

code_clipboard: true

meta:
  - name: description
    content: d33pmail API Documentation
---

# Вступление

Добро пожаловать в документацию API d33pmail! Здесь вы сможете найти достпные методы для работы с почтой и системой в целом.

# Авторизация

> Все методы API защищены авторизацией через API ключ, детальнее:

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here" \
  -H "x-api-key: api_key"
```

> Убедитесь, что заменили `api_key` вашим API ключом.

Для получения API ключа откройте [бота Telegram](https://t.me/d33pmail_bot), перейдите в профиль и скопируйте содержимое в поле "API ключ".

# Почтовое API

## Купить почту

```shell
curl --location 'https://d33pmail.com/api/v2/email?count=2' \
--header 'x-api-key: api_key'
```

> Результат

```json
{
  "error": false,
  "data": [
    "email:pass",
    "email:pass"
  ]
}
```

Метод выполняет покупку почт.

### HTTP Запрос

`GET https://d33pmail.com/api/v2/email`

### Query параметры

Параметр | Обязательный | Описание
--------- | ------- | -----------
count | Да | Указывает количество почт к покупке (от 1 до 2000)

## Получить список почтовых ящиков

```shell
curl --location 'https://d33pmail.com/api/v2/email/boxes' \
--header 'x-api-key: api_key' \
--header 'Content-Type: application/json' \
--data '{
    "email": "",
    "password": ""
}'
```

> Результат

```json
{
  "error": false,
  "data": [
    {
      "name": "INBOX"
    }
  ]
}
```

Метод выполняет получение почтовых ящиков на указанном почтовом адресе.

### HTTP Запрос

`POST https://d33pmail.com/api/v2/email/boxes`

### Тело запроса

Параметр | Обязательный | Описание
--------- | ------- | -----------
email | Да | Электронный адрес
password | Да | Пароль от электронного адреса

## Получить список писем в ящике

```shell
curl --location 'https://d33pmail.com/api/v2/email/messages' \
--header 'x-api-key: api_key' \
--header 'Content-Type: application/json' \
--data '{
    "email": "",
    "password": "",
    "box": "",
    "page": 1
}'
```

> Результат

```json
{
  "error": false,
  "data": [
    {
      "from": "test@gmail.com",
      "subject": "Greeting",
      "html": "<div>Hello!</div>",
      "text": "Hello!",
      "date": ""
    }
  ]
}
```

Метод выполняет получение писем из почтового ящика, который вы указали в теле запроса

### HTTP Запрос

`POST https://d33pmail.com/api/v2/email/messages`

### Тело запроса

Параметр | Обязательный | Описание
--------- | ------- | -----------
email | Да | Электронный адрес
password | Да | Пароль от электронного адреса
box | Да | Почтовый ящик
page | Да | Страница

# Пользовательское API

## Информация о пользователе

```shell
curl --location 'https://d33pmail.com/api/v1/user/me' \
--header 'x-api-key: api_key'
```

> Результат

```json
{
  "error": false,
  "data": {
    "balance": 200.00,
    "id": 12
  }
}
```

Метод возвращает информацию о владельце API токена, а так же его баланс.

### HTTP Запрос

`GET https://d33pmail.com/api/v1/user/me`
