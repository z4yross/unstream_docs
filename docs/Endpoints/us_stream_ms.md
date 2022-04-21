---
sidebar_position: 2
---

# us_stream_ms
En este componente se implementarán las funcionalidades de crear un stream, verificar la key de stream de usuario, proporcionar estadísticas y notificar el inicio de un stream.

![us_stream_ms](/img/plantuml/us_stream_ms.png)

Como se puede observar, se expone una interfaz por medio del protocolo [RTMP](https://rtmp.veriskope.com/docs/) para el redireccionamiento, codificación, verificación y demás procesos del stream entrante.

También se expone una interfaz con el protocolo [HLS](https://developer.apple.com/streaming/) para realizar la transmisión de los paquetes codificados de video a los espectadores.

En este componente se utiliza una base de datos no relacional en *__Firestore__* junto con un microservicio en __*JavaScript*__ en el framework __*ExpressJS*__ para la autenticación del usuario. Para la redireccion y codificacion de paquetes del protocolo RTMP se utiliza __*Ngnix*__. Finalmente para la para exponer los fragmentos de video se utilizara un microservicio en el lenguaje __*JavaScript*__.
