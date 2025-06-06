# **Reg\_test\_advanced**

**Вопрос 1**

Какие тесты нужно запустить в первую очередь после исправления дефекта в модуле оплаты?

1. Запустить тестовые сценарии для тестирования смежных модулей, чтобы убедиться в отсутствии нарушения интеграционных связей  
2. Smoke-тесты и критические сценарии оплаты, затем полный регресс  
3. Запускать все тесты, включая UI-тесты всех модулей  
4. Достаточно провести unit-тесты измененного кода  
5. Тестировать только наный функционал

**Вопрос 2**

Что включают в себя регрессионные тесты после рефакторинга?

1. Проверку работы логики и совместимости с другими модулями  
2. Достаточно запустить нагрузочные и security-тесты  
3. Использование специализированных метрик для оценки производительности кода  
4. Тестирование только новых функций  
5. Проверку только стиля кода и соответствия стандартам оформления

**Вопрос 3**

Какой из следующих этапов является первым в процессе планирования регрессионного тестирования?

1. Анализ изменений в приложении  
2. Подготовка отчетов о тестировании  
3. Выполнение тестов  
4. Определение тестовых данных  
5. Разворачивание фреймворка автотестирования

**Вопрос 4**

Какой из следующих методов лучше всего подходит для определения приоритетов тестовых случаев в регрессионном тестировании?

1. Выбор тестов на основе времени их выполнения  
2. Приоритизация тест-кейсов на основе количества задействуемых модулей  
3. Антоматический выбор всех тестов  
4. Метод черного ящика  
5. Приоритизация на основе критичности функционала

**Вопрос 5**

Как регрессионное тестирование может повлиять на сроки разработки проекта?

1. Регрессионное тестирование не влияет на сроки, так как оно выполняется только в конце релиза  
2. Регрессионное тестирование может сначала увеличить сроки разработки, но поможет рано выявить дефекты и сократить срок в дальнейшем  
3. Регрессионное тестирование не требует времени, так как все тестовые сценарии автоматизированы  
4. Регрессионное тестирование всегда ускоряет процесс разработки, так как выявляет все ошибки на ранних этапах разработки  
5. Регрессионное тестирование всегда занимает больше времени, чем другие виды тестирования и не может быть оптимизировано

**Вопрос 6**

В проекте внедрили микросервисную архитектуру. Как изменится регрессионное тестирование?

1. Теперь необходимо проводить полный end-to-end perpecc после каждого изменения в любом сервисе  
2. Достаточно тестировать только gateway-сервис, так как он объединяет все остальные  
3. Увеличится важность контрактного тестирования и интеграционных тестов между сервисами, но объем end-to-end perpeccса может сократиться  
4. Регрессионное тестирование больше не нужно, так как каждый сервис тестируется отдельно  
5. Микросервисы позволяют полностью отказаться от автоматизации в пользу ручного тестирования

**Вопрос 7**

Руководитель проекта просит вас сократить время на проведение регрессионного тестирования чтобы лучше сосредоточиться на тестировании нового функционала. Что можно сделать?

1. Необходимо проводить регрессионное тестирование строго после проведения тестирования нового функционала по остаточному принципу  
2. Нужно отказать: объем регрессионного тестирования сокращать недопустимо  
3. Нужно оценить прохождение регрессионного объема в человеко-часах и исходить из того, чтобы время на прохождение регресса занимало не более одной трети от времени прохождения всего объема тестирования  
4. Необходимо провести приоритизацию тест-кейсов объема регресса, исключить мало приоритетные тест-кейсы, останив только те, которые тестируют критичный функционал  
5. Нужно исключить самые продолжительные и трудозатратные тест-кейсы из объема регрессионного тестирования

**Вопрос 8**

Вы видите что на проекте начинают появляться дефекты в старом функционале продакшн-версии, хотя объем регрессионных тест-кейсов покрывает все необходимые сценарии. Что следует изменить в регрессионной модели?

1. Нужно чтобы все тест-кейсы регрессионного объема были пройдены двумя разными тестировщиками независимо друг от друга, для обеспечения контроля качественного выполнения тест-кейсов  
2. Необходимо изменить тестовые данные, потому что старые тестовые данные уже не находят новых дефектов  
3. Нужно в регрессионный объем добавить важные тест-кейсы по проверке нового функционала  
4. Это значит что регрессионные тест-кейсы были составлены неправильно, нужно инициировать ревью и переработку тест-кейсов регресса  
5. Необходимо приоритизировать тест-кейсы регресса и выполнять сначала только тест-кейсы с высоким приоритетом.

**Вопрос 9**

На проекте автоматизатор сообщает, что ему более интересно автоматизировать тест-кейсы по новому функционалу, чем регрессионные тест-кейсы, поэтому он откладывает их автоматизацию на более поздний срок. Какой аргумент можно привести в пользу того, что регрессионные тест-кейсы нужно автоматизировать в первую очередь?

1. Автоматизированные регрессионные тест-кейсы будут запускаться каждый релиз, поэтому они имеют больший срок жизни и регулярно будут облегчать процесс тестирования  
2. Автоматизировать регресс быстрее, чем новый функционал, поскольку регрессионных тестов, как правило, меньше по объему  
3. При автоматизации нового функционала автотесты потребуют регулярной переработки, а при автоматизации регресса тест-кейсы никогда не перерабатываются  
4. Целью автотестов является именно автоматизация наименее интересных кейсов, чтобы избавить ручных тестировщиков от монотонных, повторяющихся действий.  
5. При автоматизации регресса автотесты имеют меньше шансов показать ложноположительный результат

**Вопрос 10**

Можно ли включать негативные проверки в регрессионное тестирование?

1. Да, объем регрессионных тест-кейсов может включать в себя негативные проверки, если это требуется для качественной проверки функционала  
2. Нет, в объеме регрессионного тестирования должны быть только тесты критического пути  
3. Да, в объеме регрессионного тестирования должны быть преимущественно негативные тест-кейсы, так как это позволит увеличить степень покрытия кода  
4. Нет, поскольку негативные проверки нельзя автоматизировать  
5. Нет, негативное тестирование не относится к регрессионному тестированию

**Вопрос 11**

Вы пришли на проект, где объем регрессионных тестов давно не обновлялся и вам ставят задачу обновить его. Что следует сделать в первую очередь?

1. Необходимо исключить этап регрессионного тестирования пока он не будет полностью обновлен  
2. Необходимо провести ревью кейсов на соответствие текущим требованиям, провести приоритизацию тест-кейсов  
3. Необходимо наладить процесс автоматизации регрессионных тест-кейсов на проекте  
4. Нужно включить негативные проверки в объем регрессионного тестирования  
5. Необходимо удалить низкоприоритетные тест-кейсы, оставив только тест-кейсы с высоким приоритетом

**Вопрос 12**

Ваша команда разработала новую функцию в приложении. Какой из следующих шагов следует предпринять перед запуском регрессионного тестирования?

1. Проанализировать, какие тесты могут быть затронуты новой функцией  
2. Удалить все старые тесты  
3. Составить список известных дефектов за несколько последних релизов  
4. Сосредоточиться только на тестировании новой функции  
5. Провести раунд нагрузочного тестирования перед запуском регрессионной сессии

**Вопрос 13**

Какой из следующих факторов может повлиять на выбор тестовых данных для регрессионного тестирования?

1. Все вышеперечисленное  
2. Наличие новых функций в приложении  
3. Наличие антоматизированных тестов  
4. Ничто из вышеперечисленного  
5. Предыдущие результаты тестирования и выявленные дефекты

**Вопрос 14**

Как определить и оценить риски проекта и продукта в контексте регрессионного тестирования?

1. Риски можно игнорировать, если команда тестирования уверена в качестве кода, поэтому достаточно полагаться на ручное тестирование  
2. Риски проекта и продукта можно оценить через анализ влинния изменений и критичности функциональности, используя такие методы, как матрица рисков  
3. Чтобы оценить риски проекта необходимо обратиться к бизнес-аналитику, так как это находится в сфере его компетенций  
4. Оценка рисков происходит на этапе разработки требований, поэтому все риски, как правило, уже учтены в требованиях  
5. Риски проекта и продукта не имеют значения для регрессионного тестирования, поэтому можно просто запускать все тесты без анализа

**Вопрос 15**

Как учитывать риски продукта при планировании регрессионного тестирования?

1. Увеличить покрытие регрессом только новых функций, так как старые уже стабильны  
2. Фокусироваться только на UI-слое, так как пользователи не видят внутренние дефекты  
3. Через создание матрицы рисков чтобы учитывать вероятность и критичность дефектов  
4. Полностью исключить из регресса модули, которые не менялись больше года  
5. Тестировать все модули с одинаковой интенсивностью, чтобы избежать предвзятости