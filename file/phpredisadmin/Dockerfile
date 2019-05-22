FROM erikdubbelboer/phpredisadmin:latest
LABEL maintainer="liumenglei0211@163.com"

# set timezome
ENV TZ=Asia/Shanghai
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone