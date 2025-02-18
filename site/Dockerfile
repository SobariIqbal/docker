FROM nginx:latest

WORKDIR /usr/share/nginx/html
COPY ./nginx.conf /etc/nginx/templates/nginx.conf.template

EXPOSE 443
CMD ["nginx", "-g", "daemon off;"]

FROM nginx:latest

COPY nginx-selfsigned.crt /etc/nginx/certs/nginx-selfsigned.crt
COPY nginx-selfsigned.key /etc/nginx/certs/nginx-selfsigned.key

COPY nginx.conf /etc/nginx/nginx.conf