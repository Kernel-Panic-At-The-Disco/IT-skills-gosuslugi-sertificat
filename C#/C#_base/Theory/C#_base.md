# C#_base

## Вопрос 1
Сколько байтов занимает тип данных char в C#?

- 4 байта
- 8 байт
- 1 байт
- 16 байт
- 2 байта

---

## Вопрос 2
Что выведет следующая программа?

```csharp
public static void Main()
{
    int i;
    Console.WriteLine(i);
}
```

- Ошибка компиляции (Compile-time error)
- 0
- Null
- Ошибка выполнения (Runtime error)
- Случайное значение

---

## Вопрос 3
Укажите результат работы фрагмента программы.

```csharp
char a, b, c;
a = 'B';
b = 'C';
c = a;
b = c;
Console.WriteLine("{0}{1}{2}{3}{4}",a,b,c,'c',b);
```

- bcaab
- abccb
- bcbcb
- bbbcb
- bbbcc

---

## Вопрос 4
Какое ключевое слово следует применить для запрета наследования от определённого класса?

- abstract
- static
- internal
- const
- sealed

---

## Вопрос 5
Что такое полиморфизм в C#?

- Возможность класса скрывать его внутренние данные и защищать их от несанкционированных изменений
- Концепция, позволяющая объектам разных типов обрабатываться одинаково через общий интерфейс
- Механизм, который позволяет объектам вести себя как объекты другого типа
- Процесс объединения данных и функций в единый компонент
- Процесс, который ограничивает доступ к некоторым компонентам объекта

---

## Вопрос 6
Имеется два класса и следующий код. Что происходит при вызове a.Write()?

```csharp
class A
{
    public string InformationalString { get; set; }
    public A(string info) => InformationalString = info;
    public virtual void Write() => Console.WriteLine(InformationalString);
}
class B : A
{
    public string AdditionalInformationalString { get; set; }
    public B(string info, string additionalInfo) : base(info) => AdditionalInformationalString = additionalInfo;
    public override void Write() => Console.WriteLine($"{InformationalString} has some {AdditionalInformationalString}");
}
A a = new B("object", "properties");
a.Write();
```

- Выполняется реализация метода Write из класса A благодаря тому, что переменная a - переменная типа A
- Выполняется реализация метода Write из класса B благодаря тому, что переменная a - переменная типа A
- Выполняется реализация метода Write из класса B, несмотря на то что переменная a - переменная типа B
- Выполняется реализация метода Write из класса B, несмотря на то что переменная a - переменная типа A
- Выполняется реализация метода Write из класса A благодаря тому, что переменная a - переменная типа B

---

## Вопрос 7
Какой интерфейс должен реализовать класс, чтобы обеспечить выполнение запросов с использованием LINQ?

- IEnumerable или ILinq
- IEnumerator или ILinq
- ILinq или IQueryable
- IEnumerator или IQueryable
- IEnumerable или IQueryable

---

## Вопрос 8
У вас есть следующий список.

```csharp
List<int> items = new List<int>() { 65, 45, 100, 95, 85, 10, 30, 95, 50};
```
Вам необходимо получить все числа больше 65. Какой вариант для этого подходит?

- var result = items.Select(i => i > 65);
- var result = items.Find(i => i > 65);
- var result = items.Take(65);
- var result = items.Where(i => i > 65).Select(i);
- var result = items.Any(i => i > 65);

---

## Вопрос 9
Какой класс необходимо использовать на месте пропуска в коде ниже, чтобы получить список файлов, упорядоченный по времени создания?

```csharp
var files = new ___("*-")
    .GetFiles("*-")
    .OrderBy(f => f.CreationTime)
    .ToList();
Console.WriteLine(string.Join("\n", files));
```

- DirectoryInfo
- Directory
- Path
- File
- FileInfo

---

## Вопрос 10
Что делает следующий код?

```csharp
File.WriteAllText("NewFile.txt", "Some\tText\n");
```

- Создает новый файл и записывает в него текст. Если файл существует, перезаписывает его
- Открывает файл на запись и чтение. Если файл существует, дописывает в него
- Открывает файл на запись и чтение. Если файл существует, перезаписывает его
- Создает новый файл и записывает в него текст. Если файл существует, то дописывает в него
- Создает новый файл и записывает в него текст. Если файл существует, вызывает исключение

---