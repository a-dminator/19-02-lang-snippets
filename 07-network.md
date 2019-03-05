Для работы с сетью, вы можете использовать следующую библиотеку:
```
implementation 'com.squareup.okhttp3:okhttp:3.11.0'
```

#### Создание запроса
Сформировать запрос на сервер, вам поможет класс `Request.Builder`. Вам необходимо создать его объект. Затем с помощью соответствующих функций задать необходимые параметры. После - вызвать функцию `build` и записать её результат в константу.  
`url` - адрес файла в сети  
```
val request = Request.Builder()
    .url("<url>")
    .build()
```

#### Выполнение запроса
Чтобы выполнить запрос, вам понадобится объект класса `OkHttpClient` и сам запрос. В результате выполнения вы получите ответ от сервера (`response`)
```
val client = OkHttpClient()
val response = client.newCall(request).execute()
```

#### Получение JSON из ответа
Если вы ожидаете получить JSON в резульате запроса, вам нужно получить тело ответа как строку
```
val json = response.body()!!.string()
```

#### Десериалиация (парсинг) JSON
Вам нужно описать класс, структура которого совпадает со структурой JSON. Если ваш JSON:
```
{
    "title": "Помидор",
    "imageUrl": "https://mySite.com/tomato.jpg"
}
```
То класс должен быть:
```
@Serializable
class Product(
    val title: String,
    val imageUrl: String
)
```
Если ваш JSON - это список, то достаточно описать структуру одного элемента
```
[
    {
        "title": "Помидор",
        "imageUrl": "https://mySite.com/tomato.jpg"
    },
    {
        "title": "Картофель",
        "imageUrl": "https://mySite.com/potato.jpg"
    }
]
```
Класс:
```
@Serializable
class Product(
    val title: String,
    val imageUrl: String
)
```
Саму десериализацию вы можете сделать с помощью функции `Json.parse` из библиотеки `kotlinx.serialization`  
`1 аргумент` - сериализатор класса с нужной структорой  
`2 аргумент` - строка с JSON внутри
```
Json.parse(Product.serializer(), productJson)
```
Чтобы получить сериализатор для списка, поулчите константу `list` у сериализатора класса одного элемента
```
Json.parse(Product.serializer(), productJson)
```