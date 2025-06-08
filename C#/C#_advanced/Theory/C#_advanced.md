# С#_advanced

## **Вопрос 1**

Что выведет данный код?  
На мобильной платформе присутствует горизонтальный скролл кода  
Index myIndex2 \= ^2;  
string\[\] people \= { "Tanya", "Sasha", "Ivan", "Kate", "Anya" };  
string selected2 \= people\[myIndex2\];  
Console.WriteLine(selected2);

* Ошибка индекса ()  
* Kate  
* Sasha  
* Ошибка выполнения (Runtime error)  
* Ошибка компиляции (Compile-time error)

## **Вопрос 2**

Вы реализуете паттерн Template Method. Метод Execute() базового класса вызывает два защищённых метода Step1() и Step2(). Метод Step1() был успешно переопределён в наследнике, но Step2() всегда вызывается из базового класса, несмотря на то, что в наследнике также объявлена его собственная версия.  
Рассмотрите следующий код:  
На мобильной платформе присутствует горизонтальный скролл кода  
public class BaseProcessor  
{  
    public void Execute()  
    {  
        Step1();  
        Step2(); // вызывается всегда из BaseProcessor  
    }  
    protected virtual void Step1()  
    {  
        Console.WriteLine("Base Step1");  
    }  
    // метод намеренно не virtual  
    protected void Step2()  
    {  
        Console.WriteLine("Base Step2");  
    }  
}  
public class CustomProcessor : BaseProcessor  
{  
    protected override void Step1()  
    {  
        Console.WriteLine("Custom Step1");  
    }  
    protected new void Step2()  
    {  
        Console.WriteLine("Custom Step2");  
    }  
}

Почему при вызове Execute() используется реализация Step2() из BaseProcessor, а не из CustomProcessor?

* Метод Step2 в производном классе должен иметь одинаковую сигнатуру без ключевого слова new  
* Методы, помеченные как protected, нельзя переопределить  
* Метод Step2 вызывается через базовый тип, поэтому используется базовая версия  
* Метод Step2 не объявлен с модификатором virtual, поэтому не может быть переопределён  
* Метод Step2 не может быть вызван из унаследованного метода Execute()

## **Вопрос 3**

У вас есть коллекция List, реализующая интерфейс IReadOnlyList. Вам необходимо проверить, содержит ли коллекция значения, и выбрать первый и последний элементы. Какой из следующих способов наиболее производителен для данной задачи?

* if (list.Any())  
  {  
      var firstValue \= list.First();  
      var lastValue \= list.Last();  
  }

* if (list.Any())  
  {  
      var firstValue \= list\[0\];  
      var lastValue \= list.Last();  
  }

* if (list.Count \> 0\)  
  {  
      var firstValue \= list\[0\];  
      var lastValue \= list\[list.Count \- 1\];  
  }

* if (list.Count \> 0\)  
  {  
      var firstValue \= list.First();  
      var lastValue \= list.Last();  
  }

* if (list.Any())  
  {  
      var firstValue \= list\[0\];  
      var lastValue \= list\[list.Count \- 1\];  
  }

## **Вопрос 4**

Что выведет код ниже?  
На мобильной платформе присутствует горизонтальный скролл кода  
var newFile \= Path.GetTempFileName();  
Console.WriteLine(Path.GetExtension($"${newFile}"));

* Пустая строка  
* .TEMP  
* Ошибка выполнения  
* .tmp  
* .t

## **Вопрос 5**

Что выведет код ниже?  
На мобильной платформе присутствует горизонтальный скролл кода  
internal class Member  
{  
    \[JsonIgnore(Condition \= JsonIgnoreCondition.Never)\]  
    public int Id { get; set; }  
    \[JsonIgnore(Condition \= JsonIgnoreCondition.WhenWritingDefault)\]  
    public string Name { get; set; }  
    \[JsonIgnore(Condition \= JsonIgnoreCondition.WhenWritingNull)\]  
    public string? Description { get; set; }  
    public void Save()  
    {  
        JsonSerializerOptions options \= new() { DefaultIgnoreCondition \= JsonIgnoreCondition.WhenWritingDefault };  
        Console.WriteLine(JsonSerializer.Serialize(this, options));  
    }  
}  
// call  
new Member() { Id \= 5686529, Name \= default, Description \= null }.Save();

* {"Id":5686529, "Name":"", "Description":null}  
* {"Id":5686529, "Name":null}  
* {"Id":5686529}  
* {"Name":""}  
* {"Id":5686529, "Name":""}

## **Вопрос 6**

Сколько исключений может возникнуть в представленном коде?  
На мобильной платформе присутствует горизонтальный скролл кода  
var mainNumber \= 0xaffd;  
var number \= mainNumber ^ (0xff \<\< 4);  
number ^= 0xa \<\< 3 ^ 4;  
number ^= \~13;  
Console.WriteLine(0xfff / number);  
string\[\] names \= { "Dog", "Cat", "Fish" };  
object\[\] objs \= (Object\[\])names;  
object obj \= (Object)3;  
objs\[2\] \= obj;  
for (int i \= 0; i \< 5; i++)  
{  
    Console.WriteLine(objs\[i\]);  
}

* 1  
* 2  
* 3  
* 4  
* 5

## **Вопрос 7**

Почему стандартный интерфейс ICloneable в .NET не обеспечивает типобезопасное клонирование объектов?

* Он запрещает переопределять метод Clone() в производных классах  
* Он требует, чтобы объекты реализовывали метод Clone() как static  
* Он определяет метод Clone() как void  
* Он поддерживает клонирование только ссылочных типов  
* Он возвращает значение типа object из метода Clone()

## **Вопрос 8**

Выберите код из представленных ниже, который создает обобщение MyGenericClass коллекции со следующими требованиями:  
а) тип \<K\> должен быть структурой и расширять интерфейс IDrawable;  
б) тип \<T\> должен быть ссылочным типом, допускающим значения NULL или не допускающим значения NULL, иметь стандартный конструктор и реализовывать обобщенный интерфейс IComparable.

* public class MyGenericClass \<K,T\> where K : struct, IDrawable  
  where T : class, IComparable, new()

* public class MyGenericClass \<K,T\> where K : struct, IDrawable\<T\>  
  where T : class, new(), IComparable

* public class MyGenericClass \<K,T\> where K : struct, IDrawable\<T\>  
  where T : class, IComparable\<T\>?, new()

* public class MyGenericClass \<K,T\> where K : struct, IDrawable  
  where T : class, IComparable\<T\>?, new()

* public class MyGenericClass \<K,T\> where K : struct, IDrawable\<T\>  
  where T : class?, new(), IComparable\<T\>

## **Вопрос 9**

В представленном коде событие TaskCompleted вызывается методом OnTaskCompleted после завершения работы метода Run():  
На мобильной платформе присутствует горизонтальный скролл кода  
public class TaskRunner  
{  
    public event EventHandler\<string\> TaskCompleted;  
    public void Run()  
    {  
        // Долгая работа  
        Thread.Sleep(1000);  
        OnTaskCompleted("Задача завершена");  
    }  
    protected virtual void OnTaskCompleted(string message)  
    {  
        TaskCompleted?.Invoke(this, message);  
    }  
}

Вы подписались на событие следующим образом:

var runner \= new TaskRunner();  
runner.TaskCompleted \+= (sender, msg) \=\> Console.WriteLine(msg);  
runner.Run();

Какой из следующих способов нужно применить, если вы хотите обеспечить вызов обработчика в многопоточном контексте, исключив риски гонки между проверкой и вызовом делегата?

* Копировать делегат в локальную переменную перед вызовом  
* Вызывать событие через Task.Run  
* Заменить EventHandler\<string\> на Action\<string\>  
* Сделать метод OnTaskCompleted static  
* Использовать оператор lock вокруг вызова Invoke

## **Вопрос 10**

Что такое race condition в многопоточном программировании?

* Состояние, когда потоки выполняются в неопределенном порядке  
* Ситуация, когда два потока пытаются одновременно получить доступ к одному и тому же ресурсу  
* Ситуация, когда один поток завершает свою работу раньше другого  
* Ситуация, когда два или более потоков бесконечно ждут друг друга  
* Проблема, возникающая при неверной координации потоков

## **Вопрос 11**

Какой будет результат выполнения следующего кода?

var num \= new List\<int\> { 1, 2, 3, 4, 5 };  
num.TakeWhile(x \=\> x \< 3).ToList().ForEach(x \=\> Console.WriteLine(x));

* 1 2 3  
* Ошибка компиляции  
* 1 2  
* 1  
* Ничего не выведет

## **Вопрос 12**

Что такое Dependency Injection в C\#?

* Механизм, который позволяет классу принимать экземпляры других классов, от которых он зависит, вместо того чтобы создавать их самостоятельно  
* Принцип, который диктует, что каждый метод должен иметь явные зависимости, переданные в качестве аргументов  
* Процесс, при котором зависимые классы всегда создаются с использованием оператора new  
* Подход, который обеспечивает, что все зависимости класса инкапсулированы внутри этого же класса  
* Способ реализации статических методов для устранения зависимостей между классами

## **Вопрос 13**

Какой из операторов позволяет безопасно привести тип объекта к другому типу, возвращая null в случае неудачи?

* is  
* (type)  
* unsafe  
* as  
* typeof

## **Вопрос 14**

Что выведет данный код?

Console.WriteLine("Значение: {0:D}", 255);

* Значение: 255  
* Значение: 0x255  
* Значение: FF  
* Ошибка компиляции  
* Значение: 255.00

## **Вопрос 15**

Для чего используется ключевое слово await в C\#?

* Для ожидания завершения синхронной операции  
* Для указания, что метод не должен блокировать вызывающий поток  
* Для обозначения метода, который всегда выполняется в отдельном потоке  
* Для принудительного выполнения операции в основном потоке UI  
* Для обработки исключений в асинхронных методах