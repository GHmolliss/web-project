FROM php:8.3.1-fpm

# Копируем Composer из официального образа
COPY --from=composer:2.4.2 /usr/bin/composer /usr/bin/composer

# Устанавливаем расширения PHP и обновляем систему
RUN apt-get update && apt-get install -y --no-install-recommends \
    zlib1g-dev \
    libzip-dev \
    unzip \
    git \
    curl \
    gnupg \
    libpng-dev \
    libjpeg-dev \
    libfreetype6-dev \
    libwebp-dev \
    && docker-php-ext-configure gd --with-freetype --with-jpeg --with-webp \
    && docker-php-ext-install mysqli pdo pdo_mysql zip gd \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# Создаем пользователя и группу
RUN groupadd -g 1000 www && useradd -u 1000 -ms /bin/bash -g www www

# Устанавливаем рабочую директорию
WORKDIR /var/www/html

# Копируем файлы проекта в контейнер
COPY . /var/www/html
