FROM php:7.1-fpm

ADD .bashrc /var/www/.bashrc

ENV PHP_IDE_CONFIG="serverName=DockerSymfony"

#zlib1g-dev is required by php-zip extension
RUN apt-get update; \
    apt-get install -y zlib1g-dev wget

RUN pecl install xdebug-2.5.5 && docker-php-ext-enable xdebug
#php-zip is required by composer to download compressed packages
RUN docker-php-ext-install zip

ADD install-composer.sh ./install-composer.sh
RUN chmod +x ./install-composer.sh; \
    ./install-composer.sh; \
    mv ./composer.phar /usr/bin/composer

USER www-data