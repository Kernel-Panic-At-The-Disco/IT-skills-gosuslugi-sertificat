# API_middle

## Вопрос 1  
Какое из утверждений точно отражает ограничение стандарта SOAP по сравнению с REST?  

- SOAP работает исключительно синхронно и не может использовать асинхронную доставку сообщений  
- SOAP всегда используется в реальном времени и не поддерживает отложенные обработки  
- SOAP требует постоянного двустороннего соединения между клиентом и сервером  
- SOAP неэффективен для real-time взаимодействия из-за своей зависимости от XML и оберток сообщений  
- SOAP поддерживает только текстовные данные и не может передавать вложения  

---

## Вопрос 2  
Вы разрабатываете новый API, который должен поддерживать методы GET и POST. Требуется провести тестирование API для следующих сценариев:  
1. Проверить корректность ответа сервера на GET-запрос с параметрами в URL.  
2. Протестировать POST-запрос с передачей данных в формате JSON в теле запроса.  
3. Получить информацию о кодах ответа, заголовках и содержимом тела ответа для каждого тестового запроса.  
4. Сохранить тестовые сценарии, чтобы использовать их повторно в процессе разработки.  
Какую последовательность действий вы выберете?  

- Протестировать API с помощью Python-скрипта, отправляющего GET и POST-запросы и логирующего результаты в консоль  
- Настроить Katalon Studio для тестирования GET и POST-запросов с сохранением сценариев в проекте  
- Использовать Swagger для тестирования GET и POST-запросов, сохраняя результаты в формате документации  
- Создать в Postman коллекцию запросов, добавить GET и POST-запросы, указать параметры, тело запросов и сохранить сценарии  
- Настроить cURL-запросы с динамическими параметрами через скрипт, который будет автоматически сохранять ответы в файлы  

---

## Вопрос 3  
Вы разрабатываете API, которому требуется защита передаваемых данных. Какой метод аутентификации вы выберете, если нужно хешировать логин и пароль перед отправкой, но не использовать токены или управление сессиями?  

- JWT  
- Basic Authentication  
- API Key  
- OAuth  
- Digest Authentication  

---

## Вопрос 4  
Вам нужно интегрировать сторонние сервисы с вашей API и обеспечить автоматическое обновление токенов доступа для пользователей без их участия.  
Какие действия для аутентификации вы будете выполнять?  

- Настроить API ключи для каждого внешнего сервиса с возможностью ручного обновления  
- Использовать JWT с постоянными токенами, которые не требуют обновления  
- Применить Basic Authentication для каждого запроса и проверять токены вручную  
- Внедрить Digest Authentication с автоматической ротацией токенов  
- Использовать OAuth с refresh-токенами для автоматического обновления доступа  

---

## Вопрос 5  
Какой HTTP-код ошибки следует вернуть, если при попытке создать пользователя с уже существующим e-mail возникает конфликт, и как правильно уведомить клиента об этом? Что добавить в обработку запроса, чтобы правильно уведомить клиента?  

- Применять 400 для любых недопустимых данных, включая дублирующийся e-mail  
- Использовать 400, если входные данные противоречат требуемым полям, и добавить сообщение о дублировании e-mail  
- Возвращать 400 при обнаружении существующего e-mail, указывая, что пользователь не найден  
- Отправлять 400 и добавить в ответ информацию о том, что e-mail уже зарегистрирован  
- Вернуть 410, указывая, что пользовательский ресурс был удалён, и по этой причине e-mail недоступен  

---

## Вопрос 6  
Ваш API поддерживает обновление данных методом PUT. Вы заметили, что при отправке повторных PUT-запросов с одинаковыми данными сервер каждый раз выполняет обновление ресурса, увеличивая нагрузку на базу данных. Это нарушает принцип идемпотентности метода PUT.  
Как реализовать корректную обработку повторных запросов для восстановления идемпотентности?  

- Использовать механизм проверки на совпадение данных: если данные запроса идентичны текущим, не выполнять обновление  
- Использовать метод POST вместо PUT, чтобы обрабатывать каждый из повторных запросов независимо  
- Добавить в получаемые запросы необходимый для этого флаг, для маркировки сервером их как "повторные запросы"  
- Переключиться на метод PATCH для повторных запросов, выполнять обновление только для указанных полей  
- Настроить кэширование повторных запросов на стороне клиента для уменьшения нагрузки на сервер  

---

## Вопрос 7  
Ваш API для управления задачами использует метод DELETE для удаления завершённых задач. Клиент сообщает, что повторный запрос DELETE для удаления той же задачи возвращает ошибку 404 Not Found. Логи сервера показывают, что задача была успешно удалена при первом запросе.  
Как объяснить это поведение метода DELETE?  

- Ошибка 404 возникает, потому что метод DELETE требует подтверждения через GET перед удалением ресурса  
- Метод DELETE не нарушает идемпотентности: первый запрос удаляет ресурс, а повторный возвращает ошибку 404, так как ресурс больше не существует  
- Метод DELETE нарушает принцип идемпотентности: повторный запрос приводит к изменению состояния сервера из-за удаления ресурса, которого уже нет  
- Повторный запрос метода DELETE вызывает ошибку 404, так как сервер автоматически ожидает подтверждения на удаление ресурса  
- DELETE восстанавливает удалённые ресурсы при повторном запросе, что приводит к ошибке 404 из-за некорректного состояния сервера  

---

## Вопрос 8  
Ваше приложение работает с большими объёмами данных. Для предотвращения перегрузки вы реализуете пагинацию.  
Какой параметр указывает на количество записей, которые следует пропустить при получении данных?  

- page  
- limit  
- sort  
- offset  
- filter  

---

## Вопрос 9  
Вы разрабатываете приложение с ограниченными серверными ресурсами, которое должно поддерживать большое количество подключенных клиентов. Вам нужно выбрать метод асинхронного взаимодействия между сервером и клиентом.  
Какой метод придется использовать, если вы хотите, чтобы он привел к ошибке?  

- WebSocket для постоянного двустороннего соединения между клиентом и сервером  
- Long Polling для проверки обновлений с периодическим подключением  
- Webhooks для отправки данных только при изменении на стороне сервера  
- HTTP Polling для регулярного опроса сервера с фиксированным интервалом  
- Server-Sent Events (SSE) для однонаправленной передачи данных от сервера клиенту  

---

## Вопрос 10  
В вашей команде используется Swagger для документирования и тестирования API, однако для внутренней разработки вам нужно обеспечить возможность тестирования API в среде, где доступ к внешним сервисам ограничен по соображениям безопасности.  
Как изменить настройку Swagger, чтобы обеспечить возможность тестирования API в среде без доступа к внешним сервисам?  

- Настроить Swagger локально и отключить доступ к внешним ресурсам, добавив все необходимые зависимости напрямую  
- Переключить Swagger на использование серверов внешнего хостинга для обновлений  
- Использовать Swagger напрямую с внешних серверов для постоянного обновления  
- Включить автоматическую генерацию документации Swagger с доступом к удаленным данным  
- Изменить конфигурацию Swagger API для связи с внешними сервисами через промежуточный прокси-сервер  

---

## Вопрос 11  
Какой формат данных НЕ поддерживает представление объектов в виде пар ключ-значение для API и не позволяет использовать вложенные структуры?  

- INI  
- JSON  
- XML  
- CSV  
- YAML  

---

## Вопрос 12  
Какое ключевое свойство JWT позволяет использовать токены между разными сервисами без привязки к конкретному серверу?  

- Ограничение доступа к ресурсу на уровне авторизованного пользователя  
- Сигнатура токена, которая делает его уникальным и безопасным для передачи  
- Встроенная поддержка безопасной авторизации через API-ключи  
- Бессессионность, которая позволяет использовать токен независимо от сервера  
- Поддержка JSON-формата для быстрой передачи данных между сервисами  

---

## Вопрос 13  
Вы разрабатываете API, которое предоставляет доступ к конфиденциальным данным внешним приложениям. Необходимо обеспечить безопасность, исключая передачу паролей пользователей напрямую, и дать сторонним сервисам возможность запрашивать данные по безопасному каналу.  
Какой метод аутентификации следует использовать в этом случае?  

- Basic Authentication для передачи зашифрованных данных в заголовке  
- JWT для подписанных токенов, которые включают логин и пароль пользователя  
- Рукопожатие для хранения данных о сессии и доступа к API  
- API ключи для генерации временных паролей для каждого клиента  
- OAuth для предоставления безопасного доступа через токены, без передачи пароля  

---

## Вопрос 14  
Вам необходимо интегрировать несколько сторонних сервисов с вашей API, чтобы обеспечить безопасный доступ к данным с возможностью автоматического обновления токенов доступа без участия пользователя.  
Какова последовательность действий при использовании OAuth?  

- Генерировать access и refresh токены, которые можно обновлять вручную  
- Применять постоянные access токены для всех пользователей и обновлять их вручную  
- Создать refresh токены с бесконечным сроком действия  
- Настроить access токены с коротким сроком действия и refresh токены для автоматического обновления без участия пользователя  
- Настроить access токены с коротким сроком действия и применять ручную проверку валидности токенов  

---

## Вопрос 15  
Вы обновили версию API, добавив новые методы. После этого клиенты начали сталкиваться с проблемой: старые запросы, которые использовали предыдущие методы API, возвращают ошибку.  
Что нужно сделать при обновлении API, чтобы разрешить эту проблему?  

- Активировать новый сертификат SSL для старых маршрутов  
- Настроить миграцию маршрутов (версионирование API)  
- Настроить новые заголовки CORS для доступа к обновленному API  
- Настроить валидацию данных заголовков запросов на уровне сервера  
- Уведомить пользователей о смене аутентификационного протокола  

---

## Вопрос 16  
Как избежать удаления данных при повторном обновлении заказа, если некоторые поля в запросе отсутствуют, и нужно обновлять только указанные поля?  

- Добавить в запрос флаг для сохранения существующих данных  
- Использовать метод DELETE перед каждым обновлением для очистки полей  
- Переключиться на метод PATCH для частичного обновления полей ресурса  
- Включить параметры offset и limit для ограничения изменения данных  
- Использовать POST вместо PUT, чтобы каждый запрос создавал новую запись  

---

## Вопрос 17  
После выполнения операции обновления в вашем API часть данных ресурса была неожиданно удалена, а отсутствующие поля были автоматически заменены значениями по умолчанию.  
Почему это происходит?  

- PUT использовался для обновления ресурса без передачи данных  
- PATCH был использован с передачей только изменённых полей  
- POST был применен для обновления ресурса  
- GET был использован для обновления ресурса  
- PUT применялся без передачи незамещённых полей, что привело к удалению отсутствующих данных  

---

## Вопрос 18  
Внедрили автоматическую проверку, которая тестирует соответствие реализованных эндпоинтов спецификации OpenAPI и выдает подробные отчеты о несоответствиях (неверные типы данных или отсутствующие параметры). Требуется интеграция в CI/CD, чтобы каждый коммит проходил проверку.  
Какой инструмент решит эти задачи?  

- Postman  
- API Blueprint  
- Swagger Editor  
- ReDoc  
- Dredd  