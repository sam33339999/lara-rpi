#
#--------------------------------------------------------------------------
# Image Setup
#--------------------------------------------------------------------------
# FROM Laradock / php-worker
#   iputils         => ping
#   unzip, zip      => zip
#   build-base      => https://pkgs.alpinelinux.org/package/v3.3/main/x86/build-base
#                   => binutils, fortify-headers, g++, gcc, libc-dev, make
#   libmcrypt-dev   => 加密用
#   libxml2-dev     => xml
#   linux-headers   => kernel use ..
#

FROM php:8.1-alpine3.16
LABEL maintainer="samzheng <sam33339999@gmail.com>"

RUN set -xe; \
    apk add --no-cach \
        vim \
        bash \
        iputils \
        unzip \
        zip \
        libzip-dev \
        git \
        curl \
        build-base \
        libmcrypt-dev \
        libxml2-dev \
        linux-headers \
        pcre-dev \
        zlib-dev \
        autoconf \
        cyrus-sasl-dev \
        libgsasl-dev \
        oniguruma-dev \
        libressl \
        libressl-dev \
        supervisor

RUN pecl channel-update pecl.php.net

# 建立非 root 使用者
ARG PUID=1000
ENV PUID ${PUID}
ARG PGID=1000
ENV PGID ${PGID}

RUN addgroup -g ${PGID} worker && \
    adduser -D -G worker -u ${PUID} worker

# Redis Dep
RUN pecl install -o -f redis; \
    rm -rf /tmp/pear; \
    docker-php-ext-enable redis \

COPY supervisord.conf /etc/supervisord.conf

ENTRYPOINT ["/usr/bin/supervisord", "-n", "-c",  "/etc/supervisord.conf"]

# Clean up
RUN rm /var/cache/apk/* \
  && mkdir -p /var/www

WORKDIR /etc/supervisor/conf.d/
