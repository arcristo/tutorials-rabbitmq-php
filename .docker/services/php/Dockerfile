FROM php:fpm

MAINTAINER Adiel Cristo <adielcristo@gmail.com>

# Use args
ARG SYSTEM_USER_PHP

# Install PHP extensions and related packages
RUN apt-get update && \
    apt-get install -y --no-install-recommends \
        git \
        unzip \
        zip && \
    docker-php-ext-install \
        bcmath && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* /usr/share/doc/*

# Install Composer
RUN curl -LsS https://getcomposer.org/installer -o composer-setup.php && \
    curl -LsS https://composer.github.io/installer.sig -o composer-setup.sig && \
    php -r "if (hash('SHA384', file_get_contents('composer-setup.php')) \
            !== trim(file_get_contents('composer-setup.sig'))) { \
        unlink('composer-setup.php'); echo 'Invalid installer' . PHP_EOL; exit(1); \
    }" && \
    php composer-setup.php \
        --install-dir=/usr/local/bin \
        --filename=composer && \
    php -r "unlink('composer-setup.php');"
ENV COMPOSER_HOME /composer
ENV PATH $PATH:/composer/vendor/bin
ENV COMPOSER_ALLOW_SUPERUSER 0

# Create user
RUN useradd -ms /bin/bash ${SYSTEM_USER_PHP}
USER ${SYSTEM_USER_PHP}

WORKDIR "/usr/src/myapp"
