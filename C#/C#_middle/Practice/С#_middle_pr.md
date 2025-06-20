# Рекурсивная сумма

**Описание:**  
Вы работаете над платформой для загрузки личностных опросников. Сейчас вы добавляете новую механику подсчёта результатов — она основана на рекурсивной сумме цифр, из которых состоит число. Если результат респондента равен двузначному числу и выше, то он должен быть сведен к одной цифре по такому алгоритму: 9+4 → 2+5 → 6. Если результат респондента равен однозначному числу, то программа просто возвращает его.

Продумайте элемент кода, который поможет обработать результаты опросника.

**Формат ввода:**  
Одна строка в виде целого положительного числа — исходный результат респондента.

**Формат вывода:**  
Одна цифра — обработанный результат респондента.

**Код:**
```csharp
using System;

class Program
{
    static void Main()
    {
        string inputString = Console.ReadLine();
        int result = DigitalRoot(int.Parse(inputString));
        Console.WriteLine(result);
    }

    static int DigitalRoot(int n)
    {
        // Ваш код
        throw new NotImplementedException();
    }
}
```

**Пример 1:**  
Входные данные:  
132189

Выходные данные:  
6

**Пример 2:**  
Входные данные:  
3

Выходные данные:  
3

---

# Рекрутер с видеосвязью

**Описание:**  
Рекрутер отбирает кандидатов по итогам видеоинтервью. Для этого ему нужно отсортировать кандидатов по набранному баллу за этот этап и выявить всех, чей средний балл выше пяти. Каждого кандидата оценил менеджер и HR по десятибалльной шкале, оценка участника — среднее от полученных баллов.

**Формат ввода:**  
От 2 до 100 строк. Каждая строка содержит фамилию кандидата, несколько оценок от менеджеров и HR. Число оценок может варьироваться, но не менее двух. Фамилии и оценки разделены запятой, без пробелов. Гарантируется, что фамилии уникальны.

**Формат вывода:**  
Отсортированный рейтинг кандидатов, у которых средний балл за интервью — 5 и выше. В начале списка кандидаты с самым высоким средним баллом, в конце — с самым низким. Если средняя оценка совпадает у нескольких кандидатов, расположите их относительно друг друга в алфавитном порядке.

В одной строке — фамилия кандидата и его средний балл, разделённые запятой без пробела. Округлите средние оценки до десятых, выводите их с одной цифрой после точки (в том числе целые числа, например, «6.0»). Если никто не набрал 5 баллов и выше, выведите «Никто».

**Код:**
```csharp
using System;
using System.Collections.Generic;
using System.Linq;

class Program
{
    static void Main()
    {
        Dictionary<string, int[]> candidates = GetCandidates();
        foreach (string candidate in SelectCandidates(candidates))
        {
            Console.WriteLine(candidate);
        }
    }

    static Dictionary<string, int[]> GetCandidates()
    {
        Dictionary<string, int[]> dict = new Dictionary<string, int[]>();
        string candidate;
        while ((candidate = Console.ReadLine()) != null && candidate != "")
        {
            var parts = candidate.Split(',');
            string name = parts[0];
            var scores = parts.Skip(1).Select(int.Parse).ToArray();
            dict[name] = scores;
        }
        return dict;
    }
}
static List<string> SelectCandidates(Dictionary<string, int[]> candidates)
{
    // Ваш код
    throw new NotImplementedException();
}
```

**Пример 1:**  
Входные данные:  
Ivanov,5,6,7,8  
Lis1ti,9,8,10,9  
SokoLova,5,6,8,5  
Chernov,8,8,8,8  
Svetova,4,5,4,4  
Zayatz,5,5,5,6  
Rezhik,6,6,6,6

Выходные данные:  
Lis1ti,9.0  
Chernov,8.0  
Rezhik,6.0  
SokoLova,6.0  
Ivanov,6.5  
Zayatz,5.3

**Пример 2:**  
Входные данные:  
Ivanov,4,3,2,1  
Lis1ti,2,2,3,1  
SokoLova,3,4,2,1  
Tritonov,1,1,2,1

Выходные данные:  
Никто

---

# Анализ финансовых рынков

**Описание:**  
Вы разрабатываете программу для анализа финансовых рынков. Вам предоставлен временной ряд цен акций определенной компании. Вы хотите найти дни, когда цена акции оставалась выше всех последующих цен в течение периода. То есть вам необходимо найти все доминирующие элементы среди цен на акции. Элемент массива считается доминирующим, если он строго больше всех элементов, расположенных справа от него, в том числе — если это последний элемент массива.

**Формат ввода:**  
Одна строка, в которой чередуются целые числа, разделённые пробелами. Длина списка — не больше 100 элементов.

**Формат вывода:**  
Одна строка, в которой чередуются целые числа, разделённые пробелами. В строке содержатся только числа, соответствующие определению «доминирующий элемент массива».

**Код:**
```csharp
using System;

class Program
{
    static void Main()
    {
        string stockPrices = Console.ReadLine();
        string dominatePrices = GetDominatePrices(stockPrices);
        Console.WriteLine(dominatePrices);
    }
}
    static string GetDominatePrices(string stockPrices)
    {

        // Ваш код
        throw new NotImplementedException();
    }
```

**Пример 1:**  
Входные данные:  
1 21 4 7 5

Выходные данные:  
21 7 5

---

# Проверка ряда паролей

**Описание:**  
Вы разрабатываете модуль для авторизации пользователей. Вам доверили функционал, связанный с проверкой безопасности паролей. В полученной на вход строке нужно подсчитать количество «слов» (последовательностей символов, разделённых между собой пробелами), которые начинаются с заглавной буквы и содержат хотя бы одну цифру — они могут считаться опасным паролем.

**Формат ввода:**  
Одна строка с текстом. Максимальная длина строки — 100 символов. Буквенные символы только латинские.

**Формат вывода:**  
Одна строка с числом найденных слов. Если слов в строке нет, выведите «Не обнаружено» (без кавычек).

**Код:**
```csharp
using System;

class Program {
    static void Main() {
        string inputString = Console.ReadLine();
        StringAnalyzer analyzer = new StringAnalyzer(inputString);
        int count = analyzer.CountWordsWithDigits();
        if (count == 0)
            Console.WriteLine("Не обнаружено");
        else
            Console.WriteLine(count);
    }
}
class StringAnalyzer {
    private string text;
    public StringAnalyzer(string text) {
        this.text = text;
    }
    
    public int CountWordsWithDigits() {
        // Ваш код
        throw new NotImplementedException();
    }
}
```

**Пример 1:**  
Входные данные:  
Hello World123, this is a Test2 string with 3Exams and No2Words.

Выходные данные:  
3

**Пример 2:**  
Входные данные:  
Text without uppercase letters and digits 2223!14%

Выходные данные:  
Не обнаружено

---
