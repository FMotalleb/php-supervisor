ARG PHP_VERSION

FROM ghcr.io/fmotalleb/php-supervisor:${PHP_VERSION} AS PHP

LABEL php.tag="${PHP_VERSION}"
LABEL webserver="nginx"

RUN apt-get -y update && apt-get install -y nginx && apt-get clean
COPY nginx/defaults.d /etc/supervisor/defaults.d
COPY nginx/nginx.d/* /etc/nginx/
COPY nginx/php-fpm/ /usr/local/etc/php-fpm.d/

# USER 1000

CMD [ "supervisord","-n","-c","/etc/supervisor/supervisord.conf" ]
