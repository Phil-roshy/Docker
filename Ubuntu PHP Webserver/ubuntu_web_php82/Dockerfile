# Use the official Ubuntu base image
FROM ubuntu:20.04

# Prevent interactive prompts from opening during package installation
ENV DEBIAN_FRONTEND=noninteractive

# Update the package list and install necessary packages
RUN apt-get update && apt-get install -y \
    apache2 \
    curl \
    git \
    php \
    php-cli \
    php-curl \
    php-gd \
    php-intl \
    php-json \
    php-mbstring \
    php-mysql \
    php-soap \
    php-xml \
    php-xmlrpc \
    php-zip \
    php-bcmath \
    unzip \
    nodejs \
    npm \
    && apt-get clean

# Install Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Enable Apache mods and PHP
RUN a2enmod rewrite
RUN service apache2 restart

# Copy the Apache config file
COPY 000-default.conf /etc/apache2/sites-available/000-default.conf

# Expose port 80
EXPOSE 80

# Start Apache in the foreground
CMD ["apachectl", "-D", "FOREGROUND"]
