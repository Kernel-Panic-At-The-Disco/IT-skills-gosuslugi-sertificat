# С#_middle

## **Вопрос 1**

В чем разница между типами var и dynamic?

* dynamic — устаревшее название типа var  
* Тип var определяется во время выполнения, тогда как тип dynamic — во время компиляции  
* Тип var изменяемый, тогда как тип dynamic неизменяемый  
* Тип dynamic изменяемый, тогда как тип var неизменяемый  
* Тип var определяется во время компиляции, тогда как тип dynamic — во время выполнения

---

## **Вопрос 2**

Что необходимо вставить вместо пропуска в коде ниже, чтобы сделать класс Person неизменяемым?

\_\_\_\_ Person (string Name)  
{  
    public string Name { get; init; }  
    public Person(string name) \=\> Name \= name;  
}

* Internal  
* Virtual  
* Abstract  
* Record  
* Private

---

## **Вопрос 3**

Что выведет данный код?  
На мобильной платформе присутствует горизонтальный скролл кода  
IEnumerable\<int\> test \= new List\<int\>() { 1, 2, 3, 4, 5, 6, 7, 8, 2, 10 };  
var t \= test.Select(x \=\> x / 2).Where(x \=\> x \== 2).Single();  
Console.WriteLine(string.Join("\*", t));

* Null  
* 2  
* Ошибка компиляции (Compile-time error)  
* Ошибка выполнения (Runtime error)  
* 2,2

---

## **Вопрос 4**

Что обозначает символ \* в параметре searchPattern метода Directory.EnumerateFiles?

* Только символы расширения файла  
* Регулярное выражение для имени файла  
* Один обязательный символ перед точкой  
* Последовательность символов любой длины  
* Один любой символ

---

## **Вопрос 5**

Что произойдёт при выполнении следующего кода, если файл "log.txt" существует и открыт другим процессом с эксклюзивным доступом?

using var stream \= File.Open("log.txt", FileMode.Open, FileAccess.ReadWrite, FileShare.None);

* Метод создаст новый файл, если файл не существует  
* Файл будет успешно открыт для чтения и записи  
* Файл будет открыт только для чтения, несмотря на параметры  
* Метод вернёт null, если файл занят  
* Возникнет исключение IOException, если файл открыт другим процессом

---

## **Вопрос 6**

Какое из перечисленных преобразований типов может привести к потере точности?

1\. ulong num \= 123l;  
2\. double value \= num;

* ulong num \= 123l; double value \= num;  
* var c \= 't'; var value \= (decimal) c;  
* Int32 num \= 123; var value \= Convert.ToDouble(num);  
* byte num \= 123; var value \= (UInt16) num;  
* SByte num \= 123; decimal value \= num;

---

## **Вопрос 7**

В соответствии с принципами семантического версионирования, что означает увеличение основного номера версии (Major) NuGet-пакета, например, с 1.4.2 до 2.0.0?

* Пакет больше не поддерживается текущей версией .NET SDK  
* Появились новые функции, не влияющие на существующий код  
* Версия указывает на нестабильный релиз и требует ручной установки  
* Были исправлены ошибки без изменения поведения  
* Произошли изменения, несовместимые с предыдущей версией

---

## **Вопрос 8**

В какой строке кода ниже допущена ошибка?  
На мобильной платформе присутствует горизонтальный скролл кода  
1\. record Person (string Name);  
2\. internal class Company  
3\. {  
4\.     Person\[\] personnel;  
5\.     public Company(Person\[\] person) \=\> this.personnel \= person; // 1 строка  
6\.     public int Length \=\> personnel.Length;  
7\.     public IEnumerable\<Person\> GetPerson(int max) // 2 строка  
8\.     {  
9\.         for (int i \= 0; i \< max; i++) // 3 строка  
10\.         {  
11\.             if (i \== personnel.Length)  
12\.                 return; // 4 строка  
13\.             yield return personnel\[i\]; // 5 строка  
14\.         }  
15\.     }  
16\. }

* 1 строка  
* 2 строка  
* 3 строка  
* 4 строка  
* 5 строка

---

## **Вопрос 9**

Вы добавили в .NET-проект пакет JsonMagic через NuGet, но при запуске проекта возникает следующая ошибка:  
Could not load file or assembly 'JsonMagic, Version=1.4.0.0, Culture=neutral, PublicKeyToken=null' or one of its dependencies. The located assembly's manifest definition does not match the assembly reference.  
При этом в csproj указан \<PackageReference Include="JsonMagic" Version="1.5.0" /\>.  
В проекте также присутствует файл app.config, в котором указан bindingRedirect.  
Что является причиной ошибки?

* Пакет был удалён из глобального кэша NuGet  
* В проекте нет ссылки на Newtonsoft.Json, от которого зависит JsonMagic  
* Версия сборки в bindingRedirect или зависимость устарела  
* Пакет JsonMagic требует аутентификации в NuGet-репозитории  
* Пакет JsonMagic не поддерживается на вашей версии .NET SDK

---

## **Вопрос 10**

Какой из следующих вариантов ограничивает параметр обобщенного типа объектом класса, реализующего интерфейс IEnumerable?

* class Processor\<T\> where T:new()  
* class Processor\<T\> with T: IEnumerable  
* class Processor\<T\> where T: IEnumerable  
* class Processor\<T\> where T: class::IEnumerable  
* class Processor\<T\> T: Interface IEnumerable

---

## **Вопрос 11**

Какое ключевое слово необходимо использовать, чтобы компилятор не создавал автоматически методы доступа add и remove для событий, оставив их реализацию на усмотрение производного класса?

* Abstract  
* Extern  
* Sealed  
* Static  
* Virtual

---

## **Вопрос 12**

В ходе разработки системы распределения заказов в службе доставки маркетплейса вам необходимо реализовать метод для оптимизации доставки товаров. Суть его работы: на основе числового идентификатора заказа с помощью разработанного вашей командой алгоритма из корзины выбираются товары, которые могут быть доставлены из распределительного центра в ближайшее время, и возвращается строковый GUID заказа из этого РЦ.

Выберите подходящий делегат для описанного метода.

* Event\<int, string\>  
* Func\<int,string\>  
* Func\<string, int\>  
* Action\<string, int\>  
* Action\<int, string\>