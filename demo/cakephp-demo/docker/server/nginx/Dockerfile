FROM nginx:1.16-alpine

COPY ./docker/server/nginx/nginx.conf /etc/nginx/
COPY ./docker/server/nginx/default.conf /etc/nginx/conf.d/

COPY ./webroot /var/www/html/webroot
