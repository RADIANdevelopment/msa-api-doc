## Заказы в работе
order.js

[Главная](README.md)  /  [Система управления производством](production.md)

### Карточка заказа

Для получения карточки заказа необходимо отправить **`GET`** запрос на **`/admin_order/:id/:status`**<br>

Пример ответа:<br>
```
[
    {
        "_id": "5d0b942858300513831334c6",
        "date": "2019-08-07T17:26:57.033Z",
        "worker": [
            {
                "_id": "5d0b942858300513831334c6",
                "name": "Ольга Козлова",
                "o_id": "5cbc3c325e42968e114d631d",
                "w_id": "5ccbffa65a65c541f0614412",
                "qualification": 3,
                "operation": "Отстрочка",
                "active": false
            },
            {
                "_id": "5d0b942858300513831334c6",
                "name": "Мария Новик",
                "o_id": "5cbc39755e42968e114d6318",
                "w_id": "5ccbfeb65a65c541f061440c",
                "qualification": 3,
                "operation": "Вышивка ромбов",
                "active": false
            }
        ],
        "free_operation": [
            {
                "name": "Quality control",
                "o_id": "5cbc39755e42968e114d6345"
            },
            {
                "name": "Sew",
                "o_id": "5cbc39755e42968e114d6317"
            }
        ],
        "auto": {
            "Марка": "Ford",
            "Модель": "Focus",
            "Поколение": "2014-2017",
            "Сложность": "3",
            "Какая конструкция передних подлокотников?": "Прямая"
        },
        "list": {
            "Дизайн": "Classic",
            "Индивидуальный дизайн": "Да",
            "Основной материал": "Экозамша",
            "Основной материал цвет": "Красный",
            "Материал боковых поддержек": "Экозамша",
            "Материал боковых поддержек цвет": "Красный",
            "Количество": 1,
            "Комментарий": "Небольшое описание заказа"
        },
        "stream": {
            "_id": "5d4b074896857f169044d636",
            "name": "Комплект с ромбами"
        },
        "client": {
            "_id": "5cd6acd4ca9472beaa183775",
            "name": "Любовь Миланова"
        },
        "manager": {
            "_id": "5cf936d3792e90f84ad8d39b",
            "name": "Иван Петров"
        }
    }
]
```
Параметры:<br>
**id*** - Идентификатор заказа<br>
**status*** - Статус заказа ('active', 'order_complete', 'order_canceled')<br>

<br>

### Карточка активного заказа (сокращённый вариант)

Для получения карточки активного заказа в сокращённом виде необходимо отправить **`GET`** запрос на **`/admin_active_order/:_id/`**<br>

Пример ответа:<br>
```
[
    {
        "_id": "5e84ad400dece21b35db9f65",
        "name": "Audi 100 1990-1994",
        "stream": "Тест паралельных операций"
    }
]
```
Параметры:<br>
**_id*** - Идентификатор заказа<br>

<br>

### Поток выполнения заказа

Для получения потока выполнения заказа необходимо отправить **`GET`** запрос на **`/order_perform/:_id`**<br>

Пример ответа:<br>
```
[
    {
        "operation": {
            "position": [
                0,
                1
            ],
            "relation": [
                {
                    "_id": "5f3e73027b173c34e1197a2b",
                    "firstPointIndex": 1,
                    "secondPointIndex": 3,
                    "so_id": "5f3e72d2400180e58678b7d7"
                }
            ],
            "_id": "5e1caf0dd3a75035738e35d8",
            "type": "order",
            "status": "active"
        }
    },
    {
        "operation": {
            "position": [
                5,
                1
            ],
            "relation": [],
            "_id": "5e1caf0d9233e1655db2386a",
            "type": "order",
            "status": "complete"
        }
    },
    {
        "operation": {
            "position": [
                2,
                1
            ],
            "type": "operation",
            "relation": [
                {
                    "_id": "5e727d74d1ec1850dc967805",
                    "firstPointIndex": 1,
                    "secondPointIndex": 3,
                    "so_id": "5e727d4c2da7df285f64d263",
                    "result": "Готово (вложение)",
                    "bgr_color": "#2EA877"
                }
            ],
            "_id": "5e1caf177e0fd420769da427",
            "o_id": "5d61a101abf1fe315164d29c",
            "so_status": {
                "status": "complete"
            }
        },
        "operation_name": "Тестирование продукта",
        "worker_name": "Фадеев Руслан",
        "w_id": "5d61a182abf1fe315164d29f"
    },
    {
        "operation": {
            "position": [
                4,
                1
            ],
            "type": "operation",
            "relation": [
                {
                    "_id": "5e1caf72d3866630fda60108",
                    "firstPointIndex": 1,
                    "secondPointIndex": 3,
                    "so_id": "5e1caf0d9233e1655db2386a",
                    "result": "Готово (третий шаг)",
                    "bgr_color": "#2EA877"
                }
            ],
            "_id": "5e1caf1e3a8fcc68ebd9d5cd",
            "o_id": "5d61a101abf1fe315164d29c",
            "so_status": {
                "status": "pending"
            }
        },
        "operation_name": "Тестирование продукта",
        "worker_name": "Фадеев Руслан",
        "w_id": "5d61a182abf1fe315164d29f"
    },
    {
        "operation": {
            "position": [
                3,
                1
            ],
            "type": "template",
            "relation": [
                {
                    "_id": "5e727d74d1ec1850dc967803",
                    "firstPointIndex": 1,
                    "secondPointIndex": 3,
                    "so_id": "5e1caf1e3a8fcc68ebd9d5cd"
                }
            ],
            "_id": "5e727d4c2da7df285f64d263",
            "s_id": "5eab20190dece21b35dba663",
            "so_status": {
                "status": "active"
            }
        }
    },
    {
        "operation": {
            "position": [
                1,
                1
            ],
            "type": "operation",
            "relation": [
                {
                    "_id": "5f3e73027b173c34e1197a27",
                    "firstPointIndex": 1,
                    "secondPointIndex": 3,
                    "so_id": "5e1caf177e0fd420769da427",
                    "result": "Готово"
                }
            ],
            "_id": "5f3e72d2400180e58678b7d7",
            "o_id": "5d61a101abf1fe315164d29c",
            "so_status": {
                "status": "complete"
            }
        },
        "operation_name": "Тестирование продукта",
        "worker_name": "Фадеев Руслан",
        "w_id": "5d61a182abf1fe315164d29f"
    }
]
```
Параметры:<br>
**_id*** - Идентификатор заказа<br>

<br>

### Поток выполнения вложения заказа

Для получения потока выполнения вложения заказа необходимо отправить **`GET`** запрос на **`/order_template_perform/:_id/:oper_id`**<br>

Пример ответа:<br>
```
[
    {
        "position": [ 1, 2 ],
        "relation": [
            {
                "_id": "5e1cc0c609b190420e08f221",
                "firstPointIndex": 1,
                "secondPointIndex": 3,
                "so_id": "5e1cc0a1dccb6c6eb5aec272"
            }
        ],
        "_id": "5e1cad6ffd2d76175ebd53ce",
        "type": "start"
    },
    {
        "position": [ 4, 2 ],
        "relation": [],
        "_id": "5e1cad6ff7fdd5b6c41013ab",
        "type": "finish"
    },
    {
        "position": [ 2, 2 ],
        "type": "operation",
        "relation": [
            {
                "_id": "5e727d2dd1ec1850dc967801",
                "firstPointIndex": 1,
                "secondPointIndex": 3,
                "so_id": "5e727cfbdcb766e3e40b131c",
                "result": "Готово (вложение 1)",
                "bgr_color": "#2EA877"
            }
        ],
        "_id": "5e1cc0a1dccb6c6eb5aec272",
        "o_id": "5d61a101abf1fe315164d29c",
        "so_status": {
            "status": "complete"
        }
    },
    {
        "position": [ 3, 2 ],
        "type": "operation",
        "relation": [
            {
                "_id": "5e727d2dd1ec1850dc967800",
                "firstPointIndex": 1,
                "secondPointIndex": 3,
                "so_id": "5e1cad6ff7fdd5b6c41013ab",
                "result": "Готово (вложение 2)"
            }
        ],
        "_id": "5e727cfbdcb766e3e40b131c",
        "o_id": "5d61a101abf1fe315164d29c",
        "so_status": {
            "status": "complete"
        }
    }
]
```
Параметры:<br>
**_id*** - Идентификатор заказа<br>
**oper_id*** - Идентификатор вложения<br>

<br>

### Карточка заказа, выполнение

Для получения процесса выполнения заказа необходимо отправить **`GET`** запрос на **`/admin_order_history/:id/:status`**<br>

Пример ответа:<br>
```
[
    {
        "_id": "5d0b942858300513831334c6",
        "gap": [
            {
                "time": 1492254,
                "first_point": "2019.08.07 17:26:57:033",
                "last_point": "2019.08.07 17:51:49:287"
            },
            {
                "time": 240218,
                "first_point": "2019.08.07 17:53:38:642",
                "last_point": "2019.08.07 17:53:58:886"
            },
            {
                "time": 757581,
                "first_point": "2019.08.07 17:55:49:505",
                "last_point": "2019.08.07 17:56:18:768"
            },
            {
                "time": 62137330,
                "first_point": "2019.08.07 18:06:36:467",
                "last_point": "2019.08.08 11:10:38:786"
            },
            {
                "time": 121889,
                "first_point": "2019.08.08 11:11:56:098",
                "last_point": "2019.08.08 11:12:17:124"
            }
        ],
        "work": [
            {
                "o_id": "5cbc398f5e42968e114d6319",
                "w_id": "5cbc7c5f03a9c19c2c71e7a9",
                "worker": "Алена Болотова",
                "operation": "Раскройка",
                "time": 109355,
                "start": "2019.08.07 17:51:49:287",
                "finish": "2019.08.07 17:53:38:642"
            },
            {
                "o_id": "5cbc39755e42968e114d6318",
                "w_id": "5ccbfeb65a65c541f061440c",
                "worker": "Мария Новик",
                "operation": "Вышивка ромбов",
                "time": 110619,
                "start": "2019.08.07 17:53:58:886",
                "finish": "2019.08.07 17:55:49:505"
            },
            {
                "o_id": "5cbc39755e42968e114d6317",
                "w_id": "5ccbff215a65c541f061440f",
                "worker": "Маргарита Орешкина",
                "operation": "Cшивание комплекта",
                "time": 617699,
                "start": "2019.08.07 17:56:18:768",
                "finish": "2019.08.07 18:06:36:467"
            },
            {
                "o_id": "5cbc3c325e42968e114d631d",
                "w_id": "5ccbffa65a65c541f0614412",
                "worker": "Ольга Козлова",
                "operation": "Отстрочка",
                "time": 77312,
                "start": "2019.08.08 11:10:38:786",
                "finish": "2019.08.08 11:11:56:098"
            },
            {
                "o_id": "5cbc39755e42968e114d6317",
                "w_id": "5ccbff215a65c541f061440f",
                "worker": "Маргарита Орешкина",
                "operation": "Cшивание комплекта",
                "time": 23551,
                "start": "2019.08.08 11:12:17:124",
                "finish": "2019.08.08 11:12:40:675"
            }
        ],
        "inwork": {
            "time": 62451388,
            "first_point": "2019.08.07 17:26:57:033",
            "last_point": "2019.08.08 11:12:40:675"
        },
        "ingap": {
            "time": 64749272
        },
        "work_time": [
            {
                "first_point": "08:00",
                "last_point": "12:00"
            },
            {
                "first_point": "13:00",
                "last_point": "17:00"
            }
        ]
    }
]
```
Параметры:<br>
**id*** - Идентификатор заказа<br>
**status*** - Статус заказа ('active', 'order_complete', 'order_canceled')<br>

<br>

### Получение списка заказов в ожидании

Для получения списка заказов в работе необходимо отправить **`GET`** запрос на **`/api/order_pending/:g_id`**<br>

Пример ответа:<br>
```
[
    {
        "_id": "6023d5e3ed52b21ed785ab0e",
        "status": "pending",
        "c_id": "5dc73a298ce0ed3ec726f0d3",
        "name": "Audi 100 2020-н.в.",
        "date": "2021.02.10 15:47:31:473",
        "count": "1",
        "client": "Фадеев Руслан"
    },
    {
        "_id": "6022eddeed52b21ed785aafd",
        "status": "pending",
        "c_id": "5dc73a298ce0ed3ec726f0d3",
        "name": "Fiat Albea 2002-2010",
        "date": "2021.02.09 23:17:34:173",
        "count": "1",
        "client": "Фадеев Руслан"
    }
]
```

Параметры:<br>
**g_id*** - Идентификатор группы (null - возвращает все заказы в ожидании)<br>

<br>

### Получение списка заказов в работе

Для получения списка заказов в работе необходимо отправить **`GET`** запрос на **`/api/order`**<br>

Пример ответа:<br>
```
[
    {
        "_id": "601e96081c37fe0cf7b3ee3e",
        "s_id": "5f732a3d762cd264ad20bb6a",
        "block": true,
        "name": "Lada Веста 2015-н.в.",
        "date_getting_order": "2021.02.06 16:13:44:134",
        "date": "2021.02.06 18:31:01:311",
        "count": "1",
        "c_id": "5e423f9168c51a786b398261",
        "client": "Ольга Зубкова",
        "stream": "Тест комплект с двойной отстрочкой и стежкой"
    },
    {
        "_id": "601e78591c37fe0cf7b3ee33",
        "s_id": "5f732a3d762cd264ad20bb6a",
        "block": true,
        "name": "Chevrolet Cruze 2008-2015",
        "date_getting_order": "2021.02.06 14:07:05:750",
        "date": "2021.02.06 18:31:36:313",
        "count": "1",
        "c_id": "5e423f9168c51a786b398261",
        "client": "Ольга Зубкова",
        "stream": "Тест комплект с двойной отстрочкой и стежкой"
    }
]
```

<br>

### Получение списка заказов в работе (подзаказы)

Для получения списка заказов в работе (подзаказы) необходимо отправить **`GET`** запрос на **`/api/sub_order/:sub_id`**<br>

Пример ответа:<br>
```
[
    {
        "_id": "6047669306504e2109add17f",
        "s_id": "5ea9e7ba0dece21b35dba64a",
        "sub_id": "603ced1706504e2109add157",
        "block": true,
        "name": "Audi 100 2020-н.в.",
        "date_getting_order": "2021.03.01 16:33:11:331",
        "date": "2021.03.09 15:14:11:141",
        "c_id": "5dc73a298ce0ed3ec726f0d3",
        "client": "Фадеев Руслан",
        "stream": "Тест паралельных операций"
    },
    {
        "_id": "6047669306504e2109add180",
        "s_id": "5ea9e7ba0dece21b35dba64a",
        "sub_id": "603ced1706504e2109add157",
        "name": "Audi 100 2020-н.в.",
        "date_getting_order": "2021.03.01 16:33:11:331",
        "date": "2021.03.09 15:14:11:141",
        "c_id": "5dc73a298ce0ed3ec726f0d3",
        "client": "Фадеев Руслан",
        "stream": "Тест паралельных операций"
    }
]
```

Параметры:<br>
**sub_id*** - Идентификатор заказа в котором есть подзаказы<br>

<br>

### Получение списка отменённых заказов

Для получения списка заказов в работе необходимо отправить **`GET`** запрос на **`/api/order_canceled`**<br>

Пример ответа:<br>
```
[
    {
        "_id": "6021674d1c37fe0cf7b3ee64",
        "s_id": "5f72ee4709988855fb90d8f5",
        "name": "Renault Kaptur 2016-н.в.",
        "date": "2021.02.09 08:29:49:294",
        "count": "1",
        "c_id": "5e423f9168c51a786b398261",
        "client": "Ольга Зубкова",
        "stream": "Тест комплект с двойной строчкой"
    },
    {
        "_id": "601be095d4003602da8c8363",
        "s_id": "5f72ee4709988855fb90d8f5",
        "sub_id": "601a961bca8f1a5ff0973990",
        "name": "Lada Гранта 2018-н.в.",
        "date": "2021.02.04 14:55:00:550",
        "count": "4",
        "c_id": "5e423f9168c51a786b398261",
        "client": "Ольга Зубкова",
        "stream": "Тест комплект с двойной строчкой"
    }
]
```

### Получение списка отменённых заказов (подзаказы)

Для получения списка отменённых заказов (подзаказы) необходимо отправить **`GET`** запрос на **`/api/sub_order_canceled/:sub_id`**<br>

Пример ответа:<br>
```
[
    {
        "_id": "6047669306504e2109add17f",
        "s_id": "5ea9e7ba0dece21b35dba64a",
        "sub_id": "603ced1706504e2109add157",
        "block": true,
        "name": "Audi 100 2020-н.в.",
        "date_getting_order": "2021.03.01 16:33:11:331",
        "date": "2021.03.09 15:14:11:141",
        "c_id": "5dc73a298ce0ed3ec726f0d3",
        "client": "Фадеев Руслан",
        "stream": "Тест паралельных операций"
    },
    {
        "_id": "6047669306504e2109add180",
        "s_id": "5ea9e7ba0dece21b35dba64a",
        "sub_id": "603ced1706504e2109add157",
        "name": "Audi 100 2020-н.в.",
        "date_getting_order": "2021.03.01 16:33:11:331",
        "date": "2021.03.09 15:14:11:141",
        "c_id": "5dc73a298ce0ed3ec726f0d3",
        "client": "Фадеев Руслан",
        "stream": "Тест паралельных операций"
    }
]
```

Параметры:<br>
**sub_id*** - Идентификатор заказа в котором есть подзаказы<br>

<br>

### Получение списка завершённых заказов

Для получения списка заказов в работе необходимо отправить **`GET`** запрос на **`/api/order_complete`**<br>

Пример ответа:<br>
```
[
    {
        "_id": "5d848218beac644c90d8554e",
        "s_id": "5d6b7aeab38e701861990c5e",
        "name": "Daewoo Gentra 2013-н.в.",
        "date_getting_order": "2019.09.06 13:32:06:326",
        "date": "2019.09.20 10:10:30:103",
        "finish_date": "2019.09.20 10:41:57:415",
        "count": "1",
        "c_id": "5dc7d8ca8ce0ed3ec726f0db",
        "client": "Дубинин Антон"
    },
    {
        "_id": "5d8116f3e122775c3583b208",
        "s_id": "5d6b7aeab38e701861990c5e",
        "sub_id": "5d81161be122775c3583b205",
        "name": "Audi 100 1990-1994",
        "date_getting_order": "2019.09.17 20:21:31:213",
        "date": "2019.09.17 20:25:06:256",
        "finish_date": "2019.09.20 09:59:23:592",
        "count": "3",
        "c_id": "5dc7d8ca8ce0ed3ec726f0db",
        "client": "Дубинин Антон"
    }
]
```

<br>

### Получение списка завершённых заказов (подзаказы)

Для получения списка завершённых заказов (подзаказы) необходимо отправить **`GET`** запрос на **`/api/sub_order_complete/:sub_id`**<br>

Пример ответа:<br>
```
[
    {
        "_id": "601be095d4003602da8c8363",
        "s_id": "5f72ee4709988855fb90d8f5",
        "sub_id": "601a961bca8f1a5ff0973990",
        "name": "Lada Гранта 2018-н.в.",
        "date_getting_order": "2021.02.03 15:24:59:245",
        "date": "2021.02.04 14:55:00:550",
        "finish_date": null,
        "count": "4",
        "c_id": "5e423f9168c51a786b398261",
        "client": "Ольга Зубкова",
        "stream": "Тест комплект с двойной строчкой"
    },
    {
        "_id": "601be096d4003602da8c8364",
        "s_id": "5f72ee4709988855fb90d8f5",
        "sub_id": "601a961bca8f1a5ff0973990",
        "name": "Lada Гранта 2018-н.в.",
        "date_getting_order": "2021.02.03 15:24:59:245",
        "date": "2021.02.04 14:55:00:550",
        "finish_date": null,
        "count": "4",
        "c_id": "5e423f9168c51a786b398261",
        "client": "Ольга Зубкова",
        "stream": "Тест комплект с двойной строчкой"
    }
]
```

Параметры:<br>
**sub_id*** - Идентификатор заказа в котором есть подзаказы<br>

<br>

### Получение потока заказа в работе

Для получения потока заказа в работе необходимо отправить **`GET`** запрос на **`/api/order_stream/:id`**<br>

Пример ответа:<br>
```
[
    {
        "_id": "5cbb83829279efc1c8150a88",
        "type": "order",
        "position": [
            2,
            1
        ],
        "relation": [
            {
                "_id": "5cbc65e4631c979c2c5b2747",
                "so_id": "5cbb844a9279efc1c8150a89",
                "result": null,
                "firstPointIndex": 2,
                "secondPointIndex": 1
            }
        ]
    },
    {
        "_id": "5cbb844a9279efc1c8150a89",
        "o_id": "5cbc398f5e42968e114d6319",
        "type": "operation",
        "position": [
            2,
            2
        ],
        "relation": [
            {
                "_id": "5cbb844a9279efc1c8150a89",
                "so_id": "5cbb8d969279efc1c8150a8f",
                "result": "Выполнено",
                "firstPointIndex": 2,
                "secondPointIndex": 2
            },
            {
                "_id": "5cbc6953631c979c2c5b2749",
                "so_id": "5cc203189d461c6b6c790025",
                "result": "Отменить заказ",
                "firstPointIndex": 2,
                "secondPointIndex": 2
            }
        ],
        "worker": {
            "o_id": "5cbc398f5e42968e114d6319",
            "w_id": "5ccbfe9f5a65c541f061440b",
            "name": "Анна Иванова"
        },
        "operation": {
            "name": "Раскройка",
            "description": "Подбор лекал, по данным из заказа и раскройка материалов",
            "o_id": "5cbc398f5e42968e114d6319"
        }
    },
    {
        "_id": "5cbb8d969279efc1c8150a8f",
        "o_id": "5cbc39755e42968e114d6318",
        "type": "operation",
        "position": [
            2,
            3
        ],
        "relation": [
            {
                "_id": "5cbc44c85e42968e114d6325",
                "so_id": "5cbc45a95e42968e114d6327",
                "result": "Выполнено",
                "firstPointIndex": 2,
                "secondPointIndex": 3
            },
            {
                "_id": "5cbc471d5e42968e114d632c",
                "so_id": "5cbc5588631c979c2c5b2745",
                "result": "Найден брак",
                "firstPointIndex": 2,
                "secondPointIndex": 3
            }
        ],
        "worker": {
            "o_id": "5cbc39755e42968e114d6318",
            "w_id": "5ccbff095a65c541f061440e",
            "name": "Ольга Седурина"
        },
        "operation": {
            "name": "Вышивка ромбов",
            "description": "Подбор лекал, по данным из заказа и раскройка материалов",
            "o_id": "5cbc39755e42968e114d6318"
        }
    },
    {
        "_id": "5cbc45a95e42968e114d6327",
        "o_id": "5cbc39755e42968e114d6317",
        "type": "operation",
        "position": [
            2,
            4
        ],
        "relation": [
            {
                "_id": "5cbc468b5e42968e114d6329",
                "so_id": "5cbc4ea8631c979c2c5b2737",
                "result": "Выполнено",
                "firstPointIndex": 2,
                "secondPointIndex": 4
            },
            {
                "_id": "5cbc4f5d631c979c2c5b2739",
                "so_id": "5cbc5588631c979c2c5b2745",
                "result": "Найден брак",
                "firstPointIndex": 2,
                "secondPointIndex": 4
            }
        ],
        "worker": {
            "o_id": "5cbc39755e42968e114d6317",
            "w_id": "5ccbff215a65c541f061440f",
            "name": "Алёна Болотова"
        },
        "operation": {
            "name": "Cшивание комплекта",
            "description": "Подбор лекал, по данным из заказа и раскройка материалов",
            "o_id": "5cbc39755e42968e114d6317"
        }
    },
    {
        "_id": "5cbc4ea8631c979c2c5b2737",
        "o_id": "5cbc3c325e42968e114d631d",
        "type": "operation",
        "position": [
            3,
            4
        ],
        "relation": [
            {
                "_id": "5cbc502e631c979c2c5b273b",
                "so_id": "5cbc50d2631c979c2c5b273f",
                "result": "Выполнено",
                "firstPointIndex": 3,
                "secondPointIndex": 4
            },
            {
                "_id": "5cbc5074631c979c2c5b273d",
                "result": "Найден брак",
                "firstPointIndex": 3,
                "secondPointIndex": 4
            }
        ],
        "worker": {
            "o_id": "5cbc3c325e42968e114d631d",
            "w_id": "5ccbffa65a65c541f0614412",
            "name": "Ольга Козлова"
        },
        "operation": {
            "name": "Отстррочка",
            "description": "Подбор лекал, по данным из заказа и раскройка материалов",
            "o_id": "5cbc3c325e42968e114d631d"
        }
    },
    {
        "_id": "5cbc50d2631c979c2c5b273f",
        "o_id": "5cbc39755e42968e114d6317",
        "type": "operation",
        "position": [
            4,
            4
        ],
        "relation": [
            {
                "_id": "5cbc513a631c979c2c5b2741",
                "so_id": "5cbc5588631c979c2c5b2745",
                "result": "Выполнено",
                "firstPointIndex": 4,
                "secondPointIndex": 4
            },
            {
                "_id": "5cbc525e631c979c2c5b2743",
                "so_id": "5cbc5588631c979c2c5b2745",
                "result": "Найден брак",
                "firstPointIndex": 4,
                "secondPointIndex": 4
            }
        ],
        "worker": {
            "o_id": "5cbc39755e42968e114d6317",
            "w_id": "5ccbff215a65c541f061440f",
            "name": "Алёна Болотова"
        },
        "operation": {
            "name": "Cшивание комплекта",
            "description": "Подбор лекал, по данным из заказа и раскройка материалов",
            "o_id": "5cbc39755e42968e114d6317"
        }
    },
    {
        "_id": "5cbc5588631c979c2c5b2745",
        "o_id": "5cbc39755e42968e114d6345",
        "type": "operation",
        "position": [
            3,
            3
        ],
        "relation": [
            {
                "_id": "5cbc67a6631c979c2c5b2748",
                "so_id": "5cc2028e9d461c6b6c790024",
                "result": "Заказ выполнен",
                "firstPointIndex": 3,
                "secondPointIndex": 3
            },
            {
                "_id": "5cbf040b90a45834485c18e5",
                "so_id": "5cc1f20c9d461c6b6c790017",
                "result": "Вылезли нитки",
                "firstPointIndex": 3,
                "secondPointIndex": 3
            }
        ],
        "worker": {
            "o_id": "5cbc39755e42968e114d6345",
            "w_id": "5ccbffd35a65c541f0614415",
            "name": "Юлия Селянина"
        },
        "operation": {
            "name": "ОТК",
            "description": "Подбор лекал, по данным из заказа и раскройка материалов",
            "o_id": "5cbc39755e42968e114d6345"
        }
    },
    {
        "_id": "5cc1f20c9d461c6b6c790017",
        "s_id": "5cbf184e90a45834485c18e9",
        "type": "stream",
        "position": [
            2,
            4
        ],
        "relation": [
            {
                "_id": "5cc422f98ce16b1590ec9671",
                "so_id": "5cbc5588631c979c2c5b2745",
                "firstPointIndex": 2,
                "secondPointIndex": 4
            }
        ]
    },
    {
        "_id": "5cc2028e9d461c6b6c790024",
        "type": "order",
        "position": [
            2,
            4
        ],
        "relation": {
            "firstPointIndex": 2,
            "secondPointIndex": 4
        }
    },
    {
        "_id": "5cc203189d461c6b6c790025",
        "type": "order",
        "position": [
            2,
            4
        ],
        "relation": {
            "firstPointIndex": 2,
            "secondPointIndex": 4
        }
    }
]
```

Параметры:<br>
**id*** - Идентификатор заказа<br>

<br>

### Получение вложения потока заказа в работе

Для получения потока заказа в работе по id необходимо отправить **`GET`** запрос на **`/order_stream/:id/:s_id`**<br>

Пример ответа:<br>
```
[
    {
        "_id": "5cbf792a90a45834485c18ee",
        "o_id": "5cbc398f5e42968e114d6319",
        "position": [
            "2",
            "4"
        ],
        "relation": [
            {
                "_id": "5cbf79fc90a45834485c18f0",
                "oo_id": "5cbf7ac590a45834485c18f1",
                "result": "Выполнено",
                "firstPointIndex": "2",
                "secondPointIndex": "4"
            }
        ],
        "worker": {
            "o_id": "5cbc398f5e42968e114d6319",
            "w_id": "5ccbfe9f5a65c541f061440b",
            "name": "Анна Иванова"
        },
        "operation": {
            "name": "Раскройка",
            "description": "Подбор лекал, по данным из заказа и раскройка материалов",
            "o_id": "5cbc398f5e42968e114d6319"
        }
    },
    {
        "_id": "5cbf7ac590a45834485c18f1",
        "o_id": "5cbc39755e42968e114d6318",
        "position": [
            "2",
            "4"
        ],
        "relation": {
            "firstPointIndex": "2",
            "secondPointIndex": "4"
        },
        "worker": {
            "o_id": "5cbc39755e42968e114d6318",
            "w_id": "5ccbff095a65c541f061440e",
            "name": "Ольга Седурина"
        },
        "operation": {
            "name": "Вышивка ромбов",
            "description": "Подбор лекал, по данным из заказа и раскройка материалов",
            "o_id": "5cbc39755e42968e114d6318"
        }
    }
]
```

Параметры:<br>
**id*** - Идентификатор заказа<br>
**s_id*** - Идентификатор вложения<br>

<br>

### Изменение статус заказа находящегося в работе

Для изменения статуса заказа находящегося в работе необходимо отправить **`PUT`** запрос на **`/api/order`**<br>

Пример отправки параметров:<br>
```
{
    "id": "5cd7cdb868adbeddae98868e",
    "status": "canceled"
}
```

Параметры:<br>
**id*** - Идентификатор заказа в работе<br>
**status*** - Новый статус заказа<br>

Ответ:<br> коды состояний 204 или 404.

<br>

### Удаление сотрудника из заказа

Для удаления сотрудника из заказа необходимо отправить **`PUT`** запрос на **`/api/order_worker_delete`**<br>

Пример отправки параметров:<br>
```
{
    "_id": "5e6f705f12a21b2aed59d9bc",
    "w_id": "5d61a182abf1fe315164d29f"
}
```

Параметры:<br>
**_id*** - Идентификатор заказа<br>
**w_id*** - Идентификатор заказа<br>

Ответ:<br> коды состояний 204 или 404.

<br>

### Блокировка и разблокировка заказа находящегося в работе

Для блокировки и разблокировки заказа находящегося в работе необходимо отправить **`PUT`** запрос на **`/api/order_block`**<br>

Пример отправки параметров:<br>
```
{
    "_id": "5f10af0fa457e02ee88a0628",
    "block": true
}
```

Параметры:<br>
**_id*** - Идентификатор заказа<br>
**block*** - Блокируем (true) или разблокируем (false) заказ<br>

Ответ:<br> коды состояний 204 или 404.

<br>

### Изменение срочности заказа в работе

Для изменение срочности заказа в работе необходимо отправить **`PUT`** запрос на **`/api/order_urgently`**<br>

Пример отправки параметров:<br>
```
{
    "_id": "5f10af0fa457e02ee88a0628",
    "urgently": false
}
```

Параметры:<br>
**_id*** - Идентификатор заказа<br>
**urgently*** - Срочный (true) или не срочный (false) заказ<br>

Ответ:<br> коды состояний 204 или 404.

<br>

### Список сотрудников для операции

Для получения списка сотрудников для заказа необходимо отправить **`GET`** запрос на **`/api/order_worker_list/:_id`**<br>

Пример ответа:<br>
```
[
    {
        "_id": "5d60e3ed7c76c66d9a16a33e",
        "name": "Екатерина Юхачева"
    },
    {
        "_id": "5d60e42a7c76c66d9a16a340",
        "name": "Наталья Рыбина"
    },
    {
        "_id": "5d60e45b7c76c66d9a16a342",
        "name": "Наталья Бевер"
    }
    }
]
```

Параметры:<br>
**_id*** - Идентификатор операции для которой выводим список сотрудников<br>

<br>

### Добавление сотрудника в заказ

Для добавления сотрудника в заказ необходимо отправить **`PUT`** запрос на **`/api/order_worker_add`**<br>

Пример отправки параметров:<br>
```
{
	"_id": "5f10ae2533bde926149eb472",
    "worker":
        {
        "o_id": "5d61a182abf1fe315164d29f",
        "w_id": "5d61a182abf1fe315164d29f",
        "name": "Екатерина Юхачева"
        }
}
```

Параметры:<br>
**_id*** - Идентификатор заказа<br>
**worker*** - Объект с данными по сотруднику<br>
**o_id*** - Идентификатор операции<br>
**w_id*** - Идентификатор сотрудника<br>
**name*** - Имя сотрудника<br>

Ответ:<br> коды состояний 204 или 404.

<br>

### Создание нового заказа (в ожидании) администратором

Для создание нового заказа администратором необходимо отправить **`POST`** запрос на **`/api/new_order_pending`**<br>

Пример отправки параметров:<br>
```
{
   "status":"pending",
   "name":"Lada Нива 2121 1977-н.в.",
   "composition":
   {
        "auto":{
            "Марка":"Lada",
            "Модель":"Нива 2121",
            "Поколение":"1977-н.в.",
            "Как выглядят задние сиденья?":"Тип 2",
            "Как выглядят передние сиденья?":"Тип 2",
            "Есть ли кнопки откидывания задней спинки?":"Есть",
            "Установка":"true"
        },
        "list":{
            "Дизайн":"Classic",
            "Комплектность":"",
            "Количество":"1",
            "Основа":{
                "Материал":"Аригон гладкая",
                "Цвет":"Темно-коричневый"
            },
            "Подголовник":{
                "Материал":"Аригон гладкая",
                "Цвет":"Чёрный"
            },
            "Подголовник зад":{
                "Материал":"Аригон гладкая",
                "Цвет":"Оранжевый"
            }
            "Отстрочка":"Нет",
            "Стёжка":"Без стёжки",
            "Комментарий менеджеру":""
        },
        "price": 5000,
        "article": "Volkswagen_Golf Plus_2005-2014_55c-ef0_55b-55e"
   }
}
```

Ответ:<br> коды состояний 204 или 404.

<br>

### Редактирование заказа (в ожидании)

Для редактирования заказа необходимо отправить **`PUT`** запрос на **`/api/order_pending`**<br>

Пример отправки параметров:<br>
```
{
   "status":"pending",
   "name":"Lada Нива 2121 1977-н.в.",
   "composition":
   {
        "auto":{
            "Марка":"Lada",
            "Модель":"Нива 2121",
            "Поколение":"1977-н.в.",
            "Как выглядят задние сиденья?":"Тип 2",
            "Как выглядят передние сиденья?":"Тип 2",
            "Есть ли кнопки откидывания задней спинки?":"Есть",
            "Установка":"true"
        },
        "list":{
            "Дизайн":"Classic",
            "Комплектность":"",
            "Количество":"1",
            "Основа":{
                "Материал":"Аригон гладкая",
                "Цвет":"Темно-коричневый"
            }
            "Отстрочка":"Нет",
            "Стёжка":"Без стёжки"
        },
        "price": 5000,
        "article": "Volkswagen_Golf Plus_2005-2014_55c-ef0_55b-55e"
   }
}
```

Ответ:<br> коды состояний 204 или 404.

<br>

### Удаление заказа (в ожидании)

Для удаления заказа необходимо отправить **`DELETE`** запрос на **`/api/order_pending/:id`**<br>

Параметры:<br>
**id*** - Идентификатор заказа<br>

Ответ:<br> коды состояний 204 или 404.

<br>

### Удаление заказа (в работе)

Для удаления заказа необходимо отправить **`DELETE`** запрос на **`/api/order/:id`**<br>

Параметры:<br>
**id*** - Идентификатор заказа<br>

Ответ:<br> коды состояний 204 или 404.

<br>

### Пердача заказ в работу (в ожидании)

Для передачи заказа в работу необходимо отправить **`POST`** запрос на **`/api/order_execution`**<br>

Пример отправки параметров:<br>
```
{
    "_id": "618e55b4b05d2840612b4681",
    "s_id": "6193741bc03b9f58b55abf5e"
}
```

Ответ:<br> коды состояний 204 или 404.

<br>

### Получение списка потоков для заказа (в ожидании)

Для получения списка потоков для заказа необходимо отправить **`GET`** запрос на **`/api/stream_list`**<br>

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

### Получение потока выполненного заказа

Для получения потока выполненного заказа необходимо отправить **`GET`** запрос на **`/api/order_stream/:_id/`**<br>

Пример ответа:<br>
```
[
    {
        "operation": {
            "position": [
                0,
                2
            ],
            "relation": [
                {
                    "_id": "61c9e39e0c58e255f70ee215",
                    "firstPointIndex": 1,
                    "secondPointIndex": 3,
                    "so_id": "61c9e2e28452b203173288d9",
                    "startId": "61c9db4470fd4c52dd5f0910",
                    "result": "start proizvodnji polizdelkov",
                    "bgr_color": "#007AFC",
                    "function": []
                }
            ],
            "_id": "61c9db4470fd4c52dd5f0910",
            "type": "order",
            "status": "active"
        }
    },
    {
        "operation": {
            "position": [
                2,
                2
            ],
            "type": "operation",
            "relation": [
                {
                    "_id": "61ca1719d33d245dbba23f93",
                    "firstPointIndex": 1,
                    "secondPointIndex": 3,
                    "so_id": "61ca162d0c22d87d1b0f7d20",
                    "startId": "61c9dd30da1e897c2cf615e2",
                    "result": "Sestavljanje je zaključeno",
                    "bgr_color": "#F5982D",
                    "function": [
                        {
                            "_id": "61ca1719d33d245dbba23f97",
                            "type": "material",
                            "condition": "minus",
                            "value": 10,
                            "path": "Polizdelki.sp uležajenje SL"
                        },
                        {
                            "_id": "61ca1719d33d245dbba23f96",
                            "type": "material",
                            "condition": "minus",
                            "value": 10,
                            "path": "Polizdelki.zg uležajenje"
                        }
                    ]
                }
            ],
            "_id": "61c9dd30da1e897c2cf615e2",
            "o_id": "61c9dd240c58e255f70ee18d",
            "so_status": {
                "status": "active"
            }
        },
        "operation_name": "Sestavljanje",
        "worker_name": "zaposleni 3",
        "w_id": "61a51de117c2887ade9105f2"
    },
    {
        "operation": {
            "position": [
                1,
                2
            ],
            "type": "operation",
            "relation": [
                {
                    "_id": "61c9e39e0c58e255f70ee20b",
                    "firstPointIndex": 1,
                    "secondPointIndex": 3,
                    "so_id": "61c9dd30da1e897c2cf615e2",
                    "startId": "61c9e2e28452b203173288d9",
                    "result": "Polizdelki so narejeni",
                    "bgr_color": "#2EA877",
                    "function": [
                        {
                            "_id": "61c9e39e0c58e255f70ee20e",
                            "type": "material",
                            "condition": "plus",
                            "value": 10,
                            "path": "Polizdelki.sp uležajenje SL"
                        },
                        {
                            "_id": "61c9e39e0c58e255f70ee20d",
                            "type": "material",
                            "condition": "plus",
                            "value": 10,
                            "path": "Polizdelki.zg uležajenje"
                        }
                    ]
                }
            ],
            "_id": "61c9e2e28452b203173288d9",
            "o_id": "61c9e2cb0c58e255f70ee1e9",
            "so_status": {
                "status": "complete"
            }
        },
        "operation_name": "Proizvodnja polizdelkov",
        "worker_name": "zaposleni 2",
        "w_id": "61a51dd117c2887ade9105f0"
    },
    {
        "operation": {
            "position": [
                3,
                2
            ],
            "type": "order",
            "relation": [],
            "_id": "61ca162d0c22d87d1b0f7d20",
            "status": "complete"
        }
    }
]
```
