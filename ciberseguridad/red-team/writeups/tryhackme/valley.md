---
cover: >-
  https://tryhackme-images.s3.amazonaws.com/room-icons/2700326f6bf2127c414a0fa4582496cd.png
coverY: 0
---

# Valley

Para empezar vamos a hacer un escaneo de puertos abiertos en la maquina victima.

```
nmap -sCV -Pn --min-rate 3000 -vvv -n {IP_Victima} -o scan
```

<figure><img src="../../../../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

Únicamente vemos los puertos 22 y 80 abiertos en la máquina victima.

Vamos a encontrar directorios y subdominios en el servidores web con la herramienta gobuster

```
gobuster dir -u http://{ULR} -w {Wordlist} -x {extensiones_de_ficheros}
```

<figure><img src="../../../../.gitbook/assets/image (1) (3).png" alt=""><figcaption></figcaption></figure>

Encontramos los siguientes directorios, me parece interesante el directorio de static, donde se alojan imagenes, por lo que hacemos una segunda busqueda de directorios en esta ruta

<figure><img src="../../../../.gitbook/assets/image (2) (1) (1).png" alt=""><figcaption></figcaption></figure>

Comprobamos los diferentes directorios y encontramos que el /00 contiene un texto en el cual se encuentra una ruta, si accedemos a esta encontraremos un dormulario.

<figure><img src="../../../../.gitbook/assets/image (3) (1).png" alt=""><figcaption></figcaption></figure>

Si inspeccionamos el fichero dev.js del formulario nos encontramos con el usuario y contraseña que nos redirije a un fichero .txt

<figure><img src="../../../../.gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../../.gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>

Leyendo el fichero .txt me doy cuenta que tiene que haber un puerto abirto con el servicio ftp por lo que hago de nuevo un nmap y sorpresaa

<figure><img src="../../../../.gitbook/assets/image (7).png" alt=""><figcaption></figcaption></figure>

Vamos a loguearnos con las mismas credenciales en el servicio ftp

Nos descargamos los ficheros alojados en el servidor ftp con el comando get en busca de informacion.

<figure><img src="../../../../.gitbook/assets/image (8).png" alt=""><figcaption></figcaption></figure>

Los ficheros son infromacion recogida de wireshark, por lo que vamos a inspeccionarlos con esta herramienta

> wireshark {nombre\_fichero}

En el fichero siemHTTP2.pcapng encontramos el usuario y la contraseña de un logueo en un formulario, vamos a probar estas credenciales para loguearnos en ssh

Conseguimos loguearnos en ssh y ya tenemos nuestra primera flag :)

<figure><img src="../../../../.gitbook/assets/image (9).png" alt=""><figcaption></figcaption></figure>

### Escalada de privilegios

En el directorio /home hay un fichero con el nombre valleyAutheticator, que es un validador del usuario valley, lo que haremos sera pasarnos este fichero a nuestra maquina atacante para despues inspeccionar el contenido a ver si encontramos la contraseña para el usuario valley

<figure><img src="../../../../.gitbook/assets/image (10).png" alt=""><figcaption></figcaption></figure>

```
strings valleyAutheticator > valley.txt
cat valley.txt
```

<figure><img src="../../../../.gitbook/assets/image (11).png" alt=""><figcaption></figcaption></figure>

Vamos a crackear el hash en la pagina crackstation para ver la contraseña

<figure><img src="../../../../.gitbook/assets/image (12).png" alt=""><figcaption></figcaption></figure>

Y ya nos logueamos con el usuario valley

<figure><img src="../../../../.gitbook/assets/image (13).png" alt=""><figcaption></figcaption></figure>

Si buscamos los archivos que tenemos permisos dentro del grupo de ValleyAdmin encontramos un script de python llamado base64.py

<figure><img src="../../../../.gitbook/assets/image (42).png" alt=""><figcaption></figcaption></figure>

Si añadimos a este fichero siguiente comando, le estaremos dando permiso a valley para ejecutar una bash con permisos de root

```
os.system('chmod u+s /bin/bash')
```

<figure><img src="../../../../.gitbook/assets/image (43).png" alt=""><figcaption></figcaption></figure>

Guardamos y ejecutamos el script:

```
python3 /photos/script/photosEncrypt.py
```

Ahora simplemente ejecutamos el comando /bin/bash -p y ya estaremos como root

<figure><img src="../../../../.gitbook/assets/image (44).png" alt=""><figcaption></figcaption></figure>
