# PostgreSQL_base

---

## Вопрос 1
Какой тип данных следует использовать на месте пропуска \[...\], если планируется хранить JSON-строки с автоматической проверкой формата, при условии, что сложные операции поиска или фильтрации выполняться не будут?

1 CREATE TABLE some_table (  
2   json_field [...],  
3 );

- jsonb  
- text check (json_field is json)  
- text::json  
- json  
- varchar(json)

---

## Вопрос 2
Чем отличается тип данных char(n) от varchar(n)?

- С типом данных varchar невозможно использовать запросы с оператором LIKE  
- При вставке записей для строк char используются одинарные кавычки, а для varchar — двойные  
- Тип данных char(n) не позволяет хранить строку длиной n в отличие от varchar(n)  
- Скорость поиска строковых шаблонов данных char(n) выше, чем varchar(n)  
- Тип данных varchar(n) и char(n) имеют различия в объеме памяти, занимаемой строками длиной (x < n)

---

## Вопрос 3
Какую строчку нужно добавить на месте пропуска \[...\], чтобы при создании таблицы Person для колонки age действовало ограничение: все значения в колонке строго больше нуля?

1 CREATE TABLE Person (  
2   age [...],  
3 );

- integer > 0  
- integer unsigned  
- integer check (age > 0)  
- integer check > 0  
- integer positive

---

## Вопрос 4
В таблице some_table колонка id имеет тип данных serial. Вам нужно изменить его на bigserial. Какой из следующих вариантов команд позволяет корректно выполнить это изменение?

- alter table some_table alter column id type bigint, alter column id set default nextval('some_table_id_seq')  
- alter table some_table alter column id type bigserial  
- alter table some_table alter column id set data type bigserial using nextval('some_table_id_seq')  
- alter table some_table add column new_id bigserial, drop column id, rename column new_id to id  
- alter table some_table alter column id type bigint using id::bigint

---

## Вопрос 5
В существующую таблицу person необходимо добавить колонку fullname. Колонка должна быть конкатенацией двух полей firstname и secondname, разделенных пробелом. Какая команда позволит этого достичь?

- alter table person add column fullname text generated always (firstname || ' ' || secondname)  
- alter table person add column fullname text as (firstname || ' ' || secondname) virtual  
- alter table person add column fullname text generated always as (firstname || ' ' || secondname)  
- alter table person add column fullname text default concat(firstname, ' ', secondname)  
- alter table person add column fullname text generated always as (concat(firstname, ' ', secondname))

---

## Вопрос 6
Вы создали таблицу some_table, где колонка id использует последовательность my_sequence для автоматической генерации значений.

После чего вы выполнили команду alter table some_table drop column id cascade; Что НЕ будет удалено автоматически?

1 CREATE TABLE some_table (  
2   id INTEGER UNIQUE DEFAULT nextval('my_sequence')  
3 );

- Триггеры, связанные с id  
- Ссылающиеся записи в других таблицах  
- Индексы, связанные с id  
- Ограничения на колонку id  
- Последовательность my_sequence, связанная с id

---

## Вопрос 7
У вас есть список товаров, отсортированный по убыванию цены, и требуется отобразить вторую страницу результатов с товарами, чья цена превышает 50. На каждой странице должно быть показано по 15 товаров. Какие операторы следует использовать и в каком порядке?

- offset, limit, order by  
- where, limit, order by, offset  
- order by, limit, offset  
- limit, offset, where  
- where, order by, limit, offset

---

## Вопрос 8
У вас есть таблица some_table, в которой содержится 10,000 записей с уникальными значениями в колонке id (начиная с 1 и увеличиваясь на 1 для каждой новой записи). Вы хотите получить последние 5 записей, где id является четным числом, и при этом исключить последние две четные записи.

Какой результат для id будет получен в результате выполнения следующего запроса?

1 SELECT id FROM some_table WHERE id % 2 = 0 ORDER BY id DESC LIMIT 5 OFFSET 2;

- 9992, 9990, 9988, 9986, 9984  
- 9996, 9994, 9992, 9988, 9984  
- 9998, 9996, 9994, 9992, 9990  
- 9994, 9992, 9990, 9988, 9986  
- 9996, 9994, 9992, 9990, 9988

---

## Вопрос 9
Вам нужно создать таблицу customer с колонкой customer_id, на которую будут ссылаться другие таблицы через внешний ключ. В таблице customer допускается наличие пустых значений в customer_id, и уникальность значений в этой колонке не требуется. Какое минимальное ограничение необходимо указать для колонки customer_id, чтобы использовать её в качестве внешнего ключа?

1 CREATE TABLE customer (  
2   customer_id [...]  
3 );  
4  
5 CREATE TABLE orders (  
6   order_id SERIAL PRIMARY KEY,  
7   customer_ref INTEGER REFERENCES customer(customer_id)  
8 );

- check (customer_id > 0)  
- unique  
- not null  
- Ограничение не нужно  
- primary key

---

## Вопрос 10
В базе данных есть таблица projects, которая хранит информацию о проектах, и таблица tasks для задач, связанных с каждым проектом. При удалении проекта из projects нужно автоматически удалить все связанные с ним задачи в tasks, не затрагивая при этом подзадачи в таблице subtasks.

Какой параметр нужно использовать на месте [...] для project_id в таблице tasks, чтобы обеспечить такую логику?

1 CREATE TABLE projects (  
2   project_id SERIAL PRIMARY KEY,  
3   project_name VARCHAR NOT NULL  
4 );  
5  
6 CREATE TABLE tasks (  
7   task_id SERIAL PRIMARY KEY,  
8   task_name VARCHAR NOT NULL,  
9   project_id INTEGER REFERENCES projects(project_id) [...]  
10 );  
11  
12 CREATE TABLE subtasks (  
13   subtask_id SERIAL PRIMARY KEY,  
14   subtask_name VARCHAR NOT NULL,  
15   task_id INTEGER REFERENCES tasks(task_id)  
16 );

- ON DELETE NO ACTION  
- ON DELETE CASCADE  
- ON UPDATE SET DEFAULT  
- ON DELETE SET NULL  
- ON UPDATE RESTRICT