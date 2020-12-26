FROM nginx:latest

ARG USER=admin
ARG PASSWD=password

RUN apt-get update -y \
    && apt-get install -y nginx-extras libnginx-mod-http-dav-ext

# Create data dir
RUN mkdir -p /var/www/data
RUN chown -R nginx:nginx /var/www/data

# Create temporary dir
RUN mkdir -p /tmp/data
RUN chmod 777 /tmp/data
RUN chown -R nginx:nginx /tmp/data

# Config
COPY webdav.conf /etc/nginx/conf.d/default.conf

# User passwd
RUN echo "${USER}:$(openssl passwd -apr1 $PASSWD)" > /etc/nginx/conf.d/.htpasswd
