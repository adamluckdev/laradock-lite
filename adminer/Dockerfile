FROM adminer:latest

USER root

RUN rm /etc/php/7.4/cli/conf.d/0-upload_large_dumps.ini
RUN rm /etc/php/7.4/fpm/conf.d/0-upload_large_dumps.ini

COPY uploads.ini /etc/php/7.4/cli/conf.d/0-uploads.ini
COPY uploads.ini /etc/php/7.4/fpm/conf.d/0-uploads.ini

USER adminer

EXPOSE 8080