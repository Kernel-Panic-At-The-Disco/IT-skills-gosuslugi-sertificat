# Java_advanced

## Вопрос 1
Что будет выведено при исполнении данного участка кода?

```java
class SomeClass {
    public static int field = 0;
}
public class Main {
    public static void main(String[] args) {
        SomeClass someClass1 = new SomeClass();
        someClass1.field++;
        SomeClass someClass2 = new SomeClass();
        someClass2.field++;
        SomeClass someClass3 = new SomeClass();
        someClass3.field++;
        SomeClass.field++;
        ++SomeClass.field;
        System.out.println(++SomeClass.field);
    }
}
```

- 6
- 3
- 5
- 0
- 2

---

## Вопрос 2
Что будет выведено при исполнении следующего кода?

```java
public static void main(String[] args) {
    int[] arr = {1, 2, 3, 4, 5};
    for (int i = 0; i < arr.length; i++) {
        if (arr[i] % 2 == 0) {
            continue;
        }
        System.out.print(arr[i]);
    }
}
```

- 12345
- 12
- 24
- 135
- 15

---

## Вопрос 3
Каким будет результат выполнения данного кода?

```java
String s1 = new String("Java");
String s2 = new String("Java");
String s3 = s1;
System.out.println(s1 == s2);
System.out.println(s1.equals(s2));
System.out.println(s1 == s3);
```

- false true true
- true true false
- true false true
- true true true
- false false true

---

## Вопрос 4
Какой вызов метода addItem недопустим и приведёт к ошибке?

```java
class Storage<T> {
    T item;
    public Storage(T item) {
        this.item = item;
    }
    public static void main(String[] args) {
        Storage<Integer> s1 = new Storage<>(10);
        Storage<Number> s2 = new Storage<>(10.5);
        Storage<Object> s3 = new Storage<>(new Object());
        // addItem(...)
    }
    private static <T> void addItem(Storage<? super T> storage, T item) {
        storage.item = item;
    }
}
```

- addItem(s1, 10);
- addItem(s2, 10.5);
- addItem(s3, new Object());
- addItem(s1, new Number());
- addItem(s3, null);

---

## Вопрос 5
Что выведет на экран программа?

```java
public class Main {
    public static void main(String[] args) {
        try {
            int[] arr = new int[5];
            arr[100] = 500;
            System.out.println(1);
        } catch (ArithmeticException e) {
            System.out.println(2);
        }
    }
}
```

- Ничего, произойдёт ошибка исполнения
- Ничего, произойдёт ошибка компиляции
- 1
- 2
- Ничего, и программа завершится

---

## Вопрос 6
Какие структуры данных требуют, чтобы элементы были сравнимы с помощью интерфейса Comparator?

- HashSet
- ArrayDeque
- LinkedList
- LinkedHashMap
- PriorityQueue

---

## Вопрос 7
Какой способ итерирования по коллекции ArrayList приведёт к ConcurrentModificationException, если во время итерирования происходит модификация коллекции?

- ListIterator и метод remove()
- Цикл for с доступом по индексу
- Итератор и метод remove()
- Цикл for-each
- Стримы и метод forEach()

---

## Вопрос 8
После продолжительной работы сервиса показали, что память постоянно растет. Вы попросили вашего напарника проинспектировать код на наличие утечки памяти. Через пару дней он пришел с результатом, что утечкой памяти является циклическая ссылка в коде класса реализации графа.
Выглядит это следующим образом. Может ли это быть причиной утечки памяти? (в качестве GC используется ParallelGC)

```java
class Node {
    private Node edge = null;
    public Node getEdge() { return edge; }
    public void setEdge(Node edge) { this.edge = edge; }
    public void createAndDelete() {
        Node node1 = new Node();
        Node node2 = new Node();
        node1.setEdge(node2);
        node2.setEdge(node1);
    }
}
```

- Да. Так как у объектов с циклическими ссылками надо вызывать метод finalize() чтобы он очистился. Иначе GC не может их удалить
- Нет. Данные объекты не аллоцируются на куче при такой логике и тем самым не вызывают утечку
- Да. ParallelGC не умеет работать с циклическими ссылками, поэтому каждый вызов метода createAndDelete() увеличивает количество неуничтожаемых объектов
- Нет. Благодаря trace-логики GC циклические объекты легко очищаются, если до них невозможно дойти по ссылкам от root объектов
- Да. Из-за цикличности ссылок объекты не могут быть перемещены из молодого поколения в старое

---

## Вопрос 9
Что выведет на экран следующий код?

```java
interface Movable {
    void move();
}
abstract class Vehicle {
    abstract void fuel();
}
abstract class Car extends Vehicle implements Movable {
    public void move() {
        System.out.println("Car is moving");
    }
    public void fuel() {
        System.out.println("Car is fueled");
    }
}
public class Test {
    public static void main(String[] args) {
        Vehicle v = new Car();
        v.fuel();
    }
}
```

- Только Car is moving
- Ошибка исполнения
- Car is fueled, затем Car is moving
- Ошибка компиляции
- Только Car is fueled

---

## Вопрос 10
Вы разрабатываете многопоточное приложение, где несколько потоков должны обновлять общий счетчик. Какой из следующих подходов НЕ гарантирует, что обновления будут атомарными и НЕ приведут к ошибкам в подсчете?

- Использовать AtomicInteger для хранения значения счетчика и вызывать метод incrementAndGet() для обновления
- Использовать ReentrantLock с методами lock() и unlock() для контроля доступа к счетчику
- Использовать LongAdder вместо AtomicInteger для увеличения производительности при частых обновлениях счетчика
- Обернуть операцию увеличения счетчика в блок synchronized, чтобы гарантировать, что только один поток сможет обновлять счетчик в любой момент времени
- Использовать задержки с помощью Thread.sleep() для управления порядком выполнения потоков

---

## Вопрос 11
Что выведет на экран код?

```java
import java.util.*;
import java.util.stream.*;
public class Test {
    public static void main(String[] args) {
        List<String> strings = Arrays.asList("a", "b", "c", "d", "e");
        String result = strings.stream()
                .skip(2)
                .limit(2)
                .collect(Collectors.joining(","));
        System.out.println(result);
    }
}
```

- a,b
- c,d
- d,e
- c,d,e
- b,c

---

## Вопрос 12
Какая структура данных из перечисленных НЕ является lock-free (Java 8+)?

- ConcurrentHashMap
- ConcurrentLinkedQueue
- AtomicInteger
- Hashtable
- ConcurrentLinkedDeque

---

## Вопрос 13
В чём заключается ключевое отличие ReentrantLock от synchronized?

- ReentrantLock предоставляет более широкий набор инструментов для блокировки, в то время как synchronized такого набора не имеет
- ReentrantLock, в отличие от synchronized, позволяет только одному потоку захватывать блокировку в любой момент времени
- ReentrantLock используется для коммуникации между потоками, тогда как synchronized применяется для контроля доступа к ресурсам
- ReentrantLock всегда быстрее и эффективнее, по сравнению с synchronized
- ReentrantLock управляет приоритетом потоков, в то время как synchronized этого не делает

---

## Вопрос 14
Что выведет на экран код?

```java
ByteBuffer buffer = ByteBuffer.allocate(10);
buffer.put((byte) 1);
buffer.put((byte) 2);
buffer.flip();
System.out.print(buffer.get());
System.out.print("");
System.out.println(buffer.get());
```

- 22
- 21
- 11
- 12
- 258 0

---

## Вопрос 15
Какая гарантия отсутствует у volatile?

- Видимость изменений для других потоков
- Отношение happens-before между записью и последними чтениями
- Атомарность инкремента (x++)
- Консистентные обновления для всех потоков
- Предотвращение переупорядочивания инструкций

---

## Вопрос 16
Какие структуры данных требуют, чтобы элементы были сравнимы с помощью интерфейса Comparator?

- PriorityQueue
- HashSet
- LinkedList
- ArrayDeque
- LinkedHashMap

---

## Вопрос 17
В каком из следующих случаев возникнет ConcurrentModificationException при итерировании по LinkedList?

- Если использовать итератор и метод remove()
- Если использовать цикл for с доступом по индексу
- Если использовать ListIterator
- Если использовать метод clear() до начала итерации
- Если добавлять элемент в список в другом потоке

---

## Вопрос 18
Вы работаете над многопоточным приложением, и замечаете, что при увеличении количества потоков приложение начинает тормозить. Вы предполагаете, что проблема в сборке мусора. Какое из следующих утверждений может объяснить, что происходит?

- Многопоточные приложения всегда эффективнее, чем однопоточные, и никогда не вызывают проблем с GC
- Сборка мусора происходит быстрее, когда в приложении больше потоков, так как потоки работают параллельно и помогают GC
- GC останавливает все потоки во время сбора мусора, что и вызывает торможение
- Многопоточное приложение всегда увеличивает нагрузку на GC, так как каждый поток создаёт свои собственные объекты
- Множество потоков могут одновременно обращаться к одному и тому же объекту, что увеличивает операцию сборки мусора

---

## Вопрос 19
Что выведет на экран программа?

```java
interface I {
    default void method() {
        System.out.println("I");
    }
}
class A implements I {
    public static void smethod() {
        I.method();
    }
}
public class Main {
    public static void main(String[] args) {
        A.smethod();
    }
}
```

- Пустую строку
- Только method
- Ошибка компиляции
- Ошибку исполнения
- Только I

---

## Вопрос 20
Вы разрабатываете многопоточное приложение, где несколько потоков должны обновлять общий счетчик. Какой из следующих подходов НЕ гарантирует, что обновления будут атомарными и НЕ приведут к ошибкам в подсчете?

- Использовать ReentrantLock с методами lock() и unlock() для контроля доступа к счетчику
- Использовать AtomicInteger для хранения значения счетчика и вызывать метод incrementAndGet()
- Использовать LongAdder вместо AtomicInteger для увеличения производительности при частых обновлениях счетчика
- Использовать задержки с помощью Thread.sleep() для управления порядком выполнения потоков
- Обернуть операцию увеличения счетчика в блок synchronized, чтобы гарантировать, что только один поток сможет обновлять счетчик в любой момент времени

---

## Вопрос 21
Что выведет на экран программа?

```java
import java.util.*;
import java.util.stream.*;
public class Test {
    public static void main(String[] args) {
        List<String> list = Arrays.asList("one", "two", "Three");
        list.stream()
                .filter(s -> s.length() > 3)
                .map(s -> s.toUpperCase())
                .forEach(System.out::print);
    }
}
```

- three
- ONETWOTHREE
- Ошибка компиляции
- onetwothree
- THREE

---

## Вопрос 22
Какую основную функцию выполняет класс CyclicBarrier в Java?

- Сигнализация завершения потока с использованием notifyAll
- Выполнение метода несколько раз в одном потоке
- Приостановка потока на заданное время
- Создание потока с использованием конструктора
- Синхронизация нескольких потоков перед выполнением общей задачи

---

## Вопрос 23
Какое из следующих утверждений о механизмах синхронизации в Java является неверным (ложным)?

- Возможность выставлять приоритеты для потоков
- Обеспечение неблокирования с дополнительными возможностями
- Возможность отправлять сообщения между потоками
- Автоматическая синхронизация методов для обеспечения потокобезопасности
- Создание потоков альтернативным способом

---

## Вопрос 24
Что выведет на экран код?

```java
ByteBuffer buffer = ByteBuffer.allocate(10);
buffer.put((byte) 1);
buffer.put((byte) 2);
buffer.flip();
System.out.print(buffer.get());
System.out.print("");
System.out.println(buffer.get());
```

- 258 0
- 21
- 22
- 11
- 12

---

## Вопрос 25
Какое из следующих утверждений о методе finalize в Java является верным?

- Метод finalize всегда вызывается для всех объектов, которые становятся мусором
- Метод finalize доступен только в классах из пакета java
- Метод finalize должен быть вызван явно разработчиком
- Метод finalize автоматически вызывается до создания объекта
- Вызов метода finalize не гарантируется JVM

---

## Вопрос 26
Что будет выведено при выполнении следующего кода?

```java
class Test {
    int field = 30;
    public static int staticField = 20;
    public void increment() {
        field++;
        staticField++;
    }
}
public class Main {
    public static void main(String[] args) {
        Test obj1 = new Test();
        Test obj2 = new Test();
        obj1.increment();
        obj2.increment();
        System.out.println(obj1.field + " " + obj2.field + " " + Test.staticField);
    }
}
```

- 10 10 22
- 11 11 21
- 11 11 22
- 11 11 23
- 10 10 23

---

## Вопрос 27
Что выведет этот код?

```java
import java.util.ArrayList;
import java.util.Iterator;
import java.util.List;
public class Main {
    public static void main(String[] args) {
        List<Integer> list = new ArrayList<>();
        for (int i = 1; i <= 5; i++) {
            list.add(i);
        }
        Iterator<Integer> iterator = list.iterator();
        while (iterator.hasNext()) {
            Integer number = iterator.next();
            if (number % 2 == 0) {
                iterator.remove();
            }
        }
        System.out.print(list);
    }
}
```

- 1 3
- 3
- 1 2 3 4 5
- 1 2 4 5
- Будет выведено 1,2,3 и возникнет исключение ConcurrentModificationException

---

## Вопрос 28
Каким будет результат выполнения данного кода?

```java
String s1 = new String("Java");
String s2 = new String("Java");
String s3 = s1;
System.out.println(s1 == s2);
System.out.println(s1.equals(s2));
System.out.println(s1 == s3);
```

- true true true
- false true true
- true false true
- false false true
- true true true

---

## Вопрос 29
Какой вызов метода addItem недопустим и приведёт к ошибке?

```java
class Storage<T> {
    T item;
    public Storage(T item) {
        this.item = item;
    }
    public static void main(String[] args) {
        Storage<Integer> s1 = new Storage<>(10);
        Storage<Number> s2 = new Storage<>(10.5);
        Storage<Object> s3 = new Storage<>(new Object());
        // addItem(...)
    }
    private static <T> void addItem(Storage<? super T> storage, T item) {
        storage.item = item;
    }
}
```

- addItem(s1, 10);
- addItem(s2, 10.5);
- addItem(s3, new Object());
- addItem(s1, new Number());
- addItem(s3, null);

---

## Вопрос 30
Что выведет на экран программа?

```java
public class Main {
    public static void main(String[] args) {
        try {
            int[] arr = new int[5];
            arr[100] = 500;
            System.out.println(1);
        } catch (ArithmeticException e) {
            System.out.println(2);
        }
    }
}
```

- Ничего, произойдёт ошибка исполнения
- Ничего, произойдёт ошибка компиляции
- 1
- 2
- Ничего, и программа завершится

---