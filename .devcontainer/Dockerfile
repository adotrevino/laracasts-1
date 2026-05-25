FROM php:8.3-cli

# Paquetes base
RUN apt-get update && apt-get install -y \
    gnupg \
    curl \
    unzip \
    git \
    && rm -rf /var/lib/apt/lists/*

# Repositorio oficial MySQL 8.0 para obtener mysql-client real (no MariaDB)
RUN curl -fsSL https://repo.mysql.com/RPM-GPG-KEY-mysql-2023 \
      | gpg --dearmor -o /usr/share/keyrings/mysql-archive-keyring.gpg \
    && echo "deb [arch=amd64 signed-by=/usr/share/keyrings/mysql-archive-keyring.gpg] https://repo.mysql.com/apt/debian bookworm mysql-8.0" \
      > /etc/apt/sources.list.d/mysql.list \
    && apt-get update \
    && apt-get install -y mysql-client \
    && rm -rf /var/lib/apt/lists/*

# Extensiones PHP - pdo_mysql usa mysqlnd (bundled), sin librerías externas
RUN docker-php-ext-install pdo pdo_mysql mysqli

# Composer
COPY --from=composer:2 /usr/bin/composer /usr/bin/composer

WORKDIR /var/www/html

EXPOSE 8080

CMD ["php", "-S", "0.0.0.0:8080", "-t", "/var/www/html/public"]
