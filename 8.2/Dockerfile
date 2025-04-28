FROM ubuntu:latest
LABEL maintainer="Victor Gazotti <vgazotti@gmail.com>"
ARG DEBIAN_FRONTEND=noninteractive

RUN apt-get update && apt-get install -y software-properties-common curl \
&& add-apt-repository ppa:ondrej/php -y \
&& apt-get update -y && apt install -y libfontconfig \
    sudo \
    wget \
    unzip  \
    php8.2 \
    php8.2-cli \
    php8.2-gd  \
    php8.2-ldap \
    php8.2-mbstring \
    php8.2-mysql \
    php8.2-pgsql \
    php8.2-sqlite3 \
    php8.2-xml \
    php8.2-xsl \
    php8.2-zip \
    php8.2-curl \
    php8.2-soap \
    php8.2-gmp \
    php8.2-bcmath \
    php8.2-imagick \
    php8.2-intl \
    php8.2-imagick \
    php8.2-redis \
    php8.2-imap \ 
    openssl \
    libssl-dev \ 
    libxrender-dev \ 
    libx11-dev \ 
    libxext-dev \ 
    libfontconfig1-dev \ 
    libfreetype6-dev \ 
    fontconfig

RUN wget https://github.com/wkhtmltopdf/wkhtmltopdf/releases/download/0.12.4/wkhtmltox-0.12.4_linux-generic-amd64.tar.xz \
&& tar xvf wkhtmltox-0.12.4_linux-generic-amd64.tar.xz \ 
&& mv wkhtmltox/bin/wkhtmlto* /usr/local/bin \ 
&& ln -s /usr/local/bin/wkhtmltopdf /usr/bin/wkhtmltopdf

# composer
ENV COMPOSER_HOME=/composer
ENV PATH=./vendor/bin:/composer/vendor/bin:/root/.yarn/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
ENV COMPOSER_ALLOW_SUPERUSER=1
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer --2\ 
&& apt-get install -y mysql-client \
&& apt-get install -y git \
&& curl -sL https://deb.nodesource.com/setup_18.x | bash - \ 
&& apt-get install -y nodejs \ 
&& npm install -g yarn 