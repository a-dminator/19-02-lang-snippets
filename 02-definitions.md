# Определения

#### Функция (`fun`):
Выражают действия. В результате дают значение  
*Синтаксис:*
```
fun <name>(<param1Name>: <Param1Type>, <param2Name>: <Param2Type>, ...): <Type (optional)> = <expression> 
```
Примеры использования:
```
sum(2, 3.0)
sum(first = 2, second = 3.0)
```
На экран напечатается `5.0`
```
println(sum(2, 3.0))
```
`fun` означает начало объявления функции  
`sum` - имя функции  
`first` - имя первого параметра  
`Int` - тип первого параметра. Целое число
`second` - имя второго параметра  
`Double` - тип второго параметра. Вещественное число  

#### Константа (`val`):
Запоминают значение  
*Синтаксис:*
```  
val <name>: <Type (optional)> = <expression> 
```
Примеры объявления:
```
val solution = sum(2, 3.0)
val solution = 5.0
```
Пример использования:
```
solution
```
На экран напечатается `5.0`
```
println(solution)
```
`val` означает начало объявления константы  
`solution` - имя константы

#### Переменная (`var`):
Запоминают значение, которое может измениться в последствии  
*Синтаксис:*
```  
var <name>: <Type (optional)> = <expression> 
```  
Примеры объявления:
```
var registrationStep = 2.0
registrationStep = 3.0
```
Пример использования:
```
registrationStep
```
На экран напечатается `3.0`, затем `4.0` 
```
println(registrationStep)
registrationStep = 4.0
println(registrationStep)
```

# Выражения
Всё, что в резульате даёт значение является выражением
#### Фиксированное значение (литерал)
Примеры:
```
5
2.0
"Hello world!"
```

#### Условное выражение
В результате даёт значение в зависимости от соблюдения условия  
*Синтаксис:*
```
if (<condition, Boolean value>) <value if condition is true> else <value if condition is false> 
```
Если дождливо, то текст - "Нужен зонт". Иначе текст - "Не нужен зонт". После чего текст выводится на экран
```
val isRainy = true
val text = if (isRainy) "Нужен зонт" else "Не нужен зонт"
println(text) 
```
Если дождливо - вывести "Нужен зонт". Иначе вывести "Не нужен зонт"
```
val isRainy = true
val text = if (isRainy) println("Нужен зонт") else println("Не нужен зонт") 
```

#### Множественное условное выражение:
*Синтаксис:*
```
when {
    <condition 1> -> <value if condition 1 is true>
    <condition 2> -> <value if condition 2 is true>
    <condition 3> -> <value if condition 3 is true>
    else -> <value if all conditions (1, 2 and 3) is false>
}
```
```
when (<matching>) {
    <value 1> -> <value if matching equals value 1>
    <value 2> -> <value if matching equals value 1>
    <value 3> -> <value if matching equals value 1>
    else -> <value if matching is none of value 1, 2, 3>
}
```
Примеры:
```
val number = 3
val numberString = when {
    number == 0 -> "zero"
    number == 1 -> "one"
    number == 2 -> "two"
    number == 3 -> "three"
    else -> "another number"
}
println(numberString)
```
```
val number = 3
val numberString = when (number) {
    0 -> "zero"
    1 -> "one"
    2 -> "two"
    3 -> "three"
    else -> "another number"
}
println(numberString)
```
#### Логический тип
Может быть `true` или `false`. Испольузется для условных выражений
```
val number = 1
val isOne = number == 1
```
Выражения:  
`a == b` - проверка на равенство. `true` если `a` равно `b`  
`a > b` - больше  
`a < b` - меньше  
`a >= b` - больше или равно  
`a <= b` - меньше или равно  
Комбинации:  
`a > b && c > d` - логическое "и". `true` если `a` > `b` и `c` > `d`
`a > b || c > d` - логическое "или". `true` если `a` > `b` или `c` > `d`    