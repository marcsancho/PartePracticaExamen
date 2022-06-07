# PartePracticaExamen
Por problemas con la conexión al java, no podemos usar un usuario diferente para acceder a la base de datos, por tanto el usuario decidido por todo el grupo fue prueba con la contraseña 123456.

##Introducción
En este ejercicio se realizara un despliegue del proyecto usando un archivo de docker-compose.yml el cual se puede ver en los archivos del repositorio de github.


##Configuración del archivo docker-compose
El archivo docker compose se estructura de la siguiente manera:
<br><br>
![image](https://user-images.githubusercontent.com/91566044/172449113-d79111db-4696-434f-8645-acc877218087.png)
<br><br>
En esta primera imagen se puede ver el inicio del documento docker-compose.yml (sera dividido en tres partes).
<br>
En la linea 1 del documento se especifica la versión del docker-compose a usar
En la linea 2 se inicia **services:** donde especificaremos los servicios que se ejecutaran con este archivo
En la linea 3 se inicia el primer servicio, la base de datos, en ella definimos con que imagen se iniciara *mysql:8.0* y siguiendo se definen los volumenes de donde se extraera y donde se guardara la información del contenedor. El archivo continua configurando el entorno, donde se puede configurar la contraseña de root, para ejecutar el primer script, el nombre de la base de datos, y el usuario y contraseña del usuario con el que nos vamos a poder conectar de forma remota. Se continua con los puertos, donde se define en 3307 el puerto del contenedor y el  puerto 3306 como el puerto del servidor con el cual nos vamos a conectar a el.
<br>
<br>
![image](https://user-images.githubusercontent.com/91566044/172449982-d1182cf9-a614-4786-92c6-d5c8d82d9d1e.png)
<br><br>
Las siguientes lineas muestran los otros servicios que se van a ejecutar, en este caso ejecutamos el phpmyadmin para demostrar el funcionamiento del despliegue y asi poder ver la base de datos, ya que sin este la base de datos funciona, pero no es visible para el usuario. También se define que dependen de -db que hace referencia a la base de datos,  el servicio explicado en la primera imgaen. Las otras lineas son repeticiones de lo ya explicado en la primera imagen.

##Pasos para el despliegue de la aplicación.
La aplicación sera ejecutada desde una maquina virtual ubuntu-server 20.04 con un lubuntu instalado encima para poder ver de forma grafica que la aplicación ha sido desplegada correctamente.
<br>
<br>
1.- Lo primero que vamos a realizar una clonación de nuestro proyecto (con el archivo .war, el archivo docker-compose y el script de creación de la base de datos) en este caso, lo hemos insertado todo en la rama test2 del repositorio del proyecto. 
<br>
![image](https://user-images.githubusercontent.com/91566044/172451332-4c268071-0ae7-430f-b6d0-83d01570aa0e.png)
<br>
<br>
2.- Para continuar ejecutaremos el *docker-compose up -d* para desplegar los contenedores de forma correcta, siempre se hara dentro de la carpeta del proyecto, por la forma en la que lo hemos definido en el mismo archivo.
<br>
![image](https://user-images.githubusercontent.com/91566044/172451703-46dac77a-0c8d-4326-81f3-875a6d4477fc.png)
<br>
Como vemos empieza a descargar las imagenes indicadas en el archivo, y realiza las modificaciones necesarias en ellas.
<br>
![image](https://user-images.githubusercontent.com/91566044/172452089-2b863d1b-0583-47d2-af70-7166477464f1.png)
<br>
Finalmente se ve la ejecucion correcta de el archivo
<br>
3.-Imagenes de La web en la interficie grafica de la pàgina web y de la base de datos en el phpmyadmin
IMPORTANTE--La hora de las imagenes no es la correcta, las imagenes han sido realizadas dos horas despues, pero salen erroneas debido a la maquina virtual.
<br>
<br>
![image](https://user-images.githubusercontent.com/91566044/172452507-144e0073-3ad4-4d64-924a-02041ee8d2e2.png)
<br>
![image](https://user-images.githubusercontent.com/91566044/172452631-66b63c8e-47f9-42b7-a15d-09c4fba235a3.png)
<br>
<br>
##Preparación y subida de la imagen a dockerhub.
Lo primero que se hará es la inserción de los tags en las diferentes imagenes:
<br>
![image](https://user-images.githubusercontent.com/91566044/172453349-919404d0-0ce6-449e-8a79-40882e00c469.png)
<br>
<br>
Continuamos haciendo login en docker hub para poder subir las imagenes allí:
<br>
![image](https://user-images.githubusercontent.com/91566044/172453749-0d1b10ac-92f7-4005-b122-95d862a2a1b2.png)
<br>
<br>
![image](https://user-images.githubusercontent.com/91566044/172454046-e86eead3-c97e-43a2-9d00-412690b1d46a.png)
<br>
<br>

