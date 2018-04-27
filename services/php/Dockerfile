FROM php:5.6-fpm
RUN sed -i 's/deb.debian.org/mirrors.aliyun.com/g' /etc/apt/sources.list \
  && apt-get update && apt-get install -y libpng12-dev libjpeg-dev libmcrypt-dev libfreetype6-dev \
  && rm -rf /var/lib/apt/lists/* \
  && docker-php-ext-install -j$(nproc) iconv mcrypt \
  && docker-php-ext-configure gd --with-png-dir=/usr/include/ --with-jpeg-dir=/usr/include/ --with-freetype-dir=/usr/include/ \
  && docker-php-ext-install -j$(nproc) gd \
  && docker-php-ext-install mysql mysqli pdo_mysql zip opcache bcmath
COPY ./config/php.ini /usr/local/etc/php/conf.d/php.ini
