# Design Document: API REST CONTACTOS

##1. Descripción
Ejemplo de una API REST para gestionar contactos en una BD utilizando FAST API

## Objetivo
Realizar un ejemplo de diseño de una API REST de tipo CRUD y su posterior codificacion utilizando el framework [FASTAPI](https://fastapi.tiangolo.com/).

##3. Diseño de a BD
Para este ejemplo se utilizará el gestor de bases de datos [SQLite](https://sqlite.org). con las siguientes tablas:

###3.1 Tabla: contactos

|No.|Campo|Tipo|Restricciones|Descripción|
|--|--|--|--|--|
|1|id_contactos|int|PRIMARY KEY|Llave primaria de la tabla|
|2|nombre|varchar(100)|Not Null|
|3|primer_apellido|varchar(50)|Not Null|
|4|segundo_apellido|varchar(50)|Not Null|
|5|email|varchar(50)|Not Null|
|6|telefono|varchar(10)|Not Null|

##3.2 Script

```sql 
CREATE TABLE IF NOT EXISTS contactos(
id_contacto INT NOT NULL,
nombre VARCHAR(100) NOT NULL,
primer_apellido VARCHAR(50) NOT NULL,
segundo_apellido VARCHAR(50) NOT NULL,
email VARCHAR(50) NOT NULL,
telefono VARCHAR(10) NOT NULL); ...
```

