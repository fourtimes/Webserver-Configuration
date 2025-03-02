FROM ubuntu:latest

RUN apt update && apt install nginx -y

COPY index.html /var/www/fourtimes.ml/index.html

RUN rm -rf /etc/nginx/sites-enabled/default

COPY fourtimes.ml.conf /etc/nginx/sites-enabled/fourtimes.ml.conf

RUN ln -sf /dev/stdout /var/log/nginx/fourtimes.ml.access.log \ 
        && ln -sf /dev/stderr /var/log/nginx/fourtimes.ml.error.log

CMD ["nginx", "-g", "daemon off;"]