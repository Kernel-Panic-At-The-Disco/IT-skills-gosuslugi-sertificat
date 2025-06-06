# OOP_base

---

## Вопрос 1  
Укажите утверждение, наиболее точно описывающее разницу между классом и объектом.  

- Объект определяет структуру программы, а также процессы внутри нее, а класс является его воплощением  
- Класс — это экземпляр функции объекта, который определяет изменяемые характеристики и атрибуты  
- Класс это экземпляр объекта, а объект шаблон для создания классов, определяющих их методы и атрибуты  
- Класс содержит методы и переменные, тогда как объект является конкретной реализацией этих методов и переменных  
- Класс это программная реализация объектно-ориентированного программирования, а объект — результат работы данной программы  

---

## Вопрос 2  
Выберите вариант, в котором верно перечислены основные принципы объектно-ориентированного программирования.  

- Объектность, инкапсуляция, наследование, полиморфизм  
- Закрытость, инкапсуляция, декларативность, наследование  
- Абстракция, изменяемость, полиморфизм, декларативность  
- Абстракция, инкапсуляция, наследование, полиморфизм  
- Наследование, полиморфизм, изменяемость, объектность  

---

## Вопрос 3  
Какое из утверждений НЕ относится к принципам объектно-ориентированного программирования?  

- Можно единообразно обрабатывать объекты разного типа, но с общим классом или интерфейсом  
- Контроль за доступностью свойств и методов класса обеспечивают модификаторы доступа  
- Состояние объекта не может быть изменено после того, как объект был создан  
- Классы определяют набор методов и атрибутов, которые будут применяться ко всем объектам этого класса  
- Дочерние классы наследуют атрибуты и методы родительского класса  

---

## Вопрос 4  
Имеется класс «Еда», подкласс «Фрукт» и объект «Яблоко» класса «Фрукт». Какую иерархию иллюстрирует этот пример?  

- Массив → Переменная → Значение  
- Интерфейс → Родительский класс → Атрибут класса  
- Класс → Экземпляр класса → Атрибут класса  
- Класс → Интерфейс → Экземпляр класса  
- Родительский класс → Дочерний класс → Экземпляр класса  

---

## Вопрос 5  
Вы создаете класс «Машина» с методами «Завести», «Остановить» и «Ехать». Однако конкретные детали реализации этих методов для разных типов машин (например, бензиновых и электрических) оставляете для других классов, которые будут реализовывать этот функционал. Это пример использования какого принципа ООП?  

- Интерфейс  
- Полиморфизм  
- Абстракция  
- Инкапсуляция  
- Наследование  

---

## Вопрос 6  
Какой метод можно переопределить в классе, чтобы предоставить собственную реализацию обработки исключений для объектов данного класса?  

- `__exception__`  
- `__exit__`  
- `__tryexcept__`  
- `__handle__`  
- `__catch__`  

---

## Вопрос 7  
Какая из следующих характеристик отличает объектно-ориентированные языки программирования от процедурных?  

- Операции только с потоками данных и их фильтрацией  
- Обработка объектов через строгие декларативные структуры  
- Использование функций для разбиения программы на части  
- Преимущественная работа с реляционными данными и классами  
- Взаимодействие через объекты, содержащие данные и методы  

---

## Вопрос 8  
У вас есть класс Person, у которого атрибут Age объявлен как приватный. Вы пытаетесь напрямую изменить возраст объекта, созданного на основе этого класса, но получаете ошибку.  

Какое из утверждений верно?  

- Атрибут Age закрытый и доступен только для чтения внутри класса  
- Атрибут Age можно изменить, если установить модификатор доступа Accessible вместо Protected  
- Атрибут Age может быть изменен только при использовании программных декораторов  
- Атрибут Age доступен только в методах подклассов или в качестве внешней функции  
- Атрибут Age можно изменить, только унаследовав его от родительского класса  

---

## Вопрос 9  
Когда вызывается конструктор класса?  

- При наследовании одного класса от другого  
- При создании экземпляра класса  
- При вызове статического метода класса  
- Когда класс использует перегруженный оператор  
- Когда объект класса клонируется  

---

## Вопрос 10  
В классе Car есть метод `_update_speed`, который является защищенным. В какой ситуации будет корректно использовать этот метод?  

- Можно вызвать только внутри метода этого же класса или подклассов  
- Метод можно вызвать только через статический метод класса  
- Этот метод может быть использован любым объектом любого класса  
- Метод можно вызвать только с использованием публичных методов  
- Можно вызывать данный метод напрямую из любого класса  

---

## Вопрос 11  
Укажите утверждение, наиболее точно описывающее разницу между наследованием и полиморфизмом.  

- Наследование позволяет классу копировать методы из другого класса, а полиморфизм — это наследование с дополнительной реализацией методов  
- Наследование позволяет классу получать свойства и методы другого класса, а полиморфизм — изменять функциональность этих методов  
- Наследование — это механизм использования методов разных классов, а полиморфизм — механизм создания новых классов  
- Наследование и полиморфизм — это разные способы передачи данных, таких как информация об объекте, между классами  
- Наследование — это возможность одного класса передавать методы другому классу, а полиморфизм — возможность изменять функциональность существующих классов  

---

## Вопрос 12  
Вы создаете класс, внутри которого объявлена переменная, содержащая общее количество созданных объектов этого класса. Это пример...  

- Рекурсивного метода  
- Защищенного метода  
- Динамического поля  
- Статического поля  
- Абстрактного метода  

---

## Вопрос 13  
Вы создаёте класс Кот, в котором объявлен атрибут порода. Для него определён геттер, но отдельный сеттер не задан. Внутри конструктора класса создаётся объект Барсик с породой «персидская».  
Позже создаётся объект Пушинка. При попытке присвоить новое значение через `Пушинка.порода = «сиамская»` программа выдаёт ошибку.  
Кроме того, в дочернем классе УмныйКот вы пробуете обратиться к полю порода в методе, но получаете ошибку.  

Какое из утверждений верное?  

- Атрибут порода является protected, и попытка обращения из дочернего класса нарушает принцип инклюзивции  
- Атрибут порода недоступен извне, а также из подклассов, поскольку он private и требует использования сеттеров для изменения  
- Атрибут порода является публичным, но не может быть изменён, пока не будет использован super()  
- Атрибут порода является статическим, и его изменение через экземпляр приводит к ошибке  
- Атрибут порода можно изменить напрямую, но только внутри метода класса, не из основного тела скрипта  

---

## Вопрос 14  
Какой процесс позволяет создать новый объект на основе существующего класса?  

- Вызов метода конструктора класса с нужными аргументами  
- Использование наследования для создания объекта из родительского класса  
- Создание объекта через модификацию статического метода  
- Вызов приватного метода класса для инициализации объекта  
- Вызов метода деструктора с параметром Destruction = False  

---

## Вопрос 15  
Необходимо создать программу для управления аэропортом и отслеживания рейсов. Для этого мы будем использовать принципы ООП. Выберите вариант, который решит данную задачу наиболее полно.  

- Создаем класс «Рейс» с атрибутами «Номер рейса» и «Место назначения», который будет связан с классом «Самолет», а также методы «Отправить» и «Принять самолет»  
- Создаем класс «Аэропорт» с атрибутами «Название», «Местоположение» и «Список самолетов», а также методами «Добавить самолет» и «Убрать самолет»  
- Создаем класс «Самолет» и «Аэропорт» с атрибутами, связанными через номер рейса, и наследованием методов от класса «Диспетчер», который управляет расписанием  
- Создаем класс «Самолет» с атрибутами «Модель», «Вместимость» и «Рейс», а также методы «Вылететь» и «Приземлиться»  
- Создаем класс «Самолет» с атрибутами «Номер рейса» и «Пассажиры», который будет использовать методы класса «Аэропорт» для регистрации самолетов и пассажиров  

---

## Вопрос 16  
Какой вариант наиболее точно описывает разницу между методами и функциями в ООП?  

- Методы — это статичные блоки кода, а функции динамически взаимодействуют с данными объекта  
- Функция — это независимая единица кода, а метод привязан к объекту и может изменять его состояние  
- Метод — это переменная, которая хранит состояние объекта, а функция — блок кода, выполняющий действия над этим состоянием  
- Методы выполняют логику и изменяют состояние объекта, а функции — это блоки кода, которые возвращают результаты  
- Метод — это функция, которая может быть вызвана вне объекта, а функция — неизменяемая переменная, выполняющая действия  

---

## Вопрос 17  
Согласно принципу подстановки Барбары Лисков (Liskov Substitution Principle) в SOLID подклассы должны...  

- Иметь те же атрибуты, что и родительский класс, но не копировать методы  
- Наследовать методы родительского класса, но не изменять их функциональность  
- Заменять методы родительского класса своими атрибутами  
- Наследовать все атрибуты и методы родительского класса без изменений  
- Заменять родительские классы, не нарушая корректность программы  

---

## Вопрос 18  
Согласно принципу открытости/закрытости (Open-Closed Principle) в SOLID класс должен...  

- Быть закрыт для любых изменений и не должен расширяться  
- Быть открыт для расширения, но закрыт для модификации существующего кода  
- Позволить добавлять новые атрибуты и методы без ограничений и проверок  
- Быть открыт для модификации извне и закрыт для расширения внутри программы  
- Всегда закрывать доступ к методам и атрибутам от внешних изменений  

---

## Вопрос 19  
Вы создаете класс «Транспортное средство» и выделяете объекты «Мотоцикл» и «Автомобиль». После этого вы добавляете общие атрибуты, такие как «Количество колес» и «Максимальная скорость», и передаете объектам общий метод «Завести двигатель». Это пример реализации какого принципа ООП?  

- Закрытость  
- Полиморфизм  
- Интерфейс  
- Абстракция  
- Инкапсуляция  

---

## Вопрос 20  
В чем заключается основное различие между ООП и функциональными языками программирования?  

- В функциональных языках всегда используется неявная строгая динамическая типизация  
- В ООП акцент сделан на наследовании, полиморфизме и инкапсуляции  
- В ООП отсутствуют понятия состояния и побочных эффектов функций  
- В функциональных языках применяются только объекты и функции  
- В ООП основное внимание уделяется ресурсам  