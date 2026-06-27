FROM php:8.5-cli

# Install system packages and PHP extensions commonly needed by Laravel
RUN apt-get update && apt-get install -y \
        libpng-dev libjpeg-dev libfreetype6-dev libicu-dev zip unzip git sudo \
    && docker-php-ext-configure gd --with-freetype --with-jpeg \
    && docker-php-ext-install pdo pdo_mysql gd bcmath intl

# Opcache (separate step for PHP 8.5 compatibility)
# RUN docker-php-ext-install opcache

# Xdebug (for code coverage)
# RUN pecl install xdebug \
#     && docker-php-ext-enable xdebug

# Install Composer (latest stable)
COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

# COPY php.ini /usr/local/etc/php/conf.d/xdebug.ini

ARG UID=1000
RUN useradd -m -u ${UID} -s /bin/bash saj && \
    usermod -aG sudo saj
USER saj

WORKDIR /var/www

# Keep the container alive so you can "exec" into it
CMD ["tail", "-f", "/dev/null"]