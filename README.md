# Ejercicio de autenticación

El ejercicio parte de una código base con la siguiente estructura:

- GET / : Endpoint que sirve el index.html, que actúa como aplicación de Front-End. Se recomienda escribir el código del Front dentro del bloque \<script\> ya creado. Los endpoints 
- GET /api/protectedData : Endpoint REST que actúa como aplicación Back-End protegida.

La aplicación se arranca con `npm start` y se accede en http://localhost:3000/. Observa que el código base accede a la información del endpoint protegido (GET /api/protectedData) sin ningún tipo de control, ya que no hay ningún servicio (típicamente un proveedor de identidad) que gestione la autenticación (¿Quién es el usuario?) y la autorización (¿Qué permisos tiene ese usuario?). En este ejercicio nos vamos a centrar en la autenticación.

Importante: No cloneis el repositorio directamente; haced un fork del repositorio para realizar el ejercicio.

## Ejercicio 1

En este primer ejercicio, vamos a integrar la aplicación web con el proveedor de identidad Auth0 utilizando el protocolo OpenId Connect/OAuth 2.1. El primer paso es crear una cuenta en Auth0 y seguir los quickstart que provee el propio servicio. El objetivo es:

1. Realizar el protocolo OpenId Connect/OAuth 2.1 en la aplicación Front para obtener un Access Token.
2. Enviar el Access Token como un Bearer Token al endpoint protegido de la aplicación Back.
3. La aplicación Back validará el Access Token; si es válido, te devolvera la información protegida, de lo contrario, te devolverá un 401/403.

En este ejercicio nos vamos a centrar solamente en la autenticación, y no en la autorización.

## Ejercicio 2

Ahora que habeis experimentado los retos y problemas de integrar en tu aplicación el protocolo OpenId Connect/OAuth 2.1, vamos a dejar que un proxy de autenticación como oauth2-proxy realice el protocolo y nos devuelva la identidad del usuario mediante cabeceras HTTP :). Es importante que al acceder al endpoint protegido sin estar autenticado, se devuelva un 401/403 en vez de redirigir a la página de login.

Utilizad un docker-compose para levantar tanto la aplicación como oauth2-proxy. Es recomendable utilizar un archivo de configuración cfg para la configuración del proxy en vez de utilizar parametros de linea de comandos.

## Ejercicio 3

En este tercer ejercicio, vamos a desplegar la aplicación Front y Back en contenedores distintos. Una misma instancia de oauth2-proxy debe securizar ambas applicaciones. 

Pista: necesitas varios upstreams en la configuración del proxy.

## Ejercicio 4

Próximamente :)