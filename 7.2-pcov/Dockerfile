FROM yappabe/php:7.2

ENV ENVIRONMENT ci

RUN pecl install pcov

RUN wget -c https://phar.phpunit.de/phploc.phar \
      -P /usr/local/bin/ && \
      ln -s /usr/local/bin/phploc.phar /usr/local/bin/phploc && \
      chmod a+x /usr/local/bin/phploc

RUN wget -c https://squizlabs.github.io/PHP_CodeSniffer/phpcs.phar \
      -P /usr/local/bin/ && \
      ln -s /usr/local/bin/phpcs.phar /usr/local/bin/phpcs && \
      chmod a+x /usr/local/bin/phpcs

ADD https://github.com/FriendsOfPHP/PHP-CS-Fixer/releases/download/v2.15.0/php-cs-fixer.phar /usr/local/bin/php-cs-fixer
RUN chmod a+x /usr/local/bin/php-cs-fixer

RUN mkdir -p /etc/phpcs && \
    git clone git://github.com/escapestudios/Symfony2-coding-standard.git /etc/phpcs/Symfony2-coding-standard && \
    /usr/local/bin/phpcs --config-set installed_paths /etc/phpcs/Symfony2-coding-standard

COPY php-ci.ini    /etc/php/7.2/fpm/conf.d/20-php-ci.ini
COPY php-ci.ini    /etc/php/7.2/cli/conf.d/20-php-ci.ini

RUN  \
      phploc --version && \
      phpcs --version && \
      php-cs-fixer --version

ENTRYPOINT []
