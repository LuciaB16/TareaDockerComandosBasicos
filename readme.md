# Práctica: Docker - Comandos básicos

## La siguiente práctica es una lista de tareas que tenéis que hacer. Por cada tarea tenéis que ir poniendo los comandos utilizados y, brevemente, describir el proceso.


Utilizaremos la imagen de Ubuntu. Usa Visual Studio Code y Docker junto con esta imagen para seguir las siguientes instrucciones:

1. Descarga la imagen 'ubuntu y comprueba que está en tu equipo.

$ docker run ubuntu --> Este comando descarga la imagen de ubuntu y ejecuta un contenedor basado en ella.

$ docker image ls --> Lista las imágenes descargadas y así comprobamos que dicha imagen está en nuestro equipo.

2. Crea un contenedor sin ponerle nombre. ¿Está arrancado? Obtén el nombre.

$ docker run -it ubuntu:latest bash --> Crea el contenedor basado en la última versión de ubuntu.

$ docker ps -a --> Así podemos ver los contenedores que hay en el sistema.

Al no darle nosotros un nombre, Docker se lo asigna aleatoriamente.

3. Crea un contenedor con el nombre 'dam_ubu1'. ¿Como puedes acceder a él?

$ docker run -it --name dam_ubu1 ubuntu:latest bash --> Se crea el contenedor con el nombre que le especificamos. Podemos acceder a dicho contenedor gracias al comando -it, ya que nos permite interactuar con la terminal.


4. Comprueba que ip tiene y si puedes hacer un ping a google.com

#apt update --Z Este comando nos actuliza la lista de paquetes disponibles.

#apt install net-tools --> Nos instala las net-tools para poder así instalar ifconfig en ubuntu.

Ya descargadas, seguimos los siguientes pasos:

#ifconfig --> Nos muestra la dirección IP entre otras cosas. 

La IP es: 172.17.0.3
Para hacer ping con Google hacemos lo siguiente:


#apt install iputils-ping --> Instala las herramientas para poder hacer ping.

#ping www.google.com --> Devuelve el tiempo que tardó en hacer ping, entre otra información.

5. Crea un contenedor con el nombre 'dam_ubu2'. ¿Puedes hacer ping entre los contenedores?

$ docker run -it --name dam_ubu2 ubuntu:latest bash --> Se crea el contenedor con el nombre que le especificamos e inicia sesión en la terminal. 

No se puede hacer ping entre ambos contenedores porque en éste (dam_ubu2) no se siguieron los pasos del apartado 4 para hacer ping. En el caso de que se lleven a cabo de nuevo, sí se puede hacer ping.

6. Sal del terminal, ¿que ocurrió con el contenedor?

#exit --> Salimos del contenedor.

El contenedor se cierra pero no se borra, lo podemos ver con el comando: $ docker ps -a (comprobamos así su estado).

7. ¿Cuanta memoria en el disco duro ocupaste?

``````
$ docker system df --> Identifica la cantidad de espacio en disco con Docker.

TYPE            TOTAL     ACTIVE    SIZE      RECLAIMABLE
Images          4         4         194.7MB   0B (0%)
Containers      24        0         274.8MB   274.8MB (100%)
Local Volumes   0         0         0B        0B
Build Cache     0         0         0B        0B
``````


8. ¿Cuanta RAM ocupan los contenedores? ¿Hay algún comando docker para saber esto?.

Para saber cuanto ocupa cada contenedor de los creados, debemos seguir los siguientes pasos:

- Entrar en cada uno de ellos con el comando $docker start dam_ubu1 y respectivamente $docker start dam_ubu2

- Posteriormente lanzar el siguiente comando:


``````
$ docker stats --> Nos muestra la información sobre el uso del CPU, la memoria y otros recursos.

CONTAINER ID   NAME       CPU %     MEM USAGE / LIMIT     MEM %     NET I/O       BLOCK I/O     PIDS
9545905b3bcd   dam_ubu2   0.00%     892KiB / 15.39GiB     0.01%     4.48kB / 0B   4.1kB / 0B    1
77bb37141604   dam_ubu1   0.00%     4.324MiB / 15.39GiB   0.03%     13.3kB / 0B   4.76MB / 0B   1
``````