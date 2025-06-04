# **SQL\_middle**

**Вопрос 1**

Каков верный порядок выполнения операторов в запросе?

1. SELECT , WHERE , FROM , LIMIT  
2. WHERE , FROM , SELECT , LIMIT  
3. FROM , WHERE , SELECT , LIMIT  
4. LIMIT , FROM , WHERE , SELECT  
5. SELECT , FROM , WHERE , LIMIT

**Вопрос 2**

Что вернет указанный ниже запрос? Запрос:

select \*  
from analysts  
where 1=1  
  and profession \= 'marketing' and (profession \= 'data' and level \= 'senior')

1. цифру 1  
2. запрос отработает с ошибкой  
3. ничего, будет пустой вывод  
4. всех маркетинговых аналитиков и дата-аналитиков уровня Senior  
5. все записи в таблице

**Вопрос 3**

Есть таблица purchases, в ней находятся данные о продажах мобильных телефонов:

| Наименование колонки | Тип данных | Описание |
| :---- | :---- | :---- |
| phone\_name | str | Наименование телефона |
| amount | float | Стоимость покупки |
| client\_id | int | id покупателя |
| dt | datetime | Дата и время покупки |

Определите среднюю стоимость покупки телефона для телефонов с продажами более 10 штук:

1. select avg(amount) from purchases where amount \> 10 group by phone\_name  
2. select avg(amount) from purchases group by phone\_name having count(amount) \> 10  
3. select avg(amount) from purchases group by phone\_name having sum(amount) \> 10  
4. select avg(amount) from purchases group by phone\_name  
5. select avg(amount) from purchases group by phone\_name where count(amount) \> 10

**Вопрос 4**

Есть таблица notebooks, в ней находятся данные о количестве ноутбуков в магазине:

| Наименование колонки | Тип данных | Описание |
| :---- | :---- | :---- |
| id | int | id записи |
| firm | str | Производитель ноутбука |
| price | int | Цена |
| model | str | Наименование модели |

Как рассчитать среднюю цену ноутбука для каждой фирмы?

1. select firm , avg(price) from notebooks group by firm  
2. select avg(price) from notebooks  
3. select sum(price) / count(distinct firm) from notebooks  
4. select firm , sum(price) / sum(id) from notebooks group by Firm  
5. select model , sum(price) / count(id) from notebooks group by model

**Вопрос 5**

Есть две таблицы: таблица с юзерами и таблица с покупками юзеров. Какой запрос вернет всю информацию о юзерах, которые совершили покупки и являются работниками компании?

Таблица users:

| Наименование колонки | Тип данных | Описание |
| :---- | :---- | :---- |
| id | int | id записи |
| client\_id | int | id клиента |
| employee\_id | int | id работника |
| name | str | Имя |
| surname | str | Фамилия |

Таблица purchases:

| Наименование колонки | Тип данных | Описание |
| :---- | :---- | :---- |
| id | int | id записи |
| client\_id | int | id клиента |
| good\_id | int | id товара |
| good\_name | str | Наименование товара |
| price | int | Цена товара |

1. select \* from users left join purchases on users.client\_id \= purchases.client\_id where empl  
2. select \* from purchases join users on users.client\_id \= purchases.client\_id and employee\_id  
3. select \* from purchases right join users on users.client\_id \= purchases.client\_id  
4. select \* from users full join purchases on users.client\_id \= purchases.client\_id and client  
5. select \* from users inner join purchases on users.employee\_id \= purchases.client\_id where or

**Вопрос 6**

Выберите синтаксически верную конструкцию case:

1. case revenue \>= 100 then 'high' revenue \< 100 then 'low' end  
2. case when revenue \>= 100 then 'high' case when revenue \< 100 then 'low'  
3. case when revenue \> 100 then 'high' revenue \< 100 then 'low' end  
4. case when revenue \> 100 then "high" when revenue \< 100 then low end  
5. case when revenue \>= 100 then 'high' , when revenue \< 100 then 'low' else "unknown" end

**Вопрос 7**

Анализируются данные по продажам автомобилей в различных странах:

| Наименование колонки | Тип данных | Описание |
| :---- | :---- | :---- |
| country | str | Страна продажи |
| amount | float | Сумма продажи |
| automobile\_type | str | Тип автомобиля |
| model\_name | str | Модель автомобиля |
| num\_automobiles | int | Кол-во автомобилей |

Найдите уникальные страны, в которых продается больше машин, чем в Японии:

1. select country from automobile\_sales group by country where country \= 'Japan' having sum(am  
2. select country from automobile\_sales where sum(amount) \> ( select sum(amount) from automobil  
3. select country from automobile\_sales where amount \> ( select sum(amount) from automobile salı  
4. select country from automobile\_sales group by country having sum(num\_automobiles) \> ( select  
5. select country from automobile\_sales group by country having amount \> ( select sum(amount) fr

**Вопрос 8**

Есть таблица с описанием процесса чтения книг:

| Наименование колонки | Тип данных | Описание |
| :---- | :---- | :---- |
| dt | datetime | Дата и время чтения |
| book\_id | int | id книги |
| user\_id | int | id пользователя |
| read\_seconds | int | Кол-во секунд чтения |

Какой из запросов для каждого пользователя выведет книгу, которую он читал первой?

1. select user\_id , book\_id from ( select user\_id , book\_id , dt , row\_number ( ) over ( partition by  
2. select user\_id , First\_value(book\_id ) over(partition by user\_id , dt ) group by user\_id ;  
3. select user\_id , book\_id , first\_value(book\_id ) over ( partition by user\_id order by dt ) from 1  
4. select user\_id , min(book\_id ) over(partition by user\_id , book\_id ) from readings group by user  
5. select user\_id , first\_value(book\_id ) over(partition by user\_id order by dt ) from readings gi

**Вопрос 9**

Выберите синтаксически корректный запрос, который создаст таблицу, откуда можно будет извлечь среднюю зарплату сотрудников в различных отделах:

1. create table public.table\_1 ( user\_id int , salary str , department\_id int )  
2. create table public.table\_1 ( user\_id hoolean , salary float , department\_id str )  
3. create table public.table\_1 ( user\_id int , salary float , department\_id int )  
4. create table public.table\_1 ( user\_id float , salary str , department\_id boolean )  
5. create table public.table\_1 ( user\_id int , salary str , department\_id boolean )

**Вопрос 10**

Выберите верное утверждение о представлениях:

1. материальное представление обновляется при обращении к нему  
2. представление не обновляется без команды refresh  
3. представление — это тип физической таблицы, которая постоянно хранит данные  
4. материальное представление хранится на диске, и его невозможно обновить  
5. представление обновляет отдаваемые данные при обращении к нему

**Вопрос 11**

Выберите операторы, относящиеся только к DML:

1. CREATE , DROP , SELECT , UPDATE  
2. INSERT , TRUNCATE , DELETE , UPDATE  
3. CREATE , DROP , TRUNCATE , DELETE  
4. UPDATE , SELECT , INSERT , DELETE  
5. SELECT , TRUNCATE , UPDATE , DROP

**Вопрос 12**

Какой из приведённых ниже подходов может улучшить производительность SQL-запроса при извлечении данных из большой таблицы?

1. создание индексов по колонкам , которые участвуют в условиях where и join  
2. использование только оконных функций вместо агрегатных  
3. добавление индексов по всем колонкам  
4. использование вложенных SELECT без фильтрации  
5. отказ от использования индексов для ускорения