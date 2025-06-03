# **SQL\_base**

**Вопрос 1**

Выберите синтаксически верный запрос:

1. select \* from users group by age  
2. select id , name , age from users  
3. from users select id and name and age  
4. select id and name and age from users  
5. from users select id , name , age

**Вопрос 2**

Выберите запрос, который вернет фильмы из России и Японии с рейтингом PG-13 (это рейтинг американской киноассоциации: PG-13 означает, что детям до 13 лет просмотр нежелателен):

1. select movie from movies where ( country \= 'Russia' or country \= 'Japan' ) and rating \= 'PG-13'  
2. select movie from movies where rating \= 'PG-13' and country \= 'Russia' or country \= 'Japan'  
3. select movie from movies where country like Russia and country like Japan  
4. select movie from movies where country \= 'Russia' or country \= 'Japan' and rating \= 'PG-13'  
5. select movie from movies where country \= 'Russia' and country \= 'Japan' and rating \= 'PG-13'

**Вопрос 3**

Выберите ошибочное утверждение:

1. оператор GROUP BY выполняется перед WHERE  
2. оператор GROUP BY не требует после себя наличия оператора HAVING  
3. оператор GROUP BY можно выполнять над колонками, содержащими NULL-значения  
4. оператор GROUP BY можно использовать для удаления дубликатов  
5. оператор HAVING фильтрует строки после группировки

**Вопрос 4**

Выберите верное утверждение:

1. функция CUMSUM в SQL является агрегирующей и используется для вычисления накопительных сумм  
2. агрегирующие функции можно применять без GROUP BY при соблюдении определенных условий  
3. аргумент агрегирующей функции может содержать агрегирующую функцию  
4. для работы с датами обязательно надо использовать нестандартные агрегирующие функции, которые нельзя применять к другим типам данных  
5. агрегирующая функция COUNT, которая применяется к колонке с NULL-значениями, вернет NULL

**Вопрос 5**

Какая из диаграмм Венна соответствует запросу:

select \<select\_list\> from tableA A full outer join tableB B on A.key \= B.key where A.key is null or B.key is null

1. 2  
2. 3  
3. 1  
4. 4  
5. 5

**Вопрос 6**

Дана таблица:

| id | name | surname |
| :---- | :---- | :---- |
| 1 | Luke | Skywalker |
| 2 | Bruce | Wain |
| 3 | Tony | Stark |
| 4 | Dominic | Torreto |

Нужно вывести в одной колонке полное имя, например Luke Skywalker. Как называется метод, который сделает это?

1. инкапсуляция  
2. параметризация  
3. конкатенация  
4. рекурсия  
5. инверсия

**Вопрос 7**

Рассмотрим таблицу products со столбцами category и price.

Если SQL-запрос позволяет подсчитать количество товаров в каждой категории:

SELECT category , COUNT ( \* ) FROM products \_\_\_ category ; какая конструкция должна быть на месте пропуска?

1. HAVING  
2. DISTINCT  
3. GROUP BY  
4. WHERE  
5. ORDER BY

**Вопрос 8**

Определите только те ключевые слова, которые относятся к операторам условной логики:

1. EXISTS , CASE , NULLIF , LIKE  
2. WHEN , END , UNION , IF  
3. ELSE , NULLIF , WHEN , IFNULL  
4. IFNULL , CASE , ANY , NULL  
5. COALESCE , IF , CASE , THEN

**Вопрос 9**

Выберите верное утверждение:

1. коррелированный подзапрос выполняется автономно от основного запроса  
2. подзапрос не может возвращать NULL значения  
3. подзапрос обязан возвращать больше 1 колонки  
4. подзапрос в WHERE обязан возвращать максимум 1 значение  
5. подзапрос может вернуть как 1 значение , так и колонку со значениями

**Вопрос 10**

Выберите вариант со всеми типами данных, относящимися к числовым:

1. Float4 , integer , decimal , smallint  
2. real , char , time , numeric  
3. int4 , Ints , float4 , time  
4. higint , char , floats , numeric  
5. bigint , int4 , float4 , varchar , boolean