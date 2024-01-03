# Use an official PHP runtime as a parent image
FROM php:8.2-fpm

# Set the working directory to /var/www
WORKDIR /var/www

# Install dependencies
RUN apt-get update && apt-get install -y \
    git \
    unzip \
    libzip-dev \
    libonig-dev \
    libxml2-dev

# Install PHP extensions
RUN docker-php-ext-install pdo_mysql mbstring zip exif pcntl bcmath

# Install Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Copy the composer.json and composer.lock files to the container
COPY composer.json composer.lock /var/www/

# Install application dependencies

# Copy the application code to the container
COPY . /var/www

# Set permissions
RUN chown -R www-data:www-data /var/www/storage /var/www/bootstrap/cache

# Create the storage link
RUN composer install
# Expose port 9000 and start php-fpm server
EXPOSE 8000
CMD php artisan key:generate
CMD php artisan serve --host=0.0.0.0
