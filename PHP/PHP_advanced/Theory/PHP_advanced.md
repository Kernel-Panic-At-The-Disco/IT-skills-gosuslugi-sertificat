# PHP_advanced

## Вопрос 1
Вы реализуете калькулятор. У вас есть функция, которая должна увеличивать переданную переменную на 5:

```php
function addFive(?) {
    $value += 5;
}
$number = 10;
addFive($number);
echo $number; // Ожидается вывод: 15
```

Какое объявление функции (вместо знака ?) будет правильным и позволит получить ожидаемый результат?

- $value
- int &$value
- int $value
- &$value
- %value

---

## Вопрос 2
Вы разрабатываете систему авторизации пользователей. Допустим, у вас есть массив с данными нескольких пользователей и каждый пользователь имеет поля name и role. Вам нужно добавить каждому пользователю новый ключ permission_level для определения уровня доступа, который рассчитывается на основе значения role. Например, для role = 'manager' задаем permission_level = 2, а для role = 'employee' — permission_level = 1.

Важно: условие таково, что обновлять пользователей нужно на месте (in-place), т.е. без создания новых массивов и без потери индексов.

Имеется исходный массив:

```php
$users = [
    ['name' => 'Alice', 'role' => 'manager'],
    ['name' => 'Bob', 'role' => 'employee'],
    // и так далее
];
```

Какой фрагмент кода наиболее корректно добавит ключ permission_level каждому пользователю массива $users, учитывая, что метод должен работать с функционалом стиля PHP (используя встроенные функции для работы с массивами, а не простой foreach) и модифицировать исходные данные in-place?

- 
```php
array_walk($users, function ($user) {
    if ($user['role'] == 'manager') {
        $user['permission_level'] = 2;
    } else {
        $user['permission_level'] = 1;
    }
});
```
- 
```php
array_reduce($users, function ($carry, $user) {
    $user['permission_level'] = ($user['role'] === 'manager') ? 2 : 1;
    $carry[] = $user;
    return $carry;
}, []);
```
- 
```php
array_walk($users, function (&$user) {
    if ($user['role'] == 'manager') {
        $user['permission_level'] = 2;
    } else {
        $user['permission_level'] = 1;
    }
});
```
- 
```php
array_filter($users, function ($user) {
    return ($user['role'] === 'manager') ? 2 : 1;
});
```
- 
```php
array_map(function ($user) {
    if ($user['role'] == 'manager') {
        $user['permission_level'] = 2;
    } else {
        $user['permission_level'] = 1;
    }
    return $user;
}, $users);
```

---

## Вопрос 3
Вы получаете логин пользователя из формы ($_POST['username']) и хотите безопасно выполнить запрос к базе данных MySQL, используя mysqli. Какой способ наиболее защищен от SQL-инъекций?

- 
```php
$query = "SELECT * FROM users WHERE username = " . $username;
mysqli_query($conn, $query);
```
- 
```php
$stmt = mysqli_prepare($conn, "SELECT * FROM users WHERE username = ?");
mysqli_stmt_bind_param($stmt, "s", $username);
mysqli_stmt_execute($stmt);
```
- 
```php
$username = mysqli_real_escape_string($conn, $username);
$query = "SELECT * FROM users WHERE username = '$username'";
```
- 
```php
function sanitize($v){ return htmlspecialchars($v); }
$query = "SELECT * FROM users WHERE username = '" . sanitize($username) . "'";
```
- 
```php
$query = "SELECT * FROM users WHERE username = '$username'";
mysqli_query($conn, $query);
```

---

## Вопрос 4

Вы разрабатываете систему обработки статистики веб-приложения. Есть глобальный счетчик событий $eventsCount. Функция trackEvent() должна увеличивать глобальный счетчик на определенное значение, переданное аргументом, и возвращать новое значение счетчика.

Какой из вариантов реализации функции trackEvent() корректно решает эту задачу?

- 
```php
function trackEvent($increment) {
    globals $eventsCount;
    return $eventsCount += $increment;
}
```
- 
```php
function trackEvent($increment) {
    return static::$eventsCount += $increment;
}
```
- 
```php
function trackEvent($increment) {
    global $eventsCount;
    return $eventsCount += $increment;
}
```
- 
```php
function trackEvent($increment) {
    return $GLOBALS['eventsCount'] + $increment;
}
```
- 
```php
function trackEvent($increment) {
    static $eventsCount;
    return $eventsCount += $increment;
}
```

---

## Вопрос 5
Какую функцию нужно вставить на место пропуска в первой строке кода, чтобы предотвратить SQL-инъекцию и исправить код?

```php
$id = __________ $_GET['id'];
$mysqli = new mysqli("localhost", "my_user", "my_password", "my_db");
$result = $mysqli->query("SELECT * FROM users WHERE id = $id");
```

- htmlspecialchars()
- mysql_real_escape_string()
- addslashes()
- mysqli_real_escape_string()
- mysql_escape_string()

---

## Вопрос 6
Что нужно написать вместо знака вопроса, чтобы класс Cat воспользовался функцией класса Animal speak()?

```php
class Animal {
    protected $name;
    public function __construct($name) {
        $this->name = $name;
    }
    public function speak() {
        return "The animal says: ";
    }
}
class Cat extends Animal {
    public function speak() {
        return ?::speak() . "Meow!";
    }
}
```

- extends
- function
- static
- parent
- const

---

## Вопрос 7
Что будет выведено на экран?

```php
class A {
    const NAME = 'Class A';
    public static function show() {
        return self::NAME;
    }
    public static function display() {
        return self::NAME;
    }
}
class B extends A {
    const NAME = 'Class B';
    public static function show() {
        return static::NAME;
    }
}
echo A::show() . ", ";
echo A::display() . ", ";
echo B::show() . ", ";
echo B::display();
echo A::show() . "\n";
echo A::display() . "\n";
echo B::show() . "\n";
echo B::display() . "\n";
```

- Class A, Class A, Class B, Class A
- Class A, Class A, Class A, Class A
- Class A, Class A, Class B, Class B
- Class A, Class A, Class A, Class B
- Class A, Class B, Class B, Class A

---

## Вопрос 8
При обработке данных из формы вы хотите выбросить исключение, если пользователь не заполнил обязательное поле email. Однако следующий фрагмент кода не работает так, как ожидается: в случае отсутствия email программа продолжает выполнение без ошибки.

```php
if (empty($_POST['email'])) {
    new Exception("Email is required!");
}
// ... дальнейшая логика ...
```

Как правильно следует модифицировать код, чтобы при отсутствии email выполнение прерывалось и исключение обрабатывалось в соответствующем блоке try/catch?

- 
```php
if (empty($_POST['email'])) {
    new throw Exception("Email is required!");
}
```
- 
```php
if (empty($_POST['email'])) {
    throw \InvalidArgumentException("Email is required!");
}
```
- 
```php
if (empty($_POST['email'])) {
    throw new Exception("Email is required!");
}
```
- 
```php
if (empty($_POST['email'])) {
    throw Exception("Email is required!");
    return;
}
```
- 
```php
if (empty($_POST['email'])) {
    Exception("Email is required!");
    return;
}
```

---

## Вопрос 9
Что выведет программа ниже?

```php
$startDate = new DateTime('2022-01-15');
$endDate = new DateTime('2022-02-25');
$interval = $endDate->diff($startDate);
echo "Разница: " . $interval->format('%a');
```

- Разница: 2022-02-25
- Разница: 31
- Разница: 414
- Разница: 2022-01-15
- Разница: 41

---

## Вопрос 10
Пользователь заполняет форму авторизации на сайте. Выберите метод передачи информации, который необходимо использовать для передачи логина и пароля пользователя.

```html
<form method="?">
<p> Введите логин <input type="text" name="login"> </p>
<p> Введите пароль <input type="text" name="password"> </p>
<input type="submit" value="отправить">
</form>
```

- UPDATE
- POST
- CHANGE
- PATCH
- GET

---

## Вопрос 11
Ниже представлены регулярные выражения в PHP. Какое из них подходит для адреса электронной почты?

- /^[a-zA-Z0-9._-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,4}$/
- /\(\d{3}\) \d{3}-\d{4}$/
- /^[a-zA-Z0-9._-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,4}$/gm
- /\d{4}\w{4+}@\d{2}\w{2}-\d{2}\w{2}$/
- /\b[AB]\w*@\w*/i

---

## Вопрос 12
Вы пишете текстовый парсер, который должен находить все целые числа в строке и оборачивать их в тег <b> ... </b>. При этом:
- Числа должны идти отдельно, например быть отделенными пробелами или знаками пунктуации.
- Цифры, которые являются частью слов (например, abc123def), не должны заменяться.

Пример:
Исходная строка: "Order ID: 123, quantity: 5, item code: abc123def"
Результат: "Order ID: <b>123</b>, quantity: <b>5</b>, item code: abc123def"

Какое регулярное выражение и замена в preg_replace() удовлетворяют этим требованиям?

- preg_replace("/\b\d+\b/", "<b>$0</b>", $text);
- preg_replace("/[^\d]+\d+[^\d]+/", "<b>$0</b>", $text);
- preg_replace("/^\d+$/", "<b>$0</b>", $text);
- preg_replace("/[0-9]/", "<b>$0</b>", $text);
- preg_replace("/\d+/", "<b>$0</b>", $text);

---

## Вопрос 13
Вы разрабатываете веб-приложение, которое часто запрашивает данные из базы данных MySQL. Как можно уменьшить количество обращений к базе данных в PHP для оптимизации кода?

- Использовать Eager Loading для предварительной загрузки связанных данных
- Использовать ORM (Object-Relational Mapping) для автоматической загрузки связанных данных
- Кэшировать результаты запросов для повторного использования
- Оптимизировать код с помощью хранимых процедур в базе данных
- Использовать пакетные операции для выполнения нескольких запросов одновременно

---

## Вопрос 14
Посмотрите пример кода и ответьте, могут ли классы реализовывать несколько интерфейсов и какое ключевое слово будет использовано вместо знака вопроса в строке объявления класса?

```php
interface Drivable {
    public function startEngine();
    public function drive();
}
interface Repairable {
    public function fix();
}
class Airplane {
    public function startEngine() {}
}
class Car ? Drivable, Repairable {
    public function startEngine() {}
    public function drive() {}
    public function fix() {}
}
```

- Да, могут, будет использовано ключевое слово implements
- Нет, они могут наследовать только 1 интерфейс, будет использовано ключевое слово implements
- Да, могут, будет использовано ключевое слово static class
- Нет, они могут наследовать только 1 интерфейс, будет использовано ключевое слово use
- Да, могут, будет использовано ключевое слово parents

---

## Вопрос 15

Вы пишете модуль для добавления и вывода комментариев на сайте. Код выглядит так:

```php
// Принимаем комментарий от пользователя
$comment = $_POST['comment'];
// Сохраняем в базе (PDO):
$pdo->query("INSERT INTO comments (text) VALUES ('$comment')");
// затем выводим список комментариев
$stmt = $pdo->query("SELECT * FROM comments");
while ($row = $stmt->fetch()) {
    echo "<p>".$row['text']."</p>";
}
```

Какие уязвимости присутствуют в данном коде?

- XSS, SQL-инъекция
- XSS, SQL-инъекция, отсутствие защиты от CSRF, отсутствие ограничения на размер входных данных
- XSS, SQL-инъекция, отсутствие ограничения на размер входных данных
- SQL-инъекция, отсутствие ограничения на размер входных данных
- XSS, SQL-инъекция, отсутствие защиты от CSRF

---
