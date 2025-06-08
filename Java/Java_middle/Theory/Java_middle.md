# Java_middle

## **Вопрос 1**

Вставьте на место пропуска (\_) корректное выражение, чтобы программа вывела "Great"

int value \= 75;  
String grade \= \_\_;  
System.out.println(grade); // Great

* (value \> 70 || value \< 80\) ? "Great": (value \> 80 ? "Excellent" : "Good");  
* (value \> 70 && value \< 80\) ? "Great": (value \> 80 ? "Excellent" : "Good");  
* value \> 70 ? "Great" : value \> 80 ? "Excellent" : "Good";  
* value \> 75 ? "Great" : value \> 75 ? "Excellent" : "Good";  
* value \>= 70 && value \<= 80 ? "Great" : value \> 80 ? "Excellent" : "Good"

## **Вопрос 2**

Что выведет следующая программа?

double d \= 10.0 / 3;  
int result \= (int) d;  
System.out.println(result);

* 3  
* 3.0  
* 3.33  
* Error: incompatible types  
* 10

## **Вопрос 3**

Что выведет на экран этот код?

int\[\] arr \= {1, 2, 3, 4, 5};  
for(int i \= 0; i \< arr.length / 2; i++) {  
    int temp \= arr\[i\];  
    arr\[i\] \= arr\[arr.length \- 1 \- i\];  
    arr\[arr.length \- 1 \- i\] \= temp;  
}  
System.out.println(Arrays.toString(arr));

* \[5, 2, 3, 4, 1\]  
* \[4, 3, 2, 1, 5\]  
* \[1, 2, 3, 4, 5\]  
* \[5, 4, 3, 2, 1\]  
* \[1, 4, 3, 2, 5\]

## **Вопрос 4**

Что выведет на экран программа?

int ans \= 0;  
for (int i \= 0; i \< 5; i++) {  
    ans \+= i++;  
}  
System.out.println(ans);

* 3  
* 18  
* 9  
* 27  
* 6

## **Вопрос 5**

Какой тип можно подставить в данной строке вместо слова ТИП?

ТИП\<Integer\> obj \= new ТИП\<\>();

* Невозможно указать подходящий тип  
* Только В  
* В и его наследников  
* В и его предков  
* Любой тип

## **Вопрос 6**

Что выведет на экран программа?

public class StaticFields {  
    static int number \= increment();  
    static int increment() {  
        return number \+ 5;  
    }  
    public static void main(String\[\] args) {  
        System.out.println(StaticFields.number);  
    }  
}

* Программа не скомпилируется  
* Программа скомпилируется, но упадёт с ошибкой  
* 0  
* 5  
* 10

## **Вопрос 7**

Какое из утверждений корректно описывает переопределение метода?

* Переопределяемый метод может ничего не возвращать даже если соответствующий метод суперкласса возвращает значение  
* Переопределение добавляет новый метод с набором параметров отличным от набора в суперклассе  
* Переопределяемый метод может возвращать значение даже если соответствующий метод суперкласса не возвращает значение  
* Переопределяемый метод может иметь более строгий модификатор доступа, чем метод суперкласса  
* Переопределение заменяет реализацию метода в наследнике

## **Вопрос 8**

Что выведет программа?

public static void main(String\[\] args) {  
    interface A {  
        default void foo() {  
            System.out.println("A");  
        }  
    }  
    interface B {  
        default void foo() {  
            System.out.println("B");  
        }  
    }  
    class C implements A, B {  
        @Override  
        public void foo() {  
            System.out.println("Foo");  
        }  
    }  
    A c \= new C();  
    c.foo();  
}

* B  
* Ошибка времени выполнения  
* Foo  
* Ошибка компиляции  
* A

## **Вопрос 9**

Что выведет на экран программа?

public class Test {  
    public static void main(String\[\] args) {  
        try {  
            throw new NullPointerException("Null Pointer");  
        } catch (RuntimeException e) {  
            System.out.println("Caught RuntimeException");  
        } catch (Exception e) {  
            System.out.println("Caught Exception");  
        }  
    }  
}

* Null Pointer  
* Ничего  
* Caught Exception  
* Caught RuntimeException  
* Программа упадёт с ошибкой исполнения

## **Вопрос 10**

Что выведет этот код?

HashSet\<Integer\> set \= new HashSet\<\>();  
set.add(1);  
set.add(2);  
set.add(3);  
for (Integer num : set) {  
    if (num \== 2\) {  
        set.remove(num);  
    }  
}  
System.out.println(set);

* \[1, 2\]  
* \[1, 3\]  
* \[1\]  
* Код упадёт с ошибкой  
* \[1, 2, 3\]

## **Вопрос 11**

Какое из следующих утверждений об интерфейсах в Java верно? (Java 8+)

* Интерфейс может содержать статические методы с реализацией  
* Интерфейс не может расширять (наследовать) другие интерфейсы  
* Интерфейс не может содержать переменные, только методы  
* Интерфейс может содержать только абстрактные методы  
* Интерфейс может быть инстанцирован с использованием ключевого слова new

## **Вопрос 12**

Что произойдет с потоком, если он попытается войти в synchronized блок, который уже занят другим потоком?

* Продолжит выполнение без каких-либо ожиданий, так как synchronized блоки не влияют на его выполнение  
* Немедленно завершит свое выполнение  
* Продолжит выполнение, но с меньшим приоритетом  
* Приостановит свое выполнение до момента, когда из другого потока будет вызван метод notify  
* Заблокируется до тех пор, пока другой поток не освободит монитор, после чего продолжит выполнение

## **Вопрос 13**

Какой вид стрима используется для десериализации объектов и имеет соответствующий метод для чтения объектов?

* ObjectInputStream  
* FileInputStream  
* BytesInputStream  
* SerializedStream  
* Любой стрим

## **Вопрос 14**

Что выведет фрагмент кода?

int day \= 4;  
SWITCH (day) {  
    case 1:  
        System.out.print("One");  
        break;  
    case 2:  
    case 4:  
        System.out.print("Four");  
        day \= 1;  
    case 5:  
        System.out.print("Five");  
}

* One  
* FourOne  
* Код не скомпилируется  
* FourFiveOne  
* FourFive

## **Вопрос 15**

В программе необходимо хранить температуру воды в градусах Цельсия в рамках теста, где она может колебаться от 0 до 128 градусов (только целые значения). Какой из перечисленных ниже типов данных максимально оптимален для хранения температуры с точки зрения памяти?

* short  
* int  
* char  
* byte  
* long

## **Вопрос 16**

Что выведет на экран программа?

int\[\] array \= {20, 10, 30, 40, 50, 60};  
for (int i \= 0; i \< array.length; i++) {  
    if (i % 2 \== 0\) {  
        array\[i\] \= i \* 10;  
    }  
}  
System.out.println(Arrays.toString(array));

* \[20, 10, 30, 40, 50, 60\]  
* \[20, 30, 40, 50, 60\]  
* \[20, 20, 40, 40, 60\]  
* \[0, 10, 30, 40\]  
* \[10, 20, 30, 40, 50\]

## **Вопрос 17**

Что произойдёт в данной программе?

System.out.print("Hello");  
while (true) {  
    System.out.print("World");  
    break;  
}

* В консоли будет напечатано "Hello World"  
* Выбросится исключение  
* В консоли будет напечатано "Hello"  
* Программа уйдёт в бесконечный цикл  
* Программа не скомпилируется

## **Вопрос 18**

Какой из перечисленных типов НЕ является воспроизводимым (reifiable)?

* List\<?\>  
* Integer  
* Comparable  
* String  
* ArrayList

## **Вопрос 19**

Что выведет на экран программа?

public class Initialization {  
    static int one \= defaultTwo();  
    static int defaultTwo() {  
        return one \+ 5;  
    }  
    static {  
        one \= 3;  
    }  
    public static void main(String\[\] args) {  
        System.out.println(Initialization.one);  
    }  
}

* 3  
* 0  
* 8  
* 10  
* 5

## **Вопрос 20**

Что выведет этот код?

class A {  
    void display() {  
        System.out.println("A");  
    }  
}  
class B extends A {  
    void display() {  
        System.out.println("B");  
    }  
}  
public class Main {  
    public static void main(String\[\] args) {  
        A a \= new B();  
        B b \= (B) a;  
        b.display();  
    }  
}

* A  
* B  
* A, затем B  
* B, затем A  
* Код не скомпилируется

## **Вопрос 21**

Что выведет на экран программа?

public class Test {  
    public static void main(String\[\] args) {  
        try {  
            throw new NullPointerException("Null Pointer");  
        } catch (RuntimeException e) {  
            System.out.println("Caught RuntimeException");  
        } catch (Exception e) {  
            System.out.println("Caught Exception");  
        }  
    }  
}

* Caught RuntimeException  
* Ничего  
* Программа упадёт с ошибкой исполнения  
* Null Pointer  
* Caught Exception

## **Вопрос 22**

Что выведет этот код?

HashMap\<Integer, String\> map \= new HashMap\<\>();  
map.put(map.size(), "One");  
map.put(map.size() \+ 1, "Two");  
map.put(map.size() \- 1, "Three");  
System.out.println(map.get(1));

* Two  
* 3  
* 2  
* Three  
* One

## **Вопрос 23**

Какой из перечисленных элементов может присутствовать в интерфейсе на языке Java (Java8+)?

* Абстрактные конструкторы  
* Абстрактные методы  
* Конструкторы  
* Блоки инициализации  
* Финальные поля без инициализации

## **Вопрос 24**

Что произойдёт с потоком, если он попытается войти в synchronized блок, который уже занят другим потоком?

* Продолжит выполнение без каких-либо ожиданий, так как synchronized блоки не влияют на его выполнение  
* Немедленно завершит свое выполнение  
* Приостановит свое выполнение до момента, когда из другого потока будет вызван метод notify  
* Заблокируется до тех пор, пока другой поток не освободит монитор, после чего продолжит выполнение  
* Продолжит выполнение, но с меньшим приоритетом

## **Вопрос 25**

Какой из следующих форматов данных используется для стандартной сериализации объектов в Java?

* Бинарный формат  
* JSON-формат  
* Текстовый формат BASE64-кодирования  
* Формат .class-файла  
* XML-формат