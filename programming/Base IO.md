
## Ввод
```python
def input(*args, **kwargs): # real signature unknown  
"""  
Read a string from standard input.  The trailing newline is stripped.
The prompt string, if given, is printed to standard output without a trailing newline before reading input.
"""
name = input("What`s your name?")
```

## Вывод
```python
def print(self, *args, sep=' ', end='\n', file=None)
"""  
Prints the values to a stream, or to sys.stdout by default.  
sep    string inserted between values, default a space. 
end    string appended after the last value, default a newline.  
file    a file-like object (stream); defaults to the current sys.stdout.  
flush    whether to forcibly flush the stream.
"""

print("Hello")
print("Hello", "world")
print("Hello", name, "!")
```
## Форматированный вывод 

- `\n` — переход на новую строку;
- `\t` — табуляция;
- `\r` — возврат каретки в начало строки;
- `\b` — возврат каретки на один символ.
https://docs.python.org/3/tutorial/inputoutput.html#formatted-string-literals - про f строки

```python
# Выравнивание
print(f"{123:0>9}") #000000123
print(f"{123:0<9}") #123000000
print(f"{123:0^9}") #000123000

print(f"{math.pi:.4f}")
```

