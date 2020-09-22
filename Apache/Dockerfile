FROM php:7.0.33-apache
RUN apt-get update && apt-get install nano && apt-get install -y wget && apt-get install -y apt-utils && apt-get install debconf
RUN php -r "readfile('http://getcomposer.org/installer');" | php -- --install-dir=/usr/bin/ --filename=composer
COPY start.sh /start.sh
RUN chmod 0755 /start.sh
RUN docker-php-ext-install pdo pdo_mysql mysqli
RUN apt-get update -y && apt-get install -y libwebp-dev libjpeg62-turbo-dev libpng-dev libxpm-dev libfreetype6-dev
RUN apt-get -y update \
&& apt-get install -y libicu-dev zlib1g-dev libpng-dev libxslt-dev libmcrypt-dev sendmail \
&& docker-php-ext-configure intl \
&& docker-php-ext-install intl
RUN docker-php-ext-install mbstring
RUN docker-php-ext-install zip
RUN docker-php-ext-install xsl
RUN docker-php-ext-install mcrypt
RUN docker-php-ext-configure gd --with-gd --with-webp-dir --with-jpeg-dir \
    --with-png-dir --with-zlib-dir --with-xpm-dir --with-freetype-dir \
    --enable-gd-native-ttf
RUN docker-php-ext-install gd
COPY php.ini /usr/local/etc/php/conf.d/php.ini-production
RUN usermod -u 1000 www-data
RUN usermod -G staff www-data
CMD ["bash", "/start.sh"]
