# FROM php:7.4-fpm
FROM php:8.3-fpm

WORKDIR /var/www/html

RUN apt-get update \
  && apt-get install -y libonig-dev libzip-dev unzip \

# xdebug install
  && pecl install xdebug \
  && docker-php-ext-enable xdebug

# composer （今回は使用しませんが。。）
COPY --from=composer:2 /usr/bin/composer /usr/bin/composer

# docker-compose.ymlで指定した volumes と同じように書いてください。
# COPY [コピーする(ローカル)] [コピー先(コンテナ内)]　（詳しくは参考文献をご覧ください。）
COPY ./app /var/www/html
COPY ./docker/php/php.ini /usr/local/etc/php/php.ini
COPY ./docker/php/xdebug.ini /usr/local/etc/php/conf.d/xdebug.ini

