---
title: API Reference

language_tabs: # must be one of https://github.com/rouge-ruby/rouge/wiki/List-of-supported-languages-and-lexers
  - shell

includes:
  - errors

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
curl "http://example.com/api/kittens" \
  -H "Authorization: meowmeowmeow"
```

> Результат

```json
{
  "error": false,
  "data: [
    "email:pass",
    "email:pass"
  ]
}
```

Метод выполняет покупку почт.

### HTTP Request

`GET https://d33pmail.com/api/v1/email`

### Query параметры

Параметр | Обязательный | Описание
--------- | ------- | -----------
count | Да | Указывает количество почт к покупке (от 1 до 2000)

## Get a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get(2)
```

```shell
curl "http://example.com/api/kittens/2" \
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.get(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Max",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint retrieves a specific kitten.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to retrieve

## Delete a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.delete(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.delete(2)
```

```shell
curl "http://example.com/api/kittens/2" \
  -X DELETE \
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.delete(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ":("
}
```

This endpoint deletes a specific kitten.

### HTTP Request

`DELETE http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to delete

