FROM ubuntu:22.04

RUN apt update && \
    apt install -y nginx vim git && \
    mkdir /var/www/mysite

EXPOSE 80

CMD ["nginx","-g","daemon off;"]
