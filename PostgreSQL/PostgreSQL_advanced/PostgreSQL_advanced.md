# PostgreSQL\_advanced

**Вопрос 1**

Существует структура базы данных. Какая команда на месте \[...\] позволит создать новую запись в таблице role?

1 \-- структура базы данных  
2 CREATE TYPE permission AS ENUM (  
3   'read',  
4   'write',  
5   'execute'  
6 );  
7  
8 CREATE TABLE role (  
9   permissions permission\[\]  
10 );  
11  
12 \-- запрос  
13 INSERT INTO role (...) VALUES (... \[...\]);

1. array\['read'\]::permission\[\]  
2. (permission.read)  
3. "read"  
4. ('read') AS permission\[\]  
5. array\['read'\]

**Вопрос 2**

Какое утверждение относительно генерируемых колонок является ложью?

1. Значение генерируемой колонки нельзя установить вручную через INSERT или UPDATE  
2. Генерируемые колонки бывают двух типов: stored и virtual  
3. Генерируемые колонки могут ссылаться на другие генерируемые колонки.  
4. Выражение для вычисления генерируемой колонки не может содержать ссылки на большинство системных таблиц  
5. Для stored генерируемых колонок значение сохраняется в таблице и не пересчитывается при каждом обращении

**Вопрос 3**

Имеется следующая структура, представленная на изображении. Было решено во все существующие записи в таблице role добавить пермиссию 'read' так, чтобы не было дубликатов. Как этого достичь?

1 CREATE TYPE permission AS ENUM ('read', 'write', 'execute', 'transfer', 'download');  
2  
3 CREATE TABLE role (  
4   permissions permission\[\]  
5 );

1. UPDATE role SET permissions \= array\_append(permissions, 'demoMode') WHERE permissions \-\> 'demoMode'  
2. UPDATE role SET permissions \= array\_append(permissions, 'read') WHERE array\_position(permissions, 'read') IS NULL  
3. UPDATE role SET permissions \= array\_append(permissions, "read") WHERE array\_position(permissions, "read")  
4. UPDATE TABLE role ALTER COLUMN permissions array\_append(permissions, 'read')  
5. UPDATE TABLE role ALTER COLUMN permissions distinct(array\_append(permissions, "read"))

**Вопрос 4**

Вы создаёте временную таблицу temp\_data, объединяя результаты двух запросов с несовместимыми типами данных (например, integer и text).

Таблица должна:

* Автоматически принимать структуру первого запроса.  
* Сохранять дублирующиеся строки.

Какой подход нужно использовать?

1 CREATE TEMPORARY TABLE temp\_data AS  
2 \<оператор\> SELECT id, data FROM source1  
3 \<оператор\> SELECT id, info FROM source2;

1. Использовать UNION, чтобы исключить дубликаты и автоматически привести типы данных  
2. Использовать UNION ALL, чтобы сохранить дубликаты и автоматически привести типы данных  
3. Использовать UNION ALL, но предварительно создать временную таблицу с заданными типами данных  
4. Использовать UNION, но предварительно привести типы данных в запросах  
5. Использовать INTERSECT, чтобы сохранить только общие строки из обоих запросов

**Вопрос 5**

У вас есть две связанные таблицы, где t2 использует значение из последовательности по умолчанию при обновлении ссылочной записи. Какие проблемы могут возникнуть при удалении записей из t1?

1 CREATE SEQUENCE seq START WITH 1 INCREMENT BY 1;  
2 CREATE TABLE t1 (  
3   id SERIAL PRIMARY KEY  
4 );  
5 CREATE TABLE t2 (  
6   id INTEGER DEFAULT nextval('seq') REFERENCES t1(id) ON DELETE SET DEFAULT  
7 );

1. Операция удаления возможна только при явном использовании CASCADE, даже если задано ON DELETE SET DEFAULT  
2. Удаление завершится успешно, но строки в t2, ссылающиеся на удалённые записи, станут недействительными, требуя дополнительной проверки  
3. Транзакция с операцией удаления завершится с ошибкой, если в таблице t2 есть строки, ссылающиеся на удаляемую запись в t1  
4. Удаление записи из t1 приведёт к изменению ссылающихся записей в t2 на значение по умолчанию из последовательности, что может нарушить логику приложения  
5. Если nextval('seq') возвращает значение, отсутствующее в t1, операция удаления завершится с ошибкой

**Вопрос 6**

В таблице some\_table содержится 1 миллион записей. На колонке id создан индекс B-Tree, а на колонке name — индекс GIN для полнотекстового поиска. Какой запрос оптимально использует индекс, если выборка данных составляет менее 0.1% от общего объёма?

1 CREATE TABLE some\_table (  
2   id SERIAL,  
3   name VARCHAR(30),  
4   description TEXT  
5 );  
6 CREATE INDEX some\_table\_id\_index ON some\_table USING btree(id);  
7 CREATE INDEX some\_table\_name\_gin\_index ON some\_table USING gin(to\_tsvector('english', name));

1. SELECT \* FROM some\_table WHERE to\_tsvector('english', name) @@ to\_tsquery('example');  
2. SELECT \* FROM some\_table WHERE description ILIKE '%example%';  
3. SELECT \* FROM some\_table WHERE id \> 500000 AND id \< 500010;  
4. SELECT \* FROM some\_table WHERE name LIKE 'A%';  
5. SELECT \* FROM some\_table WHERE id \= 1000;

**Вопрос 7**

Таблица logs содержит миллиарды записей и используется для анализа активности. Наиболее частый запрос к таблице выбирает записи по колонке user\_id и фильтрует их по диапазону значений в колонке event\_time. Какой индекс лучше всего подходит для ускорения выполнения этого запроса?

1 CREATE TABLE logs (  
2   id SERIAL PRIMARY KEY,  
3   user\_id INTEGER NOT NULL,  
4   event\_time TIMESTAMP NOT NULL,  
5   action TEXT  
6 );  
7 \-- Часто используемый запрос  
8 SELECT \* FROM logs  
9 WHERE user\_id \= 12345 AND event\_time BETWEEN '2024-01-01' AND '2024-01-31';

1. CREATE INDEX logs\_user\_event\_index ON logs(user\_id, event\_time);  
2. CREATE INDEX logs\_event\_index ON logs(event\_time);  
3. CREATE INDEX logs\_event\_user\_index ON logs(event\_time, user\_id);  
4. CREATE INDEX logs\_user\_event\_hash ON logs USING hash(user\_id, event\_time);  
5. CREATE INDEX logs\_user\_index ON logs(user\_id);

**Вопрос 8**

Существует таблица some\_table.

| class | value |
| :---- | :---- |
| 1 | 10 |
| 1 | 20 |
| 1 | 100 |
| 2 | 200 |

Запускаются две транзакции Т1 и Т2. Какой вид изолированности транзакции НЕ позволит исполнить commit?

1 \-- T1  
2 SELECT SUM(value) FROM mytab WHERE class \= 1;  
3 INSERT INTO some\_table(class, value) VALUES (2, 30);  
4 COMMIT;  
5 \-- T2  
6 SELECT SUM(value) FROM mytab WHERE class \= 2;  
7 INSERT INTO some\_table(class, value) VALUES (1, 300);  
8 COMMIT;

1. read committed  
2. serializable  
3. repeatable read  
4. read uncommitted  
5. snapshot

**Вопрос 9**

В PostgreSQL вы создаёте индекс в транзакции над таблицей users. Во время выполнения этой транзакции другая транзакция пытается выполнить одну из следующих команд над той же таблицей. Какая команда выполнится без конфликтов?

1 \-- Первая транзакция  
2 BEGIN;  
3 CREATE INDEX idx\_users\_name ON users(name);  
4 \-- Вторая транзакция  
5 \<выбранная команда\>;

1. VACUUM users;  
2. SELECT \* FROM users WHERE id \= 1000 FOR UPDATE;  
3. CREATE INDEX CONCURRENTLY idx\_users\_email ON users(email);  
4. SELECT \* FROM users;  
5. INSERT INTO users (name) VALUES ('Alice');

**Вопрос 10**

Какие утверждения о следующем запросе правдивы?

1 CREATE MATERIALIZED VIEW some\_view AS SELECT \* FROM some\_table ORDER BY id DESC WITH NO DATA;

1. Возможна операция вставки в представление some\_view  
2. Чтение возможно сразу после создания представления some\_view  
3. Возможна операция REFRESH MATERIALIZED VIEW CONCURRENTLY some\_view  
4. Так как использовалось выражение SELECT \*, при модификации таблицы some\_table изменятся и колонки в представлении some\_view  
5. Для представления some\_view можно создать индекс

**Вопрос 11**

У вас есть рабочая база данных с высокой нагрузкой и её копия. Вы хотите проанализировать производительность запроса, чтобы исключить влияние нагрузки на результаты анализа.

Какую команду следует использовать для тестирования на копии базы данных?

1. Выполнить запрос несколько раз и взять среднее время выполнения.  
2. pgbench для эмуляции нагрузки и затем использовать explain analyze  
3. explain  
4. explain analyze  
5. explain (analyze, buffers)

**Вопрос 12**

В таблице orders содержится 1 миллион записей. На колонке customer\_id есть индекс B-Tree. Вы выполняете следующий запрос с фильтрацией по customer\_id и выбираете 90 % строк. Какой тип сканирования таблицы будет использован планировщиком PostgreSQL?

1 CREATE TABLE orders (  
2   order\_id SERIAL PRIMARY KEY,  
3   customer\_id INTEGER NOT NULL,  
4   order\_date DATE,  
5   total\_amount NUMERIC  
6 );  
7 \-- Индекс  
8 CREATE INDEX idx\_orders\_customer\_id ON orders (customer\_id);  
9 \-- запрос  
10 EXPLAIN SELECT \* FROM orders WHERE customer\_id \< 900000;

1. seq scan  
2. index only scan  
3. bitmap heap scan  
4. bitmap index scan  
5. index scan

**Вопрос 13**

Существует таблица, представленная на изображении. В эту таблицу сохраняются данные, журналирующие некоторые действия. После очередного релиза частота вставки записей, где action \= 'login', возросла в десять раз. Оперативно релиз починить не удается, но есть доступ к базе данных. Было решено временно не вставлять данные, где action \= 'login', сохранив уже существующие записи.

Как этого достичь?

1 CREATE TABLE action\_log (  
2   id SERIAL,  
3   action VARCHAR,  
4   description TEXT  
5 );

1. Создать instead of trigger, запрещающий 'login'  
2. Создать after insert trigger, удаляющий вставленную строку  
3. Создать constraint на колонку action, запрещающий 'login'  
4. Создать представление с условием: where action \!= 'login'  
5. Создать before insert trigger, запрещающий 'login'

**Вопрос 14**

В PostgreSQL пользователь manuel должен получить полный доступ к таблице kinds.

Следующая команда выполнена другим пользователем. Какой будет результат выполнения команды, если исполняющий пользователь не является суперпользователем и не является владельцем таблицы?

1 GRANT ALL PRIVILEGES ON kinds TO manuel;

1. manuel получит полный доступ к таблице kinds, включая возможность передавать права другим пользователям  
2. Команда завершится ошибкой, так как исполнитель команды не является владельцем таблицы  
3. manuel получит все права, которые есть у исполнителя команды на таблицу kinds  
4. Права на таблицу kinds будут изменены только для схемы, в которой она находится, но manuel доступ не получит  
5. manuel получит доступ только на чтение таблицы kinds, если исполнитель команды обладает таким правом

**Вопрос 15**

По мере продвижения бизнеса росло количество запросов к базе данных, а именно возросло в несколько раз количество запросов на запись при том же уровне запросов на чтение и повысилось требование к отказоустойчивости.

Какими методиками можно воспользоваться для поддержания работоспособности сервиса с учетом того, что запросов по ключу большинство?

1. Репликация вместе с вертикальным шардированием  
2. Репликация вместе с горизонтальным шардированием  
3. Репликация  
4. Вертикальное шардирование  
5. Горизонтальное шардирование