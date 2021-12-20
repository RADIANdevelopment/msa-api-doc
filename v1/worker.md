## Сотрудники
worker.js

[Главная](README.md)  /  [Документация по API](api.md)

### Получение списка сотрудников

Для получения списка сотрудников необходимо отправить **`GET`** запрос на **`/api/worker`**<br>

Пример ответа:<br>
```
[
    {
        "_id": "6196c543e60e7b7dd9d30585",
        "name": "Ivan Makarov"
    },
    {
        "_id": "6196c5efe60e7b7dd9d30587",
        "name": "Dmitry Lovagin"
    },
    {
        "_id": "6196c60ce60e7b7dd9d30589",
        "name": "Sergey Sobolev"
    }
]
```

<br>

### Получение списка сотрудников для группы

Для получения списка сотрудников для группы необходимо отправить **`GET`** запрос на **`/api/worker/:g_id`**<br>

Пример ответа:<br>
```
[
    {
        "_id": "5d60e7127c76c66d9a16a35b",
        "operation": [
            {
                "_id": "5cbc398f5e42968e114d6319",
                "name": "Крой"
            },
            {
                "_id": "5f759723762cd264ad20bc48",
                "name": "Докрой"
            }
        ],
        "g_id": "60e2a357a280d28560e318fd",
        "name": "Анжела Захарова",
        "qualification": 4,
        "at_work": true,
        "order_at_work": []
    },
    {
        "_id": "5d60e7357c76c66d9a16a35d",
        "operation": [
            {
                "_id": "5cbc398f5e42968e114d6319",
                "name": "Крой"
            },
            {
                "_id": "5f759723762cd264ad20bc48",
                "name": "Докрой"
            }
        ],
        "g_id": "60e2a357a280d28560e318fd",
        "name": "Мария Захаричева",
        "qualification": 4,
        "at_work": true,
        "order_at_work": []
    }
]
```

<br>

### Получение сотрудника

Для получения сотрудника необходимо отправить **`GET`** запрос на **`/api/worker_id/:id`**<br>

Пример ответа:<br>
```
[
    {
        "_id": "5ccbfe255a65c541f0614409",
        "wg_id": "5cbc71fd631c979c2c5b274a",
        "name": "Людмила Гурей",
        "operation": [
            "5cbc398f5e42968e114d6319"
        ],
        "dob": "1982-12-11T23:00:00.000Z",
        "gender": "female",
        "qualification": 3,
        "contacts": {
            "phone": "8 (927) 600 90 80",
            "email": "malkova@mail.ru",
            "adress": "г. Пенза ул. Ленина 98 кв. 27"
        },
        "filter": [
            {
                "params": "KIA Rio 2017-н.в.",
                "factor": 2
            },
            {
                "params": "Toyota RAV4 2013-2019",
                "factor": 2
            },
            {
                "params": "Hyundai Solaris 2011-2016",
                "factor": 2
            }
        ]
    }
]
```

Параметры:<br>
**id*** - Идентификатор сотрудника<br>

<br>

### Создание нового сотрудника

Для создания нового сотрудника необходимо отправить **`POST`** запрос на **`/api/worker`**<br>

Пример отправки параметров:<br>
```
{
    "g_id" : "5cbc71fd631c979c2c5b274a",
    "name":"Фадеев Руслан",
    "operation":
        [
        "5cbc398f5e42968e114d6319"
        ],

    "dob": "1982-12-11T23:00:00.000+00:00",
    "gender": "female",
    "qualification": 3,
    "contacts":
    {
        "phone":"8 (927) 600 90 80",
        "email":"malkova@mail.ru",
        "adress":"г. Пенза ул. Ленина 98 кв. 27"
    },
    "filter": [
        {
            "params": "KIA Rio 2017-н.в.",
            "factor": 2
        },
        {
            "params": "Toyota RAV4 2013-2019",
            "factor": 2
        },
        {
            "params": "Hyundai Solaris 2011-2016",
            "factor": 2
        }
    ],
    "login": "Ruslan",
    "password": "576005"
}
```

Параметры:<br>
**g_id*** - Идентификатор группы нового сотрудника<br>
**name*** - Имя сотрудника<br>
**operation*** - Массив идентификаторов операций сотрудника<br>
**dob** - Дата рождения<br>
**gender** - Пол<br>
**qualification*** - Квалификация<br>
**phone** - Телефон<br>
**email** - Электронная почта<br>
**login*** - Логин<br>
**password*** - Пароль<br>

Ответ:<br> коды состояний 204 или 404.

<br>

### Редактирование сотрудника

Для редактирования сотрудника необходимо отправить **`PUT`** запрос на **`/api/worker`**<br>

Пример отправки параметров:<br>
```
{
    "_id" : "5cefe47f67c6b0592078bf39",
    "g_id" : "5cbc71fd631c979c2c5b274a",
    "name":"Фадеев Руслан",
    "operation":
        [
        "5cbc398f5e42968e114d6319"
        ],

    "dob": "1982-12-11T23:00:00.000+00:00",
    "gender": "female",
    "qualification": 3,
    "contacts":
    {
        "phone":"8 (927) 600 90 80",
        "email":"malkova@mail.ru",
        "adress":"г. Пенза ул. Ленина 98 кв. 27"
    },    
    "filter": [
        {
            "params": "KIA Rio 2017-н.в.",
            "factor": 2
        },
        {
            "params": "Toyota RAV4 2013-2019",
            "factor": 2
        },
        {
            "params": "Hyundai Solaris 2011-2016",
            "factor": 2
        }
    ],
    "login": "Ruslan",
    "password": "576005"
}
```

Параметры:<br>
**_id*** - Идентификатор сотрудника<br>
**g_id*** - Идентификатор группы нового сотрудника<br>
**name*** - Имя сотрудника<br>
**operation*** - Массив идентификаторов операций сотрудника<br>
**dob** - Дата рождения<br>
**gender** - Пол<br>
**qualification*** - Квалификация<br>
**phone** - Телефон<br>
**email** - Электронная почта<br>
**login*** - Логин<br>
**password*** - Пароль<br>

Ответ:<br> коды состояний 204 или 404.

<br>

### Удаление сотрудника

Для удаления сотрудника необходимо отправить **`DELETE`** запрос на **`/api/worker/:id`**<br>

Параметры:<br>
**id*** - Идентификатор сотрудника<br>

Ответ:<br> коды состояний 204 или 404.
