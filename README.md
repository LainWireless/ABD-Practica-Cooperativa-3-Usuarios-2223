# ABD Práctica Cooperativa 3: Usuarios 22/23
## PRÁCTICA TEMA 3: USUARIOS

### Esta práctica ha sido realizada por Alfonso, Felipe e Iván.


   - [Parte Individual:](#parte-individual)
  - [Alumno 1 - Felipe (ORACLE):](#alumno-1---felipe-oracle)
      - [1. Crea un rol ROLPRACTICA1 con los privilegios necesarios para conectarse a la base de datos, crear tablas y vistas e insertar datos en la tabla EMP de SCOTT.](#1-crea-un-rol-rolpractica1-con-los-privilegios-necesarios-para-conectarse-a-la-base-de-datos-crear-tablas-y-vistas-e-insertar-datos-en-la-tabla-emp-de-scott)
      - [2. Crea un usuario USRPRACTICA1 con el tablespace USERS por defecto y averigua que cuota se le ha asignado por defecto en el mismo. Sustitúyela por una cuota de 1M.](#2-crea-un-usuario-usrpractica1-con-el-tablespace-users-por-defecto-y-averigua-que-cuota-se-le-ha-asignado-por-defecto-en-el-mismo-sustitúyela-por-una-cuota-de-1m)
      - [3. Modifica el usuario USRPRACTICA1 para que tenga cuota 0 en el tablespace SYSTEM.](#3-modifica-el-usuario-usrpractica1-para-que-tenga-cuota-0-en-el-tablespace-system)
      - [4. Concede a USRPRACTICA1 el ROLPRACTICA1.](#4-concede-a-usrpractica1-el-rolpractica1)
      - [5. Concede a USRPRACTICA1 el privilegio de crear tablas e insertar datos en el esquema de cualquier usuario. Prueba el privilegio. Comprueba si puede modificar la estructura o eliminar las tablas creadas.](#5-concede-a-usrpractica1-el-privilegio-de-crear-tablas-e-insertar-datos-en-el-esquema-de-cualquier-usuario-prueba-el-privilegio-comprueba-si-puede-modificar-la-estructura-o-eliminar-las-tablas-creadas)
      - [6. Concede a USRPRACTICA1 el privilegio de leer la tabla DEPT de SCOTT con la posibilidad de que lo pase a su vez a terceros usuarios.](#6-concede-a-usrpractica1-el-privilegio-de-leer-la-tabla-dept-de-scott-con-la-posibilidad-de-que-lo-pase-a-su-vez-a-terceros-usuarios)
      - [7. Comprueba que USRPRACTICA1 puede realizar todas las operaciones previstas en el rol.](#7-comprueba-que-usrpractica1-puede-realizar-todas-las-operaciones-previstas-en-el-rol)
      - [8. Quita a USRPRACTICA1 el privilegio de crear vistas. Comprueba que ya no puede hacerlo.](#8-quita-a-usrpractica1-el-privilegio-de-crear-vistas-comprueba-que-ya-no-puede-hacerlo)
      - [9. Crea un perfil NOPARESDECURRAR que limita a dos el número de minutos de inactividad permitidos en una sesión.](#9-crea-un-perfil-noparesdecurrar-que-limita-a-dos-el-número-de-minutos-de-inactividad-permitidos-en-una-sesión)
      - [10. Activa el uso de perfiles en ORACLE.](#10-activa-el-uso-de-perfiles-en-oracle)
      - [11. Asigna el perfil creado a USRPRACTICA1 y comprueba su correcto funcionamiento.](#11-asigna-el-perfil-creado-a-usrpractica1-y-comprueba-su-correcto-funcionamiento)
      - [12. Crea un perfil CONTRASEÑASEGURA especificando que la contraseña caduca mensualmente y sólo se permiten tres intentos fallidos para acceder a la cuenta. En caso de superarse, la cuenta debe quedar bloqueada indefinidamente.](#12-crea-un-perfil-contraseñasegura-especificando-que-la-contraseña-caduca-mensualmente-y-sólo-se-permiten-tres-intentos-fallidos-para-acceder-a-la-cuenta-en-caso-de-superarse-la-cuenta-debe-quedar-bloqueada-indefinidamente)
      - [13. Asigna el perfil creado a USRPRACTICA1 y comprueba su funcionamiento. Desbloquea posteriormente al usuario.](#13-asigna-el-perfil-creado-a-usrpractica1-y-comprueba-su-funcionamiento-desbloquea-posteriormente-al-usuario)
      - [14. Consulta qué usuarios existen en tu base de datos.](#14-consulta-qué-usuarios-existen-en-tu-base-de-datos)
      - [15. Elige un usuario concreto y consulta qué cuota tiene sobre cada uno de los tablespaces.](#15-elige-un-usuario-concreto-y-consulta-qué-cuota-tiene-sobre-cada-uno-de-los-tablespaces)
      - [16. Elige un usuario concreto y muestra qué privilegios de sistema tiene asignados.](#16-elige-un-usuario-concreto-y-muestra-qué-privilegios-de-sistema-tiene-asignados)
      - [17. Elige un usuario concreto y muestra qué privilegios sobre objetos tiene asignados.](#17-elige-un-usuario-concreto-y-muestra-qué-privilegios-sobre-objetos-tiene-asignados)
      - [18. Consulta qué roles existen en tu base de datos.](#18-consulta-qué-roles-existen-en-tu-base-de-datos)
      - [19. Elige un rol concreto y consulta qué usuarios lo tienen asignado.](#19-elige-un-rol-concreto-y-consulta-qué-usuarios-lo-tienen-asignado)
      - [20. Elige un rol concreto y averigua si está compuesto por otros roles o no.](#20-elige-un-rol-concreto-y-averigua-si-está-compuesto-por-otros-roles-o-no)
      - [21. Consulta qué perfiles existen en tu base de datos.](#21-consulta-qué-perfiles-existen-en-tu-base-de-datos)
      - [22. Elige un perfil y consulta qué límites se establecen en el mismo.](#22-elige-un-perfil-y-consulta-qué-límites-se-establecen-en-el-mismo)
      - [23. Muestra los nombres de los usuarios que tienen limitado el número de sesiones concurrentes.](#23-muestra-los-nombres-de-los-usuarios-que-tienen-limitado-el-número-de-sesiones-concurrentes)
      - [24. Realiza un procedimiento que reciba un nombre de usuario y un privilegio de sistema y nos muestre el mensaje 'SI, DIRECTO' si el usuario tiene ese privilegio concedido directamente, 'SI, POR ROL' si el usuario tiene ese privilegio en alguno de los roles que tiene concedidos y un 'NO' si el usuario no tiene dicho privilegio.](#24-realiza-un-procedimiento-que-reciba-un-nombre-de-usuario-y-un-privilegio-de-sistema-y-nos-muestre-el-mensaje-si-directo-si-el-usuario-tiene-ese-privilegio-concedido-directamente-si-por-rol-si-el-usuario-tiene-ese-privilegio-en-alguno-de-los-roles-que-tiene-concedidos-y-un-no-si-el-usuario-no-tiene-dicho-privilegio)
      - [25. Realiza un procedimiento llamado MostrarNumSesiones que reciba un nombre de usuario y muestre el número de sesiones concurrentes que puede tener abiertas como máximo y las que tiene abiertas realmente.](#25-realiza-un-procedimiento-llamado-mostrarnumsesiones-que-reciba-un-nombre-de-usuario-y-muestre-el-número-de-sesiones-concurrentes-que-puede-tener-abiertas-como-máximo-y-las-que-tiene-abiertas-realmente)
  - [Alumno 2 - Iván (Postgres y ORACLE):](#alumno-2---iván-postgres-y-oracle)
    - [Postgres:](#postgres)
      - [1. Averigua que privilegios de sistema hay en Postgres y como se asignan a un usuario.](#1-averigua-que-privilegios-de-sistema-hay-en-postgres-y-como-se-asignan-a-un-usuario)
      - [2. Averigua cual es la forma de asignar y revocar privilegios sobre una tabla concreta en Postgres.](#2-averigua-cual-es-la-forma-de-asignar-y-revocar-privilegios-sobre-una-tabla-concreta-en-postgres)
      - [3. Averigua si existe el concepto de rol en Postgres y señala las diferencias con los roles de ORACLE.](#3-averigua-si-existe-el-concepto-de-rol-en-postgres-y-señala-las-diferencias-con-los-roles-de-oracle)
      - [4. Averigua si existe el concepto de perfil como conjunto de límites sobre el uso de recursos o sobre la contraseña en Postgres y señala las diferencias con los perfiles de ORACLE.](#4-averigua-si-existe-el-concepto-de-perfil-como-conjunto-de-límites-sobre-el-uso-de-recursos-o-sobre-la-contraseña-en-postgres-y-señala-las-diferencias-con-los-perfiles-de-oracle)
      - [5. Realiza consultas al diccionario de datos de Postgres para averiguar todos los privilegios que tiene un usuario concreto.](#5-realiza-consultas-al-diccionario-de-datos-de-postgres-para-averiguar-todos-los-privilegios-que-tiene-un-usuario-concreto)
      - [6. Realiza consultas al diccionario de datos en Postgres para averiguar qué usuarios pueden consultar una tabla concreta.](#6-realiza-consultas-al-diccionario-de-datos-en-postgres-para-averiguar-qué-usuarios-pueden-consultar-una-tabla-concreta)
    - [ORACLE:](#oracle)
      - [7. Realiza una función de verificación de contraseñas que compruebe que la contraseña difiere en más de tres caracteres de la anterior y que la longitud de la misma es diferente de la anterior. Asígnala al perfil CONTRASEÑASEGURA. Comprueba que funciona correctamente.](#7-realiza-una-función-de-verificación-de-contraseñas-que-compruebe-que-la-contraseña-difiere-en-más-de-tres-caracteres-de-la-anterior-y-que-la-longitud-de-la-misma-es-diferente-de-la-anterior-asígnala-al-perfil-contraseñasegura-comprueba-que-funciona-correctamente)
      - [8. Realiza un procedimiento llamado MostrarPrivilegiosdelRol que reciba el nombre de un rol y muestre los privilegios de sistema y los privilegios sobre objetos que lo componen.](#8-realiza-un-procedimiento-llamado-mostrarprivilegiosdelrol-que-reciba-el-nombre-de-un-rol-y-muestre-los-privilegios-de-sistema-y-los-privilegios-sobre-objetos-que-lo-componen)
  - [Alumno 3 - Alfonso (MySQL y ORACLE):](#alumno-3---alfonso-mysql-y-oracle)
    - [MySQL:](#mysql)
      - [1. Averigua que privilegios de sistema hay en MySQL y como se asignan a un usuario.](#1-averigua-que-privilegios-de-sistema-hay-en-mysql-y-como-se-asignan-a-un-usuario)
      - [2. Averigua cual es la forma de asignar y revocar privilegios sobre una tabla concreta en MySQL.](#2-averigua-cual-es-la-forma-de-asignar-y-revocar-privilegios-sobre-una-tabla-concreta-en-mysql)
      - [3. Averigua si existe el concepto de rol en MySQL y señala las diferencias con los roles de ORACLE.](#3-averigua-si-existe-el-concepto-de-rol-en-mysql-y-señala-las-diferencias-con-los-roles-de-oracle)
      - [4. Averigua si existe el concepto de perfil como conjunto de límites sobre el uso de recursos o sobre la contraseña en MySQL y señala las diferencias con los perfiles de ORACLE.](#4-averigua-si-existe-el-concepto-de-perfil-como-conjunto-de-límites-sobre-el-uso-de-recursos-o-sobre-la-contraseña-en-mysql-y-señala-las-diferencias-con-los-perfiles-de-oracle)
      - [5. Realiza consultas al diccionario de datos de MySQL para averiguar todos los privilegios que tiene un usuario concreto.](#5-realiza-consultas-al-diccionario-de-datos-de-mysql-para-averiguar-todos-los-privilegios-que-tiene-un-usuario-concreto)
      - [6. Realiza consultas al diccionario de datos en MySQL para averiguar qué usuarios pueden consultar una tabla concreta.](#6-realiza-consultas-al-diccionario-de-datos-en-mysql-para-averiguar-qué-usuarios-pueden-consultar-una-tabla-concreta)
    - [ORACLE:](#oracle-1)
      - [7. Realiza un procedimiento llamado PermisosdeAsobreB que reciba dos nombres de usuario y muestre los permisos que tiene el primero de ellos sobre objetos del segundo.](#7-realiza-un-procedimiento-llamado-permisosdeasobreb-que-reciba-dos-nombres-de-usuario-y-muestre-los-permisos-que-tiene-el-primero-de-ellos-sobre-objetos-del-segundo)
      - [8. Realiza un procedimiento llamado MostrarInfoPerfil que reciba el nombre de un perfil y muestre su composición y los usuarios que lo tienen asignado.](#8-realiza-un-procedimiento-llamado-mostrarinfoperfil-que-reciba-el-nombre-de-un-perfil-y-muestre-su-composición-y-los-usuarios-que-lo-tienen-asignado)
  - [Parte Grupal:](#parte-grupal)
  - [Alumno 4 (MongoDB y ORACLE):](#alumno-4-mongodb-y-oracle)
    - [MongoDB:](#mongodb)
      - [1. Averigua si existe la posibilidad en MongoDB de limitar el acceso de un usuario a los datos de una colección determinada.](#1-averigua-si-existe-la-posibilidad-en-mongodb-de-limitar-el-acceso-de-un-usuario-a-los-datos-de-una-colección-determinada)
      - [2. Averigua si en MongoDB existe el concepto de privilegio del sistema y muestra las diferencias más importantes con ORACLE.](#2-averigua-si-en-mongodb-existe-el-concepto-de-privilegio-del-sistema-y-muestra-las-diferencias-más-importantes-con-oracle)
      - [3. Explica los roles por defecto que incorpora MongoDB y como se asignan a los usuarios.](#3-explica-los-roles-por-defecto-que-incorpora-mongodb-y-como-se-asignan-a-los-usuarios)
      - [4. Explica como puede consultarse el diccionario de datos de MongoDB para saber que roles han sido concedidos a un usuario y qué privilegios incluyen.](#4-explica-como-puede-consultarse-el-diccionario-de-datos-de-mongodb-para-saber-que-roles-han-sido-concedidos-a-un-usuario-y-qué-privilegios-incluyen)
    - [ORACLE:](#oracle-2)
      - [5. Realiza un procedimiento llamado MostrarObjetosAccesibles que reciba un nombre de usuario y muestre todos los objetos a los que tiene acceso.](#5-realiza-un-procedimiento-llamado-mostrarobjetosaccesibles-que-reciba-un-nombre-de-usuario-y-muestre-todos-los-objetos-a-los-que-tiene-acceso)
      - [6. Realiza un procedimiento que reciba un nombre de usuario, un privilegio y un objeto y nos muestre el mensaje 'SI, DIRECTO' si el usuario tiene ese privilegio sobre objeto concedido directamente, 'SI, POR ROL' si el usuario lo tiene en alguno de los roles que tiene concedidos y un 'NO' si el usuario no tiene dicho privilegio.](#6-realiza-un-procedimiento-que-reciba-un-nombre-de-usuario-un-privilegio-y-un-objeto-y-nos-muestre-el-mensaje-si-directo-si-el-usuario-tiene-ese-privilegio-sobre-objeto-concedido-directamente-si-por-rol-si-el-usuario-lo-tiene-en-alguno-de-los-roles-que-tiene-concedidos-y-un-no-si-el-usuario-no-tiene-dicho-privilegio)
  - [CASO PRÁCTICO 1:](#caso-práctico-1)
      - [1. (ORACLE, Postgres, MySQL) Crea un usuario llamado Becario y, sin usar los roles de ORACLE, dale los siguientes privilegios: (1,5 puntos)](#1-oracle-postgres-mysql-crea-un-usuario-llamado-becario-y-sin-usar-los-roles-de-oracle-dale-los-siguientes-privilegios-15-puntos)
      - [VERSIÓN ORACLE:](#versión-oracle)
      - [VERSIÓN POSTGRE:](#versión-postgre)
      - [VERSIÓN MYSQL:](#versión-mysql)
      - [2. (ORACLE, Postgres, MySQL) Escribe una consulta que obtenga un script para quitar el privilegio de borrar registros en alguna tabla de SCOTT a los usuarios que lo tengan.](#2-oracle-postgres-mysql-escribe-una-consulta-que-obtenga-un-script-para-quitar-el-privilegio-de-borrar-registros-en-alguna-tabla-de-scott-a-los-usuarios-que-lo-tengan)
      - [VERSIÓN ORACLE:](#versión-oracle-1)
      - [VERSIÓN POSTGRE:](#versión-postgre-1)
      - [VERSIÓN MYSQL:](#versión-mysql-1)
      - [3. (ORACLE) Crea un tablespace TS2 con tamaño de extensión de 256K. Realiza una consulta que genere un script que asigne ese tablespace como tablespace por defecto a los usuarios que no tienen privilegios para consultar ninguna tabla de SCOTT, excepto a SYSTEM.](#3-oracle-crea-un-tablespace-ts2-con-tamaño-de-extensión-de-256k-realiza-una-consulta-que-genere-un-script-que-asigne-ese-tablespace-como-tablespace-por-defecto-a-los-usuarios-que-no-tienen-privilegios-para-consultar-ninguna-tabla-de-scott-excepto-a-system)
      - [4. (ORACLE, Postgres) Realiza un procedimiento que reciba un nombre de usuario y nos muestre cuántas sesiones tiene abiertas en este momento. Además, para cada una de dichas sesiones nos mostrará la hora de comienzo y el nombre de la máquina, sistema operativo y programa desde el que fue abierta.](#4-oracle-postgres-realiza-un-procedimiento-que-reciba-un-nombre-de-usuario-y-nos-muestre-cuántas-sesiones-tiene-abiertas-en-este-momento-además-para-cada-una-de-dichas-sesiones-nos-mostrará-la-hora-de-comienzo-y-el-nombre-de-la-máquina-sistema-operativo-y-programa-desde-el-que-fue-abierta)
      - [VERSIÓN ORACLE:](#versión-oracle-2)
      - [VERSIÓN POSTGRE:](#versión-postgre-2)
      - [5. (ORACLE) Realiza un procedimiento que muestre los usuarios que pueden conceder privilegios de sistema a otros usuarios y cuales son dichos privilegios.](#5-oracle-realiza-un-procedimiento-que-muestre-los-usuarios-que-pueden-conceder-privilegios-de-sistema-a-otros-usuarios-y-cuales-son-dichos-privilegios)
  - [EJERCICIO GRUPAL 3:](#ejercicio-grupal-3)
    - [Elaboración de un vídeo grupal resumiendo las diferencias de concepto y en la gestión de usuarios, permisos de sistema y permisos sobre objetos, roles y perfiles entre los cuatro SGBDs estudiados. Cada miembro del grupo hablará de uno de los siguientes temas:](#elaboración-de-un-vídeo-grupal-resumiendo-las-diferencias-de-concepto-y-en-la-gestión-de-usuarios-permisos-de-sistema-y-permisos-sobre-objetos-roles-y-perfiles-entre-los-cuatro-sgbds-estudiados-cada-miembro-del-grupo-hablará-de-uno-de-los-siguientes-temas)
      - [a) Usuarios y permisos sobre objetos.](#a-usuarios-y-permisos-sobre-objetos)
      - [b) Permisos de sistema.](#b-permisos-de-sistema)
      - [c) Roles.](#c-roles)
      - [d) Perfiles.](#d-perfiles)
      
      
## Parte Individual:

## Alumno 1 - Felipe (ORACLE):

#### 1. Crea un rol ROLPRACTICA1 con los privilegios necesarios para conectarse a la base de datos, crear tablas y vistas e insertar datos en la tabla EMP de SCOTT.

Creación del rol y asignación de permisos.
```sql
    CREATE ROLE ROLPRACTICA1;

    GRANT CONNECT, CREATE VIEW, CREATE TABLE TO ROLPRACTICA1;

	GRANT INSERT ON SCOTT.EMP TO ROLPRACTICA1;
```
![oracle-e1-1](capturas/oracle-A1-1.PNG)

#### 2. Crea un usuario USRPRACTICA1 con el tablespace USERS por defecto y averigua que cuota se le ha asignado por defecto en el mismo. Sustitúyela por una cuota de 1M.

Creación del usuario y consulta del tablespace.
```sql
    CREATE USER USRPRACTICA1 IDENTIFIED BY "password" DEFAULT TABLESPACE USERS;

	SELECT USERNAME,BYTES FROM DBA_TS_QUOTAS
	WHERE USERNAME = 'USRPRACTICA1';
```
![oracle-e2-1](capturas/oracle-A1-2.PNG)

Cambio de cuota y consulta del tablespace.
```sql
    ALTER USER USRPRACTICA1 QUOTA 1M ON USERS;

    SELECT USERNAME,BYTES FROM DBA_TS_QUOTAS
	WHERE USERNAME = 'USRPRACTICA1';
```
![oracle-e2-2](capturas/oracle-A1-2-1.PNG)

#### 3. Modifica el usuario USRPRACTICA1 para que tenga cuota 0 en el tablespace SYSTEM.

Modificación de cuota en el tablespace SYSTEM.
```sql
    ALTER USER USRPRACTICA1 QUOTA 0 ON SYSTEM;
```
![oracle-e3-1](capturas/oracle-A1-3.PNG)

#### 4. Concede a USRPRACTICA1 el ROLPRACTICA1.

Concesión del rol ROLPRACTICA1 al usuario USRPRACTICA1.
```sql
    GRANT ROLPRACTICA1 TO USRPRACTICA1;
```
![oracle-e3-2](capturas/oracle-A1-4.PNG)

#### 5. Concede a USRPRACTICA1 el privilegio de crear tablas e insertar datos en el esquema de cualquier usuario. Prueba el privilegio. Comprueba si puede modificar la estructura o eliminar las tablas creadas.

Concesión de privilegios al usuario USRPRACTICA1.
```sql
    GRANT CREATE ANY TABLE, INSERT ANY TABLE TO USRPRACTICA1;
```
![oracle-e5-1](capturas/oracle-A1-5.PNG)

Creación de tabla y registro.
```sql
    create table SCOTT.prueba1(
		campo1 varchar2(15),
		campo2 number
	);

    INSERT INTO SCOTT.prueba1 VALUES ('Prueba1',1);
```
![oracle-e5-2](capturas/oracle-A1-5-1.PNG)

Prueba de privilegios.
```sql
	ALTER TABLE SCOTT.prueba1 DROP COLUMN campo2;

	delete from SCOTT.prueba1;

	drop table SCOTT.prueba1;
```
![oracle-e5-3](capturas/oracle-A1-5-2.PNG)

#### 6. Concede a USRPRACTICA1 el privilegio de leer la tabla DEPT de SCOTT con la posibilidad de que lo pase a su vez a terceros usuarios.

Concesión del privilegio y consulta de prueba.
```sql
	GRANT SELECT ON SCOTT.DEPT TO USRPRACTICA1 WITH GRANT OPTION;

	select * from scott.DEPT;
```
![oracle-e6-1](capturas/oracle-A1-6.PNG)

#### 7. Comprueba que USRPRACTICA1 puede realizar todas las operaciones previstas en el rol.

Conexión con el usuario usrpractica1.
```sql
	connect USRPRACTICA1;
```
![oracle-e7-1](capturas/oracle-A1-7.PNG)

Creación de tabla.
```sql
	create table scott.prueba2 (
		id varchar2(4) not null,
		campo1 varchar2(15),
		campo2 number(8)
	);
```
![oracle-e7-2](capturas/oracle-A1-7-1.PNG)

Creación y consulta sobre la vista.
```sql
	create VIEW vistaprueba AS
	select DNAME from scott.dept;

	select * from VISTAPRUEBA;
```
![oracle-e7-3](capturas/oracle-A1-7-2.PNG)

Añado registro a la tabla emp de scott.
```sql
	insert into scott.emp values(9501, 'Pepe', 'test', 8251, TO_DATE('16-JAN-2023', 'DD-MON-YYYY'),950, null, 20);
```
![oracle-e7-4](capturas/oracle-A1-7-3.PNG)

#### 8. Quita a USRPRACTICA1 el privilegio de crear vistas. Comprueba que ya no puede hacerlo.

Eliminación del privilegio de crear vistas del usuario usrpractica1 y prueba de funcionamiento.
```sql
	REVOKE CREATE VIEW FROM ROLPRACTICA1;

    create VIEW vistaprueba1 AS
	select DNAME,LOC from scott.dept;
```
![oracle-e8-1](capturas/oracle-A1-8.PNG)

#### 9. Crea un perfil NOPARESDECURRAR que limita a dos el número de minutos de inactividad permitidos en una sesión.

Creación del perfil NOPARESDECURRAR.
```sql
	CREATE PROFILE NOPARESDECURRAR LIMIT IDLE_TIME 2;
```
![oracle-e9-1](capturas/oracle-A1-9.PNG)

#### 10. Activa el uso de perfiles en ORACLE.

Activación de perfiles en Oracle.
```sql
	ALTER SYSTEM SET RESOURCE_LIMIT = TRUE;
```
![oracle-e10-1](capturas/oracle-A1-10.PNG)

#### 11. Asigna el perfil creado a USRPRACTICA1 y comprueba su correcto funcionamiento.

Asignación del perfil NOPARESDECURRAR al usuario usrpractica1.
```sql
	ALTER USER USRPRACTICA1 PROFILE NOPARESDECURRAR;
```
![oracle-e11-1](capturas/oracle-A1-11.PNG)

#### 12. Crea un perfil CONTRASEÑASEGURA especificando que la contraseña caduca mensualmente y sólo se permiten tres intentos fallidos para acceder a la cuenta. En caso de superarse, la cuenta debe quedar bloqueada indefinidamente.

Cración del perfil CONTRASEÑASEGURA.
```sql
	CREATE PROFILE contrasenasegura LIMIT
		PASSWORD_LIFE_TIME 30
		FAILED_LOGIN_ATTEMPTS 3
		PASSWORD_REUSE_TIME UNLIMITED
		PASSWORD_REUSE_MAX UNLIMITED;
```
![oracle-e12-1](capturas/oracle-A1-12.PNG)

#### 13. Asigna el perfil creado a USRPRACTICA1 y comprueba su funcionamiento. Desbloquea posteriormente al usuario.

Asignación del perfil CONTRASEÑASEGURA al usuario usrpractica1.
```sql
	ALTER USER USRPRACTICA1 PROFILE contrasenasegura;
```
![oracle-e13-1](capturas/oracle-A1-13.PNG)

Pruebas de funcionamiento.
```sql
	connect USRPRACTICA1;
```
![oracle-e13-2](capturas/oracle-A1-13-1.PNG)

```sql
		ALTER USER USRPRACTICA1 ACCOUNT UNLOCK;
```
![oracle-e13-3](capturas/oracle-A1-13-2.PNG)

#### 14. Consulta qué usuarios existen en tu base de datos.

Consulta de usuarios en la base de datos.
```sql
	SELECT username FROM dba_users;
```
![oracle-e14-1](capturas/oracle-A1-14.PNG)

#### 15. Elige un usuario concreto y consulta qué cuota tiene sobre cada uno de los tablespaces.

Cuota de usuario concreto sobre tablespaces.
```sql
	SELECT username,tablespace_name, bytes FROM dba_ts_quotas
	WHERE username = 'SCOTT';
```
![oracle-e15-1](capturas/oracle-A1-15.PNG)

#### 16. Elige un usuario concreto y muestra qué privilegios de sistema tiene asignados.

Privilegios de sistema en usuario concreto.
```sql
	SELECT * FROM DBA_SYS_PRIVS WHERE GRANTEE = 'SYS';
```
![oracle-e16-1](capturas/oracle-A1-16.PNG)

#### 17. Elige un usuario concreto y muestra qué privilegios sobre objetos tiene asignados.

Privilegios sobre objetos en usuario concreto.
```sql
	SELECT * FROM DBA_TAB_PRIVS WHERE GRANTEE = 'SYS';
```
![oracle-e17-1](capturas/oracle-A1-17.PNG)

#### 18. Consulta qué roles existen en tu base de datos.

Roles existentes en la base de datos.
```sql
	SELECT ROLE FROM DBA_ROLES;
```
![oracle-e18-1](capturas/oracle-A1-18.PNG)

#### 19. Elige un rol concreto y consulta qué usuarios lo tienen asignado.

Consulta de usuarios que poseen un rol concreto.
```sql
	SELECT GRANTEE FROM DBA_ROLE_PRIVS WHERE GRANTED_ROLE = 'CONNECT';
```
![oracle-e19-1](capturas/oracle-A1-19.PNG)

#### 20. Elige un rol concreto y averigua si está compuesto por otros roles o no.

Consulta sobre composición de roles.
```sql
	SELECT granted_role FROM dba_role_privs WHERE grantee = 'RESOURCE';
```
![oracle-e20-1](capturas/oracle-A1-20.PNG)

#### 21. Consulta qué perfiles existen en tu base de datos.

Perfiles existentes en la base de datos.
```sql
	SELECT RESOURCE_NAME FROM DBA_PROFILES;
```
![oracle-e21-1](capturas/oracle-A1-21.PNG)

#### 22. Elige un perfil y consulta qué límites se establecen en el mismo.

Consulta limites definido en perfil.
```sql
	SELECT RESOURCE_NAME, LIMIT FROM DBA_PROFILES WHERE PROFILE = 'CONTRASENASEGURA';
```
![oracle-e22-1](capturas/oracle-A1-22.PNG)

#### 23. Muestra los nombres de los usuarios que tienen limitado el número de sesiones concurrentes.

Usuarios con sesiones limitadas.
```sql
	 CREATE PROFILE LIMITE_SESIONES LIMIT SESSIONS_PER_USER 5;

    ALTER USER SCOTT PROFILE LIMITE_SESIONES;

	SELECT username, resource_name, limit FROM dba_profiles JOIN dba_users USING (profile) WHERE resource_name = 'SESSIONS_PER_USER' AND limit != 'UNLIMITED' AND limit != 'DEFAULT';
```
![oracle-e23-1](capturas/oracle-A1-23.PNG)

#### 24. Realiza un procedimiento que reciba un nombre de usuario y un privilegio de sistema y nos muestre el mensaje 'SI, DIRECTO' si el usuario tiene ese privilegio concedido directamente, 'SI, POR ROL' si el usuario tiene ese privilegio en alguno de los roles que tiene concedidos y un 'NO' si el usuario no tiene dicho privilegio.

#### 25. Realiza un procedimiento llamado MostrarNumSesiones que reciba un nombre de usuario y muestre el número de sesiones concurrentes que puede tener abiertas como máximo y las que tiene abiertas realmente.

Procedimiento MostrarNumSesiones.
```sql
	CREATE OR REPLACE PROCEDURE MostrarNumSesiones (user IN VARCHAR2) 
	IS
	v_perfil VARCHAR2(30);
	v_limitmaxsesiones VARCHAR2(40);
	v_numsesiones NUMBER;

	BEGIN
		SELECT PROFILE INTO v_perfil FROM DBA_USERS where username = user;

		select limit INTO v_limitmaxsesiones from DBA_PROFILES CDB_PROFILES
		where profile = v_perfil AND RESOURCE_NAME = 'SESSIONS_PER_USER';

		select count(username) INTO v_numsesiones from V$session where username =user;

		dbms_output.put_line('El limite de sesiones concurrentes permitidas del usuario '|| user || ' es : ' || v_limitmaxsesiones);
		dbms_output.put_line('El número real de sesiones que tiene abiertas son: '|| v_numsesiones); 	END;
	/
```
Ejecución de procedimiento MostrarNumSesiones.
```sql
    execute MostrarNumSesiones('SYS');
```
![oracle-e25-1](capturas/oracle-A1-25.PNG)

---------------------------------------------------------------------------------------------------------------------------------------------

## Alumno 2 - Iván (Postgres y ORACLE):

### Postgres:

#### 1. Averigua que privilegios de sistema hay en Postgres y como se asignan a un usuario.

Postgresql utiliza roles para determinar los privilegios de sistema. Estos roles representan usuarios y pueden ser asignados a otros roles.

Para realizar una correcta administración de los privilegios del sistema sobre los usuarios se aconseja agrupar los usuarios en diferentes roles siendo la diferencia principal entre los usuarios y los roles de grupo el privilegio de login que tendrían los primeros.
Se recomienda crear grupos de usuarios a los que se les asigne diferentes privilegios, teniendo en cuenta que sólo los usuarios individuales tendrán permitido el login. 

Estas opciones de configuración pueden ser aplicadas tanto durante la creación del rol como en algún momento posterior, siendo Postgresql capaz de asignar privilegios de manera dinámica a los roles ya existentes:
```sql
    CREATE ROLE <nombre_rol> 
        WITH <opcion>;
    ALTER ROLE <nombre_rol> 
        WITH <opcion>;
```
Ejemplo:
```sql
    CREATE ROLE usuario1 
        WITH CREATEDB 
        LOGIN 
        PASSWORD '1234';
```
![Ejercicio1](capturas/postgre-1-1.png)

Algunas posibilidades, junto con sus respectivas alternativas, son:

    SUPERUSER/NOSUPERUSER: se agregan los privilegios de superusuario.

    CREATEDB/NOCREATEDB: opción para crear bases de datos.

    CREATEROLE/NOCREATEROLE: opción para crear nuevos roles.

    VALID UNTIL: indica la expiración del rol/usuario.

    [ENCRYPTED] PASSWORD: asigna una contraseña al rol/usuario.

    LOGIN/NOLOGIN: opción para crear sesiones.

    INHERIT/NOINHERIT: opción para determinar si hereda los privilegios de los roles de los que es miembro.

    REPLICATION/NOREPLICATION: opción para controlar la transmisión.

    BYPASSRL/NOBYPASSRLS: opción para omitir los sistemas de seguridad de fila de las tablas.

    CONNECTION LIMIT: limita el número de sesiones concurrentes.

    IN ROLE: opción para indicar los roles de los que formará parte.

    ADMIN: opción para indicar el rol o los roles de los formará parte con derecho a agregar a otros roles en este.

---------------------------------------------------------------------------------------------------------------------------------------------

#### 2. Averigua cual es la forma de asignar y revocar privilegios sobre una tabla concreta en Postgres.

Para otorgar privilegios sobre una tabla en Postgres se utilizará una sintaxis particular. Esta consiste en:
```sql
GRANT <nombre_privilegio> 
  ON <nombre_tabla> 
  TO <nombre_rol | nombre_grupo_rol | PUBLIC> 
  [WITH GRANT OPTION]
```
Ejemplo:
```sql
create database db1;
\c db1;
create table tabla1 (id serial primary key, nombre varchar(50));
```
```sql
GRANT SELECT, INSERT 
  ON tabla1 
  TO usuario1
  WITH GRANT OPTION;
```
![Ejercicio2](capturas/postgre-2-1.png)

Existen tres roles que pueden otorgar los permisos deseados: 
- Rol superusuario: tiene todos los privilegios sobre todas las tablas.
- Rol propietario de la tabla: tiene todos los privilegios sobre la tabla.
- Rol que ha recibido el privilegio con la opción WITH GRANT OPTION: puede otorgar el privilegio a otros roles.

La estructura para revocar privilegios en una tabla específica es:
```sql
REVOKE <nombre_privilegio> 
  ON <nombre_tabla> 
  FROM <nombre_rol | nombre_grupo_rol | PUBLIC>
```
Ejemplo:
```sql
REVOKE SELECT, INSERT 
  ON tabla1 
  FROM postgres;
```

Además, también se puede quitar la opción WITH GRANT OPTION de un determinado rol de usuario utilizando la orden GRANT OPTION FOR.

---------------------------------------------------------------------------------------------------------------------------------------------

#### 3. Averigua si existe el concepto de rol en Postgres y señala las diferencias con los roles de ORACLE.

En Postgres se refiere a los usuarios como roles; a diferencia de ORACLE, donde estos pueden ser grupos de usuarios o/y otros roles. Los roles son los propietarios de las bases de datos en Postgres, y pueden tener otros roles dentro de ellos.

La sintaxis para la creación de roles y la asignación de privilegios sobre los objetos es común entre los dos gestores de base de datos. Esto se hace mediante una secuencia de comandos:
```sql
CREATE ROLE <nombre_rol>;
GRANT <privilegio> 
  ON <nombre_objeto> 
  TO <nombre_rol>;
```
Ejemplo:
```sql
CREATE ROLE usuario2;
GRANT SELECT, INSERT 
  ON tabla1 
  TO usuario2;
```
![Ejercicio3](capturas/postgre-3-1.png)

Mientras que la distribución de responsabilidades a otros roles es la misma, Postgres no da soporte a la asignación de roles a un usuario debido a que este concepto no existe.

- Asignación de un rol a un usuario en ORACLE:
```sql
    GRANT <nombre_rol> 
      TO <nombre_usuario>;
```

- Asignación de un rol a otro rol en ORACLE y Postgres:
```sql
GRANT <nombre_rol> 
  TO <nombre_rol>;
```

Para ver los roles y los privilegios de estos en ORACLE, se debe consultar el diccionario de datos al utilizar las vistas DBA_ROLES, DBA_ROLE_PRIVS y ROLE_ROLE_PRIVS. 
En cuanto a Postgres, se recomienda usar el comando \du+ para ver los roles y los privilegios.

Ejemplo:
![Ejercicio3](capturas/postgre-3-2.png)

---------------------------------------------------------------------------------------------------------------------------------------------

#### 4. Averigua si existe el concepto de perfil como conjunto de límites sobre el uso de recursos o sobre la contraseña en Postgres y señala las diferencias con los perfiles de ORACLE.

En Postgres no hay una noción de perfil, dado que en lugar de trabajar con usuarios como en ORACLE, todas las restricciones se aplican a los objetos. 
Aunque según tengo entendido la versión Enterprise si dispone de un concepto de Perfil.
No he conseguido encontrar mucha más información relevante en Internet sobre esto.

---------------------------------------------------------------------------------------------------------------------------------------------

#### 5. Realiza consultas al diccionario de datos de Postgres para averiguar todos los privilegios que tiene un usuario concreto.

La sintaxis para consultar todos los privilegios de un usuario en Postgres es:
```sql
select 'Privilegio '||PRIVILEGE_TYPE||
       ' en la tabla '||TABLE_NAME||
       ' del esquema '||TABLE_SCHEMA||
       ' de la base de datos '||TABLE_CATALOG
  from INFORMATION_SCHEMA.TABLE_PRIVILEGES 
  where GRANTEE=<nombre_rol>;
```
Ejemplo 1:
```sql
select 'Privilegio '||PRIVILEGE_TYPE||
       ' en la tabla '||TABLE_NAME||
       ' del esquema '||TABLE_SCHEMA||
       ' de la base de datos '||TABLE_CATALOG
  from INFORMATION_SCHEMA.TABLE_PRIVILEGES 
  where GRANTEE='usuario1';
```
![Ejercicio5](capturas/postgre-5-1.png)
Ejemplo 2:
```sql
select 'Privilegio '||PRIVILEGE_TYPE||
       ' en la tabla '||TABLE_NAME||
       ' del esquema '||TABLE_SCHEMA||
       ' de la base de datos '||TABLE_CATALOG
  from INFORMATION_SCHEMA.TABLE_PRIVILEGES 
  where GRANTEE='scott';
```
![Ejercicio5](capturas/postgre-5-2.png)

---------------------------------------------------------------------------------------------------------------------------------------------

#### 6. Realiza consultas al diccionario de datos en Postgres para averiguar qué usuarios pueden consultar una tabla concreta.

La sintaxis para averiguar qué usuarios pueden consultar una tabla concreta:
```sql
select GRANTEE
  from INFORMATION_SCHEMA.TABLE_PRIVILEGES
  where TABLE_NAME = <nombre_table>
  and PRIVILEGE_TYPE = 'SELECT';
```
Ejemplo 1:
```sql
select GRANTEE
  from INFORMATION_SCHEMA.TABLE_PRIVILEGES
  where TABLE_NAME = 'pg_tables'
  and PRIVILEGE_TYPE = 'SELECT';
```
![Ejercicio6](capturas/postgre-6-1.png)

Ejemplo 2:
```sql
select GRANTEE
  from INFORMATION_SCHEMA.TABLE_PRIVILEGES
  where TABLE_NAME = 'emp'
  and PRIVILEGE_TYPE = 'SELECT';
```
![Ejercicio6](capturas/postgre-6-2.png)

Ejemplo 3:
```sql
select GRANTEE
  from INFORMATION_SCHEMA.TABLE_PRIVILEGES
  where TABLE_NAME = 'tabla1'
  and PRIVILEGE_TYPE = 'SELECT';
```
![Ejercicio6](capturas/postgre-6-3.png)

---------------------------------------------------------------------------------------------------------------------------------------------

### ORACLE:

#### 7. Realiza una función de verificación de contraseñas que compruebe que la contraseña difiere en más de tres caracteres de la anterior y que la longitud de la misma es diferente de la anterior. Asígnala al perfil CONTRASEÑASEGURA. Comprueba que funciona correctamente.

```sql
create or replace function f_verificar_passwd (p_usuario in varchar2, p_nueva_passwd in varchar2, p_vieja_passwd in varchar2)
return boolean
is
    v_sumaRepe number:=0;
    v_letraigual number:=0;
    v_numNum number:=0;
    v_numLetra number:=0;
    v_validar number:=0;
begin
    if length(p_nueva_passwd)=length(p_vieja_passwd) then
        raise_application_error(-20020, 'La password nueva no debe ser de la misma longitud que la anterior.');
    end if;
    for i in 1..length(p_nueva_passwd) loop
        ContarNumerosYLetras(substr(p_nueva_passwd, i,1), v_numNum, v_numLetra);
        CompararCaracteres(substr(p_nueva_passwd, i,1), p_vieja_passwd, v_letraigual);
        if v_letraigual=0 then
            v_sumaRepe:=v_sumaRepe+1;
        end if;
        v_letraigual:=0; 
    end loop;
    v_validar:=f_errores(v_sumaRepe, v_numNum, v_numLetra);
    return TRUE;
end f_verificar_passwd;
/

create or replace function f_errores(p_sumaRepe number, p_numNum number, p_numLetra number)
return number
is
begin
    case
        when p_sumaRepe<4 then
            raise_application_error(-20022, 'La password nueva debe ser diferente en 3 caracteres respecto a la anterior');
        else
            return 1;
    end case;       
end f_errores;
/


create or replace procedure CompararCaracteres(p_caracter varchar2, p_passwd varchar2, p_letraigual in out number)
is
begin
    for i in 1..length(p_passwd) loop
        if substr(p_passwd,i,1)=p_caracter then
            p_letraigual:=1;
        end if;
    end loop;
end CompararCaracteres;
/


create or replace procedure ContarNumerosYLetras (p_caracter varchar2, p_numero in out number, p_letra in out number)
is
begin
    if p_caracter=REGEXP_REPLACE(p_caracter,'[0-9]') then
        p_numero:=p_numero+1;
    else
        p_letra:=p_letra+1;
    end if;
end ContarNumerosYLetras;
/
```

Creación de perfil.
```sql
create profile CONTRASENASEGURA limit PASSWORD_VERIFY_FUNCTION f_verificar_passwd;
```
![Ejercicio7](capturas/postgre-7-1.png)

Creación de usuario con contraseña.
```sql
create user pruebapasswd identified by "123456789";
grant connect, resource to pruebapasswd;
```
![Ejercicio7](capturas/postgre-7-2.png)

Cambio de contraseña por una no válida antes de asignar el perfil.
```sql
alter user pruebapasswd identified by "123456789" replace "123456789";
```
![Ejercicio7](capturas/postgre-7-3.png)

Asignación del perfil al usuario.
```sql
alter user pruebapasswd profile CONTRASENASEGURA;
```
![Ejercicio7](capturas/postgre-7-4.png)

IMPORTANTE: Se debe loguear con el usuario pruebapasswd para que se ejecute la función de verificación de contraseñas.
```sql
connect pruebapasswd/123456789;
```

Cambio de contraseña por una no válida después de asignar el perfil:
- La contraseña no es válida porque es igual a la anterior.
```sql
alter user pruebapasswd identified by "123456789" replace "123456789";
```
![Ejercicio7](capturas/postgre-7-5.png)

- La contraseña no es válida porque es de la misma longitud que la anterior.
```sql
alter user pruebapasswd identified by "ASDFGHJKL" replace "123456789";
```
![Ejercicio7](capturas/postgre-7-6.png)

- La contraseña no es válida porque no difiere en 3 caracteres de la anterior.
```sql
alter user pruebapasswd identified by "12345abc" replace "123456789";
```
![Ejercicio7](capturas/postgre-7-7.png)

La contraseña es válida.
```sql
alter user pruebapasswd identified by "nuevapassword" replace "123456789";
```
![Ejercicio7](capturas/postgre-7-8.png)

---------------------------------------------------------------------------------------------------------------------------------------------

#### 8. Realiza un procedimiento llamado MostrarPrivilegiosdelRol que reciba el nombre de un rol y muestre los privilegios de sistema y los privilegios sobre objetos que lo componen.

```sql
create or replace procedure MostrarPrivilegiosRol (p_rol varchar2)
is
    v_validacion number:=0;
begin
    v_validacion:=f_ComprobarRol(p_rol);
    if v_validacion=0 then
        BuscarPrivilegiosSistema(p_rol);
        dbms_output.put_line(' ');
        dbms_output.put_line('--------------------------------------------------------------------------------');
        dbms_output.put_line(' ');
        BuscarPrivilegiosObjetos(p_rol);
    end if;
end MostrarPrivilegiosRol;
/


create or replace procedure BuscarPrivilegiosSistema(p_rol varchar2)
is
    cursor c_sys
    is
    select distinct privilege
    from role_sys_privs
    where role in (select distinct role 
                   from role_role_privs 
                   start with role=p_rol
                   connect by role = prior granted_role)
    or role = p_rol;
    v_sys c_sys%ROWTYPE;
begin
    dbms_output.put_line('PRIVILEGIOS DEL SISTEMA');
    dbms_output.put_line('--------------------------------------------------------------------------------');
    for v_sys in c_sys loop
        dbms_output.put_line(v_sys.privilege);
    end loop;
end BuscarPrivilegiosSistema;
/


create or replace procedure BuscarPrivilegiosObjetos(p_rol varchar2)
is
    cursor c_tab
    is
    select distinct privilege, table_name, owner
    from role_tab_privs
    where role in (select distinct role 
                   from role_role_privs 
                   start with role=p_rol
                   connect by role = prior granted_role)
    or role = p_rol;
    v_tab c_tab%ROWTYPE;
begin
    dbms_output.put_line('PRIVILEGIOS SOBRE OBJETOS');
    dbms_output.put_line('--------------------------------------------------------------------------------');
    for v_tab in c_tab loop
        dbms_output.put_line(v_tab.privilege||' sobre la tabla '||v_tab.table_name||' del usuario '||v_tab.owner);
    end loop;
end BuscarPrivilegiosObjetos;
/


create or replace function f_ComprobarRol(p_rol varchar2)
return number
is
    v_resultado varchar2(30);
begin
    select role into v_resultado
    from dba_roles
    where role=p_rol;
    return 0;
exception
    when NO_DATA_FOUND then
        dbms_output.put_line('No existe el rol '||p_rol);
        return -1;
end f_ComprobarRol;
/
```
Creación de ROL1 con privilegios sobre el sistema y sobre objetos.
```sql
create role ROL1;
grant create session to ROL1;
grant create table to ROL1;
grant create view to ROL1;
grant create procedure to ROL1;
grant create trigger to ROL1;
grant create database link to ROL1;
grant create sequence to ROL1;
grant create synonym to ROL1;
grant create type to ROL1;
grant select on scott.emp to ROL1;
grant select on scott.dept to ROL1;
```
Comprobación:
- Ejecución del procedimiento sobre un rol que no existe.
```sql
exec MostrarPrivilegiosRol('ROL100');
```
![Ejercicio8](capturas/postgre-8-1.png)

- Ejecución del procedimiento sobre roles existentes.
```sql
exec MostrarPrivilegiosRol('ROL1');
```
![Ejercicio8](capturas/postgre-8-2.png)

```sql
exec MostrarPrivilegiosRol('ADM_PARALLEL_EXECUTE_TASK');
```
![Ejercicio8](capturas/postgre-8-3.png)

```sql
exec MostrarPrivilegiosRol('DBA');
```
![Ejercicio8](capturas/postgre-8-4.png)
-
![Ejercicio8](capturas/postgre-8-5.png)

---------------------------------------------------------------------------------------------------------------------------------------------

## Alumno 3 - Alfonso (MySQL y ORACLE):

### MySQL:

#### 1. Averigua que privilegios de sistema hay en MySQL y como se asignan a un usuario.

- Para listar los usuarios y comprobar desde donde tienen permitida la conexión, realizaremos la siguiente consulta:
```sql
select user,host from mysql.user;
```
![Ejercicio 1](capturas/mysql-1-1.png)

La columna host nos indicará desde donde tiene permitido el usuario conectarse.
- Con la orden “show privileges” podremos comprobar los privilegios del sistema:
```sql
show privileges;
```
![Ejercicio 1](capturas/mysql-1-2.png)

- Si queremos asignar los permisos para realizar ciertas acciones a un un usuario, utilizamos la siguiente sentencia:
```sql
GRANT SELECT, INSERT, UPDATE, DELETE, CREATE, DROP, TRIGGER
    -> ON nombre_bd.*
    -> TO 'nombre_usuario'@'localhost';
```

- Si queremos un usuario con permisos de administrador (Todos los permisos sobre todas las tablas), usamos:
```sql
GRANT ALL PRIVILEGES ON *.* TO 'nombre_usuario'@'localhost';
```

#### 2. Averigua cual es la forma de asignar y revocar privilegios sobre una tabla concreta en MySQL.
       
Para asignar privilegios utilizamos “GRANT” y para revocarlos “REVOKE”, de la siguiente forma:
Ejemplo 1:
- Asignamos (GRANT) el privilegio SELECT sobre la base de datos “2asir” en la tabla “Profesor” al usuario “alfonso”, en la máquina “localhost”:
```sql
GRANT PRIVILEGIO ON nombre_bd.nombre_tabla FROM ‘usuario’@'maquina';
```
![Ejercicio 2](capturas/mysql-2-1.png)

Ejemplo 2: 
- Revocamos (REVOKE) el privilegio UPDATE y DELETE sobre todas las tablas de todas las bases de datos al usuario “usuario”, en la máquina “localhost”:
```sql
REVOKE PRIVILEGIO1,PRIVILEGIO2 ON *.* FROM 'usuario'@'maquina';
```
![Ejercicio 2](capturas/mysql-2-2.png)

Siendo *.* todas las tablas de todas las bases de datos.

#### 3. Averigua si existe el concepto de rol en MySQL y señala las diferencias con los roles de ORACLE.
       
Los roles son grupos a los que se asignan determinados privilegios. En lugar de asignar privilegios a cada usuario individualmente, podemos crear roles que tendrán estos privilegios y luego asignar el rol en cuestión a los usuarios. También podemos asignar un rol a otro rol.

Tras investigar un poco, he podido comprobar como el concepto de rol, no existe actualmente en MySQL.

ROLES EN ORACLE

Para crear un rol en Oracle usamos la sentencia:
```sql
CREATE ROLE nombre_rol;
```

Para mayor seguridad podemos asignar una clave (contraseña) al rol, de la siguiente forma:
```sql
SET ROLE nombre_rol IDENTIFIED BY contraseña;
```

Para asignar el rol a un usuario usamos:
```sql
GRANT nombre_rol TO usuario;
```

A los roles, también podemos asignarle privilegios a nivel de objetos. De esta forma, por ejemplo, podemos permitir únicamente realizar consultas e inserciones.
```sql
CREATE ROLE consulta_inserciones;
GRANT SELECT,INSERT on usuario.tabla to consulta_inserciones;
```

Finalmente este rol con el “perfil” que hemos definido, a los distintos usuarios finales:
```sql
GRANT consulta_inserciones TO alfonso;
```

**Nota:** Existen algunos roles predefinidos, algunos de ellos son:

    CONNECT 
    CREATE SESSION 
    CREATE TABLE
    CREATE VIEW
    CREATE SYNONYM
    CREATE SEQUENCE
    CREATE DATABASE LINK
    CREATE CLUSTER
    ALTER SESSION
    RESOURCE
    CREATE PROCEDURE
    CREATE SEQUENCE
    CREATE TRIGGER
    CREATE TYPE
    CREATE CLUSTER
    CREATE INDEXTYPE
    CREATE OPERATOR SCHEDULER
    CREATE ANY JOB
    CREATE JOB
    EXECUTE ANY CLASS
    EXECUTE ANY PROGRAM
    MANAGE SCHEDULER


En Oracle, podemos encontrar 2 roles, los que es muy conveniente conocer su funcionalidad:

- DBA: Aporta la mayoría de los privilegios. No es recomendable asignarlo a usuarios que no son administradores.

- SELECT_CATALOG_ROLE: No aporta privilegios de sistema, pero tiene cerca de 1600 privilegios de objeto.

Para ver los roles definidos y los privilegios que se otorgan a través de ellos, consultamos las siguientes vistas:
```sql
select * from DBA_ROLES;
select * from DBA_ROLE_PRIVS order by GRANTEE;
```

#### 4. Averigua si existe el concepto de perfil como conjunto de límites sobre el uso de recursos o sobre la contraseña en MySQL y señala las diferencias con los perfiles de ORACLE.

MySQL:

Tras investigar, he podido comprobar como en MySQL sí existe el concepto de "perfil de usuario" el cual es un conjunto de límites que se aplican a un usuario específico en cuanto al uso de recursos y a la contraseña. Estos límites pueden incluir cosas como el número máximo de consultas por hora, el número máximo de conexiones simultáneas, y la fuerza de la contraseña.

Desde la versión 8 de MySQL se permite aplicar límites para cuentas individuales en el uso de los siguientes recursos del servidor:

    - El número de consultas que puede ejecutar una cuenta por hora.
    - El número de actualizaciones que puede ejecutar una cuenta de usuario por hora.
    - El número de veces que una cuenta de usuario puede conectarse al servidor por hora.
    - El número de conexiones simultáneas al servidor por una cuenta.

Una “cuenta” en este contexto corresponde a una fila en la tabla del sistema mysql.user. Es decir, una conexión se evalúa con los valores de Usuario y Host en la fila de la tabla de usuario que se aplica a la conexión.

Para establecer límites de recursos para una cuenta en el momento de la creación de la cuenta usamos CREATE USER. Para modificar los límites de recursos de una cuenta existente, usamos ALTER USER.

Por ejemplo, si queremos modificar los recursos de una cuenta de limitando el número de consultas por hora, podemos usar la siguiente sentencia:
```sql
ALTER USER ‘alfonso’@’localhost’ WITH MAX_QUERIES_PER_HOUR 100;
```

Si queremos eliminar este límite, establecemos el valor a 0.
```sql
ALTER USER ‘alfonso’@’localhost’ WITH MAX_QUERIES_PER_HOUR 0;
```

En cuanto a la contraseña contamos con las siguientes limitaciones:
    • Caducidad de la contraseña (así se cambian periódicamente)
    • Restricciones de reutilización de contraseñas.
    • Verificación de contraseña.
    • Usar dos contraseñas (contraseñas duales, primaria y secundaria)
    • Evaluación de la fuerza de la contraseña
    • Permite generar contraseñas aleatorias.
    • Habilitar el bloqueo temporal de la cuenta a partir de x errores mediante el parámetro ‘validate_password’.

ORACLE:

En Oracle, también existe el concepto de "perfil de usuario", pero se refiere a un conjunto de opciones de seguridad y recursos que se pueden asignar a un usuario específico. Estos pueden incluir límites en cuanto al tiempo de inactividad, el número máximo de sesiones, y los recursos de CPU y memoria.
Un ejemplo de creación de un perfil podría ser:
   create profile nombreLimite Limit
   sessions_per_user 2
   connect_time 5
   idle_time 3
   failed_login_attempts 2;

Los recursos que limitamos son recursos del kernel: uso de la CPU, duración de sesión, etc.
Y también limites de uso de las claves de acceso (passwords): duración, intentos de acceso, reuso, etc. 

Algunas de las opciones de “CREATE PROFILE” o “ALTER PROFILE” son:

    • CONNECT_TIME: Límite para el tiempo de conexión permitido para una sesión. Este limite se establece en minutos.

    • IDLE. TIME: Limite para el tiempo de inactividad permitido para una sesión. Este límite se establece en minutos.

    • SESSIONS_PER_USER: Límite para el número de sesiones activas permitidas para un usuario.

    • CPU_PER_SESSION: Límite para el uso de CPU permitido para una sesión. Este limite se establece en segundos.

    • CPU_PER_CALL: Límite para el uso de CPU permitido para una llamada a un procedimiento almacenado. Este limite se establece en segundos.

    • LOGICAL_READS_PER_SESSION: Limite para el número de lecturas lógicas permitidas para una sesión.

    • LOGICAL_READS_PER_CALL: Límite para el número de lecturas lógicas permitidas para una llamada a un procedimiento almacenado.

    • PRIVATE_SGA: Límite para el uso de memoria en el área de trabajo privada (SGA) permitido para una sesión. Este limite se establece en bytes.

Por ejemplo, para limitar el tiempo de inactividad en una sesión (En 30 minutos):
```sql
ALTER PROFILE default LIMIT IDLE_TIME  30;
```

En resumen, los perfiles de MySQL y Oracle son similares en el sentido de que ambos se utilizan para establecer límites y restricciones para los usuarios, pero los detalles específicos de lo que se puede limitar pueden variar entre los dos sistemas.


#### 5. Realiza consultas al diccionario de datos de MySQL para averiguar todos los privilegios que tiene un usuario concreto.

Si ejecutamos la sentencia “SHOW GRANTS;” veremos los privilegios del usuario actual.
```sql
SHOW GRANTS;
```
![Ejercicio 5](capturas/mysql-5-1.png)


**Nota:** Para ver con que usuario estamos conectados usamos:
```sql
SELECT CURRENT_USER();
```
![Ejercicio 5](capturas/mysql-5-2.png)

Para comprobar los privilegios de un usuario en concreto usamos:
```sql
SHOW GRANTS FOR ‘Usuario’;
```
![Ejercicio 5](capturas/mysql-5-3.png)


#### 6. Realiza consultas al diccionario de datos en MySQL para averiguar qué usuarios pueden consultar una tabla concreta.

Para ello debemos de realizar una consulta combinada de la tablas mysql.db y mysql.tables_priv. La tabla mysql.db contiene información sobre los privilegios a nivel de base de datos. En cambio la tabla mysql.tables_priv contiene información sobre los privilegios de nivel de tabla.

Ambas se puede consultar y, aunque es posible actualizarlas directamente, es mejor usar GRANT para establecer privilegios.

Para comprobar los distintos tipos de datos que podemos consultar usaremos:
```sql
describe mysql.db;
```
![Ejercicio 6](capturas/mysql-6-1.png)

```sql
desc mysql.tables_priv;
```
![Ejercicio 6](capturas/mysql-6-2.png)

A continuación realizaremos la siguiente consulta para averiguar los usuarios que pueden consultar una tabla concreta:
```sql
select t.user, d.host from mysql.tables_priv t, mysql.db d where table_name='Profesor' and t.user=d.user and select_priv='Y';
```

Como vemos en el campo table_name seleccionamos la tabla y como queremos comprobar los usuarios que puedan “consultar” dicha tabla, establecemos el campo select_priv en “Y”.


### ORACLE:
       
#### 7. Realiza un procedimiento llamado PermisosdeAsobreB que reciba dos nombres de usuario y muestre los permisos que tiene el primero de ellos sobre objetos del segundo.


**NO REALIZADO**


#### 8. Realiza un procedimiento llamado MostrarInfoPerfil que reciba el nombre de un perfil y muestre su composición y los usuarios que lo tienen asignado.

- Procedimiento principal
```sql
create or replace procedure MostrarInfoPerfil (p_perfil VARCHAR2)
is
begin
MostrarComposicionPerfil(p_perfil);
MostrarUsuariosPerfil(p_perfil);
end;
/
```

- Procedimientos dependientes (Compilar antes del procedimiento principal)
```sql
create or replace procedure MostrarComposicionPerfil(p_perfil VARCHAR2)
is
cursor c_composicion is
select resource_name from dba_profiles where profile = p_perfil;
begin
dbms_output.put_line(chr(10)||'Composicion del perfil: '||chr(10));
for recurso in c_composicion loop
dbms_output.put_line(' - '|| recurso.resource_name);
end loop;
end;
/

create or replace procedure MostrarUsuariosPerfil (p_perfil VARCHAR2)
is
cursor c_usuarios is
select username from dba_users where profile = p_perfil;
begin
dbms_output.put_line(chr(10)||'Usuarios asignados al perfil: '||chr(10));
for usuario in c_usuarios loop
dbms_output.put_line(' - ' || usuario.username);
end loop;
end;
/
```

- Comprobación:
![Ejercicio 8](capturas/mysql-8-1.png)

## Parte Grupal:

## Alumno 4 (MongoDB y ORACLE):

### MongoDB:

#### 1. Averigua si existe la posibilidad en MongoDB de limitar el acceso de un usuario a los datos de una colección determinada.

Se puede realizar mediante el uso de roles.

Ejemplo:

Creamos un nuevo rol con permisos de lectura solo para la colección "collection1" en la base de datos "dbprueba".

```mongo
    db.createRole({
        role: "rol1",
        privileges: [
            { resource: { db: "dbprueba", collection: "collection1" }, actions: [ "find" ] }
        ],
        roles: []
    })
```

Asignamos el rol a un usuario y de esta manera estaria restringido el acceso al resto de colecciones.

```mongo
    db.grantRolesToUser("prueba", [ "rol1" ])
```

#### 2. Averigua si en MongoDB existe el concepto de privilegio del sistema y muestra las diferencias más importantes con ORACLE.

Oracle tiene dos tipos de privilegios para el usuario:

System:

	Permite al usuario realizar tareas administrativas.

Object:

	En este caso le permite al usuario crear algunos objetos en la base de datos, como tabla, vista, función…


En el caso de MongoDB no tenemos esos permisos si no roles

Un rol es un conjunto de privilegios.

Un privilegio define una acción o acciones que se puede realizar sobre un recurso

Los recursos

	Bases de datos
	Colecciones
	Conjunto de colecciones
	Nivel de cluster: representa operaciones sobre el conjunto de réplica o el cluster de shards

Un rol puede heredar privilegios de otros roles

Tipos de roles

	Roles predefinidos del sistema: son los que ya se encuentran creados por el sistema

	Roles definidos por el usuario: son los creados por el administrador del sistema

#### 3. Explica los roles por defecto que incorpora MongoDB y como se asignan a los usuarios.

-read: permite leer datos de todas las colecciones.

-readWrite: permite leer y escribir datos de todas las colecciones.

-dbAdmin: permite realizar tareas administrativas.

-userAdmin: permite crear y modificar usuarios y roles en la base de datos actual

-dbOwner: puede efectuar cualquier operación administrativa en la base de datos. Por lo tanto, junta los privilegios de readWrite, dbAdmin y userAdmin.

-clusterMonitor: permite acceso de solo lectura a las herramientas de supervisión.

-clusterManager: permite realizar acciones de administración y monitorización en el cluster.

-hostManager: permite monitorizar y administrar servidores.

-clusterAdmin: combina los tres roles anteriores, añadiendo además el rol dropDatabase.

-backup: permite realizar copias de seguridad de los datos.

-restore: permite restaurar los datos de las copias de seguridad.


-Roles de superusuarios:

	-userAdmin
	-dbOwner
	-userAdminAnyDatabase
	-root: asigna privilegios completos sobre todos los recursos del sistema.

-Roles de todas las bases de datos:

	-readAnyDatabase: es el mismo rol que read pero se aplica a todas las bases de datos.
	-readWriteAnyDatabase: es el mismo rol que readWrite pero se aplica a todas las bases de datos.
	-userAdminAnyDatabase: es el mismo rol que userAdmin pero se aplica a todas las bases de datos.
	-dbAdminAnyDatabase: es el mismo rol que dbAdmin pero se aplica a todas las bases de datos.

Cuando estamos creando el usuario:
```mongo
db.createUser( {user: "USUARIO", pwd: "PASS", roles: [ { role: "NOMBRE DEL ROL", db: "DB" } ] })
```

Cuando ya está creado el usuario:
```mongo
db.grantRolesToUser( "USUARIO", [ { role : "NOMBRE DEL ROL", db : "DB" }, "NOMBRE DEL ROL", … ])
```

#### 4. Explica como puede consultarse el diccionario de datos de MongoDB para saber que roles han sido concedidos a un usuario y qué privilegios incluyen.

Para poder ver los roles que tiene un usuario sobre una base de datos primero tenemos que seleccionar la base de datos.

```mongo
    use test
```

Y para consultar los roles que tiene usamos la siguiente instrucción:

```mongo
    db.getUser("nombre-usuario")
```

Para ver los privilegios que tiene un rol usamos la siguiente instrucción:

```mongo
    db.getRole("role_name")
```

### ORACLE:

#### 5. Realiza un procedimiento llamado MostrarObjetosAccesibles que reciba un nombre de usuario y muestre todos los objetos a los que tiene acceso.

En este caso realizaré el procedimiento de forma que te muestre el objeto, junto con el tipo de objeto. Además para estructurarlo ordenadamente, lo ordenaré por tipo de objeto.
```sql
CREATE OR REPLACE PROCEDURE MostrarObjetosAccesibles (p_usuario VARCHAR2)
IS
CURSOR c_objetos IS
SELECT object_name, object_type from sys.dba_objects where owner=upper(p_usuario) order by object_type;
v_objeto c_objetos%rowtype;
BEGIN
dbms_output.put_line('Lista de objetos del usuario '||p_usuario||chr(10));
open c_objetos;
fetch c_objetos into v_objeto;
while c_objetos%found and c_objetos%rowcount>0 loop
dbms_output.put_line('Objeto: '||v_objeto.object_name||chr(10)||'Tipo: '||v_objeto.object_type||chr(10));
fetch c_objetos into v_objeto;
end loop;
if c_objetos%rowcount<=0 then
raise_application_error(-20001,'No existen objetos accesibles para el usuario '||p_usuario);
end if;
END;
/
```

- Comprobación con una ejecución correcta:
![Ejercicio 5](capturas/ejecucion-correcta.png)

- Comprobación con una ejecución incorrecta:
![Ejercicio 5](capturas/ejecucion-erronea.png)

#### 6. Realiza un procedimiento que reciba un nombre de usuario, un privilegio y un objeto y nos muestre el mensaje 'SI, DIRECTO' si el usuario tiene ese privilegio sobre objeto concedido directamente, 'SI, POR ROL' si el usuario lo tiene en alguno de los roles que tiene concedidos y un 'NO' si el usuario no tiene dicho privilegio.


**NO REALIZADO**


## CASO PRÁCTICO 1:

#### 1. (ORACLE, Postgres, MySQL) Crea un usuario llamado Becario y, sin usar los roles de ORACLE, dale los siguientes privilegios: (1,5 puntos)

    • Conectarse a la base de datos.
    
    • Modificar el número de errores en la introducción de la contraseña de cualquier usuario.
    
    • Modificar índices en cualquier esquema (este privilegio podrá pasarlo a quien quiera)
    
    • Insertar filas en scott.emp (este privilegio podrá pasarlo a quien quiera)
    
    • Crear objetos en cualquier tablespace.
    
    • Gestión completa de usuarios, privilegios y roles.
    
---------------------------------------------------------------------------------------------------------------------------------------------

#### VERSIÓN ORACLE:
Creación el usuario becario
```sql 
CREATE USER becario IDENTIFIED BY becario;
```
Asignación de privilegios para conectarse a la base de datos
```sql
GRANT CREATE SESSION TO becario;
```
- Comprobación de inicio de sesión:
```sql
connect becario/becario;
```
![Ejercicio 1](capturas/cs-oracle-1-1.png)

Modificación del número de errores en la introducción de la contraseña de cualquier usuario:

- Creamos el perfil que defina los límites en este caso hasta 5 intentos:
```sql
CREATE PROFILE limitpass LIMIT FAILED_LOGIN_ATTEMPTS 5;
```
![Ejercicio 1](capturas/cs-oracle-1-2.png)

- Le damos al usuario becarios la posibilidad de dar dicho perfil:
```sql
GRANT ALTER USER TO becario;
alter user becario profile limitpass;
```
![Ejercicio 1](capturas/cs-oracle-1-3.png)

- Ahora asignamos el perfil del usuario mediante ALTER USER para que use dicho perfil, en este caso el usuario becario y el usuario usuario1:
```sql
connect becario/becario;
ALTER USER becario PROFILE limitpass;
ALTER USER usuario1 PROFILE limitpass;
```
![Ejercicio 1](capturas/cs-oracle-1-4.png)

- Comprobación de cuantos intentos de conexión tiene el usuario becario:
![Ejercicio 1](capturas/cs-oracle-1-5.png)

- Comprobación de cuantos intentos de conexión tiene el usuario usuario1:
![Ejercicio 1](capturas/cs-oracle-1-6.png)

- Vamos a hacer una consulta para ver los usuarios que tienen el perfil bloqueado:
```sql
SELECT USERNAME, ACCOUNT_STATUS FROM DBA_USERS WHERE USERNAME = 'BECARIO' OR USERNAME = 'USUARIO1';
```
![Ejercicio 1](capturas/cs-oracle-1-7.png)

- Vamos a desbloquear el perfil del usuario becario:
```sql
ALTER USER BECARIO ACCOUNT UNLOCK;
```
![Ejercicio 1](capturas/cs-oracle-1-8.png)

Modificación de índices en cualquier esquema (este privilegio podrá pasarlo a quien quiera):
```sql
GRANT ALTER ANY INDEX TO becario WITH ADMIN OPTION;
```
![Ejercicio 1](capturas/cs-oracle-1-9.png)

- Haremos que se lo pase a otro usuario:
```sql
connect becario/becario;
GRANT ALTER ANY INDEX TO usuario1;
```
![Ejercicio 1](capturas/cs-oracle-1-10.png)

- Ver los indices:
```sql
SELECT INDEX_NAME, TABLE_OWNER, TABLE_NAME FROM ALL_INDEXES WHERE TABLE_OWNER = 'SCOTT';
```
Vemos que en la tabla emp hay un índice llamado PK_EMP y otro en la tabla dept llamado PK_DEPT.
![Ejercicio 1](capturas/cs-oracle-1-11-1.png)

- Comprobación de que el usuario becario puede modificar índices en la tabla emp:
```sql
connect becario/becario;
ALTER INDEX SCOTT.PK_EMP RENAME TO PK_EMP_BECARIO;
ALTER INDEX SCOTT.PK_EMP_BECARIO RENAME TO PK_EMP;
```
![Ejercicio 1](capturas/cs-oracle-1-11-2.png)

- Como superusuario, comprobamos que el índice se ha renombrado:
```sql
SELECT INDEX_NAME, TABLE_OWNER, TABLE_NAME FROM ALL_INDEXES WHERE TABLE_OWNER = 'SCOTT';
```
![Ejercicio 1](capturas/cs-oracle-1-11-3.png)

Insertar filas en scott.emp (este privilegio podrá pasarlo a quien quiera):
```sql
GRANT INSERT ON SCOTT.EMP TO becario with GRANT OPTION;
```
![Ejercicio 1](capturas/cs-oracle-1-12.png)

- Haremos que se lo pase a otro usuario:
```sql
connect becario/becario;
GRANT INSERT ON SCOTT.EMP TO usuario1;
```
![Ejercicio 1](capturas/cs-oracle-1-13.png)

- Comprobación de que el usuario becario puede insertar en la tabla emp:
```sql
connect becario/becario;
INSERT INTO SCOTT.EMP VALUES (9999, 'BECARIO', 'ANALISTA', 7839, SYSDATE, 5000, NULL, 10);
```
![Ejercicio 1](capturas/cs-oracle-1-14.png)

- Comprobación de que el usuario usuario1 puede insertar en la tabla emp:
```sql
connect usuario1/usuario1;
INSERT INTO SCOTT.EMP VALUES (9998, 'USUARIO1', 'ANALISTA', 7839, SYSDATE, 5000, NULL, 10);
```
![Ejercicio 1](capturas/cs-oracle-1-15.png)

- Consulta de la tabla emp para comprobar que se han insertado los registros:
```sql
SELECT * FROM SCOTT.EMP WHERE EMPNO = 9999 OR EMPNO = 9998;
```
![Ejercicio 1](capturas/cs-oracle-1-16.png)

Crear objetos en cualquier tablespace:
```sql
GRANT UNLIMITED TABLESPACE TO becario;
GRANT CREATE ANY TABLE TO becario;
```
![Ejercicio 1](capturas/cs-oracle-1-17.png)

- Comprobación de que el usuario becario puede crear objetos en cualquier tablespace:
```sql
connect becario/becario;
CREATE TABLE BECARIO (ID NUMBER(10), NOMBRE VARCHAR2(50));
CREATE TABLE SCOTT.BECARIO (ID NUMBER(10), NOMBRE VARCHAR2(50));
```
![Ejercicio 1](capturas/cs-oracle-1-18.png)

Gestión completa de usuarios, privilegios y roles:
- Gestión de usuarios:
```sql
GRANT CREATE USER TO becario;
GRANT BECOME USER TO becario;
GRANT ALTER USER TO becario;
GRANT DROP USER TO becario;
```
![Ejercicio 1](capturas/cs-oracle-1-19.png)

- Gestión de privilegios:
```sql
GRANT ALL PRIVILEGES TO becario;
```
![Ejercicio 1](capturas/cs-oracle-1-20.png)

- Gestión de roles:
```sql
GRANT CREATE ROLE TO becario;
GRANT ALTER ANY ROLE TO becario;
GRANT DROP ANY ROLE TO becario;
GRANT GRANT ANY ROLE TO becario;
```
![Ejercicio 1](capturas/cs-oracle-1-21.png)

---------------------------------------------------------------------------------------------------------------------------------------------

#### VERSIÓN POSTGRE:

Creación el usuario becario
```sql
CREATE USER becario WITH PASSWORD 'becario';
```
![Ejercicio 1](capturas/cs-postgre-1-1.png)

Asignación de privilegios para conectarse a la base de datos
```sql
CREATE DATABASE dbbecario;
GRANT CONNECT ON DATABASE dbbecario TO becario;
ALTER ROLE becario WITH LOGIN;
```
![Ejercicio 1](capturas/cs-postgre-1-2.png)

- Comprobación de inicio de sesión:
```sql
psql -U becario -d dbbecario
```
![Ejercicio 1](capturas/cs-postgre-1-3.png)

Modificación del número de errores en la introducción de la contraseña de cualquier usuario:

Este parámetro no está disponible en PostgreSQL por defecto. Para solucionar este problema, deberemos instalar el complemento pg_pam y configurarlo para que establezca el parámetro password_attempts_before_lockout.

Para ello:

1. Instalamos el complemento pg_pam
```bash
sudo apt-get install postgresql-contrib
```
2. Creamos un archivo de configuración para el complemento pg_pam
```bash
sudo nano /etc/postgresql/13/main/pg_pam.conf
```
3. Agregamos la línea siguiente al archivo de configuración:
```bash
password_attempts_before_lockout = 5
```
El fichero debe pertener al usuario postgres y al grupo postgres
```bash
sudo chown postgres:postgres /etc/postgresql/13/main/pg_pam.conf
```
4. Editamos el archivo de configuración de PostgreSQL
```bash
nano /etc/postgresql/13/main/postgresql.conf
```
5. Agregamos la siguiente línea al archivo de configuración:
```bash
shared_preload_libraries = 'pg_pam'
```
6. Reiniciamos el servicio de PostgreSQL
```bash
sudo service postgresql restart
```
Sin embargo, al tratar de iniciar sesión nos da del siguiente error:
![Ejercicio 1](capturas/cs-postgre-1-error.png)


- Creamos el perfil que defina los límites en este caso hasta 5 intentos:
```sql
CREATE ROLE limitepass     
	WITH LOGIN
    PASSWORD 'password'
    VALID UNTIL 'infinity'
    IN ROLE postgres;

ALTER ROLE limitepass
    SET password_attempts_before_lockout TO 5;
```
![Ejercicio 1](capturas/cs-postgre-1-4.png)

- Le damos al usuario becario la posibilidad de dar dicho perfil:
```sql
GRANT ALTER ANY ROLE TO becario;
```
![Ejercicio 1](capturas/cs-postgre-1-5.png)

- Ahora asignamos el perfil del usuario mediante ALTER USER para que use dicho perfil, en este caso el usuario becario y el usuario usuario1:
```sql
ALTER ROLE becario WITH ROLE limitepass;
plsql -U becarrio -d dbbecario
ALTER ROLE usuario1 WITH ROLE limitepass;
```
![Ejercicio 1](capturas/cs-postgre-1-6.png)

- Comprobación de cuantos intentos de conexión tiene el usuario becario:
```sql
psql -U usuario1 -d dbbecario
```
![Ejercicio 1](capturas/cs-postgre-1-7.png)

Modificación de índices en cualquier esquema (este privilegio podrá pasarlo a quien quiera):
```sql
ALTER ROLE becario WITH SUPERUSER;
```
![Ejercicio 1](capturas/cs-postgre-1-8.png)
- Este rol es muy arriesgado darselo a un usuario normal, por lo que si becario es propietario de tablas, tablespaces es propietario de los índices que están en ahí.

- Ejemplo:
```sql
ALTER INDEX scott.pk_dept RENAME TO pk_dept2;
```
![Ejercicio 1](capturas/cs-postgre-1-9.png)

```sql
select * from pg_indexes where tablename = 'dept';
```
![Ejercicio 1](capturas/cs-postgre-1-10.png)

- Haremos que se lo pase a otro usuario:
```sql
plsql -U becario -d dbbecario
ALTER ROLE usuario1 WITH SUPERUSER;
```
![Ejercicio 1](capturas/cs-postgre-1-11.png)

Insertar filas en scott.emp (este privilegio podrá pasarlo a quien quiera):
```sql
GRANT INSERT ON scott.emp TO becario with GRANT OPTION;
```
![Ejercicio 1](capturas/cs-postgre-1-12.png)

- Haremos que se lo pase a otro usuario:
```sql
plsql -U becario -d dbbecario
GRANT INSERT ON scott.emp TO usuario1;
```
![Ejercicio 1](capturas/cs-postgre-1-13.png)

- Comprobación:
```sql
plsql -U usuario1 -d dbbecario
INSERT INTO scott.emp VALUES (7982, 'USUARIO1', 'BECARIO', 7599,TO_DATE('03-DEC-1981', 'DD-MON-YYYY'), 3000, NULL, 20);
select * from scott.emp where empno = 7982;
```
![Ejercicio 1](capturas/cs-postgre-1-14.png)
-
![Ejercicio 1](capturas/cs-postgre-1-15.png)


Crear objetos en cualquier tablespace:
- Creamos una carpeta para el tablespace:
```bash
mkdir /var/lib/postgresql/13/main/dbbecario
```
- Creamos un tablespace:
```sql
CREATE TABLESPACE dbbecario LOCATION '/var/lib/postgresql/13/main/dbbecario';
```
![Ejercicio 1](capturas/cs-postgre-1-17.png)
- En postgresql tenemos que indicar el nombre del tablespace en concreto, si no tiene el role de superuser:
```sql
GRANT CREATE ON TABLESPACE dbbecario TO becario;
```
![Ejercicio 1](capturas/cs-postgre-1-16.png)

- Probamos a crear una tabla:
```sql
CREATE TABLE becario (id int, nombre varchar(20));
```
![Ejercicio 1](capturas/cs-postgre-1-18.png)

- Comprobamos que se ha creado en el tablespace:
```sql
\d becario;
```
![Ejercicio 1](capturas/cs-postgre-1-19.png)


Gestión completa de usuarios, privilegios y roles:
- Gestión de usuarios y privilegios:
```sql
ALTER ROLE becario WITH SUPERUSER;
```
![Ejercicio 1](capturas/cs-postgre-1-20.png)

- Gestión de roles:
```sql
ALTER ROLE becario WITH CREATEROLE;
```
![Ejercicio 1](capturas/cs-postgre-1-21.png)

---------------------------------------------------------------------------------------------------------------------------------------------

#### VERSIÓN MYSQL:

- Creación del usuario becario:
![Ejercicio 1](capturas/cs-mysql-1-1.png)


#Asignación de privilegios (totales) para conectarse a la base de datos;
![Ejercicio 1](capturas/cs-mysql-1-2.png)

- Modificación del número de errores en la introducción de la contraseña de cualquier usuario:

En MySQL, para modificar el número de intentos fallidos permitidos antes de bloquear una cuenta de usuario, se debe modificar el valor de la variable del sistema "max_failed_logins". El valor por defecto es 6.
Para cambiar el valor de esta variable, se puede utilizar la siguiente sentencia SQL:
```sql
SET GLOBAL max_failed_logins = valor;
```

Reemplazamos valor con el nuevo valor deseado. Este cambio es temporal y se aplica solo a la sesión actual. 

Si se quiere que el cambio sea permanente, debería modificar el archivo de configuración de MySQL (my.cnf), añadiendo la siguiente línea en la sección [mysqld] y posteriormente reiniciar el servidor.
```bash
max_failed_logins = valor
```

**Nota:** En este caso, al estar utilizando mariadb, la ruta del fichero de configuración será:
```bash
/etc/mysql/mariadb.conf.d/50-mysqld_safe.cnf
```
![Ejercicio 1](capturas/cs-mysql-1-3.png)

      
      
- Modificar índices en cualquier esquema (este privilegio podrá pasarlo a quien quiera):

Los índices en MySQL se utilizan para mejorar el rendimiento de las consultas de selección, actualización y eliminación que utilizan cláusulas WHERE. Si una tabla no tiene un índice en la columna utilizada en una cláusula WHERE, MySQL debe examinar cada fila de la tabla para verificar si cumple con la condición. Con un índice en esa columna, MySQL puede buscar rápidamente la información deseada en el índice en lugar de examinar cada fila de la tabla.


En MySQL, no existe “ALTER INDEX”, aunque podemos utilizar:

- Crear index: 
```sql
CREATE INDEX
```

- Eliminar index: 
```sql
DROP INDEX
```      

- Renombrar index: 
```sql
ALTER TABLE tabla RENAME INDEX nombre_antiguo_indice TO nombre_nuevo_indice;
```

- Para eliminar un index específico de una tabla: 
```sql
ALTER TABLE tabla DROP INDEX nombre_indice;
```      

- Para añadir un índice específico de una tabla con sentencia “ALTER TABLE”:
```sql
ALTER TABLE tabla ADD INDEX nombre_indice_nuevo(campo);
```

- Para añadir un índice específico de una tabla con sentencia CREATE INDEX:
```sql
create index indice on tabla(columna);
```
![Ejercicio 1](capturas/cs-mysql-1-4.png)

- Para mostrar los index:
```sql
show indexes from tabla;
```
![Ejercicio 1](capturas/cs-mysql-1-5.png)

Además de agregar un índice normal, también se puede agregar un índice UNIQUE, que garantiza que los valores en las columnas incluidas en el índice son únicos:
```sql
ALTER TABLE nombre_de_tabla ADD UNIQUE nombre_índice (campo1, campo2, ...);
```

También se puede agregar un índice FULLTEXT, que se utiliza para buscar palabras o frases en una o varias columnas de tipo texto:
```sql
ALTER TABLE nombre_de_tabla ADD FULLTEXT nombre_índice (campo1, campo2, ...);
```

Para asignar este privilegio usamos:
![Ejercicio 1](capturas/cs-mysql-1-6.png)

- Insertar filas en scott.emp (este privilegio podrá pasarlo a quien quiera)

He añadido el esquema scott a mi escenario.
![Ejercicio 1](capturas/cs-mysql-1-7.png)


Ahora vamos a darle el privilegio de inserción de datos al usuario “becario”. Para ello utilizamos la siguiente sentencia:
```sql
GRANT INSERT ON dept to 'becario'@'localhost' IDENTIFIED BY "becario" WITH GRANT OPTION;
```
![Ejercicio 1](capturas/cs-mysql-1-8.png)

Para comprobarlo, vamos a loguearnos con el usuario becario. Posteriormente realizamos una prueba de inserción y una consulta:
![Ejercicio 1](capturas/cs-mysql-1-9.png)

Como podemos comprobar podemos insertar datos pero no podemos consultar datos ya que no tenemos concedido ese privilegio.


- Crear objetos en cualquier tablespace.

Antes que nadas debemos de analizar los 2 tipos de tablespace que existen en MySQL:

1. Los tablespaces de sistema: son aquellos que vienen incluidos por defecto en una instalación de MySQL. Como por ejemplo el tablespace "mysql" que almacena las tablas de sistema de MySQL, y el tablespace "information_schema" que almacena la información de metadatos de las tablas.
   
2. Los tablespaces de usuario: son los tablespaces creados por un usuario para almacenar tablas y índices personalizados. El usuario tiene control completo sobre estos tablespaces, incluyendo la capacidad de crear, eliminar, modificar y asignar tablas y índices a ellos.
En este caso, no vamos a enfocar en los tablespaces de usuario.

De la misma forma que hemos visto anteriormente con los índices, concediendo el permiso CREATE al usuario, ya le permitiremos crear objetos en cualquier tablespace.
```sql
GRANT CREATE ON *.* TO 'becario'@'localhost';
```

Para modificar cualquier tablespace y así crear o eliminar objetos usamos la siguiente sintaxis:
```sql
ALTER TABLESPACE nombre_tablespace {ADD | DROP} DATAFILE 'nombre_archivo';
```

Si en cambio queremos crear un nuevo tablespace, usamos:
```sql
CREATE TABLESPACE `nuevo_tablespace` ADD DATAFILE 'nuevo_tablespace.ibd'
```

Como vemos, se crea un archivo con extensión .ibd bajo el mismo directorio donde está el tablespace general (/var/lib/mysql/). Podemos especificar una ruta absoluta:
```sql
CREATE TABLESPACE `nuevo_tablespace` ADD DATAFILE '/home/ubuntu/nuevo_tablespace.ibd'
```

- Gestión completa de usuarios, privilegios y roles.

Para darle a un usuario todos los permisos necesarios para la gestión completa de usuarios, privilegios y roles debemos de convertirlo en administrador, para ello le damos todos los privilegios, de la siguiente forma:
```sql
GRANT ALL PRIVILEGES ON *.* TO ‘becario’@’localhost’ WITH GRANT OPTION;
```
![Ejercicio 1](capturas/cs-mysql-1-10.png)



---------------------------------------------------------------------------------------------------------------------------------------------

#### 2. (ORACLE, Postgres, MySQL) Escribe una consulta que obtenga un script para quitar el privilegio de borrar registros en alguna tabla de SCOTT a los usuarios que lo tengan.

#### VERSIÓN ORACLE:
- Script:
```sql
select 'revoke delete on SCOTT.'||table_name||' from ' || grantee ||';'
  from DBA_TAB_PRIVS
  where OWNER='SCOTT'
  and PRIVILEGE='DELETE';
```
- Para comprobarlo le daremos el privilegio a becario y luego ejecutaremos el script:
```sql
grant delete on SCOTT.DEPT to becario;
```
![Ejercicio 2](capturas/cs-oracle-2-1.png)

---------------------------------------------------------------------------------------------------------------------------------------------

#### VERSIÓN POSTGRE:
- Script:
```sql
select 'Revoke Delete on '||table_catalog||'.'||table_name||' from '||grantee||';'
from information_schema.role_table_grants
where table_catalog='scott'
and privilege_type='DELETE'
and table_schema='scott';
```
- Para comprobarlo le daremos el privilegio a becario y luego ejecutaremos el script:
```sql
grant delete on scott.dept to becario;
```
![Ejercicio 2](capturas/cs-postgre-2-1.png)

---------------------------------------------------------------------------------------------------------------------------------------------

#### VERSIÓN MYSQL:

- Script:
```sql
select concat('Revoke Delete on ',table_schema,'.',table_name,' from ',grantee,';') as script
from information_schema.table_privileges
where table_schema='scott'
and privilege_type='DELETE';
```

Para realizar la comprobación, le he dado el privilegio DELETE sobre la tabla dept al usuario becario:
```sql
GRANT DELETE ON dept to 'becario'@'localhost' IDENTIFIED BY "becario" WITH GRANT OPTION;
```
![Ejercicio 1](capturas/cs-mysql-2-1.png)

Ahora sí, ejecutamos la consulta anterior para obtener el script.
![Ejercicio 1](capturas/cs-mysql-2-2.png)

---------------------------------------------------------------------------------------------------------------------------------------------

#### 3. (ORACLE) Crea un tablespace TS2 con tamaño de extensión de 256K. Realiza una consulta que genere un script que asigne ese tablespace como tablespace por defecto a los usuarios que no tienen privilegios para consultar ninguna tabla de SCOTT, excepto a SYSTEM.

- Creación del tablespace:
```sql
create tablespace TS2 
  datafile 'tbs_ts2.dbf' 
  size 256k;
```
![Ejercicio 3](capturas/cs-oracle-3-1.png)

- Script:
```sql
select 'alter user "'||username||'" default tablespace TS2;'
  from DBA_USERS
  where USERNAME!='SYSTEM'
  and USERNAME not in (select GRANTEE 
                         from DBA_TAB_PRIVS 
                         where PRIVILEGE='SELECT' 
                         and OWNER='SCOTT');
```
![Ejercicio 3](capturas/cs-oracle-3-2.png)

- Salida:

![Ejercicio 3](capturas/cs-oracle-3-3.png)

---------------------------------------------------------------------------------------------------------------------------------------------

#### 4. (ORACLE, Postgres) Realiza un procedimiento que reciba un nombre de usuario y nos muestre cuántas sesiones tiene abiertas en este momento. Además, para cada una de dichas sesiones nos mostrará la hora de comienzo y el nombre de la máquina, sistema operativo y programa desde el que fue abierta.

#### VERSIÓN ORACLE:
- Procedimiento:
```sql
create or replace procedure ExcepcionesSesion(p_usuario varchar2)
is
	v_existe number(1):=0;
begin
	select count(*) into v_existe
	from dba_users
	where USERNAME=p_usuario;
	if v_existe=0 then
		raise_application_error(-20031,'El usuario que buscas no existe.');
	end if;
end ExcepcionesSesion;
/

create or replace procedure p_Sesiones(p_usuario varchar2)
is
	cursor c_sesiones is
	select MACHINE as maquina,to_char(LOGON_TIME,'YYYY/MM/DD HH24:MI') as comienzo,program as programa
	from v$session 
	where USERNAME=p_usuario;
	v_contador number(2):=1;
begin
	for v_sesiones in c_sesiones loop
		dbms_output.put_line('Sesion '||v_contador||'->');
		dbms_output.put_line('Hora de comienzo: '||v_sesiones.comienzo);
		dbms_output.put_line('Nombre Maquina: '||v_sesiones.maquina);
		dbms_output.put_line('Nombre Programa: '||v_sesiones.programa);
		v_contador:=v_contador+1;
	end loop;
end p_Sesiones;
/

create or replace procedure p_SesionesAbiertas(p_usuario varchar2)
is
	v_sesiones_abiertas number(2):=0;
begin
	select count(*) into v_sesiones_abiertas
	from v$session
	where USERNAME=p_usuario;
	dbms_output.put_line('Sesiones abiertas: '||v_sesiones_abiertas);
end p_SesionesAbiertas;
/

create or replace procedure ver_conexiones(p_usuario varchar2)
is
begin
	dbms_output.put_line('Usuario: '||p_usuario);
	ExcepcionesSesion(p_usuario);
	p_SesionesAbiertas(p_usuario);
	p_Sesiones(p_usuario);
end ver_conexiones;
/
```
Comprobaciones:
- Usuario SCOTT (el cual no está conectado):
```sql
exec ver_conexiones('SCOTT');
```
![Ejercicio 4](capturas/cs-oracle-4-1.png)

- Usuario SYS:
```sql
exec ver_conexiones('SYS');
```
![Ejercicio 4](capturas/cs-oracle-4-2.png)

- Usuario Becario (para conectarnos como Becario al mismo tiempo que ejecutamos el procedimiento, abrimos una nueva ventana de SQLPlus y nos conectamos como Becario):
```sql
exec ver_conexiones('BECARIO');
```
![Ejercicio 4](capturas/cs-oracle-4-3.png)

- Usuario inexistente:
```sql
exec ver_conexiones('inexiste');
```
![Ejercicio 4](capturas/cs-oracle-4-4.png)

---------------------------------------------------------------------------------------------------------------------------------------------

#### VERSIÓN POSTGRE:

- Procedimiento:
```sql
CREATE OR REPLACE FUNCTION ver_excepciones(p_usuario VARCHAR)
RETURNS VARCHAR
AS $$
DECLARE
    v_existe INTEGER := 0;
BEGIN
    SELECT COUNT(*) INTO v_existe
    FROM pg_user
    WHERE usename = p_usuario;

    IF v_existe = 0 THEN
        RAISE EXCEPTION 'El usuario que buscas no existe.';
    END IF;

    RETURN 'OK';
END;
$$ LANGUAGE plpgsql;

CREATE OR REPLACE FUNCTION ver_sesiones(p_usuario VARCHAR)
RETURNS VARCHAR
AS $$
DECLARE
    v_contador INTEGER := 1;
    v_sesiones RECORD;
BEGIN
    FOR v_sesiones IN SELECT * FROM pg_stat_activity WHERE usename = p_usuario LOOP
        RAISE NOTICE 'Sesion % ->', v_contador;
        RAISE NOTICE 'Hora de comienzo: %', v_sesiones.backend_start;
        RAISE NOTICE 'Nombre Base de Datos: %', v_sesiones.datname;
        RAISE NOTICE 'Nombre Programa: %', v_sesiones.application_name;
        v_contador := v_contador + 1;
    END LOOP;
    
    RETURN 'OK';
END;
$$ LANGUAGE plpgsql;

CREATE OR REPLACE FUNCTION ver_sesiones_abiertas(p_usuario VARCHAR)
RETURNS VARCHAR
AS $$
DECLARE
    v_sesiones_abiertas INTEGER := 0;
BEGIN
    SELECT COUNT(*) INTO v_sesiones_abiertas
    FROM pg_stat_activity
    WHERE usename = p_usuario;
    RAISE NOTICE 'Sesiones abiertas: %', v_sesiones_abiertas;
    RETURN 'OK';
END;
$$ LANGUAGE plpgsql;


CREATE OR REPLACE FUNCTION ver_conexiones(p_usuario VARCHAR)
RETURNS VARCHAR
AS $$
DECLARE
  v_excepcion VARCHAR;
BEGIN
  RAISE NOTICE 'Usuario: %', p_usuario;
  v_excepcion := ver_excepciones(p_usuario);
  IF v_excepcion = 'OK' THEN
    PERFORM ver_sesiones_abiertas(p_usuario);
    PERFORM ver_sesiones(p_usuario);
  END IF;
  RETURN 'OK';
END;
$$ LANGUAGE PLPGSQL;
```
Comprobaciones:
- Usuario becario (el cual no está conectado):
```sql
SELECT ver_conexiones('becario');
```
![Ejercicio 4](capturas/cs-postgre-4-1.png)

- Usuario Postgres:
```sql
SELECT ver_conexiones('postgres');
```
![Ejercicio 4](capturas/cs-postgre-4-2.png)

- Usuario inexistente:
```sql
SELECT ver_conexiones('inexiste');
```
![Ejercicio 4](capturas/cs-postgre-4-3.png)

---------------------------------------------------------------------------------------------------------------------------------------------

#### 5. (ORACLE) Realiza un procedimiento que muestre los usuarios que pueden conceder privilegios de sistema a otros usuarios y cuales son dichos privilegios.

- Procedimiento:
```sql
create or replace procedure UsuarioSimple(p_rol varchar2,p_privilegio varchar2)
is
	cursor c_usuarios is
	select GRANTEE
	from dba_role_privs
	where GRANTED_ROLE=p_rol;
begin
	for v_usuarios in c_usuarios loop
		dbms_output.put_line('--------------------------------');
		dbms_output.put_line(chr(13));
		dbms_output.put_line('Usuario: '||v_usuarios.GRANTEE);
		dbms_output.put_line('Privilegio: '||p_privilegio);
		dbms_output.put_line(chr(13));
		dbms_output.put_line('--------------------------------');
	end loop;
end UsuarioSimple;
/

create or replace procedure UsuarioCompuesto(p_rol varchar2,p_privilegio varchar2)
is
	cursor c_compuesto is
	select GRANTEE
   	from dba_role_privs
	start with GRANTED_ROLE = p_rol
        connect by GRANTED_ROLE = prior GRANTEE;
	v_analizar_privilegio number(1):=0;
begin
	select count(*) into v_analizar_privilegio
	from role_sys_privs
	where ROLE=p_rol
	and PRIVILEGE=p_privilegio;
	if v_analizar_privilegio != 0 then
		for v_compuesto in c_compuesto loop
			UsuarioSimple(v_compuesto.GRANTEE,p_privilegio);
		end loop;
	else
		UsuarioSimple(p_rol,p_privilegio);
	end if;
end UsuarioCompuesto;
/

create or replace procedure PrivSuperUserRol
is
	cursor c_privs is
	select GRANTEE,PRIVILEGE
	from dba_sys_privs
	where ADMIN_OPTION='YES'
	and GRANTEE in (SELECT ROLE
			FROM DBA_ROLES);
	v_compuesto number(1):=0;
begin
	for v_privs in c_privs loop
		SELECT count(*) into v_compuesto
		FROM DBA_ROLE_PRIVS
		where GRANTED_ROLE=v_privs.GRANTEE;
		if v_compuesto=0 then
			UsuarioSimple(v_privs.GRANTEE,v_privs.PRIVILEGE);
		else
			UsuarioCompuesto(v_privs.GRANTEE,v_privs.PRIVILEGE);
		end if;
	end loop;
end PrivSuperUserRol;
/


create or replace procedure PrivSuperUserDirecto
is
	cursor c_privsd is
	select GRANTEE,PRIVILEGE
	from dba_sys_privs
	where ADMIN_OPTION='YES'
	and GRANTEE in (SELECT USERNAME
			FROM DBA_USERS);
begin
	for v_privsd in c_privsd loop
		dbms_output.put_line('--------------------------------');
		dbms_output.put_line(chr(13));
		dbms_output.put_line('Usuario: '||v_privsd.GRANTEE);
		dbms_output.put_line('Privilegio: '||v_privsd.PRIVILEGE);
		dbms_output.put_line(chr(13));
		dbms_output.put_line('--------------------------------');
	end loop;
end PrivSuperUserDirecto;
/

create or replace procedure privilegios_superusuario
is
begin
	dbms_output.put_line('--------------------------------');
	dbms_output.put_line('Usuarios que pueden dar privilegios');
	dbms_output.put_line('--------------------------------');
	PrivSuperUserDirecto;
	PrivSuperUserRol;
end privilegios_superusuario;
/
```
- Comprobación:
```sql
exec privilegios_superusuario;
```
![Ejercicio 5](capturas/cs-oracle-5-1.png)
-
![Ejercicio 5](capturas/cs-oracle-5-2.png)
-
![Ejercicio 5](capturas/cs-oracle-5-3.png)
-
![Ejercicio 5](capturas/cs-oracle-5-4.png)
-
![Ejercicio 5](capturas/cs-oracle-5-5.png)
-
![Ejercicio 5](capturas/cs-oracle-5-6.png)

---------------------------------------------------------------------------------------------------------------------------------------------

## EJERCICIO GRUPAL 3:

### Elaboración de un vídeo grupal resumiendo las diferencias de concepto y en la gestión de usuarios, permisos de sistema y permisos sobre objetos, roles y perfiles entre los cuatro SGBDs estudiados. Cada miembro del grupo hablará de uno de los siguientes temas:

#### a) Usuarios y permisos sobre objetos.

#### b) Permisos de sistema.

#### c) Roles.

#### d) Perfiles.

---------------------------------------------------------------------------------------------------------------------------------------------
