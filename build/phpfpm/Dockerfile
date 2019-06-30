FROM php:7.1-fpm

# if this use for production
#RUN groupadd kenji
#RUN useradd -u 1000 -g kenji kenji

WORKDIR /var/www
RUN apt-get update && apt-get install -my wget gnupg

# タイムゾーンの変更
ENV TZ Asia/Tokyo
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

# 言語設定
RUN apt-get install -y locales
RUN locale-gen ja_JP.UTF-8
RUN apt-get install -y task-japanese
RUN locale-gen en_US.UTF-8
ENV LANG=C.UTF-8
ENV LANGUAGE=en_US:en


#extention
RUN apt-get update && apt-get install -y \
  libfreetype6-dev \
  libjpeg62-turbo-dev \
  libmcrypt-dev \
  libpng-dev \
  && docker-php-ext-install -j$(nproc) iconv mcrypt \
  && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
  && docker-php-ext-install -j$(nproc) gd

RUN apt-get update \
  && docker-php-ext-install mbstring pdo pdo_mysql mysqli bcmath posix bcmath posix zip

#composer install
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer


#nodejs
RUN curl -sL https://deb.nodesource.com/setup_10.x | bash - \
  && apt-get update \
  && apt-get install -y nodejs

RUN apt-get update && apt-get install -y sendmail

# if this use for production vps
#USER kenji
#RUN mkdir ~/.npm-global
#RUN npm config set prefix '~/.npm-global'
#RUN echo export PATH=~/.npm-global/bin:$PATH >> ~/.profile
#RUN ls -l ~/.profile
#RUN . ~/.profile # for debian, if use ubuntu or centos use comand [source ~/.profile]
