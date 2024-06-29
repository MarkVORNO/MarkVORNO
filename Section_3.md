## ﻿**Раздел 3 - Тестирование API**

В данном разделе описана работа с запросами REST API в Swagger и Postman на примере тестирования онлайн-магазина.

Перед началом тестирования запросов, необходимо авторизоваться, для этого через post запрос генерирую токен:

![](assets/Aspose.Words.12dfdc4c-ee1c-4457-b071-31083f5085b3.001.png)

![](assets/Aspose.Words.12dfdc4c-ee1c-4457-b071-31083f5085b3.002.png)

Данный токен использую для авторизации
 
**Swagger:**

![](assets/Aspose.Words.12dfdc4c-ee1c-4457-b071-31083f5085b3.003.png)**

**Postman:** Auth Type выбираю Bearer Token

![](assets/Aspose.Words.12dfdc4c-ee1c-4457-b071-31083f5085b3.004.png)

### 1) **Запрос GET**

   Задача: Протестировать метод GET Customers

   ![](assets/Aspose.Words.12dfdc4c-ee1c-4457-b071-31083f5085b3.005.png)

   Try it out —-> Execute

   ![](assets/Aspose.Words.12dfdc4c-ee1c-4457-b071-31083f5085b3.006.png)

   Код ответа 200, проверяем тело ответа.

   **В Postman**

   ![](assets/Aspose.Words.12dfdc4c-ee1c-4457-b071-31083f5085b3.007.png)

 

### 2) **Запрос POST**

   Тестирую запрос POST на Customers добавив нового покупателя

   ![](assets/Aspose.Words.12dfdc4c-ee1c-4457-b071-31083f5085b3.008.png)

   Дополнительно необходимо узнать “RegionId” с помощью GET/Region

   ![](assets/Aspose.Words.12dfdc4c-ee1c-4457-b071-31083f5085b3.009.png)

   Ввожу все необходимые данные в тело запроса в JSON формате: 

   ```
   {

   `  `"firstName": "Portfolio",

   `  `"lastName": "Man",

   `  `"phone": "+79222222222",

   `  `"email": "malco@gmail.com",

   `  `"regionId": "5ba06412-c31e-4c1b-b61b-7780092ca83d",

   `  `"sex": "MALE"

   }
   ```

Отправляю запрос POST.

![](assets/Aspose.Words.12dfdc4c-ee1c-4457-b071-31083f5085b3.010.png)

Проверяю код ответа 201.

Далее с помощью запроса GET/Customers/{id} проверяю, что пользователь добавлен.

![](assets/Aspose.Words.12dfdc4c-ee1c-4457-b071-31083f5085b3.011.png)

Теперь протестируем в Postman, добавив точно такого же пользователя с таким же email.

![](assets/Aspose.Words.12dfdc4c-ee1c-4457-b071-31083f5085b3.012.png)

В ответе видно, что система не позволяет создать двух пользователей с одинаковой почтой (код 422 “пользователь с этой почтой уже есть в системе”) 

### 3) **Запрос PATCH**

   Теперь попробуем изменить почту созданного аккаунта с помощью запроса PATCH:

   С помощью запроса GET/Customers/{id} узнаем id, в теле PATCH/Customers/{id} указываем новую почту:

   ![](assets/Aspose.Words.12dfdc4c-ee1c-4457-b071-31083f5085b3.013.png)

   Отправляем запрос.

   Ответ:

   ![](assets/Aspose.Words.12dfdc4c-ee1c-4457-b071-31083f5085b3.014.png)

   С помощью запроса GET проверяю, что почта изменилась

   ![](assets/Aspose.Words.12dfdc4c-ee1c-4457-b071-31083f5085b3.015.png)

   В Postman изменим фамилию с “Man” на “Oleg”:

   ![](assets/Aspose.Words.12dfdc4c-ee1c-4457-b071-31083f5085b3.016.png)


### 4) **Запрос DELETE**

Удаляю созданного покупателя с помощью запроса DELETE/Customers/{id}

![](assets/Aspose.Words.12dfdc4c-ee1c-4457-b071-31083f5085b3.017.png)

Проверяю, что при запросе GET/Customers/{id} выдает 404

![](assets/Aspose.Words.12dfdc4c-ee1c-4457-b071-31083f5085b3.018.png)


