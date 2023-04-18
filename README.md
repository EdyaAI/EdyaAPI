# EdyaAPI | edyarobot.ru

Для использования API необходимо иметь токен доступа. Токен можно получить, в личном кабинете. Все обращения к API должны иметь в заголовке токен  ```Authorization: Bearer <your_token>```

## Авторизация

### Авторизация по токену

```
URL: /api/auth

Метод: POST
```
Описание: Авторизация по токену.

Параметры запроса:
```
- token (обязательный) - уникальный токен доступа.
```
Пример запроса:
```
POST /api/auth HTTP/1.1
Content-Type: application/json

{
  "token": "your_token"
}
```

Пример ответа:
```
HTTP/1.1 200 OK
Content-Type: application/json

{
  "message": "Success"
}
```

---

## Генерация текста

```
URL: /api/text

Метод: POST
```
Описание: Генерация текста с помощью нейросети.

Параметры запроса:
```
- model (обязательный) - модель для генерации.
- temperature (необязательный) 
- messages (необязательный) - сообщения.
```
Пример запроса:
```
POST /api/text HTTP/1.1
Content-Type: application/json
Authorization: Bearer your_token

{
  "model": "gpt-4",
  "temperature": 0.6,
  "messages": [
    {
      "role": "system",
      "content": "text_ai"
    },
    {
      "role": "user",
      "content": "text_user"
    }
  ]
}
```

Пример ответа:
```
HTTP/1.1 200 OK
Content-Type: application/json

{
  "token": {
    "tokens used": 51,
    "total_token": 5132
  },
  "messages": [
    {
      "role": "system",
      "content": "text_ai"
    },
    {
      "role": "user",
      "content": "text_user"
    }
  ],
  "completion": "choice_ai_message"
}
```
---
## Генерация изображений
```
URL: /api/image

Метод: POST
```
Описание: Генерация изображений с помощью нейросети.

Параметры запроса:
```
- model (обязательный) - нейросеть для генерации.
- prompt (обязательный) - описание.
```
Пример запроса:
```
POST /api/image HTTP/1.1
Content-Type: application/json
Authorization: Bearer your_token

{
  "model": "kandinsky",
  "prompt": "planet"
}
```

Пример ответа:
```
HTTP/1.1 200 OK
Content-Type: image/png

{
  "token": {
    "tokens used": 51,
    "total_token": 5132
  },
  "image": {
    "url": "url_to_image_png"
  }
}
```
---
## Получение баланса пользователя
```
URL: /api/balance

Метод: GET
```
Описание: Получение баланса пользователя.

Параметры запроса: нет.

Пример запроса:
```
GET /api/balance HTTP/1.1
Authorization: Bearer your_token
```

Пример ответа:
```
HTTP/1.1 200 OK
Content-Type: application/json

{
  "tokens": 1000
}
```
---
## Проверка статуса сервера
```
URL: /api/ping

Метод: GET
```
Описание: Проверка статуса сервера.

Параметры запроса: нет.

Пример запроса:
```
GET /api/ping HTTP/1.1
```

Пример ответа:
```
HTTP/1.1 200 OK
Content-Type: application/json

"statuses": {
    "gpt": true,
    "kandinsky": true,
    "stable_diffusion": false
  }
```
