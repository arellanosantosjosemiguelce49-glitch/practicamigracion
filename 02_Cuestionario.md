<p align="center">
  <img src="imagenes/logo1.png" width="140">
  <img src="imagenes/logo2.png" width="140">
</p>

<h1 align="center">Instituto Tecnológico Nacional de México</h1>

<h2 align="center">Práctica migración - Cuestionario</h2>

<p align="center">
<b>Alumno:</b><br>
Arellano Santos Jose Miguel<br><br>
<b>Materia:</b><br>
Administración de base de datos<br><br>
<b>Profesor:</b><br>
Diego Alberto Bollas Paredes
</p>

---

## Cuestionario

### 1. ¿Por qué se hace un respaldo antes de migrar?

Porque durante la migración puede salir algo mal (un error al importar, datos que se pierden o se dañan). Si ya tengo un respaldo, puedo regresar la base a como estaba y no pierdo información. Por eso en la práctica hice primero el archivo `respaldo_previo.sql`.

### 2. ¿Para qué sirve la opción `--single-transaction`?

Sirve para que el respaldo salga completo y sin mezclar datos, aunque alguien más esté usando la base mientras se exporta. Hace que el respaldo se tome como una "foto" de un solo momento y sin bloquear las tablas. Funciona con tablas InnoDB, que es el tipo que usé.

### 3. ¿Qué diferencia hay entre exportar con y sin `--databases`?

- **Con `--databases`:** el archivo guarda también las instrucciones para crear la base y entrar a ella. Al importarlo se vuelve a crear con el mismo nombre que tenía (`biblioteca`).
- **Sin `--databases`:** el archivo trae solo las tablas y los datos. Entonces lo puedo importar en la base que yo quiera, por ejemplo `biblioteca_nueva`, como hice en la práctica.

### 4. ¿Qué dos pruebas permiten confirmar que los datos migraron sin pérdidas?

1. **Contar los registros** de cada tabla en el origen y en el destino (`COUNT(*)`). En mi caso salieron 3 autores y 4 libros en los dos.
2. **Comparar el checksum** de las tablas (`CHECKSUM TABLE`). Los números salieron iguales en las dos bases (1184143278 y 2367132664).

### 5. Si el destino estuviera en otro servidor, ¿qué paso adicional sería necesario?

Tendría que **copiar el archivo `.sql` al otro servidor**, por ejemplo con el comando `scp`, y ya allá crear la base e importarlo. También tendría que revisar que los dos servidores se puedan comunicar y que en el nuevo existan los usuarios y permisos necesarios.
