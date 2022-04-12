---
sidebar_position: 3
---

# us_user_ms

*__Descripción del microservicio__*  
El microservicio de us_user_ms es el encargado de guardar toda la informacion personal del usuario que se registre en la plataforma UNSTREAM.

*__Vista de componentes y conectores__*  
![Diagrama de componentes del microservicio us_user_ms](https://www.plantuml.com/plantuml/png/DOex3a8n30Hxdy9AdpkaeQ05EeGY1vigIU7F_P4LlMvtPfevgSUQy0xhOQ9zsGV94FC0azCW4ooNvb5Iyu3xTj4VVGKVj-SheOevP8KrWxFgmKqsnvf_)   



*__Descripción de vista__*  
Respecto al diagrama de componentes anterior, el microservicio se realizo con el lenguaje de programacion Python con el framework Django, respecto a la base de datos se uso Postgres SQL, el micro servicio va conectado a la API REST.  

*__Modelo de datos__*  




## Endpoints

### **GET** /user

*__Descripción__*  
GET /user?uid=6naqZXx854VKeOI3PgiWufYIldB3  
Esta peticion devuelve la informacion personal del usuario

*__Parametros__*:

|Id_USer|
|--|
|uid|

*__Return__*:

|Nombre_Usuario|Nombre_Publico|Imagen_Perfil|Correo|Descripción|
|--|--|--|--|--|
|string|string|string|string|string|  

*__Descripción__*  
GET /user?nameUser="auronplay"  
Esta petición  busca los perfiles de usuario que tengan que ver con la entrada que se da en la petición.  

*__Parametros__*:  

|Nombre_Usuario|
|--|
|string|

*__Return__*:

|Nombre_Usuario|Imagen_Perfil|Descripción|
|--|--|--|--|--|
|string|string|string|

### **POST** 
*__Crear Usuario__*  
Esta peticion crea un usuario en la base de datos.

*__Body__*:  

|Nombre|Tipo|Obligatorio|Descripción|
|--|--|--|--|
|Nombre_Usuario|string|si|Es el nickname del usuario|
|Nombre_Publico|string|si|El nombre personal del usuario|
|Imagen_Perfil|uid|si|La imagen de perfil del usuario, la cual se guarda el id del usuario ya que la foto se guarda en el microservicio storage|
|Correo|string|si|correo del usuario
|Descripción|string|no|Descripción del usuario|
|Status|boolean|si|El estado del usuario es decir si no esta baneado de la app|


*__Return__*:

|Status|Causa|Respuesta|
|--|--|--|
|200|Usuario creado|<code>{<br/>"response": usuario creado<br/>}</code>|
|401|El usuario ya existe|<code>{<br/>"response": El usuario ya se encuentra en la base de datos<br/>}</code>|
|402|El usuario esta baneado|<code>{<br/>"response": El usuario esta baneado de la app<br/>}</code>|
|500|Error interno en el server|<code>{<br/>"response": error 500<br/>}</code>|


### **PUT**

*__Editar Usuario__*  
Esta peticion edita el perfil del usuario

*__Body__*:  

|Nombre|Tipo|Obligatorio|Descripción|
|--|--|--|--|
|Nombre_Usuario|string|no|Es el nickname del usuario|
|Nombre_Publico|string|no|El nombre personal del usuario|
|Imagen_Perfil|uid|no|La imagen de perfil del usuario, la cual se guarda el id del usuario ya que la foto se guarda en el microservicio storage|
|Correo|string|no|correo del usuario
|Descripción|string|no|Descripción del usuario|


*__Return__*:

|Status|Causa|Respuesta|
|--|--|--|
|402|Usuario |<code>{<br/>"response": usuario creado<br/>}</code>|
|401|El usuario ya existe|<code>{<br/>"response": El usuario ya se encuentra en la base de datos<br/>}</code>|
|500|Error interno en el server|<code>{<br/>"response": error 500<br/>}</code>|

*__Cambiar status del usuario__*  
Esta peticion edita el status del usuario, si el usuario tiene el status en false, este no podra ingresar a la aplicación.

*__Body__*:  

|Nombre|Tipo|Obligatorio|Descripción|
|--|--|--|--|
|Status|boolean|no|El estado del usuario es decir si no esta baneado de la app|


*__Return__*:

|Status|Causa|Respuesta|
|--|--|--|
|200|ok|<code>{<br/>"response":ok<br/>}</code>|
|500|Error interno en el server|<code>{<br/>"response": error 500<br/>}</code>|



