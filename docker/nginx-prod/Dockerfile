FROM nginx:1.9

RUN apt-get update && apt-get install -y nano

ADD app/public /app/public
COPY ./docker/nginx-prod/vhost.conf /etc/nginx/conf.d/default.conf