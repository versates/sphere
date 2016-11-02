FROM php:7.0-fpm
RUN apt-get update && apt-get install --no-install-recommends -y \
      libghc-postgresql-libpq-dev \
      && apt-get clean \
      && rm -r /var/lib/apt/lists/* \
      && docker-php-ext-configure pgsql --with-pgsql=/usr/include/postgresql \
      && docker-php-ext-install -j"$(nproc)" pgsql pdo_pgsql
RUN yes | pecl install xdebug \
    && echo "zend_extension=$(find /usr/local/lib/php/extensions/ -name xdebug.so)" > /usr/local/etc/php/conf.d/xdebug.ini \
    && echo "xdebug.remote_enable=on" >> /usr/local/etc/php/conf.d/xdebug.ini \
    && echo "xdebug.remote_autostart=off" >> /usr/local/etc/php/conf.d/xdebug.ini
