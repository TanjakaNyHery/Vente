# Utiliser une image Symfony de PHP
FROM php:8.2-apache

# Exposer le port Apache
EXPOSE 80

# Définir le répertoire de travail
WORKDIR /var/www/html

# Installer les dépendances système nécessaires pour Symfony
RUN apt-get update && apt-get install -y \
    unzip \
    libicu-dev \
    libzip-dev \
    zip \
    && docker-php-ext-install intl pdo pdo_mysql zip

# Activer le module Apache mod_rewrite
RUN a2enmod rewrite

# Copier les fichiers de l'application dans le conteneur
COPY . .

# Installer les dépendances de Composer
# RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer
# RUN composer install --no-dev --optimize-autoloader

# Définir les autorisations correctes
RUN chown -R www-data:www-data /var/www/html

# Point d'entrée de l'application
CMD ["apache2-foreground"]
