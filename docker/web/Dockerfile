FROM nginx:1.20-alpine

ENV TZ Asia/Tokyo

RUN chmod 755 -R /root

COPY ./docker/web/ecs/default.conf /etc/nginx/conf.d/default.conf
COPY ./docker/web/nginx.conf /etc/nginx/nginx.conf
COPY ./src/public /app/public/