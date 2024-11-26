# syntax=docker/dockerfile:1

FROM --platform=$BUILDPLATFORM drupalci/php-8.4-ubuntu-apache:production

WORKDIR /var/www/html

ARG DOMAIN=domain.local

ENV DOMAIN=$DOMAIN

RUN sed -i '/RewriteEngine On/d' /etc/apache2/sites-available/drupal.conf && \
    sed -i '/<VirtualHost \*:80>/a \RewriteEngine On\nRewriteCond %{HTTP_HOST} !^${DOMAIN}$ [NC]\nRewriteRule ^(.*)$ - [F,L]\nServerName ${DOMAIN}\nServerAlias ${DOMAIN}' /etc/apache2/sites-available/drupal.conf