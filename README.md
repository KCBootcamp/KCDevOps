# KCDevOps

En este repositorio se describen las instrciones para poder acceder al proyecto Nodepop una vez realizado su despliegue en el servidor. A continuación, se describen unas simples indicaciones para poder acceder a los contenidos.

Nota: Se ha optado por obtener una Elastic IP en para el servidor por tanto también se fucionará con el dominio  bhavish.chandnani.es

##Acceso por IP o dominio
Al acceder por IP o dominio se accederá al portfolio del autor.
IP: 23.20.0.234
Dominio/URL: [bhavishchandnani.es](bhavishchandnani.es) o [www.bhavishchandnani.es](www.bhavish.chandnani.es)

##Acceso a Nodepop
El acceso a la aplicación nodepop (se utiliza la app proporcionada por el profesor por facilidad).

###Acceso a la página principal
Al acceder a la página principal se puede observar las info para poder instalar e utilizar la api de nodepop

URL: [nodepop.bhavishchandnani.es](nodepop.bhavishchandnani.es)

###Acceso a archivos estáticos 
Para acceder a archivos estáticos se puede realizar con uan consulta a images. Para comprobar que se usa NGINX, se ha incluido en la cabecera el parametro X-Author: @BVC

URLS de ejemplo:  
	+ [http://nodepop.bhavishchandnani.es/images/anuncios/bici.jpg](http://nodepop.bhavishchandnani.es/images/anuncios/bici.jpg)
	+ [http://nodepop.bhavishchandnani.es/images/anuncios/iphone.png](http://nodepop.bhavishchandnani.es/images/anuncios/iphone.png)

##Acceso a la API

###Crear un usuario
Para crear un usuario, hay que acudir a la url de usuarios/register incluyento los parámetros de nombre, email y clave en el body con x-www-form-urlencoded. 

URL:
	+ [nodepop.bhavishchandnani.es/apiv1/usuarios/register](nodepop.bhavishchandnani.es/apiv1/usuarios/register)

Parámetros de un usuario de ejemplo (ya creado):
	+ nombre: usuario
	+ email: usuario@ejemplo.es
	+ clave: 123456

Respuesta JSON:
	{
	  "ok": true,
	  "message": "user created!"
	}

###Iniciar sesión
Para iniciar, hay que acudir a la url de usuarios/authenticate incluyento los parámetros email y clave en el body con x-www-form-urlencoded. La respuesta será el token de acceso para la api.

URL:
	+ [nodepop.bhavishchandnani.es/apiv1/usuarios/authenticate](nodepop.bhavishchandnani.es/apiv1/usuarios/authenticate)

Parámetros de un usuario de ejemplo (ya creado):
	+ email: usuario@ejemplo.es
	+ clave: 123456

Respuesta JSON:
	{
	  "ok": true,
	  "token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ1c2VyIjp7Il9pZCI6IjU3NDliOTEzOWNkNzY5OGExODQ3ZTQ1OSIsIm5vbWJyZSI6InVzdWFyaW8iLCJlbWFpbCI6InVzdWFyaW9AZWplbXBsby5lcyIsImNsYXZlIjoiOGQ5NjllZWY2ZWNhZDNjMjlhM2E2MjkyODBlNjg2Y2YwYzNmNWQ1YTg2YWZmM2NhMTIwMjBjOTIzYWRjNmM5MiIsIl9fdiI6MH0sImlhdCI6MTQ2NDQ1MzY2NSwiZXhwIjoxNDY0NTQwMDY1fQ.EbPpGOG8MAf2ilHt_EXfLyDR_3BUxwySd-yNdGfjF2Y"
	}

###Consultar anuncios
Para consultar anuncios, hay que acudir a la url de anuncios/ incluyento los parámetros de los filtros que se quieren realizar y también inclueyndo el token de acceso. La respuesta será un JSON con el resultado de la busqueda de lso anuncios

URL:
	+ [nodepop.bhavishchandnani.es/apiv1/anuncios?token={token}](eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ1c2VyIjp7Il9pZCI6IjU3NDliOTEzOWNkNzY5OGExODQ3ZTQ1OSIsIm5vbWJyZSI6InVzdWFyaW8iLCJlbWFpbCI6InVzdWFyaW9AZWplbXBsby5lcyIsImNsYXZlIjoiOGQ5NjllZWY2ZWNhZDNjMjlhM2E2MjkyODBlNjg2Y2YwYzNmNWQ1YTg2YWZmM2NhMTIwMjBjOTIzYWRjNmM5MiIsIl9fdiI6MH0sImlhdCI6MTQ2NDQ1MzY2NSwiZXhwIjoxNDY0NTQwMDY1fQ.EbPpGOG8MAf2ilHt_EXfLyDR_3BUxwySd-yNdGfjF2Y)

	Nota: se ha incluido en el enlace un token pero si este caduca habrá que iniciar sesión obtener otro e intcluirlo en las consutlas a la api

Respuesta JSON:
	{
	  "ok": true,
	  "result": {
	    "rows": [
	      {
	        "_id": "5746f662182234d025eb37f2",
	        "nombre": "Bicicleta",
	        "venta": true,
	        "precio": 230.15,
	        "foto": "/images/anuncios/bici.jpg",
	        "__v": 0,
	        "tags": [
	          "lifestyle",
	          "motor"
	        ]
	      },
	      {
	        "_id": "5746f662182234d025eb37f3",
	        "nombre": "iPhone 3GS",
	        "venta": false,
	        "precio": 50,
	        "foto": "/images/anuncios/iphone.png",
	        "__v": 0,
	        "tags": [
	          "lifestyle",
	          "mobile"
	        ]
	      }
	    ]
	  }
	}