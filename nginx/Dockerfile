FROM ubuntu:14.04
RUN apt-get update
RUN apt-get install nginx -y

RUN rm -rf /var/lib/apt/lists/* && \
echo "daemon off;" >> /etc/nginx/nginx.conf && \
chown -R www-data:www-data /var/lib/nginx

RUN mkdir -p /etc/nginx/ssl/publicfare
COPY org.publicfare.api.key /etc/nginx/ssl/publicfare/org.publicfare.api.key
COPY ssl-bundle.crt /etc/nginx/ssl/publicfare/ssl-bundle.crt
COPY search /etc/nginx/sites-available/

RUN ln -s /etc/nginx/sites-available/search \
/etc/nginx/sites-enabled/search && \ 
rm -f /etc/nginx/sites-enabled/default

COPY bootstrap-nginx.sh /usr/local/bin/
RUN chmod +x /usr/local/bin/bootstrap-nginx.sh

EXPOSE 80
EXPOSE 443

CMD ["nginx"]
