FROM alpine

LABEL maintainer=jervain@126.com

RUN sed -i "s/dl-cdn.alpinelinux.org/mirrors.aliyun.com/g" /etc/repositories \
    && apk add --no-cache php php-fpm nginx \
    && sed -i 's/user = nobody/user = nginx/g' /etc/php7/php-fpm.d/www.conf \
    && sed -i 's/group = nobody/group = nginx/g' /etc/php7/php-fpm.d/www.conf \
    && mkdir -p /run/nginx \
    && ln -s /var/lib/nginx/html /app

WORKDIR /app

ADD default.conf /etc/nginx/conf.d/
ADD index.php /app/

EXPOSE 80

VOLUME /app

ENTRYPOINT php-fpm7 && nginx && tail -f /dev/null
