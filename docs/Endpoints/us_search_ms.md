---
sidebar_position: 2
---

# us_sesion_ms
En este componente se implementarán una barra de busqueda, dado un ermino por el usuario se devulven terminos compatibles con su busqueda en este caso se devuelven posibles nombres de usuarios.

![us_search_ms](/img/plantuml/us_search_ms.png)

Como se puede observar, se expone una interfaz por medio del protocolo REST por el cual se llegan las peticiones HTTP las cuales son procesadas por el microservicio, el cual hara las querys pertinentes en la base datos respectiva para devolver los resultados compatibles con la busqueda. 


## Endpoints

### **GET** /user

Se recibe un termino de buqueda y se responde con posibles valores compatibles con el termino.

Parametros:

|Nombre|Tipo|Obligatorio|Descripción|
|--|--|--|--|
|SearchTerm|string|si|Termino a buscar|

Return:

|Status|Causa|Respuesta|
|--|--|--|
|200|Termino encontrado|<code>{<br/>  "val1": string,<br/>  "val2": string,<br/>  "...": ...<br/>}</code>|}
|...|...|...|

