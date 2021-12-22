## Потоки
stream.js

[Главная](README.md)  /  [Документация по API](api.md)


### Получение списка потоков для группы и по типу потока (можно использовать для селекторов)

Для получения списка клиентов необходимо отправить **`GET`** запрос на **`/api/stream_type/:type`**<br>

Пример ответа:<br>
```
[
    {
        "_id": "5d664567b8c86d232adea1ef",
        "type": "template",
        "name": "Вложение"
    },
    {
        "_id": "5d8ce21fb08dd438247adea0",
        "type": "stream",
        "name": "Тестирование второе"
    },
    {
        "_id": "5e283fded5a10801e4ea700b",
        "type": "template",
        "name": "Параллельный пошив и отстрочка"
    }
]
```

Параметры:<br>
**type*** - Тип потока<br>

<br>

### Получение описание потока

Для получения списка клиентов необходимо отправить **`GET`** запрос на **`/api/stream/:id`**<br>

Пример ответа:<br>
```
[
    {
        "_id": "61af20b86c76af54179464b9",
        "g_id": "61c060dab4f2cbb941edd942",
        "type": "stream",
        "status": "active",
        "name": "Kit without stich",
        "description": "Kit without stich",
        "operation": [
            {
                "position": [
                    2,
                    2
                ],
                "relation": [
                    {
                        "_id": "61af234f6c76af54179464c6",
                        "firstPointIndex": 1,
                        "secondPointIndex": 3,
                        "so_id": "61af21a9f9809c9cdbdc9cf4",
                        "startId": "61af209dbd179d7503da570b",
                        "result": "Start",
                        "bgr_color": "#007AFC",
                        "function": []
                    }
                ],
                "_id": "61af209dbd179d7503da570b",
                "type": "order",
                "status": "active",
                "worker_count": 0
            },
            {
                "position": [
                    6,
                    2
                ],
                "relation": [],
                "_id": "61af209df17c05144a19df52",
                "type": "order",
                "status": "complete",
                "worker_count": 0
            },
            {
                "position": [
                    3,
                    2
                ],
                "type": "operation",
                "relation": [
                    {
                        "_id": "61b7bfe05006d7661b15edaf",
                        "firstPointIndex": 1,
                        "secondPointIndex": 3,
                        "so_id": "61af21d24cb023a2fd4ecafa",
                        "startId": "61af21a9f9809c9cdbdc9cf4",
                        "result": "Cut complete",
                        "bgr_color": "#2EA877",
                        "function": []
                    }
                ],
                "_id": "61af21a9f9809c9cdbdc9cf4",
                "o_id": "6178503ecb30bb6aa7dc2020",
                "worker_count": 2
            },
            {
                "position": [
                    4,
                    2
                ],
                "type": "operation",
                "relation": [
                    {
                        "_id": "61af234f6c76af54179464c4",
                        "firstPointIndex": 1,
                        "secondPointIndex": 3,
                        "so_id": "61af21dc3737b2c0392f7a24",
                        "startId": "61af21d24cb023a2fd4ecafa",
                        "result": "Stich complete",
                        "bgr_color": "#2EA877",
                        "function": []
                    }
                ],
                "_id": "61af21d24cb023a2fd4ecafa",
                "o_id": "61936f09c03b9f58b55abf5a",
                "worker_count": 1
            },
            {
                "position": [
                    5,
                    2
                ],
                "type": "operation",
                "relation": [
                    {
                        "_id": "61af234f6c76af54179464c3",
                        "firstPointIndex": 2,
                        "secondPointIndex": 0,
                        "so_id": "61af21ebb9c0ca1c4080ba98",
                        "startId": "61af21dc3737b2c0392f7a24",
                        "result": "Order cancelled",
                        "bgr_color": "#EC3838",
                        "function": []
                    },
                    {
                        "_id": "61af234f6c76af54179464c2",
                        "firstPointIndex": 1,
                        "secondPointIndex": 3,
                        "so_id": "61af209df17c05144a19df52",
                        "startId": "61af21dc3737b2c0392f7a24",
                        "result": "Quality control complete",
                        "bgr_color": "#2EA877",
                        "function": [
                            {
                                "_id": "61ba001bd3b98009574a701a",
                                "type": "material",
                                "condition": "plus",
                                "value": 10,
                                "path": "Polizdelki.sp uležajenje SL"
                            }
                        ]
                    },
                    {
                        "_id": "61af234f6c76af54179464c1",
                        "firstPointIndex": 0,
                        "secondPointIndex": 0,
                        "so_id": "61af21a9f9809c9cdbdc9cf4",
                        "startId": "61af21dc3737b2c0392f7a24",
                        "result": "Cut defect",
                        "bgr_color": "#EC3838",
                        "function": [
                            {
                                "_id": "61ba0139d3b98009574a7052",
                                "type": "material",
                                "condition": "minus",
                                "value": 10,
                                "path": "Polizdelki.zg uležajenje"
                            }
                        ]
                    },
                    {
                        "_id": "61af234f6c76af54179464c0",
                        "firstPointIndex": 0,
                        "secondPointIndex": 0,
                        "so_id": "61af21d24cb023a2fd4ecafa",
                        "startId": "61af21dc3737b2c0392f7a24",
                        "result": "Stitch defect",
                        "bgr_color": "#EC3838",
                        "function": []
                    }
                ],
                "_id": "61af21dc3737b2c0392f7a24",
                "o_id": "61785096cb30bb6aa7dc2022",
                "worker_count": 1
            },
            {
                "position": [
                    5,
                    3
                ],
                "type": "order",
                "relation": [],
                "_id": "61af21ebb9c0ca1c4080ba98",
                "status": "canceled",
                "worker_count": 0
            }
        ]
    }
]
```

Параметры:<br>
**id*** - Идентификатор поколения<br>

<br>

### Создание нового потока

Для создания нового потока необходимо отправить **`POST`** запрос на **`/api/stream`**<br>

Пример отправки параметров:<br>
```
{
    "g_id": "5cbc415d5e42968e114d6321",
    "name": "Тестовый поток",
    "type": "template",
    "description": "Краткое описание потока",
    "operation": [
        {
            "_id": "5cbb83829279efc1c8150a88",
            "type": "order",
            "status": "active",
            "position": [ 2, 1 ],
            "relation": [
                {
                    "so_id": "5cbb844a9279efc1c8150a89",
                    "result": null,
                    "position": [ 2, 4 ]
                }
            ]
        },
        {
            "_id": "5cbb844a9279efc1c8150a89" ,
            "o_id": "5cbc398f5e42968e114d6319",
            "type": "operation",
            "so_status": {
                "status": "pending"
            },
            "position": [ 2, 2 ],
            "relation": [
                {
                    "so_id": "5cbb8d969279efc1c8150a8f",
                    "result": "Выполнено",
                    "position": [ 2, 4 ]
                },
                {
                    "so_id": "5cc203189d461c6b6c790025",
                    "result": "Отменить заказ",
                    "position": [ 2, 4 ]
                }
            ]
        },
        {
            "_id": "5cbb8d969279efc1c8150a8f",
            "o_id": "5cbc39755e42968e114d6318",
            "type": "operation",
            "so_status": {
                "status": "pending"
            },
            "position": [ 2, 3 ],
            "relation": [
                {
                    "so_id": "5cbc45a95e42968e114d6327",
                    "result": "Выполнено",
                    "position": [ 2, 4 ]
                },
                {
                    "so_id": "5cbc5588631c979c2c5b2745",
                    "result": "Найден брак",
                    "position": [ 2, 4 ]
                }
            ]
        },
        {
            "_id": "5cbc45a95e42968e114d6327",
            "o_id": "5cbc39755e42968e114d6317",
            "type": "operation",
            "so_status": {
                "status": "pending"
            },
            "position": [ 2, 4 ],
            "relation": [
                {
                    "so_id": "5cbc4ea8631c979c2c5b2737",
                    "result": "Выполнено",
                    "position": [ 2, 4 ]
                },
                {
                    "so_id": "5cbc5588631c979c2c5b2745",
                    "result": "Найден брак",
                    "position": [ 2, 4 ]
                }
            ]
        },
        {
            "_id": "5cbc4ea8631c979c2c5b2737",
            "o_id": "5cbc3c325e42968e114d631d",
            "type": "operation",
            "so_status": {
                "status": "pending"
            },
            "position": [ 3, 4 ],
            "relation": [
                {
                    "so_id": "5cbc50d2631c979c2c5b273f" ,
                    "result": "Выполнено",
                    "position": [ 2, 4 ]
                },
                {
                    "so_id": "5cbc5588631c979c2c5b2745",
                    "result": "Найден брак",
                    "position": [ 2, 4 ]
                }
            ]
        },
        {
            "_id": "5cbc50d2631c979c2c5b273f",
            "o_id": "5cbc39755e42968e114d6317",
            "type": "operation",
            "so_status": {
                "status": "pending"
            },
            "position": [ 4, 4 ],
            "relation": [
                {
                    "so_id": "5cbc5588631c979c2c5b2745",
                    "result": "Выполнено",
                    "position": [ 2, 4 ]
                },
                {
                    "so_id": "5cbc5588631c979c2c5b2745",
                    "result": "Найден брак",
                    "position": [ 2, 4 ]
                }
            ]
        },
        {
            "_id": "5cc1f20c9d461c6b6c790017",
            "s_id": "5cbf184e90a45834485c18e9",
            "type": "template",
            "position": [ 2, 4 ],
            "relation": [
                {
                    "so_id": "5cbc5588631c979c2c5b2745",
                    "serult": "Выполнено",
                    "position": [ 2, 4 ]
                }
            ]
        },
        {
            "_id": "5cc2028e9d461c6b6c790024",
            "type": "order",
            "status": "complete",
            "position": [ 2, 4 ]
        },
        {
            "_id": "5cc203189d461c6b6c790025",
            "type": "order",
            "status": "canceled",
            "position": [ 2, 4 ]
        }
    ]
}
```

Параметры:<br>
**g_id*** - Идентификатор группы в которой будет находиться проток<br>
**type*** - Тип потока<br>
**description*** - Описание потока<br>

**operation*** - Уровень описывающий операции<br>
**_id*** - Идентификатор операции, формировать надо на клиенте<br>
**type*** - Тип операции<br>
**status*** - Статус операции для операций типа order<br>
**s_id*** - Идентификатор вложения для операций типа template<br>
**position*** - Позиция расположения операции на экране<br>

**relation*** - Уровень описывающий связи<br>
**so_id*** - Идентификатор следующей операции в потоке (_id)<br>
**result*** - Имя результата выполнения операции<br>
**position*** - Позиция расположения связи на экране<br>

Ответ:<br> id созданного потока или 404.

<br>

### Редактирование потока

Для редактирования потока необходимо отправить **`PUT`** запрос на **`/api/stream`**<br>

Пример отправки параметров:<br>
```
{
    "id": "5cf0526700e0dd1d5b243af3",
    "g_id": "5cbc415d5e42968e114d6321",
    "name": "Тестовый поток1",
    "type": "template",
    "description": "Краткое описание потока2",
    "operation": [
        {
            "_id": "5cbb83829279efc1c8150a88",
            "type": "order",
            "status": "active",
            "position": [ 2, 1 ],
            "relation": [
                {
                    "so_id": "5cbb844a9279efc1c8150a89",
                    "result": null,
                    "position": [ 2, 4 ]
                }
            ]
        },
        {
            "_id": "5cbb844a9279efc1c8150a89" ,
            "o_id": "5cbc398f5e42968e114d6319",
            "type": "operation",
            "so_status": {
                "status": "pending"
            },
            "position": [ 2, 2 ],
            "relation": [
                {
                    "so_id": "5cbb8d969279efc1c8150a8f",
                    "result": "Выполнено1",
                    "position": [ 2, 4 ],
                    "function": [
                        {
                            "_id": "5f47455d57f4f4eb2d855cad",
                            "m_id": "5dea3bb77c08e37d7d1e34f9",
                            "operation": "minus",
                            "quantity": 8
                        },
                        {
                            "_id": "5df35bd22af7af09cdd36801",
                            "m_id": "5dea3bb77c08e37d7d1e34f9",
                            "operation": "minus",
                            "quantity": 2
                        }
                    ]
                },
                {
                    "so_id":  "5cbc5588631c979c2c5b2745",
                    "result": "Найден брак2",
                    "position": [ 2, 4 ]
                }
            ]
        }
        {
            "_id": "5cbc45a95e42968e114d6327",
            "o_id": "5cbc39755e42968e114d6317",
            "type": "operation",
            "so_status": {
                "status": "pending"
            },
            "position": [ 2, 4 ],
            "relation": [
                {
                    "so_id": "5cbc4ea8631c979c2c5b2737",
                    "result": "Выполнено",
                    "position": [ 2, 4 ]
                },
                {
                    "so_id": "5cbc5588631c979c2c5b2745",
                    "result": "Найден брак",
                    "position": [ 2, 4 ]
                }
            ]
        },
        {
            "_id": "5cbc50d2631c979c2c5b273f",
            "o_id": "5cbc39755e42968e114d6317",
            "type": "operation",
            "so_status": {
                "status": "pending"
            },
            "position": [ 4, 4 ],
            "relation": [
                {
                    "so_id": "5cbc5588631c979c2c5b2745",
                    "result": "Выполнено",
                    "position": [ 2, 4 ]
                },
                {
                    "so_id": "5cbc5588631c979c2c5b2745",
                    "result": "Найден брак",
                    "position": [ 2, 4 ]
                }
            ]
        },
        {
            "_id": "5cbc5588631c979c2c5b2745",
            "o_id": "5cbc39755e42968e114d6345" ,
            "type": "operation",
            "so_status": {
                "status": "pending"
            },
            "position": [ 3, 3 ],
            "relation": [
                {
                    "so_id": "5cc2028e9d461c6b6c790024",
                    "result": "Заказ выполнен",
                    "position": [ 2, 4 ]
                },
                {
                    "so_id": "5cc1f20c9d461c6b6c790017",
                    "result": "Вылезли нитки",
                    "position": [ 2, 4 ]
                }
            ]
        },
        {
            "_id": "5cc1f20c9d461c6b6c790017",
            "s_id": "5cbf184e90a45834485c18e9",
            "type": "template",
            "position": [ 2, 4 ],
            "relation": [
                {
                    "so_id": "5cbc5588631c979c2c5b2745",
                    "serult": "Выполнено",
                    "position": [ 2, 4 ]
                }
            ]
        },
        {
            "_id": "5cc2028e9d461c6b6c790024",
            "type": "order",
            "status": "complete",
            "position": [ 2, 4 ]
        },
        {
            "_id": "5cc203189d461c6b6c790025",
            "type": "order",
            "status": "canceled",
            "position": [ 2, 4 ]
        }
    ]
}
```

Параметры:<br>
**id*** - Идентификатор потока<br>
**g_id*** - Идентификатор группы в которой будет находиться проток<br>
**type*** - Тип потока<br>
**description*** - Описание потока<br>

**operation*** - Уровень описывающий операции<br>
**_id*** - Идентификатор операции, формировать надо на клиенте<br>
**type*** - Тип операции<br>
**status*** - Статус операции для операций типа order<br>
**s_id*** - Идентификатор вложения для операций типа template<br>
**position*** - Позиция расположения операции на экране<br>

**relation*** - Уровень описывающий связи<br>
**so_id*** - Идентификатор следующей операции в потоке (_id)<br>
**result*** - Имя результата выполнения операции<br>
**position*** - Позиция расположения связи на экране<br>

**function*** - Функции выполняемые при переходе по связи<br>
**m_id*** - Илентификатор материала или незавершённого производства к которому будет применена функция<br>
**operation*** - Операция для функции ("plus" или "minus")<br>
**quantity*** - Количество материала или незавершённого производства<br>

Ответ:<br> коды состояний 204 или 404.

<br>

### Удаление потока

Для удаления потока необходимо отправить **`DELETE`** запрос на **`/api/stream/:id`**<br>

Параметры:<br>
**id*** - Идентификатор потока<br>

Ответ:<br> коды состояний 204 или 404.
