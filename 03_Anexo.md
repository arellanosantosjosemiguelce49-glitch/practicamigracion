<p align="center">
  <img src="imagenes/logo1.png" width="140">
  <img src="imagenes/logo2.png" width="140">
</p>

<h1 align="center">Instituto Tecnológico Nacional de México</h1>

<h2 align="center">Práctica migración - Anexo</h2>

<p align="center">
<b>Alumno:</b><br>
Arellano Santos Jose Miguel<br><br>
<b>Materia:</b><br>
Administración de base de datos<br><br>
<b>Profesor:</b><br>
Diego Alberto Bollas Paredes
</p>

---

## Anexo: términos y herramientas que investigué

### Herramientas

| Herramienta | Qué es |
|---|---|
| `mysqldump` / `mariadb-dump` | Programa que saca un respaldo de una base de datos en un archivo `.sql` con todas las instrucciones para volver a crearla. `mariadb-dump` es el nombre nuevo (desde la versión 10.5); en mi versión 10.3.39 se llama `mysqldump`. |
| `mariadb` (cliente) | El programa con el que me conecto a MariaDB desde la terminal para escribir consultas. En versiones viejas se llama `mysql`. |
| `mariadb-backup` | Herramienta para hacer respaldos copiando los archivos de la base directamente. Es más rápida para bases muy grandes. |
| `scp` | Comando para copiar archivos de una computadora a otra de forma segura. Sirve para llevar el `.sql` a otro servidor. |
| Git y GitHub | Git guarda las versiones de mis archivos y GitHub es la página donde los subo para compartirlos (ahí entrego la práctica). |
| Markdown (`.md`) | Forma sencilla de escribir documentos con formato (títulos, listas, código, imágenes) usando texto normal. |

### Opciones de los comandos

| Opción | Qué hace |
|---|---|
| `--databases` | Agrega al respaldo la creación de la base y su nombre, para restaurarla igual. |
| `--single-transaction` | Toma el respaldo como una "foto" del momento, sin bloquear las tablas (InnoDB). |
| `--routines` | Incluye procedimientos y funciones guardados en la base. |
| `--triggers` | Incluye los triggers (acciones que se ejecutan solas al insertar, modificar o borrar). |
| `--events` | Incluye los eventos programados. |
| `-u` y `-p` | `-u` indica el usuario y `-p` pide la contraseña. |
| `-e` | Ejecuta una consulta directamente desde la terminal, sin entrar a MariaDB. |
| `\G` | Muestra el resultado en forma vertical, para leerlo mejor (lo usé con `SHOW CREATE TABLE`). |
| `>` | Guarda lo que sale de un comando en un archivo (así creé el `.sql`). |
| `<` | Le pasa un archivo a un comando (así importé el `.sql`). |

### Términos de bases de datos

| Término | Qué significa |
|---|---|
| **Migración** | Pasar una base de datos de un lugar a otro (otro servidor, versión o nombre) sin perder información. |
| **Respaldo** | Copia de seguridad de la base para poder recuperarla si algo falla. |
| **Llave foránea (`FOREIGN KEY`)** | Columna de una tabla que apunta a otra tabla. Evita que se guarden datos que no existen (por ejemplo, un libro con un autor que no existe). |
| **Vista (`VIEW`)** | Una consulta guardada con nombre que se usa como si fuera una tabla. |
| **`CHECKSUM TABLE`** | Instrucción que saca un número a partir del contenido de una tabla. Si dos tablas dan el mismo número, tienen el mismo contenido. |
| **`COUNT(*)`** | Cuenta cuántos registros tiene una tabla. |
| **InnoDB** | Tipo de motor que usan las tablas en MariaDB; permite transacciones y llaves foráneas. |
| **Transacción** | Grupo de operaciones que se hacen todas juntas o no se hace ninguna. |
| **Integridad de los datos** | Que la información esté completa y correcta, sin perder ni cambiar nada. |
| **Rollback** | Regresar las cosas a como estaban antes si algo sale mal. |
| **Trigger** | Acción automática que se ejecuta cuando se inserta, modifica o borra algo en una tabla. |
| **Evento** | Tarea programada dentro de la base que se ejecuta a cierta hora o cada cierto tiempo. |
| **`DEFINER`** | El usuario con cuyos permisos funciona una vista o rutina. Si ese usuario no existe en el destino, puede dar error al importar. |
| **Charset (`utf8mb4`)** | La forma en que se guardan los caracteres (acentos, ñ, etc.). Debe ser igual en origen y destino. |
