## Memoria Prácticas

Asegurarse que el usuario __oracle__ es el que está ejecutando la shell con el comando `whoami`.

#### Iniciar servicios y BD
```sql
// Iniciar listener
      lsnrctl start

// Activar shell de SQL
      sqlplus /nolog

// Conectarse a la instancia de BD como administrador (En la SQLShell) con la contraseña ABD3oradba
      connec sys as sysdba

// Iniciar BD -> informa asignaciones de memoria para la instancia, indica que monta y abre la BD
      startup

// Para salir de la SQLshell 
      exit

// Iniciar Oracle Enterprise Manager(opcional)
      emctl start dbconsole
```

#### Detener BD y servicios
``` sql
// Detener Oracle Enterprise Manager(opcional)
    emctl stop dbconsole

// Cerrar y desmontar BD
      sqlplus /nolog

// En la SQLShell
      shutdown immediate
      exit

// Detener listener
      lsnrctl stop
```
