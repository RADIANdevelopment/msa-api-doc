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

Для получения последовательности операций для заказа необходимо отправить **`GET`** запрос на **`/api/order_operations_parallel/?_id={"_id": [ "63e2a6c6edd61bbc60779a81", "63e394beedd61bbc60779aad"]}`**<br>

Пример ответа:<br>
```
[
    {
        "_id": "63e2a6c6edd61bbc60779a81",
        "urgently": false,
        "g_id": "63e0b34a113123006b9f02bd",
        "name": "Заказ 020",
        "type": "simple",
        "schedule": "2023-03-31T00:00:00.000Z",
        "streamName": "Параллельные операции",
        "s_id": "63e292d1edd61bbc60779a7a",
        "composition": {
            "Тип продукции": "тип 1",
            "Диапазон измерения": "от 0,3 до 1 метров ",
            "Точность измерения": "от ±5 мм",
            "Дисплей ": "SAP-300",
            "Выходной сигнал": "4-20 мА ",
            "Напряжение питания": "18 - 35 В постоянного тока",
            "Температура продукта измерения": "от -30 °C до +90 °C",
            "Маржинальнось": "20",
            "тип": "ААА"
        },
        "sequence_number": 6,
        "c_id": "000000000000000000000000",
        "client": "Administrator",
        "count": null,
        "status": "pending",
        "date": "2023-02-07T20:30:00.325Z",
        "operation": [
            {
                "_id": "63aecfe1fe51cf495c2162e1",
                "g_id": "63e0b1d6c62b0f27175862e3",
                "name": "Операция 10",
                "description": "Операция 10",
                "cost": "20",
                "compliance_rate": "180000",
                "resources": [
                    {
                        "name": "Resource 1",
                        "status": true,
                        "r_id": "63cedb471efbbaaea5d4b949",
                        "type": "equipments",
                        "conditions": [
                            {
                                "a_id": "629336eb81cbed3d19940c6b",
                                "r_index": 0,
                                "take": 1,
                                "return": 1
                            },
                            {
                                "a_id": "63a9af67fe51cf495c21628d",
                                "r_index": 0,
                                "take": 1,
                                "return": 1
                            }
                        ]
                    },
                    {
                        "name": "Resource 2",
                        "status": true,
                        "r_id": "63cedbac04fce7e1243cfb64",
                        "type": "worker",
                        "conditions": [
                            {
                                "a_id": "6293314681cbed3d19940af3",
                                "r_index": 1,
                                "take": 0.5,
                                "return": 0.5
                            }
                        ]
                    }
                ],
                "technical_maps": [],
                "scripts": {
                    "order_level": {
                        "script": ""
                    },
                    "operation_level": {
                        "script": ""
                    },
                    "resource_level": {
                        "script": ""
                    }
                },
                "expects": [
                    []
                ]
            },
            {
                "_id": "63aef59ffe51cf495c2162f0",
                "g_id": "63e0b1d6c62b0f27175862e3",
                "name": "Операция 12",
                "description": "Операция 12",
                "cost": "30",
                "compliance_rate": "120000",
                "technical_maps": [],
                "resources": [
                    {
                        "name": "Resource 1",
                        "status": true,
                        "r_id": "63cedb7c4797d40542ce52e4",
                        "type": "equipments",
                        "conditions": [
                            {
                                "a_id": "629337cd81cbed3d19940c6f",
                                "r_index": 0,
                                "take": 1,
                                "return": 1
                            },
                            {
                                "a_id": "62c49c8027765d12f9c70350",
                                "r_index": 0,
                                "take": 1,
                                "return": 1
                            }
                        ]
                    }
                ],
                "scripts": {
                    "order_level": {
                        "script": ""
                    },
                    "operation_level": {
                        "script": ""
                    },
                    "resource_level": {
                        "script": ""
                    }
                },
                "expects": [
                    [
                        "63aecfe1fe51cf495c2162e1"
                    ]
                ]
            },
            {
                "_id": "63bfebbb91f6cc4f4c4f97b5",
                "g_id": "63e0b1d6c62b0f27175862e3",
                "name": "ОТК",
                "description": "Отдел контроля качества",
                "cost": "0",
                "compliance_rate": "120000",
                "resources": [
                    {
                        "name": "Resource 1",
                        "status": true,
                        "r_id": "63bfecae536213fe4a8619ac",
                        "type": "worker",
                        "conditions": [
                            {
                                "a_id": "62932f1881cbed3d19940aef",
                                "r_index": 0,
                                "take": 1,
                                "return": 1
                            },
                            {
                                "a_id": "62c45e5509f2bd0ac40dd7ed",
                                "r_index": 0,
                                "take": 1,
                                "return": 1
                            }
                        ]
                    }
                ],
                "technical_maps": [],
                "scripts": {
                    "order_level": {
                        "script": ""
                    },
                    "operation_level": {
                        "script": ""
                    },
                    "resource_level": {
                        "script": ""
                    }
                },
                "expects": [
                    [
                        "63d269761ba4501b0cf39b84"
                    ],
                    [
                        "63aed7bafe51cf495c2162e2",
                        "63aef59ffe51cf495c2162f0"
                    ]
                ]
            },
            {
                "_id": "63d269761ba4501b0cf39b84",
                "g_id": "63e0b1d6c62b0f27175862e3",
                "name": "Операция 03",
                "scripts": {
                    "order_level": {
                        "script": ""
                    },
                    "operation_level": {
                        "script": ""
                    },
                    "resource_level": {
                        "script": ""
                    }
                },
                "description": "",
                "cost": "0",
                "compliance_rate": "600000",
                "technical_maps": [],
                "expects": [
                    [
                        "63aecfe1fe51cf495c2162e1"
                    ]
                ]
            },
            {
                "_id": "63aed7bafe51cf495c2162e2",
                "g_id": "63e0b1d6c62b0f27175862e3",
                "name": "Операция 11",
                "description": "Операция 11",
                "cost": 0,
                "compliance_rate": "240000",
                "resources": [
                    {
                        "name": "Resource 1",
                        "status": true,
                        "r_id": "63cc2f75f623c96470060d32",
                        "type": "material",
                        "conditions": [
                            {
                                "a_id": "6297834cd443c8021b14d59d",
                                "r_index": 0,
                                "take": 1,
                                "return": 0
                            }
                        ]
                    },
                    {
                        "name": "Resource 2",
                        "status": true,
                        "r_id": "63d8efd8ebd51f68acfcf4e4",
                        "type": "equipments",
                        "conditions": [
                            {
                                "a_id": "62c49c8027765d12f9c70350",
                                "r_index": 1,
                                "take": 1,
                                "return": 1
                            },
                            {
                                "a_id": "63aef567fe51cf495c2162ef",
                                "r_index": 1,
                                "take": 1,
                                "return": 1
                            }
                        ]
                    }
                ],
                "technical_maps": [],
                "scripts": {},
                "expects": [
                    [
                        "63aecfe1fe51cf495c2162e1"
                    ]
                ]
            }
        ]
    },
    {
        "_id": "63e394beedd61bbc60779aad",
        "urgently": false,
        "g_id": "63e0b34a113123006b9f02bd",
        "name": "Заказ 021",
        "type": "simple",
        "schedule": "2023-03-31T00:00:00.000Z",
        "streamName": "Параллельные операции",
        "s_id": "63e292d1edd61bbc60779a7a",
        "composition": {
            "Тип продукции": "тип 1",
            "Диапазон измерения": "от 0,3 до 1 метров ",
            "Точность измерения": "от ±5 мм",
            "Дисплей ": "SAP-300",
            "Выходной сигнал": "4-20 мА ",
            "Напряжение питания": "18 - 35 В постоянного тока",
            "Температура продукта измерения": "от -30 °C до +90 °C",
            "Маржинальнось": "20",
            "тип": "ААА"
        },
        "sequence_number": 6,
        "c_id": "000000000000000000000000",
        "client": "Administrator",
        "count": null,
        "status": "pending",
        "date": "2023-02-08T13:25:34.253Z",
        "operation": [
            {
                "_id": "63d269761ba4501b0cf39b84",
                "g_id": "63e0b1d6c62b0f27175862e3",
                "name": "Операция 03",
                "scripts": {
                    "order_level": {
                        "script": ""
                    },
                    "operation_level": {
                        "script": ""
                    },
                    "resource_level": {
                        "script": ""
                    }
                },
                "description": "",
                "cost": "0",
                "compliance_rate": "600000",
                "technical_maps": [],
                "expects": [
                    [
                        "63aecfe1fe51cf495c2162e1"
                    ]
                ]
            },
            {
                "_id": "63aef59ffe51cf495c2162f0",
                "g_id": "63e0b1d6c62b0f27175862e3",
                "name": "Операция 12",
                "description": "Операция 12",
                "cost": "30",
                "compliance_rate": "120000",
                "technical_maps": [],
                "resources": [
                    {
                        "name": "Resource 1",
                        "status": true,
                        "r_id": "63cedb7c4797d40542ce52e4",
                        "type": "equipments",
                        "conditions": [
                            {
                                "a_id": "629337cd81cbed3d19940c6f",
                                "r_index": 0,
                                "take": 1,
                                "return": 1
                            },
                            {
                                "a_id": "62c49c8027765d12f9c70350",
                                "r_index": 0,
                                "take": 1,
                                "return": 1
                            }
                        ]
                    }
                ],
                "scripts": {
                    "order_level": {
                        "script": ""
                    },
                    "operation_level": {
                        "script": ""
                    },
                    "resource_level": {
                        "script": ""
                    }
                },
                "expects": [
                    [
                        "63aecfe1fe51cf495c2162e1"
                    ]
                ]
            },
            {
                "_id": "63aed7bafe51cf495c2162e2",
                "g_id": "63e0b1d6c62b0f27175862e3",
                "name": "Операция 11",
                "description": "Операция 11",
                "cost": 0,
                "compliance_rate": "240000",
                "resources": [
                    {
                        "name": "Resource 1",
                        "status": true,
                        "r_id": "63cc2f75f623c96470060d32",
                        "type": "material",
                        "conditions": [
                            {
                                "a_id": "6297834cd443c8021b14d59d",
                                "r_index": 0,
                                "take": 1,
                                "return": 0
                            }
                        ]
                    },
                    {
                        "name": "Resource 2",
                        "status": true,
                        "r_id": "63d8efd8ebd51f68acfcf4e4",
                        "type": "equipments",
                        "conditions": [
                            {
                                "a_id": "62c49c8027765d12f9c70350",
                                "r_index": 1,
                                "take": 1,
                                "return": 1
                            },
                            {
                                "a_id": "63aef567fe51cf495c2162ef",
                                "r_index": 1,
                                "take": 1,
                                "return": 1
                            }
                        ]
                    }
                ],
                "technical_maps": [],
                "scripts": {}
                },
                "expects": [
                    [
                        "63aecfe1fe51cf495c2162e1"
                    ]
                ]
            },
            {
                "_id": "63aecfe1fe51cf495c2162e1",
                "g_id": "63e0b1d6c62b0f27175862e3",
                "name": "Операция 10",
                "description": "Операция 10",
                "cost": "20",
                "compliance_rate": "180000",
                "resources": [
                    {
                        "name": "Resource 1",
                        "status": true,
                        "r_id": "63cedb471efbbaaea5d4b949",
                        "type": "equipments",
                        "conditions": [
                            {
                                "a_id": "629336eb81cbed3d19940c6b",
                                "r_index": 0,
                                "take": 1,
                                "return": 1
                            },
                            {
                                "a_id": "63a9af67fe51cf495c21628d",
                                "r_index": 0,
                                "take": 1,
                                "return": 1
                            }
                        ]
                    },
                    {
                        "name": "Resource 2",
                        "status": true,
                        "r_id": "63cedbac04fce7e1243cfb64",
                        "type": "worker",
                        "conditions": [
                            {
                                "a_id": "6293314681cbed3d19940af3",
                                "r_index": 1,
                                "take": 0.5,
                                "return": 0.5
                            }
                        ]
                    }
                ],
                "technical_maps": [],
                "scripts": {
                    "order_level": {
                        "script": ""
                    },
                    "operation_level": {
                        "script": ""
                    },
                    "resource_level": {
                        "script": ""
                    }
                },
                "expects": [
                    []
                ]
            },
            {
                "_id": "63bfebbb91f6cc4f4c4f97b5",
                "g_id": "63e0b1d6c62b0f27175862e3",
                "name": "ОТК",
                "description": "Отдел контроля качества",
                "cost": "0",
                "compliance_rate": "120000",
                "resources": [
                    {
                        "name": "Resource 1",
                        "status": true,
                        "r_id": "63bfecae536213fe4a8619ac",
                        "type": "worker",
                        "conditions": [
                            {
                                "a_id": "62932f1881cbed3d19940aef",
                                "r_index": 0,
                                "take": 1,
                                "return": 1
                            },
                            {
                                "a_id": "62c45e5509f2bd0ac40dd7ed",
                                "r_index": 0,
                                "take": 1,
                                "return": 1
                            }
                        ]
                    }
                ],
                "technical_maps": [],
                "scripts": {
                    "order_level": {
                        "script": ""
                    },
                    "operation_level": {
                        "script": ""
                    },
                    "resource_level": {
                        "script": ""
                    }
                },
                "expects": [
                    [
                        "63d269761ba4501b0cf39b84"
                    ],
                    [
                        "63aed7bafe51cf495c2162e2",
                        "63aef59ffe51cf495c2162f0"
                    ]
                ]
            }
        ]
    }
]
```

Параметры:<br>
**_id*** - Массив заказов<br>

Примеры условий "expects":<br>
"expects":[["63e0de7cbe1a8520512b4128"]] - текущая операция ждёт пока завершиться операция "63e0de7cbe1a8520512b4128"<br>
"expects":[["63e0de7cbe1a8520512b4128"],["63e0de8abe1a8520512b412f"]] - текущая операция ждёт пока завершиться операция "63e0de7cbe1a8520512b4128" или "63e0de8abe1a8520512b412f"<br>
"expects":[["63e0de7cbe1a8520512b4128", "63e0dea0be1a8520512b413f"],["63e0de8abe1a8520512b412f"]] - текущая операция ждёт пока завершаться операции ("63e0de7cbe1a8520512b4128" и "63e0dea0be1a8520512b413f") или операция "63e0de8abe1a8520512b412f"<br>
"expects":[["63e0de7cbe1a8520512b4128", "63e0dea0be1a8520512b413f"],["63e0de8abe1a8520512b412f,63e0dec9be1a8520512b4153"]] - текущая операция ждёт пока завершаться операции ("63e0de7cbe1a8520512b4128" и "63e0dea0be1a8520512b413f") или операции ("63e0de8abe1a8520512b412f" и "63e0dec9be1a8520512b4153")

<br>