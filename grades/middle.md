
## Middle 

### Компетенции разработчика

- Может сделать весь проект целиком, при наличии внятного ТЗ и не самого вычурного стека
- Может окрыть сайт техническими метриками
- Может странять и предотвращать аварии
- Должен Участвовать в менторстве более младших по рангу разработчиков
- Может расширить функциональность фреймворка
- Может написать микросервис на другом языке (Go, Python)

### Содержание документа

0. [PHP](#php)
1. [Development](#development)
1. [Database](#database)
1. [Linux](#linux)
1. [Logs and Metrics](#logs-and-metrics)
1. [Security](#security)
1. [Network](#network)
1. [Common Knowledge](#common-knowledge)

<details>

<summary>

### PHP

</summary>

- Порождающие паттерны

- Опыт конфигурирования интерпретатора

1. Кэширование данных 

1. Специфика работы IO (сокетов, дескрипторов, потоков) 

</details>


<details>

<summary>

### Development

</summary>

1. Принципы разработки 

    - GRASP (General Responsibility Assignment Software Patterns) 

    - применение принципов SOLID

    - DDD (Domain-Driven Design) 

1. Архитектурные шаблоны 

    - [Шаблон ADR](https://habr.com/ru/post/260769/) (Action-Domain-Responder)
        > Доработка MVC под задачи веба

    - Шаблон [MVVM](https://habr.com/ru/company/mobileup/blog/313538/)
        > На самом деле этот шаблон подходит для десктопных или мобильных приложений. В web приложениях практически не используется.

1. [Шаблоны проектирования](https://refactoring.guru/ru/design-patterns/examples)
   > Шаблоны упрощают разработку, так как это, по сути, опыт сообщества по решению тех или иных проблем. 
   > Главное не забывайте про KISS и YAGNI, чтобы не упасть в ад абстракций и пучину сложности.

   - Порождающие шаблоны проектирования

   - Структурные шаблоны проектирования

   - Поведенческие шаблоны проектирования

1. Методологии разработки
   > Это не про scrum, agile, waterfall, планирование, проектирование и прочее. Это про методологии написания кода.

    - [TDD](https://habr.com/ru/company/ruvds/blog/450316/) (Test Driven Development)
        > Разработка через тестирование, самый известный способ разработки, требующий от разработчика сначала - написание теста к коду, а потом самого кода.

    - BDD (Behavior Driven Development)
        > Расширенная версия TDD, тем что сперва пишется не тест, а описание что нужно сделать, на предметном языке, например Gherken.

1. Тестирование. 
    - Интеграционные тесты 
        > Сложный вид тестов. Проверка работоспособности приложения, модуля, компонентом с другим приложением, модулем, компонентом. 

    - End-to-End (aka E2E aka Сквозное тестирование) 
        > Пример E2E теста - тестирование готового API приложения. Тестируются не компоненты приложения, а готовая функциональность.

    - Smoke test (aka дымовые тесты) 
        > Дымовые тесты позволяют протестировать саму возможность работать вашему приложению. 
        > Иногда используют для тестирования инфраструктуры на возможность работать в ней вашему приложению.

1. [Приёмы рефакторинга](https://refactoring.guru/ru/refactoring/techniques)
   > Чтобы избавляться от тех.долга придётся часто и много рефакторить.

1. [Антипаттерны](https://ru.wikipedia.org/wiki/Антипаттерн)
    > Полезно знать как следует делать, но не менее полезно знать как НЕ следует делать.  

1. [Semver](https://semver.org/lang/ru/)
    > Самый распространённый принцип наименования версий приложения. В некоторых языках и пакетных менеджерах является обязательным к соблюдению.

1. Распределенные системы
   > Когда приложение упирается в потолок сервера то у вас только один выход - заставить приложение работать на нескольких серверах.
   > Это сильно усложняет приложение и много ресурсов уходит на сохранение целостности и согласованности данных.

    - [Теоремы CAP и PACELC](https://habr.com/ru/company/gaz-is/blog/551986/)
        > В распределённых системах придётся чем-то жертвовать. PACELC - расширенная теорема CAP.
        > Эти теоремы как раз описывают какими параметрами придётся пожертвовать системе.

    - [Микросервисная архитектура](https://habr.com/ru/company/dataart/blog/280083/)

</details>


<details>

<summary>

### Database

</summary>

1. Реляционные базы данных MySQL/Postgres/и т.д. 

    - Диагностика производительности.
         > Всегда будут появляться медленные запросы, и чем их больше, тем медленнее будет работать ваше приложение.
        > И как правило у разных баз данных всегда есть аналитика для поиска "узких" мест.

        - Ведение логов медленных запросов — slow_log. 
            > Не получится сидеть всё время, мониторя все запросы. Проще настроить агрегацию медленных запросов.
    
    - Индексы 

        - Кластерный индекс 
            > Это не относится к вычислительным кластерам. Это индекс данных, по нему и укладываются строки в таблице.
        
        - Составные индексы. 

            - Понимание какие поля в какой последовательности добавлять в индекс при фильтрации и/или сортировке. 

        - [Понимание работы индексов](https://highload.today/indeksy-v-mysql/) 
    
    - Транзакции. 

        - Уровни изоляций транзакций. 

    - Триггеры на INSERT/UPDATE/DELETE (условия по полям)
    
    - Хранение деревьев. 
        - Алгоритм [nested sets](https://ru.wikipedia.org/wiki/Вложенное_множество_(модель)) 
         > Алгоритм позволяет достаточно дёшево собирать деревья с различными модификациями и сегментами.
         > Но затратные на вставку элементов в деревья.

    - Создание доменов

1. Документо-ориентированная база данных (часть NoSQL баз данных) — MongoDB. 

    - Типы данных в коллекциях, их назначение и различия. 

    - Анализ выполнения запросов через `explain()`, понимание его результатов. 

    - Понимание работы индексов (аналогично SQL индексам с небольшими отличиями). 
        - Sparse свойство индекса

        - Partial свойство индекса

        - TTL свойство индекса

        - Geospatial индекс

        - Text индекс

   - Вложенные объекты, массивы. 

 1. Redis

    - [Транзакции](https://redis.io/topics/transactions) :us:, но в другом, своём, понимании.

    - [Работа с Lua](https://redis.io/commands/eval) :us: 

1. Проблемы в базах данных 

    - Deadlock 

    - Full scan 

- Оптимизация запросов, устранение лишних запросов

- Полнотекстовый поиск

- Нормализация бд

</details>


<details>

<summary>

### Linux

</summary>

- Linux:
	- systemd service unit

	- полноценное знание bash

- Базовое понимание kubernetes

	- Deployments, pods, services

	- Просмотр информации об объектах kubernetes

- Знание нескольких фреймворков (laravel, yii2, fymfony, bitrix) и способность выбирать подходящий под проект

- Использование моков в тестировании

- CI/CD (конфигурация пайплайнов)

- Создание production ready docker образов

- Понимание и поддержка микросервисной архитектуры

- Дополнительный язык программирования (Go, Python)

- Elasticsearch (маппинг, индексация, поиск)

- Создание и изменение kubernetes манифестов

- Умение выделять часто используемые фрагменты кода в библиотеки

- Написание надежного, расширяемого и тестируемого кода

- Делиться знаниями, навыками, выступать на конференциях и/или писать статьи

- Знание о подходе Domain Driven Design

- Чтение и редактирование Ansible плейбуков и ролей

- Понимание механизма транзакций, репликации, шардинга

- Понимание инструментов балансировки запросов (nginx, haproxy, envoy, ingress) 

1. Базовые навыки в `bash` (улучшенный `sh` aka `shell`). 
    > В Linux-подобных системах bash'ем пронизано всё. Вы гарантировано столкнётесь с ним и будут случаи когда надо будет писать bash/shell скрипты.
    
    - Базовый синтаксис bash. 
        > По факту это единственный скриптовый язык который гарантированно будет установлен в системе.
        - Управляющие операторы `if`, `for` и `while`
        - Логические операторы `;`, `&&`, `||`
        - Исполняющие выражения `` `cmd` `` и `$(cmd)`

    - Команды обработки данных `cat`, `tail`, `head`, `grep`, `awk`, `sed`. 
        > Этот набор потребуется для сканирования и анализа логов или больших объёмов текстовых данных.

    - Команды работы с архивами данных `zcat`, `gzip`, `gunzip`, `tar`, `zgrep`. 
        > Как правило, никто не хранит логи или большие объёмы текстовых данных "как есть", обычно это архив `gz` или `tar.gz` (`tgz`).

    - Фоновые задачи, оператор `&`, команды `jobs`, `fg`, `bg`. 
        > Оператор позволит в одной shell-сессии запускать несколько команд.

    - Команда игнорирования сигналов прерываний `nohup`. 
        > Команда позволит, при завершении shell-сессии, оставлять в живых запущенные фоновые задачи до их логического завершения.

1. Понятие `процесс`. 

    - Родительский процесс, дочерний процесс. 
        > Процессы не появляются из ниоткуда, их что-то запускает. Понимание иерархии процессов облегчит работу с ними и сделает проще понимание мультипроцессовых приложений.

    - Мастер-воркер процессы, демон (daemon). 
        > Это один из распространённых видов распараллеливания вычислений в приложениях. Много программ используют именно такой подход распараллеливания.

    - Назначение сигналов [SIGKILL](https://ru.wikipedia.org/wiki/SIGKILL), [SIGTERM](https://ru.wikipedia.org/wiki/SIGTERM), [SIGINT](https://ru.wikipedia.org/wiki/SIGINT), [SIGHUP](https://ru.wikipedia.org/wiki/SIGHUP), [SIGSEGV](https://ru.wikipedia.org/wiki/SIGSEGV). 


1. Изучение понятия `дескриптор`. 
    > Любой поток данных (входящий и/или исходящий) представляется в виде дескрипторов. Что-либо читать или писать будете (вероятней всего) через дескриптор.

    - Стандартные дескрипторы `STDIN`, `STDOUT`, `STDERR` и их нумерация. 
        > Любой поток в процессе пронумерован и есть "зарезервированные" номера под определенные потоки.

    - Потоки, сокеты и unix-сокеты. 
        > Это всё разновидности дескрипторов с которыми придётся работать. На всех них распространяются правила дескрипторов, ну так как они и есть дескрипторы.

1. [Файловая система](https://gitlab.com/doatta/gnu-linux-rhcsa/-/blob/master/04.%20%D0%9E%20%D1%84%D0%B0%D0%B9%D0%BB%D0%BE%D0%B2%D1%8B%D1%85%20%D1%81%D0%B8%D1%81%D1%82%D0%B5%D0%BC%D0%B0%D1%85.md) 

    - Изменение прав доступов через команды `chmod`, `chown`. 

1. Ссылки на файловой системе. 

   - Hardlink (aka жесткая ссылка). 
     > Редкий случай использования ссылки. Потребуется если надо "дедуплицировать" большой объём файлов.
     > По сути позволяет создать несколько имён одному файлу.

1. Запуск и остановка сервисов systemd. 
   > Linux по сути просто пачка запущенных приложений как сервисов.

1. Перенос контента. 
    > Появляется потребность перекинуть логи, дамп базы и другие файлы между машинами или к себе.
    
    - `rsync` 
        > пожалуй самый мощный инструмент переноса файлов между хостами с кучами настроек, правил и протоколов.
    
    - `rclone` 
        > "rsync" для облачных хранилищ. Универсальный инструмент для работы с контентом, который хранится в облаках или где-то по сети. 

1. Планировщики задач
    - Команда `at` 

1. Оперативная память. 

    - Команда `free`, мета информация `/proc/meminfo`. 
        > Всегда оценивайте сколько памяти потребуется приложению или скриптам, чтобы не быть убитыми системой.

1. [Логи системы](https://habr.com/ru/post/332502/). Для чего и как посмотреть. 
    > Когда случаются проблемы то логи — единственное, что может навести на суть проблемы. 
    > Помимо логов приложения стоит заглядывать в логи системы, иногда её проблема может вести к проблеме в приложениях. Стоит выделить некоторые логи:

    - `dmesg` (driver messages) — важные сообщения от компонентов Linux, включая от OOM-киллера. 

    - `syslog` — системный журнал. 
     > Там могут быть сообщения от ядра Linux, различных служб, сетевых интерфейсов и многого другого.

1. Проблемы в Linux и последствия. 

    - Segmentation fault (aka segfault aka сегфолт). 
        > Не такая уж и редкая ошибка приложений, как хотелось бы. Приложение попыталось работать с памятью доступа к которой у неё нет. 
        
</details>


<details>

<summary>

### Logs and Metrics

</summary>

1. [Prometheus](https://prometheus.io/) или подобные, например, [Victoria Metrics](https://victoriametrics.com/) 
   > Популярная система сбора и хранения метрик.

   - Типы метрик 
        - count
        - gauge
        - histogram
        - summary

    - Варианты отправки метрик: push и pull 

    - Запросы (лучше и наглядней делать из Grafana) 
        - [Синтаксис](https://prometheus.io/docs/prometheus/latest/querying/basics/) 
        - Лейблы
        - Векторы
        - Интервалы
        - Операторы

    - [Функции](https://prometheus.io/docs/prometheus/latest/querying/functions/), особенно стоит выделить 2 из них: 
        - rate
        - irate

</details>

   
<details>

<summary>

### Security

</summary>

1. Виды управления доступом 
   - Access Control List (ACL) 

   - [Role-based access control](https://habr.com/ru/company/custis/blog/248649/) (RBAC) 

   - [Attribute-based access control](https://habr.com/ru/company/custis/blog/248649/) (ABAC) 

1. Аутентификация 


    - [OAuth2](https://www.digitalocean.com/community/tutorials/oauth-2-ru) 
        > Распространенный вид авторизации через посредника, который гарантирует что Вы это Вы и может выдать некоторые данные по пользователю, с его согласия.
        > Часто сталкиваются c OAuth2 тогда когда надо подключить авторизацию через соц. сети. У них у всех OAuth2 (но каждый со своими модификациями).

    - OpenID 
        > Один из первых популярных SSO. Уступает Oauth2 по популярности, но так же где-то используется.

    - Ldap 
        > Данный вид авторизации используется, чаще всего, для авторизации во внутренних сервисах своих сотрудников.

    - JSON Web Token (JWT) 
        > Это не тип авторизации, а инструмент для передачи идентифицирующих данных. Однако такой токен может иметь очень широкое применение, не только в авторизации.
        > Необходимо знать стандартные ключи, когда имеет смысл использовать, основные фичи

        - когда следует применять jwt, а когда - сессию

1. Виды атак\уязвимостей

    - IDOR уязвимость 

        - DoS/DDoS 

            - HTTP-флуд 

            - Медленный запрос 

        - Бомбы 

            - Logic Bomb 

        - Атака посредника (Man In The Middle, MITM) 

        - Спуфинг 
    
</details>


<details>

<summary>

### Network

</summary>

1. Базовое понимание работы сети.

   - Протокол TCP
        > Вы вряд ли будете читать пакеты TCP. Но полезно знать КАК работает TCP,
        > это позволит понять почему при идеальных "интернетах" всё равно приложение может лагать по сети.

      - Буферы (window size) 

    - Протокол UDP. 
        > Самый простой сетевой протокол семейства. Требуется понимание его работы.
        > HTTP/3.0, DNS работает на протоколе UDP, и понимание UDP даст немного понимания в работе HTTP/3.0

1. Проблемы сети.
    > Их, как всегда, много. Но стоит выделить те, которые явно влияют на скорость работы сети.
    > По большей части эти проблемы присущи TCP, но могут появиться и там где эмулируют TCP — на другом протоколе (например UDP)

    - Packet loss 

    - Reordering 

    - Jitter 

    - Round-Trip Time (RTT aka лаг)
    
    - [Сетевое ожидание](https://developer.mozilla.org/ru/docs/Web/Performance/Understanding_latency) (Network latency, задержка) 

1. IPv4, IPv6.
   > Базовое отличие протоколов надо знать, хотя бы, чтобы правильно создать колонку IP в базе и обработку в коде.

- [GraphQL](https://habr.com/ru/post/326986/) 

1. [DNS](https://developer.mozilla.org/ru/docs/Learn/Understanding_domain_names). 
    > Ваш код 24/7 будет работать с доменами так как никто не использует чистый IP для соединения с чем-либо.
    > Зная как работает DNS и управление резолвингом домена в системе, можно упростить отладку в некоторых случаях.
    
    - [Как работает резолвинг доменов](https://temoto.github.io/a/kak-rabotayut-domeny.html) 
    
    - [DNS записи](https://ru.wikipedia.org/wiki/Типы_ресурсных_записей_DNS) 

    - Основные MX, CNAME, NS, A, AAAA, TXT 

1. Трассировки маршрутов. 

1. [Cross-Origin Resource Sharing (CORS)](https://developer.mozilla.org/ru/docs/Web/HTTP/CORS) 
   > Для кросс-доменных XHR/WebSocket запросов надо научиться работать с CORS, иначе запросы не будут работать.

1. [Content-Security-Policy (CSP)](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Content-Security-Policy) 
   > Для повышения безопасности можно ограничить и указать что и откуда может загружаться и запускаться на странице.

1. Различия версий протокола HTTP: HTTP/1.0, HTTP/1.1 
   > Не смотря на появление новых версий протокола HTTP, версии HTTP/1.0 и HTTP/1.1 всё еще остаются частыми во внутренних сетях кластеров.

1. WebSocket протокол 
   > Это расширения версии HTTP/1.1 и выше для механизма обмена данными по одному соединению.
   > Часто используется для чатов и/или для event-driven модели.

    - [Масштабируемая конфигурация nginx](https://www.youtube.com/watch?v=jf3wIN-FwW4) 

</details>


<details>

<summary>

### Common Knowledge

</summary>

1. Регулярные выражения. Поиграться регулярными выражениями можно [тут](https://regex101.com/). Хоть каждый язык может иметь своё видение регулярных выражений, в общем смысле (и синтаксисе) они похожи. 
    > Рано или поздно придётся спарсить данные из текста или проверять данные, вот тут как раз и потребуются регулярные выражения.

1. Криптография.

    - Соль для подписей. 
     > В теории (да и на практике) хеш-функцию можно определить и чтобы сильнее обезопасить от "взлома" вашего хеша, используя так называемую соль.
     
    - Коллизии хешей. 
     > Хеш-функции могут на разных данных вернуть один и тот же результат (хеш), что может привести к проблемам и багам.
     > Лучше знать какова вероятность коллизий у хеш-функции и как их избегать.
    

1. Структуры данных. 

    - Хеш таблицы. 
        > Таблицы часто используются в самих языках программирования (ассоциативные массивы, объекты и т.п.)

    - Очередь и стек. 
        > Самые простые структуры данных, которые часто придётся использовать повседневно в коде.

    - [Связный список](https://ru.wikipedia.org/wiki/Связный_список) и [двусвязный список](https://ru.wikipedia.org/wiki/Связный_список#Двусвязный_список_(двунаправленный_связный_список)). 
        > Эти структуры данных часто используются в разработке так как являются самым простым способом связать элементы с собой.
        > Они так же активно используются внутри вашего языка (под "капотом") повсеместно.


1. Форматы хранения и передачи данных

   - Бинарные. 
     > Бинарные форматы используются сугубо для хранения и передачи данных.

     - MessagePack

     - BSON (бинарный аналог JSON)

     - ProtoBuf

</details>