---
sidebar_position: 3
---

# us_streamchat_ms

*__Descripción del microservicio__*  
El microservicio de us_streamchat_ms es el encargado de manejar el chat de cada uno de los streams como también los chats entre usuarios, haciendo uso de *rooms* o cuartos de chat.

*__Vista de componentes y conectores__*  
![Diagrama de componentes del microservicio us_streamchat_ms](http://www.plantuml.com/plantuml/png/VSqzImD14CRnVZ_5UDONqD8YvELAkmWfHCBSxfXRRdRdc9ab-ErjWcWK-z_pVpRcgDuAXpkVg10KTDAClJJdN2dOdEk2YWLoTT9tZBJ3E9zLMarxOL6ulqpP_vQYYVIg1abdqXstV-ZBbEDSoGmUlo5KbSkpCET5bcljUFCPfInIgVh1FvYW5Nu8uQiEtPupLUy03OPj2CCM-duDhyrEvafOueH-AlRs14SQuI1n9Wy97KSqWkwdIsCNVazXjLh3BGmRggaL_WG0)   



*__Descripción de vista__*  
El componente us_streamchat_ms está desarrollado utilizando **TypeScript** haciendo uso principalmente de las librerías **mongoose** y **Socket.io**. En tanto al componente de base de datos, us_streamchat_db hace uso de la base de datos **MongoDB**

*__Modelo de datos__*  

![Diagrama de componentes del microservicio us_streamchat_ms](http://www.plantuml.com/plantuml/png/VOzDwzD04CRl-od6lmT1iDZsbbDflHJqOWKFuc7SdIPBTtV2xAoXj7vtDsreeuYNaETbdb-ooOgY9GRp1Zhl2BGZo3shkIdhnGOoDSIVx1tqmZy2nGo3rmumjO4SME4Xmv58JJxvrADWXE0JwRadOD6EZNbLXoD1H2Nn-8wBZetPWKyrEQAbBTfJAroIst5WWTT3v_NVJHP7ChK-i6j9jg7yf_gby_QKA6TOpKeemiD73i7tt4zhN_zYMeuz9qfwq7CWA34iZQdIwnbUFZF75y0Cz7u95mFmLggpTz10Ll6f7QrOiTXIRk3J_UtRzz6sd19PzPngidk8U-ZpGOKmDh1b3eJ9_7fIfva9lBg37IerC3wdSQtr-MTWqOxbuSpsdl1fSdsRB9bax-O7urzUhul5zJ9o_vHhiw7aIWo_0G00)   



## Listeners

### allRooms

*__Descripción__*  
Retorna una lista de los *rooms* de stream

*__Parametros__*:
Sin parámetros

*__Procedimiento__*:
- Emite la siguiente lista


    {
      "roomId": string,
      "messages": {
        "date": string,
        "content": string,
        "author": string,
      }[],
      "connections": string[],
      "isStream": true,
    }[]

### join

*__Descripción__*  
Conecta al usuario a un room específico

*__Parametros__*:

    {
      "roomId": string,
      "userId": string
    }

*__Procedimiento__*  
1. Añade el usuario a la lista de conexiones del room en la base de datos
1. Difunde un mensaje a todos los usuarios conectados al socket room dándole la bienvenida al room
1. Conecta al socket del usuario al room

### message

*__Descripción__*  
Crea un nuevo mensaje en el chat. Actualmente el microservicio solo acepta contenido de texto.

*__Parametros__*:

    {
      "roomId": string,
      "userId": string,
      "content": string
    }

*__Procedimiento__*  
1. Añade el mensaje a la lista de mensajes del room en la base de datos
1. Difunde un mensaje a todos los usuarios conectados al socket room 
1. Conecta al socket al room

