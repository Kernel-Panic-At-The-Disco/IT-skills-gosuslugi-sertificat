# PostgreSQL_advanced

---

## Вопрос 1
Существует структура базы данных. Какая команда на месте \[...\] позволит создать новую запись в таблице role?

1 -- структура базы данных  
2 CREATE TYPE permission AS ENUM (  
3   'read',  
4   'write',  
5   'execute'  
6 );  
7  
8 CREATE TABLE role (  
9   permissions permission[]  
10 );  
11  
12 -- запрос  
13 INSERT INTO role (...) VALUES (... [...]);

- array['read']::permission[]  
- (permission.read)  
- "read"  
- ('read') AS permission[]  
- array['read']

---

## Вопрос 2
Какое утверждение относительно генерируемых колонок является ложью?

- Значение генерируемой колонки нельзя установить вручную через INSERT или UPDATE  
- Генерируемые колонки бывают двух типов: stored и virtual  
- Генерируемые колонки могут ссылаться на другие генерируемые колонки.  
- Выражение для вычисления генерируемой колонки не может содержать ссылки на большинство системных таблиц  
- Для stored генерируемых колонок значение сохраняется в таблице и не пересчитывается при каждом обращении

---

## Вопрос 3
Имеется следующая структура, представленная на изображении. Было решено во все существующие записи в таблице role добавить пермиссию 'read' так, чтобы не было дубликатов. Как этого достичь?

1 CREATE TYPE permission AS ENUM ('read', 'write', 'execute', 'transfer', 'download');  
2  
3 CREATE TABLE role (  
4   permissions permission[]  
5 );

- UPDATE role SET permissions = array_append(permissions, 'demoMode') WHERE permissions -> 'demoMode'  
- UPDATE role SET permissions = array_append(permissions, 'read') WHERE array_position(permissions, 'read') IS NULL  
- UPDATE role SET permissions = array_append(permissions, "read") WHERE array_position(permissions, "read")  
- UPDATE TABLE role ALTER COLUMN permissions array_append(permissions, 'read')  
- UPDATE TABLE role ALTER COLUMN permissions distinct(array_append(permissions, "read"))

---

## Вопрос 4
Вы создаёте временную таблицу temp_data, объединяя результаты двух запросов с несовместимыми типами данных (например, integer и text).

Таблица должна:

* Автоматически принимать структуру первого запроса.  
* Сохранять дублирующиеся строки.

Какой подход нужно использовать?

1 CREATE TEMPORARY TABLE temp_data AS  
2 <оператор> SELECT id, data FROM source1  
3 <оператор> SELECT id, info FROM source2;

- Использовать UNION, чтобы исключить дубликаты и автоматически привести типы данных  
- Использовать UNION ALL, чтобы сохранить дубликаты и автоматически привести типы данных  
- Использовать UNION ALL, но предварительно создать временную таблицу с заданными типами данных  
- Использовать UNION, но предварительно привести типы данных в запросах  
- Использовать INTERSECT, чтобы сохранить только общие строки из обоих запросов

---

## Вопрос 5
У вас есть две связанные таблицы, где t2 использует значение из последовательности по умолчанию при обновлении ссылочной записи. Какие проблемы могут возникнуть при удалении записей из t1?

1 CREATE SEQUENCE seq START WITH 1 INCREMENT BY 1;  
2 CREATE TABLE t1 (  
3   id SERIAL PRIMARY KEY  
4 );  
5 CREATE TABLE t2 (  
6   id INTEGER DEFAULT nextval('seq') REFERENCES t1(id) ON DELETE SET DEFAULT  
7 );

- Операция удаления возможна только при явном использовании CASCADE, даже если задано ON DELETE SET DEFAULT  
- Удаление завершится успешно, но строки в t2, ссылающиеся на удалённые записи, станут недействительными, требуя дополнительной проверки  
- Транзакция с операцией удаления завершится с ошибкой, если в таблице t2 есть строки, ссылающиеся на удаляемую запись в t1  
- Удаление записи из t1 приведёт к изменению ссылающихся записей в t2 на значение по умолчанию из последовательности, что может нарушить логику приложения  
- Если nextval('seq') возвращает значение, отсутствующее в t1, операция удаления завершится с ошибкой

---

## Вопрос 6
В таблице some_table содержится 1 миллион записей. На колонке id создан индекс B-Tree, а на колонке name — индекс GIN для полнотекстового поиска. Какой запрос оптимально использует индекс, если выборка данных составляет менее 0.1% от общего объёма?

1 CREATE TABLE some_table (  
2   id SERIAL,  
3   name VARCHAR(30),  
4   description TEXT  
5 );  
6 CREATE INDEX some_table_id_index ON some_table USING btree(id);  
7 CREATE INDEX some_table_name_gin_index ON some_table USING gin(to_tsvector('english', name));

- SELECT * FROM some_table WHERE to_tsvector('english', name) @@ to_tsquery('example');  
- SELECT * FROM some_table WHERE description ILIKE '%example%';  
- SELECT * FROM some_table WHERE id > 500000 AND id < 500010;  
- SELECT * FROM some_table WHERE name LIKE 'A%';  
- SELECT * FROM some_table WHERE id = 1000;

---

## Вопрос 7
Таблица logs содержит миллиарды записей и используется для анализа активности. Наиболее частый запрос к таблице выбирает записи по колонке user_id и фильтрует их по диапазону значений в колонке event_time. Какой индекс лучше всего подходит для ускорения выполнения этого запроса?

1 CREATE TABLE logs (  
2   id SERIAL PRIMARY KEY,  
3   user_id INTEGER NOT NULL,  
4   event_time TIMESTAMP NOT NULL,  
5   action TEXT  
6 );  
7 -- Часто используемый запрос  
8 SELECT * FROM logs  
9 WHERE user_id = 12345 AND event_time BETWEEN '2024-01-01' AND '2024-01-31';

- CREATE INDEX logs_user_event_index ON logs(user_id, event_time);  
- CREATE INDEX logs_event_index ON logs(event_time);  
- CREATE INDEX logs_event_user_index ON logs(event_time, user_id);  
- CREATE INDEX logs_user_event_hash ON logs USING hash(user_id, event_time);  
- CREATE INDEX logs_user_index ON logs(user_id);

---

## Вопрос 8
Существует таблица some_table.

| class | value |
| :---- | :---- |
| 1 | 10 |
| 1 | 20 |
| 1 | 100 |
| 2 | 200 |

Запускаются две транзакции Т1 и Т2. Какой вид изолированности транзакции НЕ позволит исполнить commit?

1 -- T1  
2 SELECT SUM(value) FROM mytab WHERE class = 1;  
3 INSERT INTO some_table(class, value) VALUES (2, 30);  
4 COMMIT;  
5 -- T2  
6 SELECT SUM(value) FROM mytab WHERE class = 2;  
7 INSERT INTO some_table(class, value) VALUES (1, 300);  
8 COMMIT;

- read committed  
- serializable  
- repeatable read  
- read uncommitted  
- snapshot

---

## Вопрос 9
В PostgreSQL вы создаёте индекс в транзакции над таблицей users. Во время выполнения этой транзакции другая транзакция пытается выполнить одну из следующих команд над той же таблицей. Какая команда выполнится без конфликтов?

1 -- Первая транзакция  
2 BEGIN;  
3 CREATE INDEX idx_users_name ON users(name);  
4 -- Вторая транзакция  
5 <выбранная команда>;

- VACUUM users;  
- SELECT * FROM users WHERE id = 1000 FOR UPDATE;  
- CREATE INDEX CONCURRENTLY idx_users_email ON users(email);  
- SELECT * FROM users;  
- INSERT INTO users (name) VALUES ('Alice');

---

## Вопрос 10
Какие утверждения о следующем запросе правдивы?

1 CREATE MATERIALIZED VIEW some_view AS SELECT * FROM some_table ORDER BY id DESC WITH NO DATA;

- Возможна операция вставки в представление some_view  
- Чтение возможно сразу после создания представления some_view  
- Возможна операция REFRESH MATERIALIZED VIEW CONCURRENTLY some_view  
- Так как использовалось выражение SELECT *, при модификации таблицы some_table изменятся и колонки в представлении some_view  
- Для представления some_view можно создать индекс

---

## Вопрос 11
У вас есть рабочая база данных с высокой нагрузкой и её копия. Вы хотите проанализировать производительность запроса, чтобы исключить влияние нагрузки на результаты анализа.

Какую команду следует использовать для тестирования на копии базы данных?

- Выполнить запрос несколько раз и взять среднее время выполнения.  
- pgbench для эмуляции нагрузки и затем использовать explain analyze  
- explain  
- explain analyze  
- explain (analyze, buffers)

---

## Вопрос 12
В таблице orders содержится 1 миллион записей. На колонке customer_id есть индекс B-Tree. Вы выполняете следующий запрос с фильтрацией по customer_id и выбираете 90 % строк. Какой тип сканирования таблицы будет использован планировщиком PostgreSQL?

1 CREATE TABLE orders (  
2   order_id SERIAL PRIMARY KEY,  
3   customer_id INTEGER NOT NULL,  
4   order_date DATE,  
5   total_amount NUMERIC  
6 );  
7 -- Индекс  
8 CREATE INDEX idx_orders_customer_id ON orders (customer_id);  
9 -- запрос  
10 EXPLAIN SELECT * FROM orders WHERE customer_id < 900000;

- seq scan  
- index only scan  
- bitmap heap scan  
- bitmap index scan  
- index scan

---

## Вопрос 13
Существует таблица, представленная на изображении. В эту таблицу сохраняются данные, журналирующие некоторые действия. После очередного релиза частота вставки записей, где action = 'login', возросла в десять раз. Оперативно релиз починить не удается, но есть доступ к базе данных. Было решено временно не вставлять данные, где action = 'login', сохранив уже существующие записи.

Как этого достичь?

1 CREATE TABLE action_log (  
2   id SERIAL,  
3   action VARCHAR,  
4   description TEXT  
5 );

- Создать instead of trigger, запрещающий 'login'  
- Создать after insert trigger, удаляющий вставленную строку  
- Создать constraint на колонку action, запрещающий 'login'  
- Создать представление с условием: where action != 'login'  
- Создать before insert trigger, запрещающий 'login'

---

## Вопрос 14
В PostgreSQL пользователь manuel должен получить полный доступ к таблице kinds.

Следующая команда выполнена другим пользователем. Какой будет результат выполнения команды, если исполняющий пользователь не является суперпользователем и не является владельцем таблицы?

1 GRANT ALL PRIVILEGES ON kinds TO manuel;

- manuel получит полный доступ к таблице kinds, включая возможность передавать права другим пользователям  
- Команда завершится ошибкой, так как исполнитель команды не является владельцем таблицы  
- manuel получит все права, которые есть у исполнителя команды на таблицу kinds  
- Права на таблицу kinds будут изменены только для схемы, в которой она находится, но manuel доступ не получит  
- manuel получит доступ только на чтение таблицы kinds, если исполнитель команды обладает таким правом

---

## Вопрос 15
По мере продвижения бизнеса росло количество запросов к базе данных, а именно возросло в несколько раз количество запросов на запись при том же уровне запросов на чтение и повысилось требование к отказоустойчивости.

Какими методиками можно воспользоваться для поддержания работоспособности сервиса с учетом того, что запросов по ключу большинство?

- Репликация вместе с вертикальным шардированием  
- Репликация вместе с горизонтальным шардированием  
- Репликация  
- Вертикальное шардирование  
- Горизонтальное шардирование