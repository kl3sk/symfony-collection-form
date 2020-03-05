ARG PHP_VERSION=7.2

FROM php:${PHP_VERSION}-fpm

#RUN curl -L https://phar.phpunit.de/phpunit.phar > /tmp/phpunit.phar \
#    && chmod +x /tmp/phpunit.phar \
#    && mv /tmp/phpunit.phar /usr/local/bin/phpunit

# Install OS utilities
RUN apt-get update
RUN apt-get -y install \
    curl \
    iputils-ping \
    net-tools \
    git \
    zip \
    unzip \
    wget \
    dnsutils \
    zlib1g-dev \
    libicu-dev\
    g++ \
    vim \
    watch \
    libcurl4-gnutls-dev \
    gettext \
    libpng-dev

RUN pecl install xdebug

RUN docker-php-ext-install zip;
RUN docker-php-ext-install curl;
RUN docker-php-ext-install intl;
RUN docker-php-ext-install mysqli;
RUN docker-php-ext-install pdo pdo_mysql;
RUN docker-php-ext-install mbstring;
RUN docker-php-ext-install gd;
RUN docker-php-ext-enable xdebug

# Install composer
COPY --from=composer:latest /usr/bin/composer /usr/bin/composer
RUN mkdir /var/composer
ENV COMPOSER_HOME /var/composer
ENV COMPOSER_ALLOW_SUPERUSER 1

WORKDIR /app

CMD ["php-fpm"]

EXPOSE 9000
