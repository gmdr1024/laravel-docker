FROM amazonlinux:2023

# Add vim, ps
RUN dnf install -y vim procps

# Add Apache
RUN dnf install -y httpd

# Add PHP & Composer
RUN dnf install -y php8.3 php8.3-mysqlnd
COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

# Make directory for php-fpm
RUN mkdir /run/php-fpm

# Add Node.js
COPY --from=node:20-slim /usr/local/bin /usr/local/bin
COPY --from=node:20-slim /usr/local/lib/node_modules /usr/local/lib/node_modules

# Change UID, GID
RUN usermod -u 1000 apache \
  && groupmod -g 1000 apache

COPY ./entrypoint.sh /
RUN chmod 755 /entrypoint.sh
ENTRYPOINT ["/entrypoint.sh"]
