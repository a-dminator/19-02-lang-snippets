Чтобы корутины заработали, необходимо подключить следующие зависимости:
```
implementation 'org.jetbrains.kotlinx:kotlinx-coroutines-core:1.1.1'
implementation 'org.jetbrains.kotlinx:kotlinx-coroutines-android:1.1.1'
```

#### Создание контекста
```
GlobalScope.launch(Dispatchers.Main) {
 
}
```

#### Запуск задачи в фоне
Результат выполнения задачи должен быть на последней строчке
```
GlobalScope.async(Dispatchers.IO) {
    "Результат выполнения"
}
```

Внутри функции высшего порядка, передаваемой `GlobalScope.async`, можно написать любой код
```
GlobalScope.async(Dispatchers.IO) {

    // Здесь может быть сколько угодно
    // строк любого кода
    
    val hello = "Hello"
    val world = "world"
    
    "$hello, $world"
}
```

Функция `GlobalScope.async` возвразщает `Deferred` (отложенный результат). Чтобы получить сам результат, нужно вызвать функцию `await` (дождаться) у `Deferred`
```
val greetingDeferred = GlobalScope.async(Dispatchers.IO) { 
    "Hello, world!" 
}

// Константа greeting сожержит внутри значение "Hello, world!"
val greeting = greetingDeferred.await()

// Вывод значния внутри константы greeting на экран
print(greeting)
```

Можно запустить несколько фоновых задач параллельно. Они будут исполнятся одновременно друг с другом
```
val fbDeferred = GlobalScope.async(Dispatchers.IO) {
    delay(1000) // задержка 1000 мс (1 сек)
    "Лента Facebook"
}

val vkDeferred = GlobalScope.async(Dispatchers.IO) {
    delay(1000) // задержка 1000 мс (1 сек)
    "Лента ВКонтакте"
}

val fb = fbDeferred.await()
val vk = vkDeferred.await()

print("$fb $vk") // Выведется через 1 сек т.к. задачи выполнятся параллельно
```

Формирование списка в фоне:
```
class Product

GlobalScope.async(Dispatchers.IO) {
    
    val meat = Product()
    val potato = Product()
    val shampoo = Product()
    
    listOf(meat, potato, shampoo)
}
```

Использование `GlobalScope.launch` и `GlobalScope.async` вместе:
```
GlobalScope.launch(Dispatchers.Main) {
    
    val greetingDeferred = GlobalScope.async(Dispatchers.IO) { 
        "Hello, world!" 
    }
     
    val greeting = greetingDeferred.await()
    
    // Вывод "Hello, world!" на экран
    print(greeting)
}
```