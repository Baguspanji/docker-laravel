FROM php:8.0.13-fpm-alpine

# Arguments defined in docker-compose.yml
ARG user

# Install system dependencies
RUN apk add --no-cache mysql-client msmtp perl wget procps shadow libzip libpng libjpeg-turbo libwebp freetype icu

# Install PHP extensions
RUN apk add --no-cache --virtual build-essentials \
    icu-dev icu-libs zlib-dev g++ make automake autoconf libzip-dev \
    libpng-dev libwebp-dev libjpeg-turbo-dev freetype-dev && \
    docker-php-ext-configure gd --enable-gd --with-freetype --with-jpeg --with-webp --with-xpm; \
    docker-php-ext-install pdo_mysql mbstring exif gd pcntl bz2 opcache zip bcmath mysqli pdo_mysql; \
    pecl install redis; \
    docker-php-ext-enable redis; \
    apk del build-essentials && rm -rf /usr/src/php*

# Get latest Composer
RUN wget https://getcomposer.org/composer-stable.phar -O /usr/local/bin/composer && chmod +x /usr/local/bin/composer

# Create system user to run Composer and Artisan Commands
RUN useradd -G www-data,root -u 1000 -d /home/$user $user
RUN mkdir -p /home/$user/.composer && \
    chown -R $user:$user /home/$user

# Set working directory
WORKDIR /var/www

USER $user 