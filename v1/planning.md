## Планирование
planning.js

[Главная](README.md)  /  [Manufacturing Execution System](mes.md)

### Получение списка планирований

Для получения списка планирований необходимо отправить **`GET`** запрос на **`/api/planning/:g_id`**<br>

Пример ответа:<br>
```
[
    {
        "_id": "608abb6b60699007fac77f67",
        "name": "Новое планирование",
        "s_id": "5ea9e7ba0dece21b35dba64a",
        "stream_name": "Тест паралельных операций"
    },
    {
        "_id": "609b7d01fe1b3840e89a9ae0",
        "name": "Новое планирование 2",
        "s_id": "5ea9e7ba0dece21b35dba64a",
        "stream_name": "Тест паралельных операций"
    }
]
```

Параметры:<br>
**g_id*** - Идентификатор группы<br>

<br>

### Получение планирования

Для получения планирования необходимо отправить **`GET`** запрос на **`/api/planning_info/:_id`**<br>

Пример ответа:<br>
```
[
    {
        "_id": "608abb6b60699007fac77f67",
        "name": "Новое планирование",
        "s_id": "5ea9e7ba0dece21b35dba64a",
        "condition": [
            {
                "type": "material",
                "m_id": "5cf7abef4829431ec863a9d1",
                "condition": "gte",
                "value": 5
            },
            {
                "type": "material",
                "m_id": "5cf8128262eb21ed4ac7968f",
                "condition": "gte",
                "value": 4
            }
        ],
        "history": [
            {
                "date": "2021-05-18T16:00:00.000Z"
            }
        ]
    }
]
```

Параметры:<br>
**_id*** - Идентификатор планирования<br>

<br>

###  Получение заказов для планирования

Для получения заказов для планирования необходимо отправить **`GET`** запрос на **`/api/order_planning`**<br>

Пример ответа:<br>
```
[
    {
        "_id": "5e21b0bc7ef0d64448df7896",
        "p_id": "608abb6b60699007fac77f67",
        "name": "Audi 100 1990-1994"
    },
    {
        "_id": "5e21b0dd7ef0d64448df7897",
        "p_id": "608abb6b60699007fac77f67",
        "name": "BMW 5 1995-2000"
    },
    {
        "_id": "5e21b0ff7ef0d64448df7898",
        "name": "Chery Amulet 2003-2012"
    }
]
```

<br>

###  Получение потоков для планирования

Для получения потоков для планирования необходимо отправить **`GET`** запрос на **`/api/stream_planning`**<br>

Пример ответа:<br>
```
[
    {
        "_id": "5ea9e7ba0dece21b35dba64a",
        "name": "Тест паралельных операций"
    },
    {
        "_id": "5f72ee4709988855fb90d8f5",
        "name": "Тест комплект с двойной строчкой"
    },
    {
        "_id": "5f73278a762cd264ad20bb58",
        "name": "Тест комплект без двойной отстрочки"
    }
]
```

<br>

### Создание планирования

Для создания планирования необходимо отправить **`POST`** запрос на **`/api/planning`**<br>

Пример отправки параметров:<br>
```
{
   "name":"Новое планирование",
   "s_id":"5ea9e7ba0dece21b35dba64a",
   "condition":[
      {
         "type":"material",
         "m_id":"5cf7abef4829431ec863a9d1",
         "condition":"gte",
         "value":5
      },
      {
         "type":"material",
         "m_id":"5cf8128262eb21ed4ac7968f",
         "condition":"gt",
         "value":4
      }
   ]
}
```

Параметры:<br>
**name*** - Название планирования<br>
**s_id*** - Идентификатор потока по которому будут выполнятся выбранные заказы<br>
**type** - Тип данных для условия (по умолчанию всегда ставим "material")<br>
**m_id** - Идентификатор материала<br>
**condition*** - Условие выполнения операции "=" - "eq", "⩽" - "lte", "⩾" - "gte", "<" - "lt", ">" - "gt"<br>
**value*** - Значение с которым будем сравнивать<br>

Ответ:<br> коды состояний 204 или 404.

<br>

### Редактирование планирования

Для редактирования планирования необходимо отправить **`PUT`** запрос на **`/api/planning`**<br>

Пример отправки параметров:<br>
```
{
    "_id": "6108eed404e3e7482cfb9815",
    "name":"Новое планирование",
    "s_id":"5ea9e7ba0dece21b35dba64a",
    "condition":[
        {
            "type":"material",
            "m_id":"5cf7abef4829431ec863a9d1",
            "condition":"lte",
            "value":5,
            "material_name": "Нитки обычные (Жёлтый)"
        },
        {
            "type":"material",
            "m_id":"5cf8128262eb21ed4ac7968f",
            "condition":"gt",
            "value":4,
            "material_name": "Нитки для двойной отстрочки (Черный 901)"
        }
    ]
}
```

Параметры:<br>
**name*** - Название планирования<br>
**s_id*** - Идентификатор потока по которому будут выполнятся выбранные заказы<br>
**type** - Тип данных для условия (по умолчанию всегда ставим "material")<br>
**m_id** - Идентификатор материала<br>
**condition*** - Условие выполнения операции "=" - "eq", "⩽" - "lte", "⩾" - "gte", "<" - "lt", ">" - "gt"<br>
**value*** - Значение с которым будем сравнивать<br>

Ответ:<br> коды состояний 204 или 404.

<br>

### Добавление или удалиние планирования в заказе

Для редактирования планирования необходимо отправить **`PUT`** запрос на **`/api/order_planning`**<br>

Пример отправки параметров:<br>
```
{
    "_id": "5e21b0dd7ef0d64448df7897",
    "p_id": "608abb6b60699007fac77f62"
}
```

Параметры:<br>
**_id*** - Идентификатор заказа<br>
**p_id*** - Идентификатор планирования<br>

Ответ:<br> коды состояний 204 или 404.

<br>

### Удаление операции

Для удаления планирования необходимо отправить **`DELETE`** запрос на **`/api/planning/:_id`**<br>

Параметры:<br>
**_id*** - Идентификатор планирования<br>

Ответ:<br> коды состояний 204 или 404.

<br>

### Получение последовательности операций для заказа

Для получения последовательности операций для заказа необходимо отправить **`GET`** запрос на **`/api/order_operations/:_id`**<br>

Пример ответа:<br>
```
[
    {
        "_id": "62722d5453a18d6600067bfb",
        "operation": {
            "_id": "625c661fd286c349c9ea64ed",
            "g_id": "6256b3af9be5936347adca37",
            "name": "Melting and casting (for write-off)",
            "cost": "20",
            "sort": [],
            "description": "Melting and casting",
            "compliance_rate": "00:10:00"
        },
        "materials": [
            {
                "condition": "plus",
                "value": 10,
                "path": "Rough wheels.Rough wheel",
                "price": null
            }
        ],
        "equipment": [
            {
                "_id": "626152f8abcdd2752d22d733",
                "g_id": "625b0118d286c349c9ea645b",
                "name": "Zhenli ZLC-550T",
                "operation": [
                    {
                        "_id": "6262630036cb561e329f668d",
                        "status": true,
                        "o_id": "625c661fd286c349c9ea64ed"
                    }
                ],
                "specification": {
                    "Machine Type": "Cold Chamber Die Casting Machine",
                    "Core Components": "PLC, Gearbox, Pump",
                    "Min Thickness of Die Block (mm)": "350 mm"
                },
                "occupied": false
            },
            {
                "_id": "6262635036cb561e329f668e",
                "g_id": "625b0118d286c349c9ea645b",
                "name": "Zhenli ZLC-1300T",
                "operation": [
                    {
                        "_id": "6262635036cb561e329f668f",
                        "status": true,
                        "o_id": "625c661fd286c349c9ea64ed"
                    }
                ],
                "specification": {
                    "Machine Type": "Cold Chamber Die Casting Machine",
                    "Core Components": "PLC, Gearbox, Pump",
                    "Min Thickness of Die Block (mm)": "350 mm"
                },
                "occupied": false
            },
            {
                "_id": "6262636836cb561e329f6690",
                "g_id": "625b0118d286c349c9ea645b",
                "name": "Zhenli ZLC-1000T",
                "operation": [
                    {
                        "_id": "6262636836cb561e329f6691",
                        "status": true,
                        "o_id": "625c661fd286c349c9ea64ed"
                    }
                ],
                "specification": {
                    "Machine Type": "Cold Chamber Die Casting Machine",
                    "Core Components": "PLC, Gearbox, Pump",
                    "Min Thickness of Die Block (mm)": "350 mm"
                },
                "occupied": false
            },
            {
                "_id": "6262638736cb561e329f6692",
                "g_id": "625b0118d286c349c9ea645b",
                "name": "Zhenli ZLC-450T",
                "operation": [
                    {
                        "_id": "6262638736cb561e329f6693",
                        "status": true,
                        "o_id": "625c661fd286c349c9ea64ed"
                    }
                ],
                "specification": {
                    "Machine Type": "Cold Chamber Die Casting Machine",
                    "Core Components": "PLC, Gearbox, Pump",
                    "Min Thickness of Die Block (mm)": "350 mm"
                },
                "occupied": false
            },
            {
                "_id": "6262641136cb561e329f6694",
                "g_id": "625b0118d286c349c9ea645b",
                "name": "HM15-HM480",
                "operation": [
                    {
                        "_id": "6262641136cb561e329f6695",
                        "status": true,
                        "o_id": "625c661fd286c349c9ea64ed"
                    }
                ],
                "specification": {
                    "Machine Type": "Cold Chamber Die Casting Machine",
                    "Core Components": "PLC, Gearbox, Pump",
                    "Min Thickness of Die Block (mm)": "350 mm"
                },
                "occupied": false
            }
        ]
    },
    {
        "_id": "62722d5453a18d6600067bfb",
        "operation": {
            "_id": "625c669ad286c349c9ea64ef",
            "g_id": "6256b3af9be5936347adca37",
            "name": "Checking and machining (for write-off)",
            "cost": "10",
            "sort": [],
            "description": "Checking and machining",
            "compliance_rate": "00:30:00"
        },
        "materials": [
            {
                "condition": "plus",
                "value": 10,
                "path": "Machined wheels.Machined wheel",
                "price": null
            },
            {
                "condition": "minus",
                "value": 100,
                "path": "Paint.Paint",
                "price": null
            }
        ],
        "equipment": []
    },
    {
        "_id": "62722d5453a18d6600067bfb",
        "operation": {
            "_id": "625c665cd286c349c9ea64ee",
            "g_id": "6256b3af9be5936347adca37",
            "name": "Painting and packing (for write-off)",
            "cost": "10",
            "technical_maps": [],
            "sort": [],
            "compliance_rate": "00:20:00"
        },
        "materials": [
            {
                "condition": "plus",
                "value": 10,
                "path": "Wheels ready for shipping.Ready wheel",
                "price": null
            }
        ],
        "equipment": []
    }
]
```

Параметры:<br>
**_id*** - Идентификатор заказа<br>

<br>