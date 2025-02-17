```rust
fn main() {
    println!("Hello, world!");
}
```

[[Cargo]] - система сборки для раста и менеджер пакетов
```shell
cargo new name # создать проект name
cargo run
cargo build 
```

rustc - компилятор

```shell
rustc main.rs
```

----

## Переменные, константы 

По умолчанию создаваемые переменные в Rust - неизменяемые (immutable). 
```rust
fn main() {
    let x = 5;
    println!("The value of x is: {x}");
    x = 6; // compile error ^^^^^ cannot assign twice to immutable variable
    println!("The value of x is: {x}");
}
```

Ключевое слово `let` связывает переменную со значением.
```rust
let (part1, part2) = (1, 2);
let a: i32 = 5;
```

Однако, переменную можно сделать изменяемой добавив ключевое слово `mut` перед именем переменной.
```rust
let mut x = 5;
x = 10; // OK
```

**Константы** 
Всегда immutable. Обязательна аннотация типа.
```rust
const PI: f64 = 3.1415;
```

**Shadowing**
```rust
let x: u32 = 10;
{
	let x: f32 = 5.54;
	println!("{x}"); // 5.54 and dif type. inner x shadowed outer
}
println!("{x}"); // 10
```

## Statements and Expressions

- **Statements** are instructions that perform some action and do not return a value.
- **Expressions** evaluate to a resultant value.

```rust
let mut y = 6; // statement
fn foo() {} // statement
foo() // expr
{ 5 + 6 } // expr
{
	let x = 3;
	x + 3 // Expressions do not include ending semicolons
} // expr, returns 6

let a = {
	let x = 10;
	x + 20 // Expressions do not include ending semicolons
}; // expr
```
## Типы данных

Rust статические типизирован.
Есть две группы вида данных: скалярные и составные. 
### Скалярные
[Операции с числами](https://doc.rust-lang.org/book/appendix-02-operators.html)
#### Целочисленные типы

| Length (bits)   | Signed  | Unsigned |
| --------------- | ------- | -------- |
| 8               | `i8`    | `u8`     |
| 16              | `i16`   | `u16`    |
| 32              | `i32`   | `u32`    |
| 64              | `i64`   | `u64`    |
| 128             | `i128`  | `u128`   |
| arch (64 or 32) | `isize` | `usize`  |
`arch` - архитектурно зависимый тип, 64 бит на x64, 32 на x32 

Формы записи целочисленных чисел

| Number literals  | Example       |
| ---------------- | ------------- |
| Decimal          | `98_222`      |
| Hex              | `0xff`        |
| Octal            | `0o77`        |
| Bin              | `0b1111_0000` |
| Byte (`u8` only) | `b'A'`        |

#### Вещественные
`f32` и `f64` как `float` и `double` соответсвенно.
Floating-point numbers are represented according to the *IEEE-754* standard. The `f32` type is a single-precision float, and `f64` has double precision.


#### Boolean + char

`char` - 4 байта
`bool` - 1 байт
```rust
let a: bool = true;
let c: char = 'A';
let heart_eyed_cat = '😻';
```


### Составные типы

В Rust два составных типа - массивы и кортежи

#### Кортеж
Неизменяемый. Группирует несколько значений (можно разного типа).

```rust
let tup: (i32, f32, char) = (1, 1.5, 'A');
let (x, y, z) = tup;
```

Обращаться к элементам кортежа можно через `.`
```rust
let x: (i32, f64, u8) = (500, 6.4, 1);
let five_hundred = x.0;
let six_point_four = x.1;
let one = x.2;
```

The tuple without any values has a special name, _unit_. This value and its corresponding type are both written `()` and represent an empty value or an empty return type. Expressions implicitly return the unit value if they don’t return any other value.

#### Массив
Создается на стеке, на куче используется вектор.
```rust
let arr = [1, 2, 3, 4, 5];
let arr1: [i32; 5] = [1, 2, 3, 4, 5]
let arr2: [i32, 5] = [1; 10]; // тоже самое что и 10 1 [1, 1, 1 ..., 1]
```

Обращение к элементам как обычно через `[]`. Если обратиться к несущ. индексу, программа упадет (Runtime Error), не обратившись к памяти (безопасно).


## Функции

Rust code uses _snake case_ as the conventional style for function and variable names, in which all letters are lowercase and underscores separate words. 

```rust
fn my_foo() {
	println!("Im foo");
}
```

У параметров обязательно нужно указывать тип.
```rust
fn main() { my_foo_with_params(5, 'h'); }
fn my_foo_with_params(x: i32, y: char) {
	println!("you passed - {x}{y}");
}
```

Функция - *expression*. Если функция возвращает что-то должен указываться тип через `->` , иначе она возвращает `()` (unit).
```rust

fn five() -> u32 {
	5
} // OK

fn five_plus_x(x: i32) -> i32 {
	x + 5; // Error bc of ; 
}

fn five_plus_x(x: i32) -> i32 {
	x + 5 // OK
}
```
