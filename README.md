# Despliegue Docker: MySQL 8.0 + phpMyAdmin

> Stack mínimo para levantar **MySQL 8.0** y administrarlo con **phpMyAdmin**.

---

## 1) Resumen

| Ítem | Detalle |
|---|---|
| Objetivo | Desplegar MySQL 8.0 y phpMyAdmin en contenedores Docker, conectados por red. |
| Resultado | Acceso a phpMyAdmin vía navegador para gestionar la BD. |
| Componentes | `mysql:8.0`, `phpmyadmin:5.2.1` |

---

## 2) Requisitos

| Requisito | Versión/Nota |
|---|---|
| Docker Engine | 24+ (recomendado) |
| Docker Compose | v2+ |
| SO Host | Linux/Mac/Windows |
| Puertos libres | `3306`, `8080` |

---

## 3) Estructura del proyecto

| Ruta | Descripción |
|---|---|
| `docker-compose.yml` | Orquesta los servicios y la red. |
| `.env` | Variables de entorno (NO subirlo a Git). |
| `.env.example` | Plantilla de variables de entorno. |
| `mysql-init/01-init.sql` | Scripts de inicialización (opcional). |
| `README.md` | Este informe. |

---

## 4) Variables de entorno

| Variable | Ejemplo | Descripción |
|---|---|---|
| `MYSQL_ROOT_PASSWORD` | `S3cret!` | Clave del usuario root. |
| `MYSQL_DATABASE` | `app_db` | BD inicial a crear. |
| `MYSQL_USER` | `app_user` | Usuario app. |
| `MYSQL_PASSWORD` | `AppUserP@ss` | Clave del usuario app. |
| `PMA_PORT` | `3306` | Puerto del servicio MySQL. |
| `PMA_HOST` | `mysql-container` | Hostname del contenedor MySQL. |

> Crea tu `.env` a partir de `.env.example`.

---

## 5) Despliegue

| Acción | Comando |
|---|---|
| Crear red/volumen (auto en Compose) | _No requiere paso manual_ |
| Levantar stack | `docker compose up -d` |
| Ver estado | `docker compose ps` |
| Ver logs | `docker compose logs -f mysql` |
| Apagar | `docker compose down` |
| Borrar datos (⚠️) | `docker volume rm mysql-volume` |

Acceso: abre `http://localhost:8080/` y autentícate con las credenciales definidas en `.env`.

---

## 6) Servicios

| Servicio | Imagen | Puerto | Red | Volumen |
|---|---|---:|---|---|
| `mysql` | `mysql:8.0` | 3306 | `mysql-network` | `mysql-volume:/var/lib/mysql` |
| `phpmyadmin` | `phpmyadmin:5.2.1` | 8080→80 | `mysql-network` | — |

---

## 7) Seguridad y buenas prácticas

| Recomendación | Detalle |
|---|---|
| `.env` privado | Añádelo a `.gitignore`. No subas secretos. |
| Usuarios mínimos | Usa `MYSQL_USER`/`MYSQL_PASSWORD` y evita trabajar con `root`. |
| Copias de seguridad | Programa dumps o snapshots del volumen. |
| Red interna | Mantén ambos servicios en la misma red de Docker. |

---

## 8) Troubleshooting

| Síntoma | Posible causa | Solución |
|---|---|---|
| phpMyAdmin no conecta | Host/puerto mal configurados | Verifica `PMA_HOST=PMA_PORT` y que `mysql` esté “healthy”. |
| Datos no persisten | Volumen no montado | Confirma `mysql-volume:/var/lib/mysql`. |
| `Access denied` | Credenciales incorrectas | Revisa `.env`, reinicia el stack. |
| Puerto ocupado | 8080/3306 en uso | Cambia mapeo de puertos en Compose. |

---

## 9) Créditos/Licencia

| Ítem | Detalle |
|---|---|
| Imágenes | MySQL y phpMyAdmin (Docker Hub oficiales) |
| Licencia | MIT (ajústala según tu proyecto) |
