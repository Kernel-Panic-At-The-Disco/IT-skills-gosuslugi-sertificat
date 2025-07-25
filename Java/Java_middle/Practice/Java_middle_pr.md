# Проверка на палиндром

**Описание:**  
Вы разрабатываете программу для проверки строк на палиндром. Палиндромом называется строка, которая читается одинаково как с начала, так и с конца. При этом пробелы и регистр букв игнорируются.

Напишите программу, которая определяет, является ли заданная строка палиндромом.

**Формат ввода:**  
Одна строка, содержащая только заглавные и/или строчные буквы русского алфавита и, в некоторых случаях, пробелы. Длина строки от 2 до 100 символов включительно.

**Формат вывода:**  
Одна из двух фраз (без кавычек): «Палиндром» или «Не палиндром».

**Код:**
```
class PalindromeChecker {
  
  public String checkPalindrome(String input) {
    // Ваш код
    return "";
  }
}
```

**Пример 1:**  
Входные данные:  
Тут как тут

Выходные данные:  
Палиндром

**Пример 2:**  
Входные данные:  
Программист

Выходные данные:  
Не палиндром

---

# Значительное похолодание

**Описание:**  
Вы разрабатываете приложение для определения по массиву значений температуры по дням. В нем вам нужно найти значительные падения температуры — дни, когда температура упала на 3 и более градуса относительно предшествующего значения. Температура может принимать положительные, нулевые и отрицательные значения.

**Формат ввода:**  
Одна строка, в которой чередуются целые числа, разделённые пробелами. Числа могут быть положительными, отрицательными или нулем. Длина списка — не больше 100 элементов.

**Формат вывода:**  
Одна строка, в которой чередуются целые числа, разделённые пробелами. В строке содержатся индексы дней, соответствующие определению «значительное падение температуры». Если таких дней нет, выводится «Нет».

**Код:**
```
class SignificantTemperatureDrop {

  public String findDrops(String input) {
    // Ваш код
    return "";
  }
}
```

**Пример 1:**  
Входные данные:  
0 5 2 7 4 1

Выходные данные:  
2 4 5

**Пример 2:**  
Входные данные:  
10 8 6 4 2 0 -2 -4

Выходные данные:  
Нет

---

# Только безопасные пароли

**Описание:**  
Вы разрабатываете программу для проверки безопасности паролей. Ваша задача — проверить набор паролей и определить, какие из них безопасны. Пароль считается таковым, если он удовлетворяет пяти условиям:
1. Содержит хотя бы одну заглавную букву;
2. Содержит хотя бы одну строчную букву;
3. Содержит хотя бы одну цифру;
4. Содержит хотя бы один специальный символ (допустимый набор символов: !@#$%*&()-+);
5. Длина пароля больше или равна 8 символам.

Реализуйте метод, который принимает на вход один пароль и проверяет его на соответствие условиям. Проверьте каждый пароль в наборе с помощью этого метода и верните только безопасные пароли.

**Формат ввода:**  
Одна строка, в которой чередуются пароли, разделённые пробелами. Длина строки — не более 100 символов.

**Формат вывода:**  
Одна строка, в которой содержатся только безопасные пароли, разделённые пробелами. Выводите пароли в том порядке, в котором они были даны на вход. Если подходящих паролей нет, выводите «Не найдено» (без кавычек).

**Код:**
```
class SafePasswordChecker {
  // Набор спецсимволов
  private static final String specialChars = "!@#$%^&*()-+";
  
  public String findSafePasswords(String input) {
    // Ваш код
    return "";
  }
}
```

**Пример 1:**  
Входные данные:  
Password1 Pass@word 12345 pass!word Passw@rd Password1!

Выходные данные:  
Password1!

**Пример 2:**
Входные данные:  
Password1 Pass@word 12345 pass!word Passw@rd

Выходные данные:  
Не найдено

---

# Список задач по приоритету

**Описание:**  
Вы разрабатываете программу для управления задачами в списке дел. Сначала вам необходимо реализовать односвязный список, который будет хранить задачи. Каждая задача имеет название и приоритет.

Затем реализуйте методы для управления задачами: добавление задачи в список, удаление задачи из списка и вывод всех задач. Из списка всегда удаляется наиболее приоритетная задача, вывод задач также отсортирован по приоритету.

**Формат ввода:**  
Одна строка, которая содержит команды и их параметры (если есть). Команды разделены через точку с запятой, параметры — через запятую. Команды могут быть следующими:
1. ADD,название_задачи,приоритет_задачи — добавление новой задачи в список;
2. REMOVE — удаление наиболее приоритетной задачи из списка. Если несколько задач имеют одинаковый приоритет, удаляется первая по алфавиту задача. Если задач в списке нет, игнорируется;
3. Набор команд гарантированно заканчивается командой GET — вывести все задачи, которые остались в списке, по порядку приоритета.

Название задачи содержит только буквы кириллицы, без пробелов и иных символов. Каждое название, хранящееся в списке, уникально. Приоритет — это целое число от 1 до 5, где 1 — наиболее приоритетные, 5 — наименее приоритетные задачи.

Длина строки — не более 500 символов.

**Формат вывода:**  
Одна строка — все задачи, которые остались в списке, через точку с запятой. Строка имеет вид:  
<название_задачи,приоритет_задачи;название_задачи,приоритет_задачи;...>. Задачи отсортированы от наиболее к наименее приоритетной (от 1 до 5), задачи с одним приоритетом — в алфавитном порядке.

Если в списке не осталось задач, выводится «Список пуст» (без кавычек).

**Код:**
```
class TaskManager {
  
  public String manageTasks(String input) {
    // Ваш код
    return "";
  }
}
```

**Пример 1:**  
Входные данные:  
ADD,НаписатьКод,2;ADD,ТестироватьКод,3;ADD,ОтветитьНаСообщения,1;REMOVE;GET

Выходные данные:  
НаписатьКод,2;ТестироватьКод,3

**Пример 2:**  
Входные данные:  
ADD,КупитьПродукты,3;REMOVE;ADD,СделатьОтчет,4;ADD,Постирать,5;ADD,Погладить,5;GET

Выходные данные:  
СделатьОтчет,4;Погладить,5;Постирать,5

**Пример 3:**  
Входные данные:  
ADD,ПосетитьВстречу,2;REMOVE;ADD,ПрочитатьГазету,1;REMOVE;GET

Выходные данные:  
Список пуст

---