# Run commnad
php -S localhost:8888 -t public

# Reconstruir el Codespace (Command Palette → "Rebuild Container")
# O desde la terminal, levantar los servicios manualmente:
cd .devcontainer && docker compose up -d

# Conectarse a MySQL desde la terminal
mysql -h 127.0.0.1 -P 3306 -u myapp_user -psecret myapp

# Como root
mysql -h 127.0.0.1 -P 3306 -u root -prootpassword myapp -e "SHOW TABLES;"