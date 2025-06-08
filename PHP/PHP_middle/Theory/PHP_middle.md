# PHP_middle

## Вопрос 1  
Какое значение будет выведено при выполнении следующего кода?

```php
class A {
    const A = 1;
    public static function test() {
        return static::A;
    }
}
class B extends A {
    const A = 2;
}
class C extends B {
    const B = 3;
}
print(C::test());
```

- PHP Fatal error: Uncaught Error: Undefined constant A
- 2
- PHP Fatal error: Uncaught Error: Call to undefined method C::test()
- 1
- Null

---

## Вопрос 2 
Рассмотрите фрагмент PHP-кода:

```php
$x = 10;
$x %= 3;
echo $x;
```

Какое значение будет выведено и почему?

- 3, потому что переменной $x присваивается результат целочисленного деления
- 10, так как оператор %= просто сохраняет исходное значение переменной Выдаст ошибку, поскольку оператор %= не существует в PHP
- 1, так как оператор %= присваивает переменной остаток от деления ее текущего значения
- Выдаст ошибку, поскольку оператор %= не существует в PHP
- 0, так как оператор %= возвращает целое число от деления переменной слева на указанное число справа

---

## Вопрос 3
У вас есть ассоциативный массив, где ключи — это не обязательно последовательные числа, а значения — это строки, которые потенциально могут повторяться, но в разных регистрах. Вы хотите:

1. Сохранить только первое вхождение каждой строки (дубликаты удалить).
2. При этом игнорировать регистр (т.е. "Apple" и "apple" считать одинаковым).
3. Сохранить оригинальную форму строки (т.е. если встретили "Apple" раньше "apple", в итоговый массив попадет именно "Apple").
4. Сохранить исходные ключи, соответствующие первому вхождению.

Какой из приведённых вариантов кода корректно достигнет описанного результата?

- 
```php
$result = [];
foreach ($data as $k => $v) {
    if (!in_array(strtolower($v), array_map('strtolower', $result), true)) {
        $result[$k] = $v;
    }
}
```
- 
```php
$result = [];
foreach ($data as $k => $v) {
    $result[strtolower($v)] = $v;
}
```
- 
```php
$result = array_unique($data);
```
- 
```php
$result = array_filter($data, fn($val, $key) => !isset($result[strtolower($val)]), ARRAY_FILTER_USE_BOTH);
```
- 
```php
$result = [];
foreach ($data as $v) {
    if (!isset($result[$v])) {
        $result[$v] = $v;
    }
}
```

---

## Вопрос 4
Вы работаете над системой управления заказами интернет-магазина. В системе используется массив, где ключи — номера заказов, а значения — статусы этих заказов. Во время обработки заказов происходит следующее:

- Создаётся начальный список заказов.
- Новые заказы автоматически добавляются в массив без указания конкретного номера.
- Некоторые заказы могут быть отменены (удалены).

Рассмотрим пример реализации:

```php
$orders = [1001 => 'новый', 'новый', 1005 => 'оплачен', 'отправлен', 1003 => 'доставлен'];
$orders[] = 'новый';
unset($orders[1005]);
$orders[] = 'возврат';
print_r($orders);
```

Каким будет итоговое состояние массива с заказами после выполнения кода?

- 
```php
Array (
    [1001] => новый
    [0] => новый
    [1003] => доставлен
    [1] => новый
    [2] => отправлен
    [3] => новый
    [4] => возврат
)
```
- 
```php
Array (
    [1001] => новый
    [1002] => новый
    [1003] => доставлен
    [1006] => новый
    [1007] => возврат
)
```
- 
```php
Array (
    [1001] => новый
    [1002] => новый
    [1003] => доставлен
    [1006] => новый
    [1008] => возврат
)
```
- 
```php
Array (
    [1001] => новый
    [1002] => новый
    [1003] => доставлен
    [1005] => отправлен
    [1006] => новый
    [1007] => возврат
)
```
- 
```php
Array (
    [1001] => новый
    [1002] => новый
    [1003] => доставлен
    [1005] => отправлен
    [1006] => новый
    [1008] => возврат
)
```

---

## Вопрос 5
Вы разрабатываете веб-приложение, где необходимо создать функцию process_data, которая должна:

- Принимать произвольное количество отдельных аргументов.
- Принимать массив в качестве единственного аргумента.
- Выводить все переданные значения через пробел.

Какой вариант кода корректно реализует данную функцию?

- 
```php
function process_data(array $args) {
    foreach ($args as $arg) {
        echo $arg . " ";
    }
}
```
- 
```php
function process_data(...$args) {
    if (count($args) === 1 && is_array($args[0])) {
        $args = $args[0];
    }
    foreach ($args as $arg) {
        echo $arg . " ";
    }
}
```
- 
```php
function process_data($args) {
    if (is_array($args)) {
        foreach ($args as $arg) {
            echo $arg . " ";
        }
    } else {
        echo $args . " ";
    }
}
```
- 
```php
function process_data(...$args) {
    foreach ($args as $arg) {
        echo $arg . " ";
    }
}
```
- 
```php
function process_data() {
    $args = func_get_args();
    foreach ($args as $arg) {
        echo $arg . " ";
    }
}
```

---

## Вопрос 6  
Предположим, у вас есть PDO-подключение к MySQL. Вам необходимо выполнить несколько взаимосвязанных INSERT- и UPDATE-запросов так, чтобы при возникновении ошибки в одном из них никакие изменения в базе не были зафиксированы. Как корректно реализовать транзакцию, учитывая, что по умолчанию PDO не использует автокоммит для транзакций?

- 
```php
$pdo->beginTransaction();
$pdo->query("INSERT INTO orders (id, amount) VALUES (10, 100)");
$pdo->query("UPDATE accounts SET balance = balance - 100 WHERE id = 5");
$pdo->query("COMMIT");
```
- 
```php
try {
    $pdo->query("START TRANSACTION");
    $pdo->query("INSERT INTO orders (id, amount) VALUES (10, 100)");
    $pdo->query("UPDATE accounts SET balance = balance - 100 WHERE id = 5");
    $pdo->query("COMMIT");
} catch (Exception $e) {
    $pdo->query("ROLLBACK");
}
```
- 
```php
$pdo->query("INSERT INTO orders (id, amount) VALUES (10, 100)");
$pdo->query("UPDATE accounts SET balance = balance - 100 WHERE id = 5");
```
- 
```php
$pdo->beginTransaction();
try {
    $pdo->query("INSERT INTO orders (id, amount) VALUES (10, 100)");
    $pdo->query("UPDATE accounts SET balance = balance - 100 WHERE id = 5");
    $pdo->commit();
} catch (Exception $e) { $pdo->rollBack(); }
```
- 
```php
try {
    $pdo->query("BEGIN");
    $pdo->query("INSERT INTO orders (id, amount) VALUES (10, 100)");
    $pdo->query("UPDATE accounts SET balance = balance - 100 WHERE id = 5");
    $pdo->query("COMMIT");
} catch (Exception $e) {
    $pdo->query("ROLLBACK");
}
```

---

## Вопрос 7 
У вас есть класс Car с защищённым свойством $engineStatus и методом startEngine(). Вам необходимо, чтобы вызов startEngine() переводил двигатель в состояние «включено».

```php
class Car {
    protected $engineStatus = false;
    public function startEngine() {
        // Дополните код здесь
    }
}
```

Какой код нужно использовать внутри метода, чтобы обратиться к свойству текущего объекта и установить $engineStatus в true?

- parent::$engineStatus = true;
- $this->engineStatus = true;
- object->engineStatus = true;
- class->engineStatus = true;
- self::$engineStatus = true;

---

## Вопрос 8 
Выберите из предложенных ключевых слов то, которое следует поставить вместо знака вопроса в коде ниже.

```php
class Animal {
    public function speak() {
        return "The animal says: ";
    }
}
class Cat ? Animal {
    public function speak() {
        return parent::speak() . "Meow!";
    }
}
```

- extends
- private
- public
- implements
- static

---

## Вопрос 9 
Вы реализуете регистрацию пользователя и выполняете SQL-запрос на добавление нового пользователя в базу данных. Как нужно отлавливать ошибку, возникающую при нарушении уникального ключа (email уже существует)?

- Использовать оператор throw внутри SQL-запроса
- Добавить finally { ... } после SQL-запроса
- Установить глобальную переменную $_ERROR_HANDLER, для обработки ошибок по умолчанию, перед выполнением запроса
- Обернуть выполнение SQL-запроса в блок try и перехватить ошибку в блоке catch
- Проверять результат запроса с помощью if ($result === false)

---

## Вопрос 10
Дан фрагмент кода на PHP, в котором разработчик хотел перехватить Zero value not allowed. Проанализируйте код и выберите ответ с правильным результатом работы кода.

```php
class NegativeNumberException extends Exception {}
class ZeroNumberException extends Exception {}
function processNumber($n) {
    try {
        if ($n < 0) {
            new NegativeNumberException("Negative numbers not allowed");
        }
        if ($n === 0) {
            new ZeroNumberException("Zero value not allowed");
        }
        return 100 / $n;
    } catch (NegativeNumberException $e) {
        return "Error: " . $e->getMessage();
    } catch (ZeroNumberException $e) {
        return "Warning: " . $e->getMessage();
    }
}
echo processNumber(0);
```

- Вывод будет Error: Negative numbers not allowed, потому что любое исключение класса NegativeNumberException или ZeroNumberException перехватывает первый блок catch
- Код сгенерирует фатальную ошибку Division by zero и ничего не выведет, потому что new ZeroNumberException(...) не прерывает выполнение
- Вывод будет Warning: Zero value not allowed, потому что выбрасывается ZeroNumberException и код ловит его в catch (ZeroNumberException ...)
- Будет Notice об использовании неинициализированной переменной $n, так как мы не объявили ее глобально
- Скрипт успешно выведет число Infinity, потому что в PHP деление на ноль приводит к бесконечности

---

## Вопрос 11  
Вы пишете скрипт, который обрабатывает дату и время в UTC, затем добавляет 1 день и выводит результат в указанном часовом поясе в формате Y-m-d H:i:s P. Рассмотрим такой код:

```php
function getUTCtoNextDayTimeZoneTime(
    string $timeString,
    string $tz
): string {
    $dt = new DateTime($timeString, new DateTimeZone("UTC"));
    $dt->modify("+1 day");
    $dt->setTimezone(new DateTimeZone($tz));
    return $dt->format("Y-m-d H:i:s P");
}
echo getUTCtoNextDayTimeZoneTime("2024-06-15 15:30:00", "America/New_York");
```

Какой результат будет выведен на экран?

- 2024-06-16 15:30:00 -04:00
- 2024-06-15 11:30:00 -04:00
- 2024-06-16 11:30:00 -05:00
- 2024-06-16 19:30:00 +02:00
- 2024-06-16 11:30:00 -04:00

---

## Вопрос 12  
Данные на сервере выводятся на экран с помощью следующей строки кода: echo $_POST['email']. Какое поле ввода должно быть в форме, чтобы после заполнения формы на сервере данные были доступны в глобальном массиве $_POST с ключом 'email'?

- <input type="email" id="e-mail" name="e-mail">
- <input type="email" id="email" name="e-mail">
- <input type="email" id="email" name="mail">
- <input type="email" id="e-mail" name="email">
- <input type="mail" id="email" name="e-mail">