---
sidebar_position: 4
---

# us_mod_ms

*__Descripción:__*

En este componente se implementaran las acciones de moderacion para registrar reportes, usando C# con .NET y ASP.NET y Firebase para la base datos NoSQL.

*__Vista de componentes y conectores:__*
<!-- ![us_mod_ms](/img/plantuml/us_mod_ms.jpeg) -->
<img src="/img/plantuml/us_mod_ms.jpeg" alt="us_mod_ms" width="200"/>

*__Vista de modelo de datos__*
<img src="/img/plantuml/us_mod_db.jpeg" alt="us_mod_ms" width="200"/>

## Endpoints

### **GET** /report/{id}

Devuelve un reporte dado su id

Parametros:

|Nombre|Tipo|Obligatorio|Descripción|
|--|--|--|--|
|id|string|si|id del reporte|

Return:

|Status|Causa|Respuesta|
|--|--|--|
|200|Reporte encontrado|<code>{<br/>  "id": string,<br/>  "reporter": string,<br/>  "cause": string,<br/>  "status": string,<br/>  "idMessage": string,<br/>  "idStream": string,<br/>  "assignedModerator": string<br/>}</code>|
|404|Reporte no encontrado|<code>{<br/>  "error": "Reporte no encontrado."<br/>}</code>|

Ejemplo:

    GET /report/6naqZXx854VKeOI3PgiWufYIldB3

### **GET** /report/unchecked

Devuelve los reportes que no se han revisado aún.

Parametros: Ninguno

Return:

|Status|Causa|Respuesta|
|--|--|--|
|200|Existen reportes|<code>[<br/>{<br/>  "id": string,<br/>  "reporter": string,<br/>  "cause": string,<br/>  "status": "unchecked",<br/>  ... <br/>},<br/>{<br/>  "id": string,<br/>  "reporter": string,<br/>  "cause": string,<br/>  "status": "unchecked",<br/>  ... <br/>},<br/>...<br/>]</code>|
|404|No existen reportes|<code>{<br/>  "error": "No hay reportes registrados."<br/>}</code>

Ejemplo:

    GET /report/unchecked

### **POST** /report

Creacion de reportes

Body:

|Nombre|Tipo|Obligatorio|Descripción|
|--|--|--|--|
|id|string|si|id del reporte|
|reporter|string|si|id del usuario que realizo el reporte|
|cause|string|si|la causa del reporte|
|status|string|si|estado del reporte|
|idMessage|string|no|id del mensaje, si se reporto un mensaje|
|idStream|string|no|id del stream, si se reporto un stream|
|assignedModerator|string|no|moderador que reviso el reporte|

Return:

|Status|Causa|Respuesta|
|--|--|--|
|200|Reporte creado creado|<code>{<br/>  "id": string,<br/>  "reporter": string,<br/>  "cause": string,<br/>  ...<br/>}</code>|
|400|El reporte no se registro|<code>{<br/>  "error": "No se pudo crear el reporte."<br/>}</code>|

### **PUT** /report/{id}

Actualizar un reporte dado su id.

Body:

|Nombre|Tipo|Obligatorio|Descripción|
|--|--|--|--|
|id|string|si|id del reporte|
|status|string|si|nuevo estado del reporte|
|assignedModerator|string|si|moderador que reviso el reporte|

Return:

|Status|Causa|Respuesta|
|--|--|--|
|200|Reporte actualizado|<code>{<br/>  "id": string,<br/>  "reporter": string,<br/>  "cause": string,<br/>  ...<br/>}</code>|
|400|El reporte no se actualizó|<code>{<br/>  "error": "No se pudo actualizar el reporte."<br/>}</code>|

### **DELETE** /report/{id}

Eliminar un reporte por id.

Parametros:

|Nombre|Tipo|Obligatorio|Descripción|
|--|--|--|--|
|id|string|si|id del reporte|

Return:

|Status|Causa|Respuesta|
|--|--|--|
|204|Reporte eliminado||
|404|El reporte no se encontró|<code>{<br/>  "error": "No se encontró el reporte."<br/>}</code>|


