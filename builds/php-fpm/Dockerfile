FROM php:5.6-fpm

ADD php.ini /usr/local/etc/php/conf.d/

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

RUN apt-get update && apt-get install zip unzip wget git -y

RUN docker-php-ext-install pdo
RUN docker-php-ext-install pdo_mysql

RUN yes | pecl install xdebug
ADD xdebug.ini /usr/local/etc/php/conf.d/

RUN echo 'alias ll="ls -alF"' >> ~/.bashrc
RUN echo 'alias la="ls -A"' >> ~/.bashrc
RUN echo 'alias  l="ls -CF"' >> ~/.bashrc

RUN echo 'alias  dsu="php app/console doctrine:schema:update --dump-sql --force"' >> ~/.bashrc
RUN echo 'alias  dge="php app/console doctrine:generate:entity"' >> ~/.bashrc
RUN echo 'alias  dfl="php app/console doctrine:fixtures:load"' >> ~/.bashrc
RUN echo 'alias  gb="php app/console generate:bundle"' >> ~/.bashrc
RUN echo 'alias  dr="php app/console debug:router"' >> ~/.bashrc
RUN echo 'alias  ai="php app/console asset:install --symlink --relative"' >> ~/.bashrc
RUN echo 'alias  cc="rm -fr /app/app/cache/* && chmod -R 777 /app/app/cache"' >> ~/.bashrc
RUN echo 'alias  ccc="php /app/app/console cache:clear"' >> ~/.bashrc

RUN wget https://phar.phpunit.de/phpunit-5.7.phar
RUN chmod +x phpunit-5.7.phar
RUN mv phpunit-5.7.phar /usr/local/bin/phpunit

WORKDIR /app