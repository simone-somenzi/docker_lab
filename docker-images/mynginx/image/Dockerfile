FROM nginx:1.26.0-otel

LABEL authors="AiFACTORY"

ARG NGINX_PATH=./usr/share/nginx/html/

ENV ENV=test

COPY . $NGINX_PATH
