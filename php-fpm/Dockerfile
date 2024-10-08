ARG PHP_VERSION=8.1

FROM php:${PHP_VERSION}-fpm

ADD https://github.com/mlocati/docker-php-extension-installer/releases/latest/download/install-php-extensions /usr/local/bin/

# Used for additional extensions or extensions not supported in every PHP version
ARG ADDITIONAL_PHP_EXTENSIONS=''

RUN chmod uga+x /usr/local/bin/install-php-extensions
RUN sync
RUN install-php-extensions bcmath gd exif zip imap intl opcache pdo_mysql pdo_pgsql redis xdebug soap ${ADDITIONAL_PHP_EXTENSIONS}

#Disable Xdebug by default
RUN sed -i 's/^zend_extension=/;zend_extension=/g' /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini

WORKDIR /var/www

RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
RUN php -r "if (hash_file('sha384', 'composer-setup.php') === file_get_contents('https://composer.github.io/installer.sig')) { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
RUN php composer-setup.php
RUN php -r "unlink('composer-setup.php');"
RUN mv composer.phar /usr/local/bin/composer

#Non-root user
ARG PUID=1000
ARG PGID=1000

RUN groupmod -o -g ${PGID} www-data && \
    usermod -o -u ${PUID} -g www-data www-data

CMD ["php-fpm"]

EXPOSE 9000
