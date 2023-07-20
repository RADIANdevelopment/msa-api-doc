## Материалы
material.js

[Главная](README.md)  /  [Система управления производством](production.md)

### Получение материалов

Для получения списка материалов необходимо отправить **`GET`** запрос на **`/api/material/:g_id`**<br>

Пример ответа:<br>
```
[
    {
        "_id": "618e640bb05d2840612b4687",
        "g_id": "60a959e632a2dcd7f7ac8daf",
        "name": "Тестовый материал",
        "measure": "Метр квадратный",
        "description": "Нет описания"
    },
    {
        "_id": "618e65acb05d2840612b4689",
        "g_id": "60a959e632a2dcd7f7ac8daf",
        "name": "Тестовый материал",
        "measure": "сантиметры",
        "description": "нет описания"
    }
]
```

Параметры:<br>
**g_id*** - Идентификатор группы материалов<br>

<br>

### Получение материала

Для получения материала необходимо отправить **`GET`** запрос на **`/api/material_info/:id`**<br>

Пример ответа:<br>
```
[
    {
        "_id": "618e65acb05d2840612b4689",
        "g_id": "60a959e632a2dcd7f7ac8daf",
        "name": "Тестовый материал",
        "measure": "сантиметры",
        "description": "нет описания",
        "value": {
            "тест": "тест"
        }
    }
]
```

Параметры:<br>
**id*** - Идентификатор материала<br>

<br>

### Создание нового материала

Для создания нового материала необходимо отправить **`POST`** запрос на **`/api/material`**<br>

Пример отправки параметров:<br>
```
{
    "_id": "5cf6ebe496a76a6c5aadb18f",
    "g_id": "5d754a01b128da140c95eed8",
    "s_id": "64b2778599cb0e28a3f7df6d",
    "name": "Материал",
    "amount": "10",
    "description": "Описание материала"
    "measure": "л.",
    "value": {
            "supply": [
                {
                    "date": "2023-08-24T08:30:00.325Z",
                    "amount": 200
                }
            ]
        }
}
```

Параметры:<br>
**g_id** - Идентификатор группы редактируемого материала<br>
**s_id** - Идентификатор потока<br>
**name** - Имя материала<br>
**amount** - Текущий остаток материала<br>
**description** - Описание материала<br>
**measure** - Мера измерения<br>
**value** - Состав материала<br>
**value.supply** - График поставок материала<br>
**value.supply.date** - Дата поставки<br>
**value.supply.amount** - Количество поставки<br>

Ответ:<br> коды состояний 204 или 404.

<br>

### Редактирование материала

Для редактирования материала необходимо отправить **`PUT`** запрос на **`/api/material`**<br>

Пример отправки параметров:<br>
```
{
    "_id": "5cf6ebe496a76a6c5aadb18f",
    "g_id": "5d754a01b128da140c95eed8",
    "s_id": "64b2778599cb0e28a3f7df6d",
    "name": "Материал",
    "amount": "10",
    "description": "Описание материала"
    "measure": "л.",
    "value": {
            "supply": [
                {
                    "date": "2023-08-24T08:30:00.325Z",
                    "amount": 200
                }
            ]
        }
}
```

Параметры:<br>
**_id*** - Идентификатор материала<br>
**g_id** - Идентификатор группы редактируемого материала<br>
**s_id** - Идентификатор потока<br>
**name** - Имя материала<br>
**amount** - Текущий остаток материала<br>
**description** - Описание материала<br>
**measure** - Мера измерения<br>
**value** - Состав материала<br>
**value.supply** - График поставок материала<br>
**value.supply.date** - Дата поставки<br>
**value.supply.amount** - Количество поставки<br>

Ответ:<br> коды состояний 204 или 404.

<br>

### Удаление материала

Для удаления материала необходимо отправить **`DELETE`** запрос на **`/api/material/:id`**<br>

Параметры:<br>
**id*** - Идентификатор материала<br>

Ответ:<br> коды состояний 204 или 404.

<br>

### Получение BOM

Для получения BOM материала необходимо отправить **`GET`** запрос на **`/bom_new/:m_id/:filter_date/:grade`**<br>
Описание: Для верхнего урованя (конечная продукция/родительский узел) grade передавать не нужно, на нижние уровни (разветвления) передаём grade верхнего уровня (родительский grade)<br>

Параметры:<br>
**m_id*** - Идентификатор материала<br>
**filter_date*** - Текущая дата (для проверки заказов в ожидании, возможно какие-то элементы уже производятся)<br>
**grade*** - Комплектация (массив, находиться в "value.grade"). <br>
   Пример: <br>
   [<br>
     {"r_id": "642b0995507acba2fa401a48", "a_id": "64058bb0d6ef95a980f29b34", "take": 8, "return": 0},<br>
     {"r_id": "64184083c17b5d7e359ee4d3", "a_id": "642bf16168d67b78a2afc45b", "take": 3, "return": 0}<br>
   ]
<br>  

Пример ответа:<br>
```
[
    {
        "_id": "640237adff8d6b0e26819dfc",
        "operation": "Сборка бампера",
        "compliance_rate": "2400000",
        "res_m": [
            {
                "name": "Resource 13",
                "status": true,
                "r_id": "64023a4b935d7a8d7e4a9ff0",
                "type": "material",
                "conditions": [
                    {
                        "a_id": "6402fcaeff8d6b0e2681a626",
                        "r_index": 12,
                        "take": 0,
                        "return": 1
                    }
                ],
                "change": false,
                "arsenal": {
                    "a_id": "6402fcaeff8d6b0e2681a626",
                    "r_index": 12,
                    "take": 0,
                    "return": 1,
                    "name": "Бампер модель Б1",
                    "amount": 0
                }
            },
            {
                "name": "Resource 7",
                "status": true,
                "r_id": "640238c6723dd04214260b33",
                "type": "material",
                "conditions": [
                    {
                        "a_id": "640236b6ff8d6b0e26819df6",
                        "r_index": 6,
                        "take": 8,
                        "return": 0
                    }
                ],
                "change": false,
                "arsenal": {
                    "a_id": "640236b6ff8d6b0e26819df6",
                    "r_index": 6,
                    "take": 8,
                    "return": 0,
                    "name": "Болт М16х 1,5-6gх35",
                    "amount": 1000
                }
            },
            {
                "name": "Resource 11",
                "status": true,
                "r_id": "6402394ccbadd761aac04244",
                "type": "material",
                "conditions": [
                    {
                        "a_id": "64023745ff8d6b0e26819dfa",
                        "r_index": 10,
                        "take": 8,
                        "return": 0
                    }
                ],
                "change": false,
                "arsenal": {
                    "a_id": "64023745ff8d6b0e26819dfa",
                    "r_index": 10,
                    "take": 8,
                    "return": 0,
                    "name": "Шайба пружинная 16",
                    "amount": 900
                }
            }
        ],
        "res_w": [
            {
                "name": "Resource 1",
                "status": true,
                "r_id": "64023800d4027812d445e2ca",
                "type": "worker",
                "conditions": [
                    {
                        "a_id": "640073c253d5a7d95a8f86d4",
                        "r_index": 0,
                        "take": 1,
                        "return": 1
                    },
                    {
                        "a_id": "64058fdfd6ef95a980f29b56",
                        "r_index": 0,
                        "take": 1,
                        "return": 1
                    },
                    {
                        "a_id": "640eda8c34903b7cc212cca3",
                        "r_index": 0,
                        "take": 1,
                        "return": 1
                    }
                ],
                "change": false,
                "arsenal": {
                    "a_id": "640073c253d5a7d95a8f86d4",
                    "r_index": 0,
                    "take": 1,
                    "return": 1,
                    "name": "Попов Михаил",
                    "amount": 1
                }
            }
        ],
        "res_e": [],
        "res_d": [],
        "position": {
            "r_id": "642b0995507acba2fa401a48",
            "a_id": "64058bb0d6ef95a980f29b34",
            "take": 8,
            "return": 0
        }
    }
]
```

<br>

### Конструктор комплектации

Для получения данных для конструктора комплектации необходимо отправить **`GET`** запрос на **`/grade/:m_id/:grade`**<br>

Параметры:<br>
**m_id*** - Идентификатор материала<br>
**grade*** - Комплектация (grade) родительского элемента. <br>
   Пример: <br>
   [<br>
     {"r_id": "642b0995507acba2fa401a48", "a_id": "64058bb0d6ef95a980f29b34", "take": 8, "return": 0},<br>
     {"r_id": "64184083c17b5d7e359ee4d3", "a_id": "642bf16168d67b78a2afc45b", "take": 3, "return": 0}<br>
   ]
<br>  

Пример ответа:<br>
```
[
    {
        "_id": "6402fcaeff8d6b0e2681a626",
        "name": "Resource 3",
        "grade": [
            {
                "_id": "641c6e4ae54f7a08825d9872",
                "g_id": "640588ca3c0a8b77d11f359f",
                "name": "Лист металлический 6 мм сталь 45",
                "measure": "шт.",
                "description": "",
                "amount": 95.6,
                "operation": [],
                "technical_maps": [],
                "take": 1,
                "return": 0
            },
            {
                "_id": "6424233bb2a91b63aa4bdf38",
                "g_id": "640588ca3c0a8b77d11f359f",
                "name": "Лист металлический 8 мм сталь 45",
                "measure": "шт.",
                "description": "",
                "amount": 96.4,
                "operation": [],
                "take": 51,
                "return": 0
            },
            {
                "_id": "64058bb0d6ef95a980f29b34",
                "g_id": "640588ca3c0a8b77d11f359f",
                "name": "Лист металлический 10 мм сталь 45",
                "measure": "шт",
                "description": "",
                "amount": "103.2",
                "operation": [],
                "take": 1,
                "return": 0
            }
        ],
        "r_id": "642b0995507acba2fa401a48"
    }
]
```