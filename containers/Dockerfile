FROM docker.io/alpine:3

# S6
RUN apk add --no-cache wget ca-certificates && \
apk --no-cache --update upgrade && \
cd /tmp && \
export s6_ver=$(wget -qO- https://api.github.com/repos/just-containers/s6-overlay/releases/latest | grep '"tag_name":' | sed -E 's/.*"([^"]+)".*/\1/') && \
export s6_arch=$(arch) && \
wget https://github.com/just-containers/s6-overlay/releases/download/${s6_ver}/s6-overlay-noarch.tar.xz && \
wget https://github.com/just-containers/s6-overlay/releases/download/${s6_ver}/s6-overlay-${s6_arch}.tar.xz && \
wget https://github.com/just-containers/s6-overlay/releases/download/${s6_ver}/s6-overlay-symlinks-arch.tar.xz && \
wget https://github.com/just-containers/s6-overlay/releases/download/${s6_ver}/s6-overlay-symlinks-noarch.tar.xz && \
tar -C / -Jxpf /tmp/s6-overlay-noarch.tar.xz && \
tar -C / -Jxpf /tmp/s6-overlay-${s6_arch}.tar.xz && \
tar -C / -Jxpf /tmp/s6-overlay-symlinks-arch.tar.xz && \
tar -C / -Jxpf /tmp/s6-overlay-symlinks-noarch.tar.xz && \
rm s6-overlay-noarch.tar.xz && \
rm s6-overlay-${s6_arch}.tar.xz && \
rm s6-overlay-symlinks-arch.tar.xz && \
rm s6-overlay-symlinks-noarch.tar.xz

ARG PHP_VERSION=84
# 安装依赖
RUN apk --no-cache add \
  php${PHP_VERSION} \
  php${PHP_VERSION}-fpm \
  php${PHP_VERSION}-mysqli \
  php${PHP_VERSION}-mysqlnd \
  php${PHP_VERSION}-json \
  php${PHP_VERSION}-openssl \
  php${PHP_VERSION}-curl \
  php${PHP_VERSION}-zlib \
  php${PHP_VERSION}-xml \
  php${PHP_VERSION}-xmlreader \
  php${PHP_VERSION}-xmlwriter \
  php${PHP_VERSION}-xsl \
  php${PHP_VERSION}-phar \
  php${PHP_VERSION}-intl \
  php${PHP_VERSION}-dom \
  php${PHP_VERSION}-xmlreader \
  php${PHP_VERSION}-xmlwriter \
  php${PHP_VERSION}-exif \
  php${PHP_VERSION}-fileinfo \
  php${PHP_VERSION}-sodium \
  php${PHP_VERSION}-gd \
  php${PHP_VERSION}-simplexml \
  php${PHP_VERSION}-ctype \
  php${PHP_VERSION}-mbstring \
  php${PHP_VERSION}-zip \
  php${PHP_VERSION}-opcache \
  php${PHP_VERSION}-iconv \
  php${PHP_VERSION}-pcntl \
  php${PHP_VERSION}-session \
  php${PHP_VERSION}-tokenizer \
  php${PHP_VERSION}-bcmath \
  php${PHP_VERSION}-bz2 \
  php${PHP_VERSION}-calendar \
  php${PHP_VERSION}-cgi \
  php${PHP_VERSION}-embed \
  php${PHP_VERSION}-enchant \
  php${PHP_VERSION}-ftp \
  php${PHP_VERSION}-gmp \
  php${PHP_VERSION}-odbc \
  php${PHP_VERSION}-pdo \
  php${PHP_VERSION}-pdo_dblib \
  php${PHP_VERSION}-pdo_mysql \
  php${PHP_VERSION}-pdo_odbc \
  php${PHP_VERSION}-pdo_pgsql \
  php${PHP_VERSION}-pdo_sqlite \
  php${PHP_VERSION}-pgsql \
  php${PHP_VERSION}-posix \
  php${PHP_VERSION}-shmop \
  php${PHP_VERSION}-snmp \
  php${PHP_VERSION}-soap \
  php${PHP_VERSION}-sockets \
  php${PHP_VERSION}-sqlite3 \
  php${PHP_VERSION}-tidy \
  php${PHP_VERSION}-pecl-redis \
  php${PHP_VERSION}-pecl-yaml \
  php${PHP_VERSION}-pecl-imagick \
  php${PHP_VERSION}-pecl-mongodb \
  php${PHP_VERSION}-pecl-mailparse \
  php${PHP_VERSION}-pecl-zstd \
  php${PHP_VERSION}-pecl-apcu \
  php${PHP_VERSION}-pecl-brotli \
  php${PHP_VERSION}-pecl-opentelemetry \
  php${PHP_VERSION}-spx \
  php${PHP_VERSION}-pecl-excimer \
  php${PHP_VERSION}-pecl-uuid \
  php${PHP_VERSION}-pecl-ds \
  php${PHP_VERSION}-pecl-maxminddb \
  php${PHP_VERSION}-pecl-grpc \
  php${PHP_VERSION}-pecl-swoole \
  php${PHP_VERSION}-pecl-couchbase \
  php${PHP_VERSION}-pecl-event \
  php${PHP_VERSION}-pecl-lzf \
  php${PHP_VERSION}-pecl-memcache \
  php${PHP_VERSION}-pecl-memcached \
  php${PHP_VERSION}-pecl-xlswriter \
  ghostscript \
  curl \
  bash \
  less \
  caddy

RUN mkdir -p /usr/local/sbin

RUN ln -s /usr/bin/php${PHP_VERSION} /usr/local/sbin/php \
  && ln -s /usr/sbin/php-fpm${PHP_VERSION} /usr/local/sbin/php-fpm \
  && ln -s /usr/sbin/caddy /usr/local/sbin/caddy