# **PostgreSQL\_base**

**Вопрос 1**

Какой тип данных следует использовать на месте пропуска \[...\], если планируется хранить JSON-строки с автоматической проверкой формата, при условии, что сложные операции поиска или фильтрации выполняться не будут?

1 CREATE TABLE some\_table (  
2   json\_field \[...\],  
3 );

1. jsonb  
2. text check (json\_field is json)  
3. text::json  
4. json  
5. varchar(json)

**Вопрос 2**

Чем отличается тип данных char(n) от varchar(n)?

1. С типом данных varchar невозможно использовать запросы с оператором LIKE  
2. При вставке записей для строк char используются одинарные кавычки, а для varchar — двойные  
3. Тип данных char(n) не позволяет хранить строку длиной n в отличие от varchar(n)  
4. Скорость поиска строковых шаблонов данных char(n) выше, чем varchar(n)  
5. Тип данных varchar(n) и char(n) имеют различия в объеме памяти, занимаемой строками длиной (x \< n)

**Вопрос 3**

Какую строчку нужно добавить на месте пропуска \[...\], чтобы при создании таблицы Person для колонки age действовало ограничение: все значения в колонке строго больше нуля?

1 CREATE TABLE Person (  
2   age \[...\],  
3 );

1. integer \> 0  
2. integer unsigned  
3. integer check (age \> 0\)  
4. integer check \> 0  
5. integer positive

**Вопрос 4**

В таблице some\_table колонка id имеет тип данных serial. Вам нужно изменить его на bigserial. Какой из следующих вариантов команд позволяет корректно выполнить это изменение?

1. alter table some\_table alter column id type bigint, alter column id set default nextval('some\_table\_id\_seq')  
2. alter table some\_table alter column id type bigserial  
3. alter table some\_table alter column id set data type bigserial using nextval('some\_table\_id\_seq')  
4. alter table some\_table add column new\_id bigserial, drop column id, rename column new\_id to id  
5. alter table some\_table alter column id type bigint using id::bigint

**Вопрос 5**

В существующую таблицу person необходимо добавить колонку fullname. Колонка должна быть конкатенацией двух полей firstname и secondname, разделенных пробелом. Какая команда позволит этого достичь?

1. alter table person add column fullname text generated always (firstname || ' ' || secondname)  
2. alter table person add column fullname text as (firstname || ' ' || secondname) virtual  
3. alter table person add column fullname text generated always as (firstname || ' ' || secondname)  
4. alter table person add column fullname text default concat(firstname, ' ', secondname)  
5. alter table person add column fullname text generated always as (concat(firstname, ' ', secondname))

**Вопрос 6**

Вы создали таблицу some\_table, где колонка id использует последовательность my\_sequence для автоматической генерации значений.

После чего вы выполнили команду alter table some\_table drop column id cascade; Что НЕ будет удалено автоматически?

1 CREATE TABLE some\_table (  
2   id INTEGER UNIQUE DEFAULT nextval('my\_sequence')  
3 );

1. Триггеры, связанные с id  
2. Ссылающиеся записи в других таблицах  
3. Индексы, связанные с id  
4. Ограничения на колонку id  
5. Последовательность my\_sequence, связанная с id

**Вопрос 7**

У вас есть список товаров, отсортированный по убыванию цены, и требуется отобразить вторую страницу результатов с товарами, чья цена превышает 50\. На каждой странице должно быть показано по 15 товаров. Какие операторы следует использовать и в каком порядке?

1. offset, limit, order by  
2. where, limit, order by, offset  
3. order by, limit, offset  
4. limit, offset, where  
5. where, order by, limit, offset

**Вопрос 8**

У вас есть таблица some\_table, в которой содержится 10,000 записей с уникальными значениями в колонке id (начиная с 1 и увеличиваясь на 1 для каждой новой записи). Вы хотите получить последние 5 записей, где id является четным числом, и при этом исключить последние две четные записи.

Какой результат для id будет получен в результате выполнения следующего запроса?

1 SELECT id FROM some\_table WHERE id % 2 \= 0 ORDER BY id DESC LIMIT 5 OFFSET 2;

1. 9992, 9990, 9988, 9986, 9984  
2. 9996, 9994, 9992, 9988, 9984  
3. 9998, 9996, 9994, 9992, 9990  
4. 9994, 9992, 9990, 9988, 9986  
5. 9996, 9994, 9992, 9990, 9988

**Вопрос 9**

Вам нужно создать таблицу customer с колонкой customer\_id, на которую будут ссылаться другие таблицы через внешний ключ. В таблице customer допускается наличие пустых значений в customer\_id, и уникальность значений в этой колонке не требуется. Какое минимальное ограничение необходимо указать для колонки customer\_id, чтобы использовать её в качестве внешнего ключа?

1 CREATE TABLE customer (  
2   customer\_id \[...\]  
3 );  
4  
5 CREATE TABLE orders (  
6   order\_id SERIAL PRIMARY KEY,  
7   customer\_ref INTEGER REFERENCES customer(customer\_id)  
8 );

1. check (customer\_id \> 0\)  
2. unique  
3. not null  
4. Ограничение не нужно  
5. primary key

**Вопрос 10**

В базе данных есть таблица projects, которая хранит информацию о проектах, и таблица tasks для задач, связанных с каждым проектом. При удалении проекта из projects нужно автоматически удалить все связанные с ним задачи в tasks, не затрагивая при этом подзадачи в таблице subtasks.

Какой параметр нужно использовать на месте \[...\] для project\_id в таблице tasks, чтобы обеспечить такую логику?

1 CREATE TABLE projects (  
2   project\_id SERIAL PRIMARY KEY,  
3   project\_name VARCHAR NOT NULL  
4 );  
5  
6 CREATE TABLE tasks (  
7   task\_id SERIAL PRIMARY KEY,  
8   task\_name VARCHAR NOT NULL,  
9   project\_id INTEGER REFERENCES projects(project\_id) \[...\]  
10 );  
11  
12 CREATE TABLE subtasks (  
13   subtask\_id SERIAL PRIMARY KEY,  
14   subtask\_name VARCHAR NOT NULL,  
15   task\_id INTEGER REFERENCES tasks(task\_id)  
16 );

1. ON DELETE NO ACTION  
2. ON DELETE CASCADE  
3. ON UPDATE SET DEFAULT  
4. ON DELETE SET NULL  
5. ON UPDATE RESTRICT