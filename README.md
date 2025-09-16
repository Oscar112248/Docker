# MySQL 8.0 + phpMyAdmin en Docker

| Paso | Descripción | Comando |Resultado |
|------|-------------|---------|---------|
| 1 | Crear red Docker | ```network create mysql-network``` |<img width="886" height="194" alt="image" src="https://github.com/user-attachments/assets/ad87f830-8578-4a33-8998-7c051ba28854" />|
| 2 | Crear volumen para persistencia | ```bash\ndocker volume create mysql-volume\n``` |
| 3 | Crear contenedor de MySQL (reemplaza placeholders) | ```bash\ndocker run -d \\\n  --name mysql-container \\\n  --network mysql-network \\\n  -e MYSQL_ROOT_PASSWORD=<ROOT_PASSWORD> \\\n  -e MYSQL_DATABASE=<DB_NAME> \\\n  -e MYSQL_USER=<DB_USER> \\\n  -e MYSQL_PASSWORD=<DB_PASSWORD> \\\n  -v $(pwd)/mysql-volumen:/var/lib/mysql \\\n  -v $(pwd)/mysql-init:/docker-entrypoint-initdb.d \\\n  mysql:8.0\n``` |
| 4 | Crear contenedor de phpMyAdmin | ```bash\ndocker run -d \\\n  --name phpmyadmin-container \\\n  --network mysql-network \\\n  -e PMA_HOST=mysql-container \\\n  -e PMA_PORT=3306 \\\n  -p 8080:80 \\\n  phpmyadmin:5.2.1\n``` |
| 5 | Acceso desde navegador | Abre `http://localhost:8080/index.php?route=/` e ingresa con las credenciales configuradas en el contenedor MySQL |
