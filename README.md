# Design Document: API REST CONTACTOS

##1. Descripción
Ejemplo de una API REST para gestionar contactos en una BD utilizando FAST API

##2. Objetivo
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
## 5. Diseño de los métodos

### 5.1 GET - http://localhost:8000/
|No|Propiedad|Detalle|
|--|--|--|
|1|Description|Endpoint raíz de la API|
|2|Summary|Endpoint raiz|
|3|Method|GET|
|4|Endpoint|http://localhost:8000/|
|5|QueryParam|NA|
|6|PathParam|NA|
|7|DATA|NA|
|8|Versiones|V1|
|9|Status code|200 ok|
|10|Response-Type|application/json|
|11|Response|{"version":"v1","message":"endpoint raiz","datatime":"27/09/23 10:11"}|
|12|Curl|curl -X 'GET' 'http://localhost:8000/' -H 'accept: application/json'|
|13|Status code(error)|NA|
|14|Response Type(error)|NA|
|15|Response(error)|NA|

### 5.2 GET - http://localhost:8000/contactos
|No|Propiedad|Detalle|
|--|--|--|
|1|Description|Endpoint para obtener datos|
|2|Summary|Endpoint para listar|
|3|Method|GET|
|4|Endpoint|http://localhost:8000/contactos|
|5|QueryParam|limit:int, offset:int, nombre:string|
|6|PathParam|NA|
|7|DATA|NA|
|8|Versiones|V1|
|9|Status code|200 ok|
|10|Response-Type|application/json|
|11|Response|{"version":"v1","message":"Lista de contactos","datatime":"25/9/23 9:36"}|
|12|Curl|curl -X 'GET' 'http://localhost:8000/?limit=10&offset=0&nombre=Juan' -H 'accept: application/json'|
|13|Status code(error)|400|
|14|Response Type(error)|application/json|
|15|Response(error)|{"version":"v1","message-error":"error","datatime":"21/9/27 10:16"}|

### 5.3 POST - http://localhost:8000/contactos
|No|Propiedad|Detalle|
|--|--|--|
|1|Description|Endpoint para enviar datos a la API|
|2|Summary|Endpoint para enviar datos|
|3|Method|POST|
|4|Endpoint|http://localhost:8000/contactos|
|5|QueryParam|NA|
|6|PathParam|NA|
|7|DATA|{"id_contacto":int, "nombre":string, "apellido_paterno":string, "apellido_materno":string, "email":string, "telefono":string}|
|8|Versiones|V1|
|9|Status code|201 Created|
|10|Response-Type|application/json|
|11|Response|{"version":"v1","message":"Lista de contactos","datatime":"27/09/23 4:36"}|
|12|Curl|curl -X 'POST' 'http://localhost:8000/contactos' -H 'accept: application/json' -d '{"id_contacto":int, "nombre":string, "apellido_paterno":string, "apellido_materno":string, "email":string, "telefono":string}'|
|13|Status code(error)|400 Bad Request|
|14|Response Type(error)|application/json|
|15|Response(error)|{"version":"v1","message-error":"error","datatime":"27/09/27 1:16"}|

### 5.4 DELETE - http://localhost:8000/contactos/?id_contacto=
|No|Propiedad|Detalle|
|--|--|--|
|1|Description|Endpoint para eliminar un recurso de la API|
|2|Summary|Endpoint para eliminar un recurso|
|3|Method|DELETE|
|4|Endpoint|http://localhost:8000/contactos/?id_contacto=|
|5|QueryParam|id_contacto|
|6|PathParam|NA|
|7|DATA|NA|
|8|Versiones|V1|
|9|Status code|204 No Content|
|10|Response-Type|application/json|
|11|Response|{"version":"v1","message":"Eliminación éxitosa","datatime":"25/9/23 9:36"}|
|12|Curl|curl -X 'DELETE' 'http://localhost:8000/?id_contacto=1' -H 'accept: application/json'|
|13|Status code(error)|400 Bad Request|
|14|Response Type(error)|application/json|
|15|Response(error)|{"version":"v1","message-error":"ocurrió un error al eliminar","datatime":"21/9/27 10:16"}|

### 5.5 PUT - http://localhost:8000/contactos/?id_contactos=
|No|Propiedad|Detalle|
|--|--|--|
|1|Description|Endpoint para actualizar recursos de la API|
|2|Summary|Endpoint para actulizar datos|
|3|Method|PUT|
|4|Endpoint|http://localhost:8000/contactos/?id_contacto=|
|5|QueryParam|id_contacto|
|6|PathParam|NA|
|7|DATA|NA|
|8|Versiones|V1|
|9|Status code|200 Ok|
|10|Response-Type|application/json|
|11|Response|{"version":"v1","message":"Actualización éxitosa","datatime":"25/9/23 9:36"}|
|12|Curl|curl -X 'DELETE' 'http://localhost:8000/?id_contacto=1' -H 'accept: application/json'|
|13|Status code(error)|400 Bad Request|
|14|Response Type(error)|application/json|
|15|Response(error)|{"version":"v1","message-error":"ocurrió un error al actualizar","datatime":"21/9/27 10:16"}|
