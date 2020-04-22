FROM ubuntu:18.04
LABEL maintainer="Victor Gazotti <vgazotti@gmail.com>"
ARG DEBIAN_FRONTEND=noninteractive

ENV GOSS_VERSION="0.3.6"

RUN apt-get update && apt-get install -y software-properties-common curl \
&& apt-get install xvfb -y libfontconfig wkhtmltopdf \
&& add-apt-repository ppa:ondrej/php -y \
&& apt-get update -y \
&& apt-get install -y \
    unzip  \
    php7.4-cli \
    php7.4-gd \
    php7.4-json \
    php7.4-ldap \
    php7.4-mbstring \
    php7.4-mysql \
    php7.4-pgsql \
    php7.4-sqlite3 \
    php7.4-xml \
    php7.4-xsl \
    php7.4-zip \
    php7.4-curl \
    php7.4-soap \
    php7.4-gmp \
    php7.4-bcmath \
    php7.4-imagick \
    php7.4-intl \
    php7.4-imagick \
    php7.4-redis \
    php7.4-imap

# composer
ENV COMPOSER_HOME=/composer
ENV PATH=./vendor/bin:/composer/vendor/bin:/root/.yarn/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
ENV COMPOSER_ALLOW_SUPERUSER=1
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer \ 
&& composer global require hirak/prestissimo \
&& apt-get install -y mysql-client \
&& apt-get install -y git \
&& curl -sL https://deb.nodesource.com/setup_9.x | bash - \ 
&& apt-get install -y nodejs \ 
&& npm install -g yarn \
&& curl -fsSL https://goss.rocks/install | GOSS_VER=v${GOSS_VERSION} sh
