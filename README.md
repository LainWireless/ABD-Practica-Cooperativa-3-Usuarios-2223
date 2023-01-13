# ABD Práctica Cooperativa 3: Usuarios 22/23
## PRÁCTICA TEMA 3: USUARIOS

### Esta práctica ha sido realizada por Alfonso, Felipe e Iván.

## Parte Individual:

## Alumno 1 - Felipe (ORACLE):

### 1. Crea un rol ROLPRACTICA1 con los privilegios necesarios para conectarse a la base de datos, crear tablas y vistas e insertar datos en la tabla EMP de SCOTT.

### 2. Crea un usuario USRPRACTICA1 con el tablespace USERS por defecto y averigua que cuota se le ha asignado por defecto en el mismo. Sustitúyela por una cuota de 1M.

### 3. Modifica el usuario USRPRACTICA1 para que tenga cuota 0 en el tablespace SYSTEM.

### 4. Concede a USRPRACTICA1 el ROLPRACTICA1.

### 5. Concede a USRPRACTICA1 el privilegio de crear tablas e insertar datos en el esquema de cualquier usuario. Prueba el privilegio. Comprueba si puede modificar la estructura o eliminar las tablas creadas.

### 6. Concede a USRPRACTICA1 el privilegio de leer la tabla DEPT de SCOTT con la posibilidad de que lo pase a su vez a terceros usuarios.

### 7. Comprueba que USRPRACTICA1 puede realizar todas las operaciones previstas en el rol.

### 8. Quita a USRPRACTICA1 el privilegio de crear vistas. Comprueba que ya no puede hacerlo.

### 9. Crea un perfil NOPARESDECURRAR que limita a dos el número de minutos de inactividad permitidos en una sesión.

### 10. Activa el uso de perfiles en ORACLE.

### 11. Asigna el perfil creado a USRPRACTICA1 y comprueba su correcto funcionamiento.

### 12. Crea un perfil CONTRASEÑASEGURA especificando que la contraseña caduca mensualmente y sólo se permiten tres intentos fallidos para acceder a la cuenta. En caso de superarse, la cuenta debe quedar bloqueada indefinidamente.

### 13. Asigna el perfil creado a USRPRACTICA1 y comprueba su funcionamiento. Desbloquea posteriormente al usuario.

### 14. Consulta qué usuarios existen en tu base de datos.

### 15. Elige un usuario concreto y consulta qué cuota tiene sobre cada uno de los tablespaces.

### 16. Elige un usuario concreto y muestra qué privilegios de sistema tiene asignados.

### 17. Elige un usuario concreto y muestra qué privilegios sobre objetos tiene asignados.

### 18. Consulta qué roles existen en tu base de datos.

### 19. Elige un rol concreto y consulta qué usuarios lo tienen asignado.

### 20. Elige un rol concreto y averigua si está compuesto por otros roles o no.

### 21. Consulta qué perfiles existen en tu base de datos.

### 22. Elige un perfil y consulta qué límites se establecen en el mismo.

### 23. Muestra los nombres de los usuarios que tienen limitado el número de sesiones concurrentes.

### 24. Realiza un procedimiento que reciba un nombre de usuario y un privilegio de sistema y nos muestre el mensaje 'SI, DIRECTO' si el usuario tiene ese privilegio concedido directamente, 'SI, POR ROL' si el usuario tiene ese privilegio en alguno de los roles que tiene concedidos y un 'NO' si el usuario no tiene dicho privilegio.

### 25. Realiza un procedimiento llamado MostrarNumSesiones que reciba un nombre de usuario y muestre el número de sesiones concurrentes que puede tener abiertas como máximo y las que tiene abiertas realmente.


## Alumno 2 - Iván (Postgres y ORACLE):

### Postgres:

1) Averigua que privilegios de sistema hay en Postgres y como se asignan a un usuario.

2) Averigua cual es la forma de asignar y revocar privilegios sobre una tabla concreta en Postgres.

3) Averigua si existe el concepto de rol en Postgres y señala las diferencias con los roles de ORACLE.

4) Averigua si existe el concepto de perfil como conjunto de límites sobre el uso de recursos o sobre la contraseña en Postgres y señala las diferencias con los perfiles de ORACLE.

5) Realiza consultas al diccionario de datos de Postgres para averiguar todos los privilegios que tiene un usuario concreto.

6) Realiza consultas al diccionario de datos en Postgres para averiguar qué usuarios pueden consultar una tabla concreta.

### ORACLE:

7) Realiza una función de verificación de contraseñas que compruebe que la contraseña difiere en más de tres caracteres de la anterior y que la longitud de la misma es diferente de la anterior. Asígnala al perfil CONTRASEÑASEGURA. Comprueba que funciona correctamente.
       
8) Realiza un procedimiento llamado MostrarPrivilegiosdelRol que reciba el nombre de un rol y muestre los privilegios de sistema y los privilegios sobre objetos que lo componen.

## Alumno 3 - Alfonso (MySQL y ORACLE):

### MySQL:

1. Averigua que privilegios de sistema hay en MySQL y como se asignan a un usuario.
       
2. Averigua cual es la forma de asignar y revocar privilegios sobre una tabla concreta en MySQL.
       
3. Averigua si existe el concepto de rol en MySQL y señala las diferencias con los roles de ORACLE.
       
4. Averigua si existe el concepto de perfil como conjunto de límites sobre el uso de recursos o sobre la contraseña en MySQL y señala las diferencias con los perfiles de ORACLE.

5. Realiza consultas al diccionario de datos de MySQL para averiguar todos los privilegios que tiene un usuario concreto.

6. Realiza consultas al diccionario de datos en MySQL para averiguar qué usuarios pueden consultar una tabla concreta.


### ORACLE:
       
1. Realiza un procedimiento llamado PermisosdeAsobreB que reciba dos nombres de usuario y muestre los permisos que tiene el primero de ellos sobre objetos del segundo.

2. Realiza un procedimiento llamado MostrarInfoPerfil que reciba el nombre de un perfil y muestre su composición y los usuarios que lo tienen asignado.


## Parte Grupal:

## Alumno 4 (MongoDB y ORACLE):

### MongoDB:

1. Averigua si existe la posibilidad en MongoDB de limitar el acceso de un usuario a los datos de una colección determinada.
       
2. Averigua si en MongoDB existe el concepto de privilegio del sistema y muestra las diferencias más importantes con ORACLE.

3. Explica los roles por defecto que incorpora MongoDB y como se asignan a los usuarios.

4. Explica como puede consultarse el diccionario de datos de MongoDB para saber que roles han sido concedidos a un usuario y qué privilegios incluyen.

### ORACLE:

1. Realiza un procedimiento llamado MostrarObjetosAccesibles que reciba un nombre de usuario y muestre todos los objetos a los que tiene acceso.

2. Realiza un procedimiento que reciba un nombre de usuario, un privilegio y un objeto y nos muestre el mensaje 'SI, DIRECTO' si el usuario tiene ese privilegio sobre objeto concedido directamente, 'SI, POR ROL' si el usuario lo tiene en alguno de los roles que tiene concedidos y un 'NO' si el usuario no tiene dicho privilegio.

## CASO PRÁCTICO 1:

1. (ORACLE, Postgres, MySQL) Crea un usuario llamado Becario y, sin usar los roles de ORACLE, dale los siguientes privilegios: (1,5 puntos)

    • Conectarse a la base de datos.
    
    • Modificar el número de errores en la introducción de la contraseña de cualquier usuario.
    
    • Modificar índices en cualquier esquema (este privilegio podrá pasarlo a quien quiera)
    
    • Insertar filas en scott.emp (este privilegio podrá pasarlo a quien quiera)
    
    • Crear objetos en cualquier tablespace.
    
    • Gestión completa de usuarios, privilegios y roles.

2. (ORACLE, Postgres, MySQL) Escribe una consulta que obtenga un script para quitar el privilegio de borrar registros en alguna tabla de SCOTT a los usuarios que lo tengan.

3. (ORACLE) Crea un tablespace TS2 con tamaño de extensión de 256K. Realiza una consulta que genere un script que asigne ese tablespace como tablespace por defecto a los usuarios que no tienen privilegios para consultar ninguna tabla de SCOTT, excepto a SYSTEM.

4. (ORACLE, Postgres) Realiza un procedimiento que reciba un nombre de usuario y nos muestre cuántas sesiones tiene abiertas en este momento. Además, para cada una de dichas sesiones nos mostrará la hora de comienzo y el nombre de la máquina, sistema operativo y programa desde el que fue abierta.

5. (ORACLE) Realiza un procedimiento que muestre los usuarios que pueden conceder privilegios de sistema a otros usuarios y cuales son dichos privilegios.


## EJERCICIO GRUPAL 3:

Elaboración de un vídeo grupal resumiendo las diferencias de concepto y en la gestión de usuarios, permisos de sistema y permisos sobre objetos, roles y perfiles entre los cuatro SGBDs estudiados. Cada miembro del grupo hablará de uno de los siguientes temas:

a) Usuarios y permisos sobre objetos.

b) Permisos de sistema.

c) Roles.

d) Perfiles.
