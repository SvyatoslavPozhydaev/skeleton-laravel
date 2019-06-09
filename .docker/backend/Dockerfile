FROM php:7.2-apache

# Declare an environment variable with a default value for changing Apache's document root
# We will override this in docker-compose.yml
ENV APACHE_DOCUMENT_ROOT /var/www/html

# Configure web root
RUN sed -ri -e 's!/var/www/html!${APACHE_DOCUMENT_ROOT}!g' /etc/apache2/sites-available/*.conf
RUN sed -ri -e 's!/var/www/!${APACHE_DOCUMENT_ROOT}!g' /etc/apache2/apache2.conf /etc/apache2/conf-available/*.conf

RUN \
    # Install: dependencies
    apt-get update -y && \
    apt-get install -y --no-install-recommends \
        curl \
        zip \
        unzip \
        libpng-dev \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libmagickwand-dev \
        imagemagick \
        libicu-dev \
        libnotify-bin \
        libcurl4-openssl-dev \
        mysql-client && \
    # Purge so apt-get update is more reliable
    rm -rf /var/lib/apt/lists/* && \
    # Install: PHP extensions
    pecl install imagick && \
    docker-php-ext-enable imagick && \
    docker-php-ext-configure gd \
        --with-freetype-dir=/usr/include/ \
        --with-jpeg-dir=/usr/include/ && \
    docker-php-ext-configure intl && \
    docker-php-ext-install \
        curl \
        iconv \
        mbstring \
        pdo \
        pdo_mysql \
        mysqli \
        pcntl \
        tokenizer \
        xml \
        gd \
        zip \
        bcmath
# Install composer
ENV COMPOSER_HOME /composer
ENV PATH ./vendor/bin:/composer/vendor/bin:$PATH
ENV COMPOSER_ALLOW_SUPERUSER 1
RUN curl -s https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin/ --filename=composer
