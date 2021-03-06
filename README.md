# Универсальные инструменты 1С для управляемых форм

[![Статус Порога Качества](https://sonar.cprit.ru/api/project_badges/measure?project=tools_ui_1c&metric=alert_status)](https://sonar.cprit.ru/dashboard?id=tools_ui_1c)

Задумывается как аналог подсистемы http://devtool1c.ucoz.ru/, но который будет:
- работать в тонком и веб клиенте
- доступен только для управляемых форм
- работать как в windows, так и в Linux


### Планируется следующий набор инструментов

- Консоль запросов
- Консоль кода
- Структура таблиц базы данных
- Консоль отчетов СКД
- Универсальный динамический список
- Редактор констант
- Редактор объекта базы данных
- Редактор предопределенных элементов
- Подбора и обработка объектов базы данных
- Консоль заданий
- Навигатор по конфигурации- замена меню "Все функции"
- Редактор параметров сеанса
- Регистрация изменений для обмена 
- Консоль HTTP запросов
- Выгрузка загрузка XML с фильтрами
- Поиск и замена дублей
- Редактор хранилищ настроек
- Удаление помеченных объектов без монопольного доступа

### На текущий момент содержит инструменты:

- **Групповая обработка справочников и документов**- Аналогична типовой обработке от 1С с диска ИТС
- **Редактор констант** - позволяет редактировать значения констант в режиме таблицы
- **Структура хранения базы данных**- Просмотр имен таблиц и их взаимосвязей с объектами метаданных.
- **Удаление помеченных объектов**- копия стандартной обработки из БСП, адаптированной для жизни вне БСП
- **Консоль запросов**- Обработка для разработки и выполнения запросов без написания дополнительных обработок. Форк https://github.com/Synoecium/Uniform-query-console-1C
- **Консоль заданий**- просмотр и настройка регламентных и фоновых заданий. Форк https://github.com/kuzyara/JobsConsole2019.epf
- **Регистрация изменений для обмена**- Форк обработки с диска ИТС с адаптациями под подсистему
- **Поиск и удаление дублей**- Форк стандартной обработки из БСП, в которую добавлены несколько параметров выполнения замены
- **Консоль кода**- Позволяет выполнять код из предприятия без создания внешних обработок
- **Регистрации изменений для обмена данными**- Форк стандартной обработки из БСП
- **Поиск ссылок на объект**- аналог стандартной обработки из меню "Все функции". 
- **Редактор реквизитов объекта**- позволяет низкоуровневое редактирование ссылочных объектов. Поддерживает редактирование движений документа.
- **Консоль отчетов**- переработанная консоль компоновок с диска ИТС. Теперь ей удобнее пользоваться
- **Динамический список**- удобный просмотр списков таблиц базы из одной обработки
- **Консоль HTTP запросов**-  позволяет из 1С делать HTTP запросы. Пока поддерживает только строковое содержимое тела запроса

# Отладка

### Вызов

Необходимо в форме вычисления выражения вызвать функцию **УИ.От(ВашаПеременнаяОбъектаОтладки,НастройкиСКД)**. Где вместо ВашаПеременнаяОбъектаОтладки нужно передать переменную, содержащую один из доступных к отладке объектов

### Логика работы

Если контекст запуска отладки является толстым клиентом открытие формы консоли происходит сразу по окончании выполнения вызова кода

Если отладка вызывается в контексте сервера или тонкого или веб клиента, необходимая информация сохраняется в справочник **Данные для отладки**. В таком случае вызов отладки проиходит потом из списка справочника "Данные для отладки". 


### Поддерживается отладка объектов:

* **Запрос**- на текущий момент отлаживаются запросы без менеджеров временных таблиц. 
Вызов отладки 

`УИ.От(Запрос)`

* **Схема компоновки данных**- поддерживается отладка без внешних источников данных. 

Вызов отладки

`УИ.От(СхемаКомпоновкиДанных,НастройкиСКД)` - будет вызвана отладка с переданными настройками

Или

`УИ.От(СхемаКомпоновкиДанных)` - будет вызвана отладка с настройками по умолчанию для СКД


# Развитие инструментов

Разработка ведется в 1С:EDT

Замечания и предложения оставляйте в разделе **issues**. 

Если кто хочет поучаствовать - добро пожаловать. Больше идей- лучше конечное решение
