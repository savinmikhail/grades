# Pre Junior

### Компетенции разработчика

- Может сделать CRUDы (+пагинация, фильтры)
- Может сделать отправку на почту при наличии сконфигурированного SMTP сервера

### Содержание документа

0. [PHP](#php)
1. [Development](#development)
1. [Database](#database)
1. [Docker](#docker)
1. [Linux](#linux)
1. [Logs and Metrics](#logs-and-metrics)
1. [Security](#security)
1. [Network](#network)
1. [Common Knowledge](#common-knowledge)

<details>

<summary>

### PHP

</summary>

- Отличия php7 от php8

- Типы данных

- TypeHinting, strict mode

- Строгое и нестрогое сравнение

- Работа с ссылками

- Copy-on-write

- Область видимости переменной

- Модификаторы доступа

- Магические методы

- Autoloader

- Composer

- XDebug

- Rest API

- Инкапсуляция/наследование/полиморфизм

- Абстрактные классы/методы

- Авторизация и аутентификация
(Различия. Авторизация через сессию и через jwt token. Basic Auth)

- Как забрать результат PUT в php 

- Как работает автозагрузка классов в пхп?

- Можно ли перебить автозагрузчик классов в пхп?

- Магические методы у пхп?

- Чем отличается класс от объекта?

- Когда вызывается деструктор?

-  Как указать, что метод возвращает определенный тип?

- Зачем нужен composer.json?

-  Нужно ли комитить composer.lock?

- Как получить первый символ строки в пхп? А в случаях с юникодом?


</details>


<details>

<summary>

### Development

</summary>

1. Принципы разработки 

    - Понимание принципов SOLID

    - Kiss

    - Dry

    - YAGNI

1. Архитектурные шаблоны 

    - Шаблон MVC 
        > Самый старый и достаточно распространённый шаблон проектирования приложения, разделяющий UI от логики приложения.

1. [Типы приложения](https://dou.ua/forums/topic/31720/)
    > Существует разделение приложения по способу генерации UI.
    
    - MPA (Multi-Page Application)
        > Классический тип приложения, с несколькими страницами генерируемыми на back-end для создания UI.
    
    - SPA (Single Page Application)
        > Общее название типа приложения когда приложение живёт в браузере и ходит за данными на сервер. Может быть как SSG, SSR, CSR или любое их сочетание.

1. Тестирование. 

    - Unit тестирование 
        > Тестирование отдельных (в том числе отдельных друг от друга) частей продукта, обычно отдельных функций/методов.
        > Unit-тесты так же несут ещё одну цель - проверка архитектуры вашей реализации.
        > Как правило, если у вас не получается написать unit-тест на функцию/метод, не вовлекая сторонние компоненты приложения
        > то возможно стоит пересмотреть архитектуру. Хорошее Unit-тестирование ведёт к хорошей инверсии контроля (IoC, см. выше)

</details>


<details>

<summary>

### Database

</summary>

1. Реляционные базы данных MySQL/Postgres/и т.д

- Базовый синтаксис запросов `SELECT`/`INSERT`/`UPDATE`/`DELETE`

- Создание и модификация таблиц 

- Типы колонок таблиц их назначение и различие

- Создание и применение `ALTER` запросов

- Объединение таблиц `LEFT JOIN`, `RIGHT JOIN`, `INNER JOIN`, `OUTER JOIN`, `JOIN`

- Группировка данных через `GROUP BY`

- Фильтрация после группировки. 

- Функции работы с группами `MAX`/`MIN`/`AVG`/и т.д

- Понимание и назначение внешних ключей (foreign key)

- Какие особенности у prepared statement?

- Что такое транзакция?

- Какие команды есть у транзакции?

- Принцип работы HAVING. Можно на примере SQL-запроса и пояснить как работает

</details>


<details>

<summary>

### Docker

</summary>

Docker, docker-compose, docker compose

- commands: `build`, `up`, `down`, `stop`, `rm`, `ps`, `create `, `run`, 

Быть способным добавить в связку нужный контейнер, сконфигурировать его, написать простой докер образ (к имаджу добавить composer, набор библиотек, нужные права, файлы, запуск скриптов на старте)

Уметь писать Makefile или Task.yaml

</details>


<details>

<summary>

### Linux

</summary>

1. Установка пакетов и обновление системы через `apt`/`apt-get` в Ubuntu/Debian и `apk` в Alpine. 

1. Базовые навыки в `bash` (улучшенный `sh` aka `shell`). 

    - Базовые команды для работы с файловой системой `cd`, `cp`, `rm`, `chmod`, `ls`, `echo`, `pwd`, `apt`, `find`, `cat`, `tail`, `mv`, `mkdir`, `which`

    - [Консольные редакторы vim, nano.](https://basis.gnulinux.pro/ru/latest/basis/10/10._Текстовые_редакторы_nano_и_vi.html) Открыть файл, внести изменения, сохранить. 
        > Редактирование файла из консоли не такая редкость. Кстати, чтобы выйти из vim: esc, напечатайте `:q!`, enter.

    - Консольный файловый менеджер `mc`. 

    - Потоки, перенаправление потоков > >> <  (2>&1)
        > Куда писать вывод, а куда ошибки, помогут указать эти операции.
    
    - Понимание описания доступов вида --xr-xrwx и 0137 (восьмеричная) у файлов и директорий

1. [Пользователи](https://gitlab.com/doatta/gnu-linux-rhcsa/-/blob/master/19.%20Пользователи.md) 

    - Пользователь `root`. 
        > По сути это админ системы. Избегайте использование root (даже в контейнерах) так как доступ к root даёт доступ ко всей системе, о чем мечтают все зловреды.
    
    - Супер пользователь, команды [su](https://gitlab.com/doatta/gnu-linux-rhcsa/-/blob/master/17.%20su.md) и [sudo](https://gitlab.com/doatta/gnu-linux-rhcsa/-/blob/master/18.%20sudo.md). 
        > Никто не даст вам root на проде, но вполне можете иметь "привилегированного" пользователя, который умеет в `sudo`.

1. Ссылки на файловой системе. 

    - Symlink (aka символическая ссылка). 
        > Самый распространённый вид ссылки. Повсеместно используется в Linux да и пакетных менеджерах разных языков. Вы тоже будете это использовать.

1. [SSH](https://ru.wikipedia.org/wiki/SSH). 
    > Самый доступный способ запустить `shell` на удалённой машине это использовать SSH. Используется повсеместно.

    - Генерация собственного ssh-rsa ключа через `ssh-keygen`. 
        > Без него вы не попадёте на хосты по SSH.

    - Использование публичного ssh-rsa ключа для входа на удалённую машину (используйте второй контейнер с Linux). 

</details>


<details>

<summary>

### Logs and Metrics

</summary>

- использование разных уровней логирования

</details>


<details>

<summary>

### Security

</summary>

1. [Виды атак и уязвимостей](https://docs.wallarm.ru/attacks-vulns-list/) 

    - Инъекции (например SQL-инъекции) 

    - CSRF атака

</details>


<details>

<summary>

### Network

</summary>


- HTTP
    - (PUT, PATCH, GET, POST, DELETE, OPTIONS. в каких случаях какой использовать, отличия, особенности)

    - DNS

    - Cookie

    - Headers

- Что такое CORS-политика

- Как выглядит HTTP - запрос, из чего он состоит

- Статусы ответов

- Web сервера

    - [Nginx](https://nginx.org). 
        > Самый распространённый Web-сервер. Вероятность натолкнуться на него во время разработки web-приложения - высока.
        
        - [Ознакомление с базовыми возможностями](https://nginx.org/ru/docs/beginners_guide.html) 

        - Написание простых локаций в `/etc/nginx/nginx.conf` раздачи файлов 

        - HTTP, FastCGI проксирование 
    
    - [Apache httpd](https://httpd.apache.org/). 
        > Один из старых, но активно использующихся Web-серверов широкого профиля. 
        > Хоть он уже и уступает nginx-у в популярности, но столкнуться с ним в проекта есть всё так же легко. 

</details>


<details>

<summary>

### Common Knowledge

</summary>

1. Git

- commands: `fetch`, `pull`, `push`, `commit`, `add`, `log`, `merge`, `checkout`

- Формирование commit message

- Чем отличается merge от cherry pick

1. Форматы хранения и передачи данных

    - Текстовые. 
        > Текстовые форматы используются так же для хранения конфигурации приложений

        - JSON

        - YAML

        - XML


</details>
