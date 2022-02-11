# https://hub.docker.com/_/nginx

FROM ghcr.io/linianhui/nginx:1.21

ARG CONFIG_FILE

COPY ${CONFIG_FILE} /etc/nginx/nginx.conf

EXPOSE 80