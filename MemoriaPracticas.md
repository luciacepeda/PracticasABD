# Memoria Prácticas

##  1. Tipos de Sentencias SQL  

### DML (Data Manipulation Language) - Manipulación de Datos  
Se usa para consultar, insertar, actualizar y eliminar datos en una base de datos.  

#### Principales Sentencias DML:  
- `SELECT` → Recupera datos de una tabla.  
- `INSERT` → Inserta nuevos registros.  
- `UPDATE` → Modifica registros existentes.  
- `DELETE` → Elimina registros de una tabla.  

####  Ejemplos:  
```sql
-- Seleccionar datos
SELECT nombre, edad FROM usuarios WHERE edad > 25;

-- Insertar un nuevo usuario
INSERT INTO usuarios (id, nombre, edad) VALUES (1, 'Juan', 30);

-- Actualizar la edad de un usuario
UPDATE usuarios SET edad = 35 WHERE nombre = 'Juan';

-- Eliminar usuarios menores de 18 años
DELETE FROM usuarios WHERE edad < 18;
```
---

### DDL (Data Definition Language) - Definición de Datos  
Se usa para crear y modificar la estructura de la base de datos.  

#### Principales Sentencias DDL:  
- `CREATE` → Crea tablas, índices y bases de datos.  
- `ALTER` → Modifica la estructura de una tabla.  
- `DROP` → Elimina tablas, vistas o bases de datos.  
- `TRUNCATE` → Borra todos los datos de una tabla sin eliminar su estructura.  

#### Ejemplos:  
```sql
-- Crear una tabla
CREATE TABLE usuarios (
    id INT PRIMARY KEY,
    nombre VARCHAR(50),
    edad INT
);

-- Agregar una nueva columna a la tabla
ALTER TABLE usuarios ADD email VARCHAR(100);

-- Eliminar la tabla de usuarios
DROP TABLE usuarios;

-- Vaciar la tabla usuarios sin eliminar su estructura
TRUNCATE TABLE usuarios;
```
---

### DCL (Data Control Language) - Control de Accesos y Permisos  
Se usa para gestionar los permisos y la seguridad en la base de datos.  

#### Principales Sentencias DCL:  
- `GRANT` → Otorga permisos a usuarios.  
- `REVOKE` → Revoca permisos previamente concedidos.  

#### Ejemplos:  
```sql
-- Otorgar permisos de lectura y escritura a un usuario
GRANT SELECT, INSERT ON usuarios TO maria;

-- Revocar permisos de inserción a un usuario
REVOKE INSERT ON usuarios FROM maria;
```
---

### TCL (Transaction Control Language) - Control de Transacciones  
Se usa para manejar transacciones en la base de datos y garantizar la integridad de los datos.  

#### Principales Sentencias TCL:  
- `COMMIT` → Guarda los cambios de una transacción.  
- `ROLLBACK` → Revierte los cambios si ocurre un error.  
- `SAVEPOINT` → Crea puntos intermedios dentro de una transacción.  

#### Ejemplos:  
```sql
-- Iniciar una transacción
BEGIN;

-- Modificar datos en la tabla usuarios
UPDATE usuarios SET edad = 40 WHERE nombre = 'Ana';

-- Guardar los cambios
COMMIT;

-- Iniciar otra transacción
BEGIN;

-- Intentar modificar datos
UPDATE usuarios SET edad = 50 WHERE nombre = 'Carlos';

-- Revertir cambios si hay un error
ROLLBACK;

-- Crear un punto de guardado
SAVEPOINT sp1;

-- Hacer cambios y revertir hasta el SAVEPOINT
UPDATE usuarios SET edad = 45 WHERE nombre = 'Laura';
ROLLBACK TO sp1;
```
---

### Resumen General

| **Tipo** | **Propósito** | **Ejemplo de Sentencias** | **Afecta estructura** | **Se puede deshacer (`ROLLBACK`)?** | **Impacto inmediato** |
|----------|-------------|------------------|----------------|----------------------|------------------|
| **DML** | Manipulación de datos | `SELECT`, `INSERT`, `UPDATE`, `DELETE` | ❌ No | ✅ Sí | 🚫 No (hasta `COMMIT`) |
| **DDL** | Definición de estructuras | `CREATE`, `ALTER`, `DROP`, `TRUNCATE` | ✅ Sí | ❌ No | ✅ Sí |
| **DCL** | Gestión de permisos | `GRANT`, `REVOKE` | ❌ No | ❌ No | ✅ Sí |
| **TCL** | Control de transacciones | `COMMIT`, `ROLLBACK`, `SAVEPOINT` | ❌ No | ✅ Sí | 🚫 No (hasta `COMMIT`) |

---

## 2. Cheatsheet inicio y cierre DB

Asegurarse que el usuario _oracle_ es el que está ejecutando la shell con el comando `whoami`.

### Iniciar servicios y BD
```sql
--- Iniciar listener
lsnrctl start

--- Activar shell de SQL
sqlplus /nolog

--- Conectarse a la instancia de BD como administrador (En la SQLShell) con la contraseña ABD3oradba
connect sys as sysdba

--- Iniciar BD -> informa asignaciones de memoria para la instancia, indica que monta y abre la BD
startup

--- Para salir de la SQLshell 
exit

--- Iniciar Oracle Enterprise Manager(opcional)
emctl start dbconsole
```

### Detener BD y servicios
``` sql
--- Detener Oracle Enterprise Manager(opcional)
emctl stop dbconsole

--- Abrimos shell de SQLPlus con la contraseña
sqlplus sys as sysdba

--- En la SQLShell derribamos BD -> informa que cierra y desmonta BD, derriba instancia
shutdown immediate
exit

--- Derribar listener
lsnrctl stop
```

---
