FROM php:7.3-apache-stretch

RUN apt-get update
RUN apt-get install -y \
    zlib1g-dev \
    libzip-dev \
    git

RUN docker-php-ext-install zip
RUN docker-php-ext-install pdo_mysql

# nvmを入れる（nodeバージョン管理）
RUN curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.11/install.sh | bash

# npm & nodejs install
RUN apt-get install -y gnupg
RUN curl -sL https://deb.nodesource.com/setup_10.x | bash -
RUN apt-get install -y nodejs
RUN nodejs -v
RUN npm install -g n
RUN npm -v

# エディタ
RUN apt-get install vim -y

# 各種設定
COPY php.ini /usr/local/etc/php

# apache2
COPY apache2.conf /etc/apache2
COPY 000-default.conf /etc/apache2/sites-available/


EXPOSE 80 443

