FROM php:8.2-apache
# Update repositories and install some PHP core extensions
RUN apt-get update && apt-get -y install \
    libfreetype6-dev \
    libjpeg62-turbo-dev \
    libpng-dev \
    libpq-dev
# Install and configure extensions
RUN docker-php-source extract \
    && docker-php-ext-configure gd --with-freetype --with-jpeg \
    && docker-php-ext-install -j$(nproc) gd \
    && docker-php-ext-install pgsql \
    && docker-php-source delete
# Install through PECL some extensions
RUN pecl install redis-5.3.7 \
    && pecl install xdebug-3.2.1 \
    && docker-php-ext-enable redis xdebug
# Set enviroment as development
RUN cp "$PHP_INI_DIR/php.ini-development" "$PHP_INI_DIR/php.ini"
# Copy to html directory files from project
COPY ./html /var/www/html
