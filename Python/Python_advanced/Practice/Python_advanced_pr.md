## Размер выигрыша в лотерее

**Описание:**  
Вы работаете над программой для проведения лотерей. Чтобы победить в лотерее, участник должен угадать загаданную последовательность цифр. Те, кто не угадал, тоже получают утешительный приз. Размер приза в баллах рассчитывает ваша программа. При этом максимальный размер ограничен.

Программа находит сумму цифр числовой последовательности участника, и если сумма чётная, удвоить её, если нечётная — утроить. Если результат больше 100, верните «Превышено» (без кавычек).

**Формат ввода:**  
Одна строка с цифрами.

**Формат вывода:**  
Одна строка, в которой есть сумма цифр последовательности, удвоенная или утроенная. Если сумма превышает 100, вернётся «Превышено» (без кавычек).

**Код:**
```python
def process_number(n):
    """Ваш код"""

input_string = input()
result = process_number(input_string)
print(result)
```

**Пример 1:**  
Входные данные:  
13133  
Выходные данные:  
33

**Пример 2:**  
Входные данные:  
99999  
Выходные данные:  
Превышено

**Пример 3:**  
Входные данные:  
99  
Выходные данные:  
36

---

## Космическая дипломатия

**Описание:**  
На связь с Землёй вышла инопланетная цивилизация. Они общаются необычным образом: каждое их сообщение — это набор «слов», состоящих только из букв a и b, а также знаков препинания. Каждое слово отражает настроение — хорошее или плохое — и влияет на дипломатический счёт. От него зависит, собираются ли инопланетяне нападать на Землю.

В языке пришельцев есть два вида слов:
- Плохое настроение: сначала идут a, потом буквы b (например: aaabbb). Это даёт –1 к счёту.
- Хорошее настроение: сначала идут b, потом a (например: bbbaaa). Это даёт +1 к счёту.

Каждое слово состоит строго из двух однородных блоков подряд — либо a за b, либо b за a.

После каждого слова могут идти специальные знаки:
- ! — усиливает влияние слова: умножает его счёт на количество восклицаний в этом слове.
- ? — инвертирует счёт слова (меняет знак на противоположный).

**Формат ввода:**  
Единственная строка вышеуказанного формата длиной от 10 до 30 символов — сообщение.

**Формат вывода:**  
Строка в зависимости от результата — 'счёт <число>: нападение неизбежно' или 'счёт <число>: нападения не будет'.

**Код:**
```python
import re

def alien_translator(message: str) -> str:
    """Ваш код"""

message = input()
translation = alien_translator(message)
print(translation)
```

**Пример 1:**  
Входные данные:  
bbbaaa! aaab! aaaa! bbb!  
Выходные данные:  
счёт 0: нападение неизбежно

**Пример 2:**  
Входные данные:  
aaabbb?!!!??? bbba! ba  
Выходные данные:  
счёт -77: нападение неизбежно

---

## Прочтение числа

**Описание:**  
Вы работаете над системой, которая преобразует числа в текст — это часть модуля синтеза речи.  
На текущем этапе нужно реализовать функцию, которая переводит целое число от 1 до 99 в его словесную форму на русском языке.

**Формат ввода:**  
Одно целое число от 1 до 99 (0 < x < 100).

**Формат вывода:**  
Строка — число, записанное словами русского языка в именительном падеже.

**Код:**
```python
def number_to_text(number: int) -> str:
    units = ['ноль', 'один', 'два', 'три', 'четыре', 'пять', 'шесть', 'семь', 'восемь', 'девять']
    teens = ['одиннадцать', 'двенадцать', 'тринадцать', 'четырнадцать', 'пятнадцать', 'шестнадцать', 'семнадцать', 'восемнадцать', 'девятнадцать']
    tens = ['десять', 'двадцать', 'тридцать', 'сорок', 'пятьдесят', 'шестьдесят', 'семьдесят', 'восемьдесят', 'девяносто']
    "Ваш код"


number = input()

text = number_to_text(number)

print(text)
```

**Пример 1:**  
Входные данные:  
1  
Выходные данные:  
один

**Пример 2:**  
Входные данные:  
34  
Выходные данные:  
тридцать четыре

**Пример 3:**  
Входные данные:  
67  
Выходные данные:  
шестьдесят семь

---

## Рейтинг по предмету

**Описание:**  
Вам необходимо написать программу для учебного офиса. Программа будет строить отсортированный список студентов, которые набрали больше проходного балла по определённому предмету.

**Формат ввода:**  
Первая строка содержит информацию о студентах, курсах и их оценках в формате:  
`имя_студента,курс,оценка;имя_студента,курс,оценка;...`  
В строке есть информация хотя бы об одном студенте.  
Вторая строка содержит предмет, по которому запрошена ситуация, и его проходной балл:  
`курс,проходной_балл`.

**Формат вывода:**  
Имена студентов и их баллы за этот предмет через запятую без пробела, каждый студент с новой строки.  
Если таких нет, выводится слово "Никто" (без кавычек).

**Код:**
```python
class Student:
    def __init__(self, name):
        self.name = name
        self.courses = {}

class CourseManager:
    def __init__(self):
        self.students = {}

    # Ваш код

students_info = input()
scores_info = input()
# Ваш код
```

**Пример 1:**  
Входные данные:  
Анна,Математика,85;Анна,Химия,90;Борис,Математика,75;Борис,История,80;Евгений,Математика,95;Евгений,История,85  
Математика,80  
Выходные данные:  
Евгений,95  
Анна,85

**Пример 2:**  
Входные данные:  
Анна,Психология,8;Алексей,Психология,6  
Психология,8  
Выходные данные:  
Никто

---

## Отчёты по продажам

**Описание:**  
Напишите программу, которая принимает информацию о продажах и формирует агрегированный отчёт о продажах по месяцам в соответствии с требуемым форматом.

**Формат ввода:**  
Одна строка с данными в формате `Дата:Продукт:Количество;Дата:Продукт:Количество;...`.  
Дата в формате YYYY-MM-DD, через двоеточие указано название продукта на русском языке и через ещё одно двоеточие — целое число, указывающее на количество проданных товаров.

**Формат вывода:**  
Набор строк, в котором выводится информация о продажах товаров. Сначала даётся название месяца с двоеточием, а после — маркированным списком с дефисом перечисляются товары с количеством продаж через двоеточие.

**Код:**
```python
class Item:
    def __init__(self, date, product, quantity):
        self.date = date
        self.product = product
        self.quantity = quantity

    @property
    def month(self):
        months_dict = {
            "01": "Январь",
            "02": "Февраль",
            "03": "Март",
            "04": "Апрель",
            "05": "Май",
            "06": "Июнь",
            "07": "Июль",
            "08": "Август",
            "09": "Сентябрь",
            "10": "Октябрь",
            "11": "Ноябрь",
            "12": "Декабрь"
        }
        month = self.date.split('-')[1]
        return months_dict.get(month, "Неизвестный месяц")


def generate_monthly_report(data):
    """Ваш код"""


input_data = input()
monthly_report_generator = generate_monthly_report(input_data)
for report in monthly_report_generator:
    print(report)
```

**Пример 1:**  
Входные данные:  
2023-01-15:Книга:10;2023-01-20:Орешки:5;2023-02-05:Наушники:8  
Выходные данные:  
Январь:  
- Книга: 10  
- Орешки: 5  
Февраль:  
- Наушники: 8

---

## Оценивание студентов

**Описание:**  
Вам требуется реализовать функцию, подсчитывающую число неуспевающих по каждому предмету.

**Формат ввода:**  
Две строки:  
Первая содержит предметы и проходные баллы в формате `<предмет>:<балл>; ...`  
Вторая — список студентов и их оценки в формате `<студент>: <предмет> <балл>, ...`

**Формат вывода:**  
Число получивших неудовлетворительную оценку по каждому предмету студентов в формате  
`<предмет>: <число студентов>; ...`  
Если таких нет, вывести строку "Полная успеваемость".

**Код:**
```python
def get_results(subjects: str, students: str):
    "Ваш код"


subjects = input()

students = input()

results = get_results(subjects, students)

print(results)
```

**Пример 1:**  
Входные данные:  
Физкультура: 30; Музыка: 50; Искусство: 40  
Дима: Физкультура 20, Музыка 60, Искусство 30; Лена: Физкультура 40, Музыка 50, Искусство 50  
Выходные данные:  
Физкультура: 1; Музыка: 0; Искусство: 1

**Пример 2:**  
Входные данные:  
История 45, География 55, Биология 65  
Смирнов: История 45, География 60, Биология 70; Кузнецов: История 50, География 58, Биология 65  
Выходные данные:  
Полная успеваемость

---

## Внутрисистемный доступ пользователей

**Описание:**  
Реализуйте класс UserManager, который будет управлять доступом пользователей к системе.

**Формат ввода:**  
Несколько строк, состоящих из команд add_user, remove_user, promote, demote, get_users. Входные данные гарантированно завершаются командой get_users.

**Формат вывода:**  
Несколько строк, в которой может быть один из вариантов:  
Пользователи с уровнем доступа или если список пуст — "Не найдено, если пользователей в списке не осталось".

**Код:**
```python
class UserManager:
    def __init__(self):
        self.users = {}

    def add_user(self, name, level):
        """Ваш код"""

    def remove_user(self, name):
        """Ваш код"""

    def promote(self, name):
        """Ваш код"""

    def demote(self, name):
        """Ваш код"""

    def get_users(self):
        """Ваш код"""

user_manager = UserManager()
input_string = []
while True:
    try:
        line = input()
        if line == "":
            break
    except EOFError:
        break
    input_string.append(line)

for command in input_string:
    """Ваш код"""
```

**Пример 1:**  
Входные данные:  
add_user Анна 1  
add_user Борис 2  
promote Анна  
get_users  
Выходные данные:  
Анна: 2  
Борис: 2

**Пример 2:**  
Входные данные:  
add_user Bob 3  
add_user Charlie 2  
remove_user Bob  
remove_user Charlie  
get_users  
Выходные данные:  
не найдено

---

# Анализ текста

**Описание:**
В рамках работы над проектом по анализу текста на натуральном языке требуется реализовать функцию, возвращающую манхэттенское расстояние между строками. Оно вычисляется следующим образом:
1. Общее расстояние равно сумме расстояний между буквами
2. Расстояние между двумя буквами равно модулю разности их мест в алфавите
3. Расстояние между буквой и любым другим символом (или отсутствием символа, если одна строка короче другой) равно её месту в алфавите.

**Формат ввода:**
Две произвольных строки (от 3 до 250 символов, латинские буквы, пробелы и знаки препинания)

**Формат вывода:**
Строка, содержащая число, являющееся вычисленным вышеописанным образом манхэттенским расстоянием

**Код:**
```python
def manhattan_distance(string_one: str, string_two: str) -> str:
    "Ваш код"


string_one = input()

string_two = input()

distance = manhattan_distance(string_one,string_two)

print(manhattan_distance)
```
**Пример 1:**
Входные данные:
For whom the bell tolls?
For you

Выходные данные:
170

**Пример 2:**
Входные данные:
Something
Something

Выходные данные:
0

---
