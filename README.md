# Web project

## Структура
```
/project-root
│── /app                 # Основное приложение (PHP-код, контроллеры, сервисы)
│   ├── /Controllers     # Slim-контроллеры
│   ├── /Models          # Классы моделей для работы с БД
│   ├── /Services        # Логика приложения (сервисы, обработчики)
│   ├── /Middleware      # Slim Middleware (например, аутентификация)
│   ├── /Config          # Конфигурационные файлы (например, database.php)
│   ├── /Routes          # Определение API-маршрутов
│   ├── bootstrap.php    # Инициализация Slim-приложения
│   ├── dependencies.php # Подключение сервисов, контейнеров
│── /public              # Публичные файлы (доступны через веб-сервер)
│   ├── /assets          # Статика (JS, CSS, изображения)
│   │   ├── /css         # Скомпилированные CSS
│   │   ├── /js          # Скомпилированные JS-файлы
│   │   ├── /images      # Изображения
│   │   ├── /fonts       # Шрифты
│   ├── /uploads         # Загруженные пользователем файлы
│   ├── index.php        # Точка входа в приложение
│── /resources           # Исходные ресурсы (Vue, SCSS, компоненты)
│   ├── /views           # Шаблоны (если используются Twig, Blade и т. д.)
│   ├── /site            # Шаблоны для веб-сайта
│   │   ├── layouts      # Главные шаблоны (header, footer)
│   │   ├── pages        # Страницы (главная, контакты и т. д.)
│   │   ├── components   # Повторно используемые части (карточки, модалки)
│   ├── /emails          # Шаблоны для email-рассылки
│       ├── layouts      # Основные макеты email (шапка, подвал)
│       ├── templates    # Конкретные письма (подтверждение, сброс пароля)
│       ├── components   # Общие элементы (кнопки, подписи)
│   ├── /scss            # Исходные SCSS файлы
│   ├── /js              # Исходные JS-файлы (Vue-компоненты)
│   ├── /components      # Повторно используемые Vue-компоненты
│── /database            # База данных (миграции, сиды)
│   ├── /migrations      # Миграции базы данных
│   ├── /seeds           # Сиды (начальные данные)
│   ├── /factories       # Фабрики (если используются)
│── /docker
│   ├── /php
│   │   ├── Dockerfile       # Dockerfile для PHP
│   │   ├── php.ini          # Конфигурация PHP
│   │   ├── entrypoint.sh    # Скрипт инициализации
│   ├── /nginx
│   │   ├── nginx.conf       # Конфигурация веб-сервера
│   ├── /mysql
│   │   ├── init.sql         # SQL-скрипты
│   ├── /scripts             # Скрипты для контейнеров (например, начальная настройка)
│── /storage             # Закрытые файлы (не доступны извне)
│   ├── /logs            # Логи приложения
│   ├── /cache           # Кэшированные данные
│   ├── /sessions        # Файлы сессий
│── /tests               # Тесты (PHPUnit, Jest и др.)
│   ├── /Unit            # Unit-тесты
│   ├── /Feature         # Функциональные тесты
│── /node_modules        # Установленные npm-зависимости
│── /vendor              # Установленные Composer-зависимости
│── .env                 # Файл окружения (конфиденциальные настройки)
│── .env.example         # Пример файла окружения
│── .gitignore           # Игнорируемые файлы в Git
│── docker-compose.yml   # Конфигурация Docker Compose
│── composer.json        # Composer-конфигурация
│── package.json         # npm-конфигурация
│── webpack.config.js    # Конфигурация Webpack/Vite
│── README.md            # Документация проекта
```

## Domain-Driven Design (DDD)
/app
│── /Domain             # Чистая бизнес-логика (Сущности, Агрегаты, Репозитории, Сервисы)
│   ├── /Entities       # Основные бизнес-сущности (User.php, Order.php)
│   ├── /ValueObjects   # Объекты-значения (Email.php, Money.php)
│   ├── /Repositories   # Интерфейсы репозиториев (UserRepositoryInterface.php)
│   ├── /Services       # Бизнес-правила (UserRegistrationService.php)
│   ├── /Events         # Доменные события (UserRegistered.php)
│── /Application        # Сценарии использования (Use Cases, DTO, Команды)
│   ├── /DTO            # Data Transfer Objects (UserDTO.php)
│   ├── /UseCases       # Приложенческая логика (RegisterUser.php)
│   ├── /Commands       # Командный слой (CreateOrderCommand.php)
│   ├── /Queries        # Чтение данных (GetUserOrdersQuery.php)
│── /Infrastructure     # Взаимодействие с внешними сервисами (БД, API)
│   ├── /Persistence    # Реализация репозиториев (EloquentUserRepository.php)
│   ├── /ORM            # Модели Eloquent (если используются)
│   ├── /Cache          # Кеширование (RedisCache.php)
│   ├── /Email          # Почтовые сервисы (MailgunMailer.php)
│   ├── /Queue          # Очереди задач (RabbitMQJob.php)
│── /Interfaces         # Взаимодействие с пользователем (HTTP, CLI, API)
│   ├── /Controllers    # Slim-контроллеры (UserController.php)
│   ├── /Middleware     # Slim Middleware (AuthMiddleware.php)
│   ├── /CLI            # Консольные команды (ImportUsersCommand.php)
│   ├── /API            # API-контроллеры (UserApiController.php)
│── bootstrap.php       # Инициализация приложения
│── dependencies.php    # Подключение сервисов и контейнеров


## Объяснение структуры
 - `/app` → Backend-логика (контроллеры, сервисы, модели)
 - `/public` → Папка, доступная извне (веб-сервер открывает только ее!)
 - `/resources` → Исходные файлы (Vue-компоненты, SCSS)
 - `/database` → SQL-механизмы (миграции, начальные данные)
 - `/storage` → Закрытые файлы (сессии, логи, кэш)
 - `/tests` → Тесты (PHPUnit, Jest и т. д.)
 - `/vendor` и `/node_modules` → Зависимости PHP и npm

## Где что хранить?
| Файл                     | Расположение                                      | Доступность                                      |
|--------------------------|---------------------------------------------------|--------------------------------------------------|
| PHP-код                  | /app                                              | ❌ закрыто                                       |
| JS (Vue)                 | /resources/js                                     | ❌ закрыто                                       |
| SCSS                     | /resources/scss                                   | ❌ закрыто                                       |
| Скомпилированный CSS/JS  | /public/assets/css и /public/assets/js            | ✅ открыто                                       |
| Картинки                 | /public/assets/images                             | ✅ открыто                                       |
| Загруженные файлы        | /public/uploads                                   | ✅ открыто (но лучше через Nginx ограничения)    |
| Конфиг                   | /app/Config или .env                              | ❌ закрыто                                       |
| Логи                     | /storage/logs                                     | ❌ закрыто                                       |
