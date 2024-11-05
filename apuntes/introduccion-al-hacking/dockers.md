# Dockers

### **Que es Docker y su uso para el Hacking Ético**

**Docker** es una plataforma de **contenedores** de software que permite crear, distribuir y ejecutar aplicaciones en entornos aislados. Esto significa que se pueden empaquetar las aplicaciones con todas sus dependencias y configuraciones en un contenedor que se puede mover fácilmente de una máquina a otra, independientemente de la configuración del sistema operativo o del hardware.

Algunas de las ventajas que se presentan a la hora de practicar hacking usando Docker son:

* **Aislamiento**: los contenedores de Docker están aislados entre sí, lo que significa que si una aplicación dentro de un contenedor es comprometida, el resto del sistema no se verá afectado.
* **Portabilidad**: los contenedores de Docker se pueden mover fácilmente de un sistema a otro, lo que los hace ideales para desplegar entornos vulnerables para prácticas de hacking.
* **Reproducibilidad**: los contenedores de Docker se pueden configurar de forma precisa y reproducible, lo que es importante en el hacking para poder recrear escenarios de ataque.

En las próximas clases, se mostrará cómo instalar Docker, cómo crear y administrar contenedores, y cómo usar Docker para desplegar entornos vulnerables para practicar hacking.

### Instalación

```
apt install docker.io -y
// Comprobar servicio
service docker start
```

### Crear una imagen de Docker

1. Para crear una imagen de Docker, es necesario tener un archivo **Dockerfile** que defina la configuración de la imagen. Algunas de las secciones más comunes en un archivo Dockerfile son:

* **FROM**: se utiliza para especificar la imagen base desde la cual se construirá la nueva imagen.
* **RUN**: se utiliza para ejecutar comandos en el interior del contenedor, como la instalación de paquetes o la configuración del entorno.
* **COPY**: se utiliza para copiar archivos desde el sistema host al interior del contenedor.
* **CMD**: se utiliza para especificar el comando que se ejecutará cuando se arranque el contenedor.

2. &#x20;Una vez que se tiene el Dockerfile, ejecutamos instrucciones para crear, ver, ejecutar e iniciar comandos dentro de Docker.

{% hint style="info" %}
Con "docker pull" para descargar la imagen existentes
{% endhint %}

```
// El parámetro “-t” se utiliza para etiquetar la imagen con un nombre y una etiqueta. Por ejemplo, si se desea etiquetar la imagen con el nombre “mi_imagen” y la etiqueta “v1“, se puede usar la siguiente sintaxis:
docker build -t mi_imagen:v1 ruta_al_Dockerfile
docker images
docker run -dit mi_imagen
docker ps -a
docker exec -it 123456789 bash
```

3. Parar docker, eliminar proceso o eliminar imagen

```
// maquinas que estan corriendo
docker ps 
Docker stop ID 
docker ps -a (docker ps -a -q) -> para ver solo los ID
Docker rm ID
// imagenes creadas
docker images
docker rmi ID
// para eliminar todo
docker rm $(docker ps -a -q) –force
docker rmi $(docker images -q)
```

4. Otras opciones mas avanzadas

```
// Para utilizar el port forwarding, se utiliza la opción “-p”
docker run -p 80:8080 mi_imagen
docker run -p 53:53/udp mi_imagen
// Para utilizar las monturas, se utiliza la opción “-v”
docker run -v /home/usuario/datos:/datos mi_imagen
docker run -v /home/usuario/datos:/datos:ro mi_imagen
```
