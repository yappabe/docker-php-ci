FROM yappabe/php:7.0

ENV ENVIRONMENT ci

RUN \
  apt-get update && \
  apt-get install -y --no-install-recommends \
  wget \
  php7.0-xdebug

COPY php-ci.ini    /etc/php/7.0/fpm/conf.d/20-php-ci.ini
COPY php-ci.ini    /etc/php/7.0/cli/conf.d/20-php-ci.ini

RUN php -i | grep 'xdebug'

ENTRYPOINT []
