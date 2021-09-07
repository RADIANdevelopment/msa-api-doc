[Главная](README.md)
<br>
# Авторизация сотрудников
users.js

<br>

### Авторизация

Для авторизации необходимо отправить
**`POST`** запрос на **`/api/users/login`**<br>

Пример ответа:<br>
```
{
    "user": {
        "_id": "5ce3ef2fbedee15ea193c4de",
        "u_id": "5ccbfe9f5a65c541f061440b",
        "name": "selyanina",
        "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJuYW1lIjoiYmVsa2F6bDExMSIsImlkIjoiNWNlM2VmMmZiZWRlZTE1ZWExOTNjNGRlIiwiZXhwIjoxNTYzNzgwNzM3LCJpYXQiOjE1NTg1OTY3Mzd9.C_euxHfVcjOJFX5bbXLvuI8BKBhf2E60B5qvpVdHqeg"
    },
    "role": "worker"
}
```

Параметры передаются как json:<br>
```
{
  "user":
  {
   "name": "belkazl111",
   "password": "576005"
  }
}
```

В дальнейшем в хедере запросов передаем:<br>
**KEY:** **`Authorization`** 
**VALUE:** **`Token `** + **`eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJlbWFpbCI6ImJlbGthemxAZ21haWwuY29tIiwiaWQiOiI1Y2I0YmIzODE0ZTA5Mjg2ZDBkYjQ0ZGMiLCJleHAiOjE1NjA1MzI0MjYsImlhdCI6MTU1NTM0ODQyNn0.t4jKvmilElNhMXGukLZCtdE8rp_tKLwfQjnZIZcvCEU`**

Существует 4 типа пользователя со своими правами доступа:
1. administrator
2. manager
3. client
4. worker

**u_id** возвращает идентификатор пользователя системы
