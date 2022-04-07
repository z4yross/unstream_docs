---
sidebar_position: 3
---

# us_user_ms

*__descripción__*

*__vista de componentes y conectores__*

*__descripción de vista__*

## Endpoints

### **GET** /user

descripción

Parametros:

|Nombre|Tipo|Obligatorio|Descripción|
|--|--|--|--|
|uid|string|si|uid del usuario|

Return:

|Status|Causa|Respuesta|
|--|--|--|
|200|Usuario encontrado|<code>{<br/>  "uid": string,<br/>  "name": string",<br/>  "state": int",<br/>  "...": ...<br/>}</code>|
|404|Usuario no encontrado|<code>{<br/>  "error": "Usuario no encontrado."<br/>}</code>|
|...|...|...|

Ejemplo:

    GET /user?uid=6naqZXx854VKeOI3PgiWufYIldB3

### **POST** /user

descripcion

Body:

|Nombre|Tipo|Obligatorio|Descripción|
|--|--|--|--|
|uid|string|si|uid del usuario|
|name|string|si|nombre del usuario|
|state|int|si|estado de moderacion del usuario|
|...|...|...|...|

Return:

|Status|Causa|Respuesta|
|--|--|--|
|200|Usuario creado|<code>{<br/>"uid": string,<br/>"name": string",<br/>"state": int",<br/>"...": ...<br/>}</code>|
|401|El usuario ya existe|<code>{<br/>"error": "el usuario ya se encuentra en la base de datos."<br/>}</code>|
|...|...|...|

