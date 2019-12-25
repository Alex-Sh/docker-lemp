FROM php:7.4-fpm

# Install dependencies
RUN apt-get update && apt-get install --no-install-recommends -y \
    libfreetype6-dev \
    libjpeg62-turbo-dev \
    libpng-dev \
    libicu-dev \
    libzip-dev \
    git \
    unzip \
     && docker-php-ext-configure gd --with-freetype --with-jpeg \
     && docker-php-ext-configure opcache --enable-opcache \
     && docker-php-ext-configure intl \
        && docker-php-ext-install -j$(nproc) gd intl pdo_mysql exif zip \
        && pecl install xdebug \
        && docker-php-ext-enable xdebug opcache \
    # Cleanup
    && apt-get clean && rm -rf /var/lib/apt/lists/*

# Install composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Set container working dir
WORKDIR /var/www/app

CMD ["php-fpm"]