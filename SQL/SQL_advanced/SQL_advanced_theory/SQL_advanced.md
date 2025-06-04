# **SQL\_advanced**

**Вопрос 1**

Что произойдет, если при использовании GROUP BY указаны колонки, но не указаны агрегирующие функции?

1. запрос вернет уникальные значения по всем колонкам, которые прописаны в GROUP BY, а остальные колонки проигнорирует  
2. запрос вернет уникальные значения по всем колонкам, которые прописаны в SELECT, а остальные колонки проигнорирует  
3. запрос вернет уникальные значения по колонкам, которые прописаны и в GROUP BY, и в SELECT  
4. запрос вернет ошибку.  
5. запрос вернет уникальные значения по всем колонкам из таблицы

**Вопрос 2**

Что произойдет, если при использовании GROUP BY применить агрегирующую функцию MAX к колонке, содержащей строковые значения?

1. для каждого уникального значения в GROUP BY вернется NULL  
2. для каждого уникального значения в GROUP BY вернется последняя строка по алфавиту  
3. для каждого уникального значения в GROUP BY вернется самая длинная строка  
4. для каждого уникального значения в GROUP BY вернется первая строка по алфавиту  
5. ошибка

**Вопрос 3**

Есть две таблицы из одной колонки, в них содержатся NULL-значения. В левой таблице пять значений NULL, в правой семь. Сколько строк вернется с NULL при выполнении различных типов соединений, если соединение происходит по единственной колонке, содержащей NULL?

1. INNER-0 , LEFT-5 , RIGHT-7 , FULL-12  
2. INNER-5 , LEFT-5 , RIGHT-7 , FULL-7  
3. INNER-5 , LEFT-5 , RIGHT-7 , FULL-12  
4. INNER-0 , LEFT-5 , RIGHT-5 , FULL-7  
5. INNER-5 , LEFT-35 , RIGHT-35 , FULL-27

**Вопрос 4**

Какой будет результат, если значение в колонке таблицы подходит под несколько условий в CASE?

1. вернется NULL  
2. вернутся все значения THEN, подходящие под условия  
3. вернется значение THEN первого условия  
4. ошибка  
5. вернется значение THEN последнего условия

**Вопрос 5**

В этом SQL-запросе допущено несколько ошибок (в данных при этом ошибок нет). Выберите вариант со всеми перечисленными ошибками:

with base as (  
  select  
  from payments  
  where exists(select payment\_system\_id from payment\_systems )  
)  
select  
  from base  
where amount \> ( select countries , count(distinct payment\_types ) from table\_countries group by 1 )  
left join (  
  select  
  from ( select id from users union select id from employees )  
) on base.id \= users.id  
group by 1,2  
right join ( select payment\_id , old\_payment\_id from payments\_history ) old on base.id \= old.id  
having sum(revenue ) \> ( select min(amount ) from revenue )

1. JOIN происходит по полю, которого нет в подзапросе; EXISTS нельзя применять в CTE; для всех подзапросов нет алиаса  
2. подзапросы не могут быть больше первого уровня вложенности; подзапрос нельзя писать в HAVING; один из подзапросов в WHERE возвращает две колонки  
3. подзапрос нельзя писать в HAVING; для всех подзапросов нет алиаса; JOIN происходит по полю, которого нет в подзапросе  
4. один из подзапросов в WHERE возвращает две колонки; подзапрос нельзя указывать в WHERE: для одного подзапроса нет алиаса  
5. один из подзапросов в WHERE возвращает две колонки; для двух подзапросов нет алиаса; JOIN происходит по полю, которого нет в подзапросе

**Вопрос 6**

У вас есть уже существующее материальное представление test\_view. Вы хотите добавить в него новый столбец num\_purchases. Как сделать это синтаксически верно?

1. delete materialized view test\_view ; create alter materialized view test\_view add column num  
2. replace alter materialized view test\_view as select user\_id , min(dt ) as first\_payed , sum(pr  
3. delete materialized view test\_view ; create or replace materialized\_view test\_view as select  
4. drop materialized view ; create materialized view as select user\_id , min(dt ) as first\_payed ,  
5. drop materialized view ; create view test\_view as select user\_id , min(dt ) as first\_payed , sur

**Вопрос 7**

Укажите запрос, который выберет все фильмы, связанные со словами bad, good, angry. В названиях фильмов могут содержаться эти слова в разном виде, например в разных регистрах (Badboys) или в измененной форме (goodspeed):

1. select movie\_name from movies where lower(movie\_name ) like 'bad ' or lower ( movie\_name ) like  
2. select movie\_name from movies where movie\_name like "Good " or movie\_name like ' % Bad or m  
3. select movie\_name from movies where lower ( movie\_name ) like ' % bad % or lower ( movie\_name ) lik  
4. select movie\_name from movies where movie\_name like " Sbad % or movie\_name like ' % angry % or  
5. select movie\_name from movies where movie\_name in ( ' bad ' , ' angry ' , ' good ' )

**Вопрос 8**

В данных есть особенность: в поле amount могут находиться целые и дробные данные с указанием валюты, например 1.43 EUR , 250 , 37.18 , 893 RUB.

Также есть SQL-запрос, который написан аналитиком и рассчитывает сумму одобренных транзакций по месяцам 2023 года.

Запрос:

select  
  to\_char(transaction\_date::date , "YYYY-MM ) as month ,  
  sum(cast ( regexp\_replace(amount , '\[^0-9.\]', '','g' ) as numeric ) ) as total\_approved\_amount  
from transactions  
where  
  status \= 'approved'  
  and date\_trunc ( 'YEAR' , transaction\_date::date ) \= '2023'  
group by month  
order by month

Выберите вариант, где для каждого запроса указана ошибка, из\-за которой запрос либо не сработает, либо вернет неверные значения:

1. regexp\_replace возвращает некорректное значение для CAST, а date\_trunc('YEAR' , transaction\_date::date ) \= "2023" записано с ошибкой  
2. regexp\_replace искажает числовые значения, а group by month некорректно сгруппирует данные  
3. to\_char(transaction\_date , 'YYYY-MM" ) не поддерживает преобразование дат, а sum ( ... ) не суммирует значения типа numeric  
4. cast(regexp\_replace ( ... ) ) as numeric нельзя применять в агрегатных функциях, а date\_trunc('YEAR' , transaction\_date::date ) " 2023 " не фильтрует по году  
5. date\_trunc не работает с датами в формате YYYY, а regexp\_replace удаляет только буквы, но не лишние символы

**Вопрос 9**

Дана таблица с заказами:

Для данной таблицы необходимо:

* Рассчитать скользящую сумму заказов за пять последних заказов пользователя.  
* Определить разницу во времени между текущим заказом и предыдущим для каждого пользователя.  
* Пронумеровывать заказы каждого пользователя по дате.  
* Вычислить процент заказа от общей суммы заказов пользователя.  
* Вывести ранг пользователя по сумме заказов за месяц.

Ниже дан запрос, который выводит всю запрашиваемую информацию, однако в нем некоторые из пяти показателей подсчитаны неверно. Какие?

Запрос:

select  
  user\_id ,  
  order\_id ,  
  order\_date ,  
  order\_amount ,  
  sum(order\_amount ) over ( partition by user\_id order by order\_date rows between 5 preceding and current row) as rolling\_sum ,  
  extract ( epoch from ( order\_date \- lag(order\_date ) over ( partition by user\_id order by order\_date ) ) ) as time\_diff ,  
  row\_number ( ) over ( partition by user\_id order by order\_date ) as order\_number ,  
  order\_amount/sum(order\_amount ) over ( partition by user\_id ) as order\_percentage ,  
  rank ( ) over ( partition by date\_trunc("month " , order\_date ) order by sum(order\_amount ) over ( partition by user\_id ) ) as user\_rank  
from orders

1. скользящая сумма заказов, разница во времени между заказами, ранг пользователя по сумме заказов  
2. скользящая сумма заказов, ранг пользователя по сумме заказов, процент заказа от общей суммы  
3. разница во времени между заказами, номер заказа по дате, ранг пользователя по сумме заказов  
4. номер заказа по дате, процент заказа от общей суммы, разница во времени между заказами  
5. скользящая сумма заказов, номер заказа по дате, процент заказа от общей суммы

**Вопрос 10**

Выберите синтаксически корректный запрос:

1. update table public.table\_1 ( user\_id int , salary float , department\_id str )  
2. alter table public.table\_1 add ( user\_id int , salary float , department\_id int )  
3. modify table public.table\_1 ( user\_id int , salary float , department\_id str )  
4. alter table public.table\_1 ( user\_id int , add salary float , add department\_id int )  
5. alter table public.table\_1 add user\_id int , add salary float , add department\_id int

**Вопрос 11**

Какой из следующих индексов будет наиболее оптимальным для ускорения запросов, фильтрующих данные по user\_id и сортирующих их по created\_at?

1. create index payments\_gin\_idx on payments using gin ( to\_tsvector('english ' , user\_id::text ) ) ;  
2. create index payments\_user\_id\_hash\_idx on payments using hash ( user\_id ) ;  
3. create index payments\_user\_id\_idx on payments using btree ( user\_id ) ;  
4. create index payments\_user\_id\_created\_at\_idx on payments using btree ( user\_id , created\_at ) ;  
5. create index payments\_brin\_idx on payments using brin ( created\_at ) ;

**Вопрос 12**

Определите список разрешений, на который можно выдать или отозвать права с помощью операторов GRANT , REVOKE:

1. GRANT , INSERT , UPDATE , EXCEPT  
2. IF , SELECT , JOIN , UNION  
3. INTERSECT , DROP , SELECT , ALL  
4. CREATE , TRUNCATE , DELETE , TRIGGER  
5. INSERT , SELECT , JOIN , CREATE

**Вопрос 13**

Выберите верное утверждение:

1. ANY и EXISTS полностью взаимозаменяемы, так как оба проверяют наличие значений в подзапросе  
2. ANY всегда используется только с оператором \= для сравнения значений из подзапроса  
3. ANY EXISTS можно использовать только в WHERE, но не в HAVING  
4. EXISTS проверяет, содержит ли подзапрос хотя бы одну строку, и возвращает TRUE, подзапрос возвращает одну или несколько строк  
5. EXISTS выполняет подзапрос один раз и кэширует результат, а ANY выполняет подзапрос для каждой строки

**Вопрос 14**

Выберите верное утверждение:

1. INTERSECT выполняет пересечение минимум трех наборов данных или таблиц  
2. ключевое слово ALL является обязательным для операторов INTERSECT и EXCEPT  
3. смена порядка запросов для INTERSECT поменяет выводимые данные  
4. команда UNION выполняется быстрее, чем команда UNION ALL  
5. смена порядка запросов для EXCEPT поменяет выводимые данные

**Вопрос 15**

Выберите операторы, относящиеся только к DDL:

1. SELECT , TRUNCATE , UPDATE , DROP  
2. RENAME , ALTER , TRUNCATE , DELETE  
3. DROP , ALTER , CREATE , RENAME  
4. INSERT , DROP , DELETE , UPDATE  
5. CREATE , DROP , RENAME , UPDATE