# MySQL 8.0 + phpMyAdmin en Docker (Markdown listo para GitHub)

```bash
# 1) Red Docker
docker network create mysql-network

# 2) Volumen (persistencia)
docker volume create mysql-volume

# 3) Contenedor MySQL (sustituye los placeholders)
docker run -d \
  --name mysql-container \
  --network mysql-network \
  -e MYSQL_ROOT_PASSWORD=<ROOT_PASSWORD> \
  -e MYSQL_DATABASE=<DB_NAME> \
  -e MYSQL_USER=<DB_USER> \
  -e MYSQL_PASSWORD=<DB_PASSWORD> \
  -v $(pwd)/mysql-volumen:/var/lib/mysql \
  -v $(pwd)/mysql-init:/docker-entrypoint-initdb.d \
  mysql:8.0

# 4) Contenedor phpMyAdmin
docker run -d \
  --name phpmyadmin-container \
  --network mysql-network \
  -e PMA_HOST=mysql-container \
  -e PMA_PORT=3306 \
  -p 8080:80 \
  phpmyadmin:5.2.1
