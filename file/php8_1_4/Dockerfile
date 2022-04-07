FROM php:8.1.4-fpm
LABEL maintainer="liumenglei0211@163.com"


# 设置时区
ENV TZ=Asia/Shanghai
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

# 替换源
# COPY ./sources.list /etc/apt/sources.list.tmp
# RUN mv /etc/apt/sources.list /etc/apt/sources.list.bak \
#     && mv /etc/apt/sources.list.tmp /etc/apt/sources.list \
#     && rm -rf /etc/apt/sources.list.tmp

# 安装PHP扩展
RUN apt-get update && apt-get install -y \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libpng-dev \
        git \
        libsodium-dev \
        libzip-dev \
        libssl-dev \
		libxml2-dev \
    && docker-php-ext-configure gd --with-freetype --with-jpeg \
    && docker-php-ext-install -j$(nproc) gd \
    && docker-php-ext-install zip \
    && docker-php-ext-install pdo_mysql \
    && docker-php-ext-install opcache \
    && docker-php-ext-install mysqli \
    && docker-php-ext-install sodium \
    && rm -r /var/lib/apt/lists/*



# 复制扩展文件
# COPY ./ext /home/

# pecl 安装 扩展
# RUN pecl install /home/memcached-3.1.3.tgz && docker-php-ext-enable memcached \
#     && pecl install /home/redis-4.3.0.tgz && docker-php-ext-enable redis \
#     && pecl install /home/xdebug-2.7.2.tgz && docker-php-ext-enable xdebug \
#     && pecl install /home/swoole-4.3.3.tgz && docker-php-ext-enable swoole
#     
RUN pecl install redis && docker-php-ext-enable redis 

#安装php composer 如果无法安装可以下面的hash无法对应 到网站获取最新的hash值 https://getcomposer.org/download/
RUN php -r "copy('https://install.phpcomposer.com/installer', 'composer-setup.php');" \
    && php composer-setup.php \
    && php -r "unlink('composer-setup.php');" \
    && mv composer.phar /usr/local/bin/composer

# RUN rm -f /home/redis.tgz \
#     && rm -f /home/xdebug.tgz \
#     && rm -f /home/swoole.tgz \
#     && rm -f /home/memcached.tgz 

WORKDIR /data

# Write Permission
RUN usermod -u 1000 www-data
