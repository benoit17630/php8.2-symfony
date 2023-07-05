FROM php:8.2-apache

RUN echo "ServerName localhost" >> /etc/apache2/apache2.conf

RUN apt-get update \
    && apt-get install -y --no-install-recommends locales apt-utils git libicu-dev g++ unzip libpng-dev libxml2-dev libzip-dev libonig-dev libxslt-dev; \
    apt-get clean; rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* /usr/share/doc/*

RUN echo "en_US.UTF-8 UTF-8" > /etc/locale.gen && \
    echo "fr_FR.UTF-8 UTF-8" >> /etc/locale.gen && \
    locale-gen

RUN curl -sSk https://getcomposer.org/installer | php -- --disable-tls && \
   mv composer.phar /usr/local/bin/composer &&  \
    chmod +x /usr/local/bin/composer

# Installez Symfony CLI via Composer \
RUN curl -sS https://get.symfony.com/cli/installer | bash
RUN  mv /root/.symfony5/bin/symfony /usr/local/bin/symfony



# installer nodejs et yarn \
RUN curl -sL https://deb.nodesource.com/setup_14.x | bash -
RUN apt-get install -y nodejs
# install npm
RUN apt-get install -y npm

RUN npm install -g yarn

RUN docker-php-ext-configure intl
RUN docker-php-ext-install pdo pdo_mysql gd opcache intl calendar dom mbstring zip xsl
RUN pecl install apcu && docker-php-ext-enable apcu

WORKDIR /var/www/
RUN symfony server:ca:install
# initialisation de symfony pour la creation de projet
RUN git config --global user.name "Entre votre nom pour la creation de projet symfony"
RUN git config --global user.email "Entre votre email pour la creation de projet symfony"

