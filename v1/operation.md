## Операции
operation.js

[Главная](README.md)  /  [Manufacturing Execution System](mes.md)

### Получение списка операций

Для получения списка операций необходимо отправить **`GET`** запрос на **`/api/operation`**<br>

Пример ответа:<br>
```
[
    {
        "_id": "61936f89c03b9f58b55abf5c",
        "name": "Assembly",
        "worker_count": 3
    },
    {
        "_id": "61936f09c03b9f58b55abf5a",
        "name": "Stitch",
        "worker_count": 2
    },
    {
        "_id": "61936cc3c03b9f58b55abf58",
        "name": "Sew",
        "worker_count": 2
    },
    {
        "_id": "61785096cb30bb6aa7dc2022",
        "name": "Quality control",
        "worker_count": 2
    }
]
```

<br>

### Получение списка операций для группы

Для получения списка клиентов необходимо отправить **`GET`** запрос на **`/api/operation_group/:g_id`**<br>

Пример ответа:<br>
```
[
     {
        "_id": "5cbc398f5e42968e114d6319",
        "name": "Крой",
        "description": "Подбор лекал, по данным из заказа и раскройка материалов",
        "sort": [
            {
                "_id": "617940cecb30bb6aa7dc2079",
                "": ""
            }
        ]
    },
    {
        "_id": "5cbc39755e42968e114d6318",
        "name": "Стежка",
        "description": "Подбор лекал, по данным из заказа и раскройка материалов",
        "sort": []
    },
    {
        "_id": "5cbc39755e42968e114d6317",
        "name": "Пошив",
        "description": "",
        "sort": []
    }
]
```

Параметры:<br>
**g_id*** - Идентификатор группы<br>

<br>

### Получение операции

Для получения операции необходимо отправить **`GET`** запрос на **`/api/operation_info/:id`**<br>

Пример ответа:<br>
```
[
    {
        "_id": "5d61a101abf1fe315164d29c",
        "og_id": "5ceee8e102736acec4e97f25",
        "sort": {
            "_id": "5e3943d3cc05cd1955698426",
            "Марка": 1,
            "Модель": 1
        },
        "name": "Тестирование продукта",
        "description": "Тестирование продукта",
    }
]
```

Параметры:<br>
**id*** - Идентификатор операции<br>

<br>

### Создание операции

Для создания операции необходимо отправить **`POST`** запрос на **`/api/operation`**<br>

Пример отправки параметров:<br>
```
{
	"_id": "5d5a556d52aa910e046fc9dc",
	"g_id": "5cbc39755e42968e114d6318",
	"name": "Упаковка",
	"description": "Упаковка",
	"sort": 
        {
        "sort\uFF0EМарка": 1,
        "sort\uFF0EПоколение вашего автомобиля": 1
        }
}
```

Параметры:<br>
**g_id*** - Идентификатор группы новой операции<br>
**name*** - Имя операции<br>
**description** - Описание операции<br>
**sort** - Сортировка для операции. "1" - прямая сортировка (ставится по умолчанию), "0" - сортировка отсутствует, "-1" - обратная сортировка<br>
**deskbook*** - id справочника<br>

Ответ:<br> коды состояний 204 или 404.

<br>

### Редактирование операции

Для редактирования операции необходимо отправить **`PUT`** запрос на **`/api/operation`**<br>

Пример отправки параметров:<br>
```
{
	"_id": "5d5a556d52aa910e046fc9dc",
	"og_id": "5cbc39755e42968e114d6318",
	"name": "Упаковка",
	"description": "Упаковка",
	"sort": 
        {
        "sort\uFF0EМарка": 1,
        "sort\uFF0EПоколение вашего автомобиля": 1
        }
}
```

Параметры:<br>
**og_id*** - Идентификатор группы новой операции<br>
**name*** - Имя операции<br>
**description** - Описание операции<br>
**sort** - Сортировка для операции. Если сортировка по времени поступления, то отправляем "sort":[]. "1" - прямая сортировка (ставится по умолчанию), "0" - сортировка отсутствует, "-1" - обратная сортировка<br>
**deskbook*** - id справочника<br>

Ответ:<br> коды состояний 204 или 404.

<br>

### Получение списка справочников

Для получения списка справочников необходимо отправить **`GET`** запрос на **`/operation_deskbook`**<br>

Пример ответа:<br>
```
[
    {
        "_id": "5cbc398f5e42968e114d6319",
        "name": "Раскройка"
    },
    {
        "_id": "5cbc39755e42968e114d6318",
        "name": "Вышивка ромбов"
    }
]
```

<br>

### Удаление операции

Для удаления операции необходимо отправить **`DELETE`** запрос на **`/api/operation/:id`**<br>

Параметры:<br>
**id*** - Идентификатор операции<br>

Ответ:<br> коды состояний 204 или 404.

<br>

### Получение количества сотрудников для операции

Для получения количества сотрудников для операции необходимо отправить **`GET`** запрос на **`/operation_worker_count/:id`**<br>

Пример ответа:<br>
```
[
    {
        "_id": "5cbc398f5e42968e114d6319",
        "worker_count": 4
    }
]
```

Параметры:<br>
**id*** - Идентификатор операции<br>

<br>
