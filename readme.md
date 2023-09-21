# Práctica: Docker - Comandos básicos

## La siguiente práctica es una lista de tareas que tenéis que hacer. Por cada tarea tenéis que ir poniendo los comandos utilizados y, brevemente, describir el proceso.


Utilizaremos la imagen de Ubuntu. Usa Visual Studio Code y Docker junto con esta imagen para seguir las siguientes instrucciones:

1. Descarga la imagen 'ubuntu y comprueba que está en tu equipo.

$ docker run ubuntu

$ docker image ls

2. Crea un contenedor sin ponerle nombre. ¿Está arrancado? Obtén el nombre.

$ docker run -it ubuntu:latest bash

$ docker ps -a

3. Crea un contenedor con el nombre 'dam_ubu1'. ¿Como puedes acceder a él?

$ docker run -it --name dam_ubu1 ubuntu:latest bash


4. Comprueba que ip tiene y si puedes hacer un ping a google.com

#apt update

#apt install net-tools

#ifconfig --> 172.17.0.3


#apt install iputils-ping

#ping www.google.com

5. Crea un contenedor con el nombre 'dam_ubu2'. ¿Puedes hacer ping entre los contenedores?

$ docker run -it --name dam_ubu2 ubuntu:latest bash

No se puede hacer ping entre ambos contenedores porque en éste (dam_ubu2) no se siguieron los pasos del apartado 4 para hacer ping. En el caso de que se lleven a cabo de nuevo, sí se puede hacer ping.

6. Sal del terminal, ¿que ocurrió con el contenedor?

#exit

El contenedor se cierra pero no se borra, lo podemos ver con $ docker ps -a

7. ¿Cuanta memoria en el disco duro ocupaste?

``````
$ docker system df

TYPE            TOTAL     ACTIVE    SIZE      RECLAIMABLE
Images          4         4         194.7MB   0B (0%)
Containers      24        0         274.8MB   274.8MB (100%)
Local Volumes   0         0         0B        0B
Build Cache     0         0         0B        0B
``````


8. ¿Cuanta RAM ocupan los contenedores? ¿Hay algún comando docker para saber esto?.

Para saber cuanto ocupa cada contenedor de los creados, debemos runnear cada uno de ellos con el comando docker start dam_ubu1 y respectivamente docker start dam_ubu2, y posteriormente lanzar el siguiente comando:


``````
$ docker stats

CONTAINER ID   NAME       CPU %     MEM USAGE / LIMIT     MEM %     NET I/O       BLOCK I/O     PIDS
9545905b3bcd   dam_ubu2   0.00%     892KiB / 15.39GiB     0.01%     4.48kB / 0B   4.1kB / 0B    1
77bb37141604   dam_ubu1   0.00%     4.324MiB / 15.39GiB   0.03%     13.3kB / 0B   4.76MB / 0B   1
``````