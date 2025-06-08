# PHP_base

## Вопрос 1  
Какой из перечисленных операторов присваивания НЕ поддерживается в PHP?  

- $a = 1;
- $a %= 1;
- $a == 1;
- $a += 1;
- $a != 1;

---

## Вопрос 2  
Какой результат выведет следующий код?

```php
$x = 50;
$y = "50";
if ($x === $y) {
    echo "Equal";
} else {
    echo "---";
}
```

- Error
- Equal
- Null
- 5050

---

## Вопрос 3  
В каком из этих вариантов выполнения кода значение переменной $a в global scope будет равно 6?

```php
$a = 5;
function sum($a) { return $a + 1; }
sum($a);
```
```php
$a = 5;
function sum($a) { return $a++; }
sum($a);
```
```php
$a = 5;
function sum(&$a) { return $a + 1; }
sum($a);
```
```php
$a = 4;
function sum(&$a) { return $a + 2; }
sum($a);
```
```php
$a = 5;
function sum($a) { $a = $a + 1; }
sum($a);
```

---

## Вопрос 4  
Как в PHP можно создать массив?

- $a = {1, b=>2, 1=>3};
- $a = [1, 'b'=>2, 1=>3];
- $a = {1, "b":2, "1":3};
- $a = array(1, 'b':2, '1':3);
- $a = [1, 'b'=>2, '1'=>3];

---

## Вопрос 5  
Вы разрабатываете функцию, которая должна объединять два массива так, чтобы значения второго массива добавлялись в конец первого. Если элементы массивов имеют одинаковые ключи, значения из второго массива должны перезаписывать значения из первого.

Какой из вариантов кода корректно реализует данное требование?

- $result = $array1 + $array2;
- $result = array_combine($array1, $array2);
- $result = array_merge($array1, $array2);
- $result = array_push($array1, $array2);
- $result = array_replace($array2, $array1);

---

## Вопрос 6  
Какую ошибку содержит код?

```php
$array1 = array("a", "b", "c");
$array2 = array("x", "y", "z");
$result = $array1 + $array2;
echo $result;
```

- Массивы нельзя вывести через echo, необходимо использовать цикл while
- Переменные $array1 и $array2 должны иметь одинаковые размеры для операции +
- Оператор + не работает для массивов. Нужно использовать array_merge()
- Функция echo не может вывести массив, нужно использовать print_r($result)
- Нужно заменить оператор + на оператор . для объединения массивов

---

## Вопрос 7  
Посмотрите код и определите результат выполнения вывода программы.

```php
$text = "hello world";
echo substr($text, 5, 10);
```

- "Hello"
- "world Hello"
- "world"
- "HELLO WORLD"
- "WORLD"

---

## Вопрос 8  
Пользователь заполнил форму, в которой было поле:

<input type="text" id="username" name="login">

Выберите код, который вы будете использовать для проверки наличия переменной, отправленной методом POST.

- isset() && !empty($_POST['login']);
- isset($_POST['login']) == true;
- exists($_POST['login']);
- isset($_POST['login']);
- isset($POST['login']);

---

## Вопрос 9  
Вам нужно подключиться к базе данных MySQL (my_database) на хосте db.local под пользователем user с паролем pass и установить кодировку соединения utf8mb4, а также корректно обработать возможные ошибки при подключении. Какой из вариантов решения будет соответствовать современным рекомендациям — использование mysqli, установка кодировки и базовая обработка ошибок?

```php
$mysqli = new mysqli('db.local', 'user', 'pass', 'my_database');
if ($mysqli->connect_error) {
    die("Connection failed: " . $mysqli->connect_error);
}
$mysqli->set_charset('utf8mb4');
```
```php
$mysqli = mysqli_init();
mysqli_options($mysqli, MYSQLI_OPT_CONNECT_TIMEOUT, 5);
mysqli_real_connect($mysqli, 'db.local', 'user', 'my_database');
$mysqli->query("SET CHARACTER SET utf8");
```
```php
$mysqli = @mysqli_connect('db.local', 'user', 'pass');
$mysqli->query("SET NAMES 'utf8mb4'");
```
```php
$mysqli = new mysqli('db.local', 'user', 'pass', 'my_database');
$mysqli->set_charset('utf8mb4');
```
```php
$link = mysqli_connect('db.local', 'user', 'pass', 'my_database');
if (!$link) {
    echo "Error: Unable to connect to MySQL." . PHP_EOL;
    echo mysqli_connect_error();
    exit;
}
``` 

---

## Вопрос 10  
В проекте используется MySQLi, поэтому для работы с БД мы можем применять только ее. Какой запрос нужно использовать в коде ниже, чтобы получить все данные из таблицы users?

```php
$mysqli = new mysqli("localhost", "myuser", "mypassword", "mydb");
$result = $mysqli->query("__");
```

- SELECT *, CONCAT(first_name, '', last_name) AS full_name FROM users
- FETCH ALL_DATA FROM users
- SELECT * FROM users
- GET * FROM user
- SELECT username FROM users