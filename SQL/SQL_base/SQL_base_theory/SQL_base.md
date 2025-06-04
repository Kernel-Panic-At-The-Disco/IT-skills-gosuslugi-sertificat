# SQL_base

## Вопрос 1  
Выберите синтаксически верный запрос:  

- select * from users group by age  
- select id, name, age from users  
- from users select id and name and age  
- select id and name and age from users  
- from users select id, name, age  

---

## Вопрос 2  
Выберите запрос, который вернет фильмы из России и Японии с рейтингом PG-13:  

- select movie from movies where (country = 'Russia' or country = 'Japan') and rating = 'PG-13'  
- select movie from movies where rating = 'PG-13' and country = 'Russia' or country = 'Japan'  
- select movie from movies where country like Russia and country like Japan  
- select movie from movies where country = 'Russia' or country = 'Japan' and rating = 'PG-13'  
- select movie from movies where country = 'Russia' and country = 'Japan' and rating = 'PG-13'  

---

## Вопрос 3  
Выберите ошибочное утверждение:  

- оператор GROUP BY выполняется перед WHERE  
- оператор GROUP BY не требует после себя наличия оператора HAVING  
- оператор GROUP BY можно выполнять над колонками, содержащими NULL-значения  
- оператор GROUP BY можно использовать для удаления дубликатов  
- оператор HAVING фильтрует строки после группировки  

---

## Вопрос 4  
Выберите верное утверждение:  

- функция CUMSUM в SQL является агрегирующей и используется для вычисления накопительных сумм  
- агрегирующие функции можно применять без GROUP BY при соблюдении определенных условий  
- аргумент агрегирующей функции может содержать агрегирующую функцию  
- для работы с датами обязательно надо использовать нестандартные агрегирующие функции, которые нельзя применять к другим типам данных  
- агрегирующая функция COUNT, которая применяется к колонке с NULL-значениями, вернет NULL  

---

## Вопрос 5  
Какая из диаграмм Венна соответствует запросу:  
`select <select_list> from tableA A full outer join tableB B on A.key = B.key where A.key is null or B.key is null`  

- 2  
- 3  
- 1  
- 4  
- 5  

---

## Вопрос 6  
Дана таблица:  
| id | name    | surname    |
|----|---------|------------|
| 1  | Luke    | Skywalker |
| 2  | Bruce   | Wain      |
| 3  | Tony    | Stark     |
| 4  | Dominic | Torreto   |  

Нужно вывести в одной колонке полное имя. Как называется метод?  

- инкапсуляция  
- параметризация  
- конкатенация  
- рекурсия  
- инверсия  

---

## Вопрос 7  
Рассмотрим таблицу products со столбцами category и price.  
Запрос:  
`SELECT category, COUNT(*) FROM products ___ category`  
Какая конструкция должна быть на месте пропуска?  

- HAVING  
- DISTINCT  
- GROUP BY  
- WHERE  
- ORDER BY  

---

## Вопрос 8  
Определите только те ключевые слова, которые относятся к операторам условной логики:  

- EXISTS, CASE, NULLIF, LIKE  
- WHEN, END, UNION, IF  
- ELSE, NULLIF, WHEN, IFNULL  
- IFNULL, CASE, ANY, NULL  
- COALESCE, IF, CASE, THEN  

---

## Вопрос 9  
Выберите верное утверждение:  

- коррелированный подзапрос выполняется автономно от основного запроса  
- подзапрос не может возвращать NULL значения  
- подзапрос обязан возвращать больше 1 колонки  
- подзапрос в WHERE обязан возвращать максимум 1 значение  
- подзапрос может вернуть как 1 значение, так и колонку со значениями  

---

## Вопрос 10  
Выберите вариант со всеми типами данных, относящимися к числовым:  

- Float4, integer, decimal, smallint  
- real, char, time, numeric  
- int4, Ints, float4, time  
- higint, char, floats, numeric  
- bigint, int4, float4, varchar, boolean  