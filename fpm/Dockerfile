FROM php:7.2-fpm

ENV PHP_INI_DIR /usr/local/etc/php/
ENV WORKDIR /var/www/html
WORKDIR ${WORKDIR}

COPY ./customized/customized.ini $PHP_INI_DIR/conf.d/customized.ini
COPY ./customized/opcache.ini $PHP_INI_DIR/conf.d/opcache.ini

# Install Composer
COPY ./composer/composer.phar $WORKDIR/composer.phar
RUN mv composer.phar /usr/local/bin/Composer

# Install dependencies
RUN apt-get update \
  && apt-get install -y \
    libfreetype6-dev \ 
    libicu-dev \ 
    libjpeg62-turbo-dev \ 
    libmcrypt-dev \ 
    libpng-dev \ 
    libxslt1-dev \ 
    libzip-dev \
    sudo

# Configure the gd library
RUN docker-php-ext-configure \
  gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/

# Install required PHP extensions
RUN docker-php-ext-install \
  dom \ 
  gd \ 
  intl \ 
  mbstring \ 
  pdo_mysql \ 
  xsl \ 
  zip \ 
  soap \ 
  bcmath

# tools
RUN apt-get install -y htop cron nano zip wget git-core gcc make
