---
sidebar_position: 2
---

# us_sesion_ms
En este componente se implementarán las funcionalidades asociadas a crear e iniciar una sesiosn dentro de la aplicacion, Entre ellos la creacion y validacion de tokens de usuario.

![us_sesion_ms](/img/plantuml/us_sesion_ms.png)

Como se puede observar, se expone una interfaz por medio del protocolo REST por el cual se llegan las peticiones HTTP las cuales son procesadas por el modulo main, el modulo account se encarga de conectarse con la base de datos, y el modulo JWT se encarga de proveer las funcionalidades de generar y validar las tokens 

En este componente se utiliza una base de datos relacional en *__Postgres__* junto con un microservicio en __*Go*__ en el framework __*GorillaMUX*__ para la autenticación del usuario.

## Endpoints

### **GET** /user

Dado el Id de un usuario se retorna el email del mismo.

Parametros:

|Nombre|Tipo|Obligatorio|Descripción|
|--|--|--|--|
|ID|string|si|ID del usuario|

Return:

|Status|Causa|Respuesta|
|--|--|--|
|200|Usuario encontrado|<code>{<br/>  "uid": string,<br/>  "email": string",<br/>  "status": int",<br/>  "...": ...<br/>}</code>|
|404|Usuario no encontrado|<code>{<br/>  "error": "Usuario no encontrado."<br/>}</code>|
|...|...|...|

Ejemplo:

    GET /user/uid=6naqZXx854VKeOI3PgiWufYIldB3

### **POST** /user

Dado un email, un status, y una contrasena se crea un nuevo usuario.

Body:

|Nombre|Tipo|Obligatorio|Descripción|
|--|--|--|--|
|email|string|si|email del usuario|
|status|int|si|estado de moderacion del usuario|
|password|int|si|contraseña del usuario|
|...|...|...|...|

Return:

|Status|Causa|Respuesta|
|--|--|--|
|200|Usuario creado|<code>{<br/>"token": string,<br/>}</code>|
|401|El usuario ya existe|<code>{<br/>"error": "el usuario ya se encuentra en la base de datos."<br/>}</code>|
|...|...|...|

### **GET** /auth

Se recibe un email y una contraseña de un mismo usuario, si las credeciales son validas se retorna un token.

Body:

|Nombre|Tipo|Obligatorio|Descripción|
|--|--|--|--|
|email|string|si|email del usuario|
|password|int|si|contraseña del usuario|
|...|...|...|...|

Return:

|Status|Causa|Respuesta|
|--|--|--|
|200|Usuario Validado|<code>{<br/>"token": string,<br/>}</code>|
|401|Usuario no Validado|<code>{<br/>"error": "Credenciales no Validas."<br/>}</code>|
|...|...|...|

### **GET** /validate

Dado un token se valida si este token funciona o esta vigente.

Body:

|Nombre|Tipo|Obligatorio|Descripción|
|--|--|--|--|
|email|string|si|token de usuario|
|...|...|...|...|

Return:

|Status|Causa|Respuesta|
|--|--|--|
|200|Token Validado|<code>{<br/>"ok": string,<br/>}</code>|
|401|Token no Validado|<code>{<br/>"error": "Token no Valido."<br/>}</code>|
|...|...|...|
