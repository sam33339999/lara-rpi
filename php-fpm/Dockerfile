#
#--------------------------------------------------------------
# Image Setup
#--------------------------------------------------------------
#
# 藉由編輯 'php-fpm' 的基本映像檔；觀摩該 repo
#   https://github.com/Laradock/php-fpm
# 

# CONSTRAINT
# php -r "echo PHP_MAJOR_VERSION;" => 顯示 PHP 大版本號
# $PHP_INI_DIR => container php PATH
#

ARG DEV_PHP_VERSION
ARG BASE_IMAGE_TAG_PREFIX=latest
FROM php:8.1-fpm-alpine3.16 
LABEL maintainer="samzheng <sam33339999@gmail.com>"


# set   -e 讓使用者方便追蹤腳本
#       -x 命令返回值不為 0 ，會使腳本跳脫出去；這特點使腳本更為健全

RUN set -xe; \
    apk add vim; \
    apk add --no-cach bash; \
    apk add iputils; \
    apk add unzip zip libzip-dev

# 變更 sh 為 bash
RUN ln -sf /bin/bash /bin/sh
COPY ./rootfs/root/.bashrc /root/.bashrc
COPY ./rootfs/root/.vimrc /root/.vimrc

# php - bcmath 字串精度數字使用
RUN docker-php-ext-install bcmath; \
    docker-php-configure bcmath; \
    php -m | grep -q 'bcmath'

# php - zip 壓縮用
RUN docker-php-ext-install zip; \
    docker-php-ext-configure zip; \
    php -m | grep -q 'zip'

# php - redis 函式庫連接用 
RUN pecl install redis; \
    docker-php-ext-enable redis; \
    rm -rf /tmp/pear

# opcache
RUN docker-php-ext-install opcache

# composer install
RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" ;\
    php composer-setup.php; \
    php -r "unlink('composer-setup.php');"; \
    mv composer.phar /usr/local/bin/composer


WORKDIR /var/www
CMD ["php-fpm"]
EXPOSE 9000
