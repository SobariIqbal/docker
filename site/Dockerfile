FROM nginx:latest

WORKDIR /usr/share/nginx/html
COPY ./nginx.conf /etc/nginx/templates/nginx.conf.template

EXPOSE 443
CMD ["nginx", "-g", "daemon off;"]