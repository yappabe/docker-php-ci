FROM yappabe/php:5.6

ENV ENVIRONMENT ci

RUN \
  apt-get update && \
  apt-get install -y --no-install-recommends \
  php5-xdebug

COPY php-ci.ini    /etc/php5/fpm/conf.d/
COPY php-ci.ini    /etc/php5/cli/conf.d/

RUN php -i | grep 'xdebug'

ENTRYPOINT []
