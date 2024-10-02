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

| append()  | Adds an element at the end of the list                                       |
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


