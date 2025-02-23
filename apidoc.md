## Работа с наборами

### Добавление продуктов в набор

POST /api/v1/kits/id/products

Набор — перечень возможных продуктов в приложении для их продажи.

Параметры набора: идентификатор набора, название набора, список набора состоящий из идентификаторов продуктов и их количества.

Параметры продукта: идентификатор продукта, название продукта, количество продукта, вес продукта, цена продукта

**Параметры запроса:**

id - id набора в таблице kit_model. Передается в url, число

productsList - список продуктов набора. Массив, содержащий id продуктов и их количества. Передается в теле запроса. Тип - строка

**Пример запроса**

POST /api/v1/kits/8/products

{

    "productsList": \[

        {

            "id": 1,

            "quantity": 2

        },

        {

            "id": 6,

            "quantity": 2

        }

    \]

}

**Ответ - успех**

  HTTP/1.1 200 OK

 {

    "id": 2,

    "name": "Мой набор для выходных",

    "productsList": \[

        {

            "id": 1,

            "name": "Икра красная Белое море",

            "price": 45,

            "weight": 5,

            "units": "кг",

            "quantity": 2

        },

        {

            "id": 5,

            "name": "Багет французский",

            "price": 15,

            "weight": 1,

            "units": "кг",

            "quantity": 2

        }

    \],

    "productsCount": 4

}

**Ответ - ошибка
**Набор не найден

HTTP/1.1 404 Not found.

{

       "code": 404,

       "message": "Not found"

   }


## Работа с доставкой

### Курьерская служба “Привезём быстро“

POST /fast-delivery/v3.1.1/calculate-delivery.xml

Служба должна работать в указанное в заказе время

**Параметры запроса:**

productsCount- Количество продуктов в заказе. Тип - число

productsWeight- Вес продуктов. Тип - число

deliveryTime - Планируемое время доставки. Тип число

**Пример запроса**

POST /fast-delivery/v3.1.1/calculate-delivery.xml

<InputModel>

    <productsCount>2</productsCount>

    <productsWeight>5.1</productsWeight>

    <deliveryTime>20</deliveryTime>

</InputModel>

**Пример ответа**

HTTP/1.1 200 OK

<response name="Привезём быстро" isItPossibleToDeliver="true" hostDeliveryCost="43" clientDeliveryCost="0">

    <toBeDeliveredTime>

        <min>25</min>

        <max>30</max>

    </toBeDeliveredTime>

</response>


## Работа с корзиной

### Получение продуктов

GET /api/v1/orders/id

**Параметр**

id корзины в таблице order_model. Передается в url, число

**Пример запроса**

GET /api/v1/orders/1

**Ответ - успех**

HTTP/1.1 200 OK

\[

    {

           "id": 1,

           "name": "Сок Jumex апельсин без сахара",

           "price": 149,

           "weight": 473,

           "units": "мл",

           "quantity": 3

       },

    {

           "id": 4,

           "name": "Sprite классический",

           "price": 79,

           "weight": 900,

           "units": "мл",

           "quantity": 4

       }

    \]

**Ответ - ошибка**

Корзина не найдена

HTTP/1.1 404 Not found.

{

       "code": 404,

       "message": "Not found"

}

### Добавление товаров

PUT /api/v1/orders/id

**Параметры:**

id корзины в таблице order_model. Передается в url, число

productsList список продуктов, которые надо добавить в корзину, содержащий id продуктов и их количества. Передается в теле запроса, массив

**Пример запроса**

PUT /api/v1/orders/1

{

    "productsList": \[

        {

            "id": 1,

            "quantity": 4

        },

        {

            "id": 5,

            "quantity": 2

        }

    \]

}

**Ответ - успех**

 HTTP/1.1 200 OK

 {

"productsList": \[

    {

        "id": 1,

        "quantity": 10

    },

    {

        "id": 5,

        "quantity": 10

    }

\],

        "status": 0,

        "deliveryPriceOur": 30,

        "deliveryTime": "25\~30",

        "courierService": "Привезём быстро",

        "deliveryPrice": 0,

        "wareHouse": "Шведский дом",

        "userId": 1,

        "id": 5,

        "productsCost": 75,

        "finalCCost": 174

    }

**Ответ - ошибка**

Корзина не найдена

HTTP/1.1 404 Not found.

{

       "code": 404,

       "message": "Not found"

}

Нет склада, способного обработать Ваш заказ

HTTP/1.1 409 Conflict.

{

       "code": 409,

       "message": "Нет склада, способного обработать Ваш заказ"

}

### Удаление корзины

DELETE /api/v1/orders/:id

**Параметр**

id корзины в таблице order_model. Передается в url, число

**Пример запроса**

DELETE /api/v1/orders/1

**Ответ - успех**

HTTP/1.1 200 OK

{

       "ok": true

}

**Ответ - ошибка**

Корзина не найдена

HTTP/1.1 404 Not found.

{

       "code": 404,

       "message": "Not found"

}


