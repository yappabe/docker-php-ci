FROM yappabe/php:8.0

ENV ENVIRONMENT ci

RUN \
  apt-get update && \
  apt-get install -y --no-install-recommends \
  wget \
  php-pcov

COPY php-ci.ini /etc/php/8.0/fpm/conf.d/20-php-ci.ini
COPY php-ci.ini /etc/php/8.0/cli/conf.d/20-php-ci.ini

COPY 20-pcov.ini /etc/php/8.0/fpm/conf.d/20-pcov.ini
COPY 20-pcov.ini /etc/php/8.0/cli/conf.d/20-pcov.ini

RUN  php -i | grep 'pcov'

ENTRYPOINT []
