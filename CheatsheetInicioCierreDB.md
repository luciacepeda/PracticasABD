## 2. Cheatsheet inicio y cierre DB

---
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
