FROM yappabe/php:5.6

ENV ENVIRONMENT ci

RUN apt-get update && \
    apt-get install -y php5-xdebug

RUN wget -c https://phar.phpunit.de/phploc-4.0.1.phar \
      -P /usr/local/bin/ && \
      ln -s /usr/local/bin/phploc-4.0.1.phar /usr/local/bin/phploc && \
      chmod a+x /usr/local/bin/phploc

RUN wget -c https://squizlabs.github.io/PHP_CodeSniffer/phpcs.phar \
      -P /usr/local/bin/ && \
      ln -s /usr/local/bin/phpcs.phar /usr/local/bin/phpcs && \
      chmod a+x /usr/local/bin/phpcs

RUN wget -c https://squizlabs.github.io/PHP_CodeSniffer/phpcbf.phar \
      -P /usr/local/bin/ && \
      ln -s /usr/local/bin/phpcbf.phar /usr/local/bin/phpcbf && \
      chmod a+x /usr/local/bin/phpcbf

RUN wget -c https://github.com/bytepark/php-phar-qatools/raw/master/phpcb.phar \
      -P /usr/local/bin/ && \
      ln -s /usr/local/bin/phpcb.phar /usr/local/bin/phpcb && \
      chmod a+x /usr/local/bin/phpcb


RUN wget -c https://phar.phpunit.de/phpunit-5.7.27.phar \
      -P /usr/local/bin/ && \
      ln -s /usr/local/bin/phpunit-5.7.27.phar /usr/local/bin/phpunit && \
      chmod a+x /usr/local/bin/phpunit

ADD http://get.sensiolabs.org/php-cs-fixer.phar /usr/local/bin/php-cs-fixer
RUN chmod a+x /usr/local/bin/php-cs-fixer

RUN mkdir -p /etc/phpcs && \
    git clone git://github.com/escapestudios/Symfony2-coding-standard.git /etc/phpcs/Symfony2-coding-standard && \
    /usr/local/bin/phpcs --config-set installed_paths /etc/phpcs/Symfony2-coding-standard

COPY php-ci.ini    /etc/php5/fpm/conf.d/
COPY php-ci.ini    /etc/php5/cli/conf.d/

RUN  \
      phploc --version && \
      phpcs --version && \
      phpcbf --version && \
      phpcb --version && \
      phpunit --version && \
      php-cs-fixer --version

ENTRYPOINT []
