FROM php:8.1.10-fpm-bullseye

RUN apt-get update && apt-get install -y \
  curl bash zip git git-core unzip \
  && curl -sL https://deb.nodesource.com/setup_17.x | bash - \
  && apt-get install -y \
  nodejs \
  libfreetype6-dev \
  libjpeg62-turbo-dev \
  libpng-dev \
  libpq-dev \
  && docker-php-ext-configure gd --with-freetype --with-jpeg \
  && docker-php-ext-install -j$(nproc) gd \
  && docker-php-ext-configure pgsql -with-pgsql=/usr/local/pgsql \
  && docker-php-ext-install pdo pdo_pgsql pgsql \
  && php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" \
  && php composer-setup.php  --install-dir=/root \
  && php -r "unlink('composer-setup.php');" \
  && mv /root/composer.phar /usr/bin/composer \
  && apt-get clean && rm -rf /var/lib/apt/lists \
  && rm -rf /tmp/* /var/tmp/*
  #&& chown -R www-data:www-data /var/www/html

WORKDIR /var/www/html

#USER www-data

COPY ../../src/composer.json /var/www/html
COPY ../../src/composer.lock /var/www/html

# Install composer
RUN composer install --no-cache --no-scripts --no-interaction --no-plugins --no-autoloader

# Copy php settings
#COPY ../docker/php  /etc/php/conf.d

COPY  ../../src .

EXPOSE 9000