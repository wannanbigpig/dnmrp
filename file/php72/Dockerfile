FROM php:7.2-fpm
# set timezome
ENV TZ=Asia/Shanghai
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

RUN apt-get update \
    # 手动安装依赖
    && apt-get install -y libmemcached-dev zlib1g-dev \
    # 安装需要的扩展
   && pecl install memcached-3.1.3 \
   # 启用扩展
   && docker-php-ext-enable memcached

WORKDIR /data

# Write Permission
RUN usermod -u 1000 www-data