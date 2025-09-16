# MySQL 8.0 + phpMyAdmin en Docker

| Paso | Descripción | Comando |Resultado |
|------|-------------|---------|---------|
| 1 | Crear red Docker | ```docker network create mysql-network``` |<img width="886" height="194" alt="image" src="https://github.com/user-attachments/assets/ad87f830-8578-4a33-8998-7c051ba28854" />|
| 2 | Crear Volumen | ```docker volume create mysql-volume``` |<img width="886" height="174" alt="image" src="https://github.com/user-attachments/assets/9dcdbde4-aab8-43e8-a49f-456c57902745" />|
| 3 | Crear volumen para persistencia | ```docker run -d \ --name mysql-container \ --network mysql-network \ -e MYSQL_ROOT_PASSWORD=Admin1992@ \ -e MYSQL_DATABASE=epmmop \  -e MYSQL_USER=adminmdmq \ -e MYSQL_PASSWORD=Emmeth2906@ \ -v $(pwd)/mysql-volumen:/var/lib/mysql \ -v $(pwd)/mysql-init:/docker-entrypoint-initdb.d \ mysql:8.0 ``` |<img width="886" height="97" alt="image" src="https://github.com/user-attachments/assets/79a38fba-af0f-4fd2-b4a0-3eb06744996e" />|
| 4 | Crear contenedor de phpMyAdmin | ```docker run -d \   --name phpmyadmin-container \ --network mysql-network \    -e PMA_HOST=mysql-container \ -e PMA_PORT=3306 \   -p 8080:80 \``` |<img width="886" height="97" alt="image" src="https://github.com/user-attachments/assets/79a38fba-af0f-4fd2-b4a0-3eb06744996e" />|
| 5 | Acceso desde navegador | Abrir `http://localhost:8080/index.php?route=/` e ingresar con las credenciales configuradas en el contenedor MySQL |<img width="886" height="580" alt="image" src="https://github.com/user-attachments/assets/7dbb7dd2-8a42-4bc9-b649-8f24275792f5" /> <img width="886" height="553" alt="image" src="https://github.com/user-attachments/assets/e1dbae8b-4424-412e-a2ed-2978b0e81f7d" />
|

