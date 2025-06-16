# Rust - Лабораторная работа №1
## Информация о студенте
Шарманов ДА, 1 курс, ИВТ-1.1
## Задача 1
### Постановка задачи
Напишите программу, которая запрашивает у пользователя имя и выводит на экран приветственное сообщение с использованием этого имени.
### Математическая модель
--
### Список идентификаторов
| Имя  | Тип    | Смысл                       |
| ---- | ------ | --------------------------- |
| name | string | Хранение имени пользователя |
### Код программы
```Rust
use std::io;

fn main() {
    println!("Enter your name: ");

    let mut name = String::new();

    // Читаем строку
    io::stdin()
        .read_line(&mut name)
        .expect("Can not read the string");

    // Обрезаем пробелы
    let name = name.trim();

    print!("Hello, {}!", name);
}
```

### Результаты выполненной работы
[![image.png](https://i.postimg.cc/HsV55gHr/image.png)](https://postimg.cc/ppMpb3mv)
## Задача 2
### Постановка задачи
Создайте переменную типа целое беззнаковое число и выведите ее значение на экран. Явно укажите тип переменной. Затем измените значение переменной и снова выведите его.
### Математическая модель
--
### Список идентификаторов
| Имя | Тип | Смысл                                   |
| --- | --- | --------------------------------------- |
| num | u32 | Хранение и изменение беззнакового числа |
### Код программы
```Rust
fn main() {
    let mut num: u32 = 22;
    println!("Первоначальное значение x: {}", num);
    num = 13;
    println!("Новое значение x: {}", num);
}
```
### Результаты выполненной работы
[![image.png](https://i.postimg.cc/vm3H34tb/image.png)](https://postimg.cc/8FfSCPY0)
## Задача 3
### Постановка задачи
Напишите функцию, которая принимает строку и возвращает ее длину (количество символов). Затем вызовите эту функцию с различными строками.
### Математическая модель
--
### Список идентификаторов
| Имя                       | Тип   | Смысл                          |
| ------------------------- | ----- | ------------------------------ |
| s                         | &str  | Параметр функции string_length |
| s1, s2, s3                | &str  | Тестовые строки                |
| len_s1, len_s2, len_s3    | usize | Перменные с размерностью строк |

### Код программы
```Rust
fn string_length(s: &str) -> usize {
    s.chars().count()
}

fn main() {
    // Тестовые строки
    let s1: &str = "one";
    let s2: &str = "hi";
    let s3: &str = "hello";

    // Перменные хранящие длины строк
    let len_s1: usize = string_length(s1);
    let len_s2: usize = string_length(s2);
    let len_s3: usize = string_length(s3);

    println!("Str len \"{}\": {}", s1, len_s1);
    println!("Str len \"{}\": {}", s2, len_s2);
    println!("Str len \"{}\": {}", s3, len_s3);
}
```
### Результаты выполненной работы
[![image.png](https://i.postimg.cc/8zC1spVY/image.png)](https://postimg.cc/hfHF5qv8)
## Задача 4
### Постановка задачи
Задайте структуру Car с полями brand, model и year, и создайте несколько экземпляров этой структуры. Выведите информацию о каждой машине на экран.
### Математическая модель
--
### Список идентификаторов
| Имя              | Тип    | Смысл                               |
| ---------------- | ------ | ----------------------------------- |
| Car              | struct | Структура для описания автомобиля   |
| brand            | String | Поле структуры для хранения бренда. |
| model            | String | Поле структуры для хранения модели. |
| year             | u32    | Поле структуры для хранения года.   |
| car1, car2, car3 | Car    | Экземпляры структуры Car            |

### Код программы
```Rust
struct Car {
    brand: String,
    model: String,
    year: u32,
}

fn main() {
    let car1 = Car {
        brand: "Haval".to_string(),
        model: "Jolion".to_string(),
        year: 2020,
    };
    let car2 = Car {
        brand: "Toyota".to_string(),
        model: "Corolla".to_string(),
        year: 1995,
    };
    let car3 = Car {
        brand: "Ford".to_string(),
        model: "Focus".to_string(),
        year: 2007,
    };

    // Вывод переменных
    println!("Car 1: {} {} ({})", car1.brand, car1.model, car1.year);
    println!("Car 2: {} {} ({})", car2.brand, car2.model, car2.year);
    println!("Car 3: {} {} ({})", car3.brand, car3.model, car3.year);
}
```

### Результаты выполненной работы
[![image.png](https://i.postimg.cc/L5vcMPh8/image.png)](https://postimg.cc/n9jR4Cvy)
## Задача 5
### Постановка задачи
Напишите программу, которая запрашивает у пользователя число 𝑁 и выводит на экран 𝑁-ное число Фибоначчи. Используйте рекурсию для решения этой задачи.
### Математическая модель
$$
F(n) = 
\begin{cases}
0, & \textrm{если } n=0 \\
1, & \textrm{если } n=1 \\
F(n-1) + F(n-2), & \textrm{если } n \geq 2
\end{cases}
$$
### Список идентификаторов
| Имя    | Тип                     | Смысл                 |
| ------ | ----------------------- | --------------------- |
| num    | u32                     | Номер числа Фибоначчи |
| result | u64                     | Число Фибоначчи       |
| input  | String                  | Строка ввода          |
### Код программы
```Rust
use std::io; 

// Функция для вычисления числа Фибоначчи
fn f(num: u32) -> u64 { 
    match num {
        0 => 0,
        1 => 1,
        _ => f(num - 1) + f(num - 2), // Рекурсия
    }
}

fn main() {
    println!("Enter n:");
    let mut input = String::new(); 
    io::stdin().read_line(&mut input).expect("Error"); 
    let n: u32 = input.trim().parse().expect("Enter int");
    let result = f(n); 
    println!("{} Fibonacci number: {}", n, result);
}
```
### Результаты выполненной работы
[![image.png](https://i.postimg.cc/7YGFR5ww/image.png)](https://postimg.cc/tYbvZCsM)

## Задача 6
### Постановка задачи
Реализуйте перечисление DayOfWeek для дней недели. Напишите функцию, которая принимает день недели и возвращает следующий день. Обработайте случаи перехода на следующий день недели, если текущий день– воскресенье.
### Математическая модель
--
### Список идентификаторов
| Имя       | Тип                  | Смысл                                 |
| --------- | -------------------- | ------------------------------------- |
| DayOfWeek | enum                 | Перечисление дней недели              |
| day       | DayOfWeek (параметр) | Параметр функции next_day             |
| today     | DayOfWeek            | Переменная, хранящая сегодняшний день |
| tomorrow  | DayOfWeek            | Переменная, хранящая завтрашний день  |
### Код программы
```Rust
#[derive(Debug)] 
// Перечисление дней недели
enum DayOfWeek {
    Monday,
    Tuesday,
    Wednesday,
    Thursday,
    Friday,
    Saturday,
    Sunday,
}

fn next_day(day: DayOfWeek) -> DayOfWeek {
    match day {
        DayOfWeek::Monday => DayOfWeek::Tuesday,
        DayOfWeek::Tuesday => DayOfWeek::Wednesday,
        DayOfWeek::Wednesday => DayOfWeek::Tuesday,
        DayOfWeek::Thursday => DayOfWeek::Friday,
        DayOfWeek::Friday => DayOfWeek::Saturday,
        DayOfWeek::Saturday => DayOfWeek::Sunday,
        DayOfWeek::Sunday => DayOfWeek::Monday,
    }
}

fn main() {
    let today = DayOfWeek::Sunday;
    println!("Today: {:?}", today);
    let tomorrow = next_day(today);
    println!("Yesterday will be: {:?}", tomorrow);
}
```
### Результаты выполненной работы
[![image.png](https://i.postimg.cc/wvnCxzQS/image.png)](https://postimg.cc/bDHCLKMT)
