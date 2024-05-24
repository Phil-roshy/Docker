# Use the official PHP 7.4 Apache image
FROM php:7.4-apache

# Install necessary PHP extensions and tools
RUN apt-get update && apt-get install -y \
    curl \
    git \
    unzip \
    libpng-dev \
    libzip-dev \
    && docker-php-ext-install mysqli pdo pdo_mysql gd bcmath zip \
    && apt-get clean

# Install Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Enable Apache mods
RUN a2enmod rewrite

# Copy the Apache virtual host configuration
COPY vhost.conf /etc/apache2/sites-available/000-default.conf

# Enable the virtual hosts configuration
RUN a2ensite 000-default.conf

# Expose port 80
EXPOSE 80

# Start Apache in the foreground
CMD ["apache2-foreground"]
