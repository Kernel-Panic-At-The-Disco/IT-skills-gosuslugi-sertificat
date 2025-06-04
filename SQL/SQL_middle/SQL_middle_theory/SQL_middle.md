## Вопрос 1  
Каков верный порядок выполнения операторов в запросе?  

- SELECT , WHERE , FROM , LIMIT  
- WHERE , FROM , SELECT , LIMIT  
- FROM , WHERE , SELECT , LIMIT  
- LIMIT , FROM , WHERE , SELECT  
- SELECT , FROM , WHERE , LIMIT  

---

## Вопрос 2  
Что вернет указанный ниже запрос? Запрос:  
select *  
from analysts  
where 1=1  
  and profession = 'marketing' and (profession = 'data' and level = 'senior')  

- цифру 1  
- запрос отработает с ошибкой  
- ничего, будет пустой вывод  
- всех маркетинговых аналитиков и дата-аналитиков уровня Senior  
- все записи в таблице  

---

## Вопрос 3  
Есть таблица purchases, в ней находятся данные о продажах мобильных телефонов:  
| Наименование колонки | Тип данных | Описание |  
| :---- | :---- | :---- |  
| phone_name | str | Наименование телефона |  
| amount | float | Стоимость покупки |  
| client_id | int | id покупателя |  
| dt | datetime | Дата и время покупки |  
Определите среднюю стоимость покупки телефона для телефонов с продажами более 10 штук:  

- select avg(amount) from purchases where amount > 10 group by phone_name  
- select avg(amount) from purchases group by phone_name having count(amount) > 10  
- select avg(amount) from purchases group by phone_name having sum(amount) > 10  
- select avg(amount) from purchases group by phone_name  
- select avg(amount) from purchases group by phone_name where count(amount) > 10  

---

## Вопрос 4  
Есть таблица notebooks, в ней находятся данные о количестве ноутбуков в магазине:  
| Наименование колонки | Тип данных | Описание |  
| :---- | :---- | :---- |  
| id | int | id записи |  
| firm | str | Производитель ноутбука |  
| price | int | Цена |  
| model | str | Наименование модели |  
Как рассчитать среднюю цену ноутбука для каждой фирмы?  

- select firm , avg(price) from notebooks group by firm  
- select avg(price) from notebooks  
- select sum(price) / count(distinct firm) from notebooks  
- select firm , sum(price) / sum(id) from notebooks group by Firm  
- select model , sum(price) / count(id) from notebooks group by model  

---

## Вопрос 5  
Есть две таблицы: таблица с юзерами и таблица с покупками юзеров. Какой запрос вернет всю информацию о юзерах, которые совершили покупки и являются работниками компании?  
Таблица users:  
| Наименование колонки | Тип данных | Описание |  
| :---- | :---- | :---- |  
| id | int | id записи |  
| client_id | int | id клиента |  
| employee_id | int | id работника |  
| name | str | Имя |  
| surname | str | Фамилия |  
Таблица purchases:  
| Наименование колонки | Тип данных | Описание |  
| :---- | :---- | :---- |  
| id | int | id записи |  
| client_id | int | id клиента |  
| good_id | int | id товара |  
| good_name | str | Наименование товара |  
| price | int | Цена товара |  

- select * from users left join purchases on users.client_id = purchases.client_id where empl  
- select * from purchases join users on users.client_id = purchases.client_id and employee_id  
- select * from purchases right join users on users.client_id = purchases.client_id  
- select * from users full join purchases on users.client_id = purchases.client_id and client  
- select * from users inner join purchases on users.employee_id = purchases.client_id where or  

---

## Вопрос 6  
Выберите синтаксически верную конструкцию case:  

- case revenue >= 100 then 'high' revenue < 100 then 'low' end  
- case when revenue >= 100 then 'high' case when revenue < 100 then 'low'  
- case when revenue > 100 then 'high' revenue < 100 then 'low' end  
- case when revenue > 100 then "high" when revenue < 100 then low end  
- case when revenue >= 100 then 'high' , when revenue < 100 then 'low' else "unknown" end  

---

## Вопрос 7  
Анализируются данные по продажам автомобилей в различных странах:  
| Наименование колонки | Тип данных | Описание |  
| :---- | :---- | :---- |  
| country | str | Страна продажи |  
| amount | float | Сумма продажи |  
| automobile_type | str | Тип автомобиля |  
| model_name | str | Модель автомобиля |  
| num_automobiles | int | Кол-во автомобилей |  
Найдите уникальные страны, в которых продается больше машин, чем в Японии:  

- select country from automobile_sales group by country where country = 'Japan' having sum(am  
- select country from automobile_sales where sum(amount) > ( select sum(amount) from automobil  
- select country from automobile_sales where amount > ( select sum(amount) from automobile salı  
- select country from automobile_sales group by country having sum(num_automobiles) > ( select  
- select country from automobile_sales group by country having amount > ( select sum(amount) fr  

---

## Вопрос 8  
Есть таблица с описанием процесса чтения книг:  
| Наименование колонки | Тип данных | Описание |  
| :---- | :---- | :---- |  
| dt | datetime | Дата и время чтения |  
| book_id | int | id книги |  
| user_id | int | id пользователя |  
| read_seconds | int | Кол-во секунд чтения |  
Какой из запросов для каждого пользователя выведет книгу, которую он читал первой?  

- select user_id , book_id from ( select user_id , book_id , dt , row_number ( ) over ( partition by  
- select user_id , First_value(book_id ) over(partition by user_id , dt ) group by user_id ;  
- select user_id , book_id , first_value(book_id ) over ( partition by user_id order by dt ) from 1  
- select user_id , min(book_id ) over(partition by user_id , book_id ) from readings group by user  
- select user_id , first_value(book_id ) over(partition by user_id order by dt ) from readings gi  

---

## Вопрос 9  
Выберите синтаксически корректный запрос, который создаст таблицу, откуда можно будет извлечь среднюю зарплату сотрудников в различных отделах:  

- create table public.table_1 ( user_id int , salary str , department_id int )  
- create table public.table_1 ( user_id hoolean , salary float , department_id str )  
- create table public.table_1 ( user_id int , salary float , department_id int )  
- create table public.table_1 ( user_id float , salary str , department_id boolean )  
- create table public.table_1 ( user_id int , salary str , department_id boolean )  

---

## Вопрос 10  
Выберите верное утверждение о представлениях:  

- материальное представление обновляется при обращении к нему  
- представление не обновляется без команды refresh  
- представление — это тип физической таблицы, которая постоянно хранит данные  
- материальное представление хранится на диске, и его невозможно обновить  
- представление обновляет отдаваемые данные при обращении к нему  

---

## Вопрос 11  
Выберите операторы, относящиеся только к DML:  

- CREATE , DROP , SELECT , UPDATE  
- INSERT , TRUNCATE , DELETE , UPDATE  
- CREATE , DROP , TRUNCATE , DELETE  
- UPDATE , SELECT , INSERT , DELETE  
- SELECT , TRUNCATE , UPDATE , DROP  

---

## Вопрос 12  
Какой из приведённых ниже подходов может улучшить производительность SQL-запроса при извлечении данных из большой таблицы?  

- создание индексов по колонкам , которые участвуют в условиях where и join  
- использование только оконных функций вместо агрегатных  
- добавление индексов по всем колонкам  
- использование вложенных SELECT без фильтрации  
- отказ от использования индексов для ускорения  