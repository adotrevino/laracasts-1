# Run commnad
php -S 0.0.0.0:8880 -t public

# Reconstruir el Codespace (Command Palette → "Rebuild Container")
# O desde la terminal, levantar los servicios manualmente:
cd .devcontainer && docker compose up -d

# Conectarse a MySQL desde la terminal
# MySQL corre en el contenedor "db" (no en localhost)
mysql -h db -P 3306 -u myapp_user -psecret myapp --skip-ssl

# Como root
mysql -h db -P 3306 -u root -prootpassword myapp --skip-ssl -e "SHOW TABLES;"