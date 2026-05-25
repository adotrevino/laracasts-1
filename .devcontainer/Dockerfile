FROM php:8.3-cli

# Paquetes base + cliente MySQL compatible (funciona con MySQL 8.0)
# Para el cliente MySQL nativo usa: docker compose exec db mysql ...
RUN apt-get update && apt-get install -y \
    curl \
    unzip \
    git \
    default-mysql-client \
    && rm -rf /var/lib/apt/lists/*

# Extensiones PHP - pdo_mysql usa mysqlnd (bundled), sin librerías externas
RUN docker-php-ext-install pdo pdo_mysql mysqli

# Composer
COPY --from=composer:2 /usr/bin/composer /usr/bin/composer

WORKDIR /var/www/html

EXPOSE 8080

CMD ["php", "-S", "0.0.0.0:8080", "-t", "/var/www/html/public"]
