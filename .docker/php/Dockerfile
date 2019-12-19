FROM centos:7.3.1611

# EPELリポジトリ
RUN yum -y install epel-release
# Remiリポジトリ
RUN rpm -Uvh http://rpms.famillecollet.com/enterprise/remi-release-7.rpm

# PHPインストール
RUN yum install -y --enablerepo=remi,remi-php73 php php-cli php-common php-devel php-gd php-json php-mbstring php-mcrypt php-mysqlnd php-pdo php-xml

# 諸々
RUN yum install -y git bash openssl libpng-devel make gcc libtool gcc-c++ nasm
RUN yum update -y

# nvmを入れる（nodeバージョン管理）
RUN curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.35.2/install.sh | bash

# nodeを入れる
RUN source ~/.nvm/nvm.sh && \
nvm install 13.5.0 && \
nvm alias default 13.5.0 && \
nvm use default

# confファイル更新
COPY ./httpd.conf /etc/httpd/conf/httpd.conf

# マウントに必要なファイルを作る
RUN mkdir /var/www/html/public

EXPOSE 80 443

# Apache起動
CMD httpd -D FOREGROUND
