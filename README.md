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

## Задача 7
### Постановка задачи
Создайте структуру Product с полями name, price и category, а также перечисление (enum) Category для категорий товаров. Напишите метод для вывода информации о продукте и ассоциированную функцию для подсчета общей суммы товаров в заданной категории из массива продуктов.
### Математическая модель
--
### Список идентификаторов
| Имя        | Тип                     | Смысл                                                             |
| ---------- | ----------------------- | ----------------------------------------------------------------- |
| Category   | enum                    | Перечисление категорий товаров                                    |
| Product    | struct                  | Структура, описывающая товар                                      |
| name       | String (поле Product)   | Название продукта                                                 |
| price      | f64 (поле Product)      | Цена продукта                                                     |
| category   | Category (поле Product) | Категория продукта                                                |
| products   | Vec<Product>            | Переменная в main, вектор тестовых продуктов                      |
| product    | &Product                | Ссылка на продукт                                                 |
| sum        | f64                     | Сумма цен в функции total_price                                   |
| target_cat | Category                | Параметр total_price                                              |
| total        | f64                   | Сумма цен в функции main                                          |

### Код программы
```Rust
// Перечисление всех доступных категорий
#[derive(Debug)]
enum Category {
    Electronics,
    Clothing,
    Food,
    Other,
}

struct Product {
    name: String,
    price: f64,
    category: Category,
}

impl Product {
    fn print_info(&self) {
        println!("Good: {}", self.name);
        println!("Price: {:.2}", self.price);
        println!("Category: {:?}", self.category);  // Используем {:?} для вывода Debug
    }
    
    // Функция для подсчета суммы
    fn total_price(products: &[Product], target_cat: Category) -> f64 {
        let mut sum = 0.0;
        for product in products {
            match (&product.category, &target_cat) { 
                (Category::Electronics, Category::Electronics) |
                (Category::Clothing, Category::Clothing) |
                (Category::Food, Category::Food) |
                (Category::Other, Category::Other) => {
                    sum += product.price;
                }
                _ => {}
            }
        }
        sum
    }
}

fn main() {
    // Тестовые продукты
    let products = vec![
        Product {
            name: String::from("Powerbank"),
            price: 2600.60,
            category: Category::Electronics,
        },
        Product {
            name: String::from("Microphone"),
            price: 9999.99,
            category: Category::Electronics,
        },
        Product {
            name: String::from("Screw"),
            price: 0.99,
            category: Category::Other,
        },
        Product {
            name: String::from("Trousers"),
            price: 1000.00,
            category: Category::Clothing,
        },
    ];
    
    products[0].print_info();

    let total = Product::total_price(&products, Category::Electronics);
    println!("Sum: {:.2}", total);
}
```
### Результаты выполненной работы
[![image.png](https://i.postimg.cc/W4wzJ9HW/image.png)](https://postimg.cc/NyLB3xYm)
## Задача 8
### Постановка задачи
Создайте структуру Employee с полями name, position, salary, а также перечисление Position для должностей сотрудников. Напишите функцию, которая принимает вектор сотрудников и возвращает вектор сотрудников заданной должности.
### Математическая модель
--
### Список идентификаторов
| Имя       | Тип                      | Смысл                                                      |
| --------- | ------------------------ | ---------------------------------------------------------- |
| Position  | enum                     | Перечисление возможных должностей                          |
| Employee  | struct                   | Структура, описывающая сотрудника                          |
| name      | String (поле Employee)   | Имя сотрудника                                             |
| position  | Position (поле Employee) | Должность сотрудника                                       |
| salary    | f64 (поле Employee)      | Оклад сотрудника                                           |
| employees | &[Employee]              | Срез исходного списка сотрудников для фильтрации           |
| target    | Position                 | Целевая должность для фильтрации                           |
| e         | &Employee                | Ссылка на текущего сотрудника при фильтрации               |
| staff     | Vec<Employee>            | Вектор сотрудников в main                                  |
| testers   | Vec<Employee>            | Вектор сотрудников с должностью tester                     |

### Код программы
```Rust
#[derive(Debug, PartialEq, Clone)] 
enum Position {
    Manager,
    Developer,
    Designer,
    Tester,
}

#[derive(Debug, Clone)]
struct Employee {
    name: String,
    position: Position,
    salary: f64,
}

fn filter_by_position(employees: &[Employee], target: Position) -> Vec<Employee> {
    employees
        .iter()
        .filter(|e| e.position == target)
        .cloned()
        .collect()
}

fn main() {
    // Инициализация вектора сотрудников
    let staff = vec![
        Employee { name: "Petya".into(),  position: Position::Tester, salary: 50000.0 },
        Employee { name: "Viktor".into(), position: Position::Manager,   salary: 90000.0 },
        Employee { name: "Nikita".into(), position: Position::Developer, salary: 100000.0 },
        Employee { name: "Vitya".into(), position: Position::Designer,  salary: 70000.0 },
    ];

    let testers = filter_by_position(&staff, Position::Tester); 
    println!("Testers: {:?}", testers);
}
```
[![image.png](https://i.postimg.cc/y8XsfDyW/image.png)](https://postimg.cc/FYRMzsqQ)
