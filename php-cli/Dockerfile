FROM php:8.2-cli
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

COPY . /usr/src/myapp
WORKDIR /usr/src/myapp

CMD [ "php", "-m" ]
