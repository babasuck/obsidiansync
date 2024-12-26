https://education.yandex.ru/handbook/python
## Строки, кортежи, списки

*Список* - изменяемый тип данных, имеет целочисленные индексы, отрицательные индексы начинаются с конца, при обращении по несуществующему индексу – IndexError

```python
nums = [1, 2, 3]
mixed = ['a', 1, 0.5] # можно хранить данные разного типа
empty = []
nested = [1, 2, [3, 4], [5]]

nums[0] # 1
nums[-1] # 3
nums[3] # IndexError

# Итерация по списку

for el in nums:
	print(el)

for i in range(len(nums)):
	print(nums[i])

```

### *Операции и Срезы
Умножение - повторяет список n раз
Срезы возвращают copy
```python
text = "Привет, мир!"
print(text[8:11])
print(text[:6])
print(text[8:])
print(text[:])
print(text[::2])
#мир 
#Привет
#мир!
#Привет, мир!
#Пие,мря

numbers = [1, 2, 3, 4, 5] 
del numbers[::2] 
print(numbers)
# [2, 4]

```

| Метод     | Описание                                                                     |
| --------- | ---------------------------------------------------------------------------- |
| clear()   | Removes all the elements from the list                                       |
| copy()    | Returns a copy of the list                                                   |
| count()   | Returns the number of elements with the specified value                      |
| extend()  | Add the elements of a list (or any iterable), to the end of the current list |
| index()   | Returns the index of the first element with the specified value              |
| insert()  | Adds an element at the specified position                                    |
| pop()     | Removes the element at the specified position                                |
| remove()  | Removes the first item with the specified value                              |
| reverse() | Reverses the order of the list                                               |
| sort()    | Sorts the list                                                               |

## Кортежи (tuple)
Кортеж - неизменяемый список 
```python
a = (1, 2)
b = (1, )
```

## Методы работы со строками

| Метод        | Описание                                                                                         |
| ------------ | ------------------------------------------------------------------------------------------------ |
| capitalize() | Возвращает копию строки, у которой первая буква заглавная, а остальные приведены к строчным      |
| count()      | кол-во определенных подстрок не перекрывающееся                                                  |
| startwith()  | начинается ли с заданной подстроки или одной из подстрок в кортеже например ('a', 'b', 'c')      |
| endwith()    | тоже самое толлько с концом                                                                      |
| find()       | индекс первого вхождения подстроки или -1 если нет                                               |
| index()      | индекс первого вхождения подстроки или вызывает исключение ValueError, если подстрока не найдена |
| isalnum()    | если все символы буквы и цифры                                                                   |
| isalpha()    | если все символы буквы                                                                           |
| isdigit()    | если все символы цифры                                                                           |
| islower()    | если все маленькие                                                                               |
| isupper()    | если все большие                                                                                 |
| join()       | конкатенирует все элементы коллекции через разделитель                                           |
| lower()      | привести к маленьким                                                                             |
| upper()      | привести к большим                                                                               |
| split()      | разделить по разделителю и вернуть список                                                        |
| title()      | каждое отдельное слово будет с большой буквы                                                     |
