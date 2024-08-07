# Whoiam

Comienzo con un escaneo de puertos con la herramienta de nmap:

<figure><img src="../../../.gitbook/assets/image (14).png" alt=""><figcaption></figcaption></figure>

Veo que la pagina esta creada con wordpress por lo que hago un escaneo con la herramienta wpscan:

```
wpscan --url {URL} -e u
```

<figure><img src="../../../.gitbook/assets/image (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

La herramienta encuentra dos usuarios, erik y developer, por lo que voy a probar a realizar una fuerza bruta en el login con la misma herramienta (wpscan):

```
wpscan --url {URL} -U {lista usuarios} -P {diccionario de contraseñas}
```

No he tenido suerte con la fuerza bruta, por lo que vamos a pasar encontrar directorios con gobuster

<figure><img src="../../../.gitbook/assets/image (2) (1) (1).png" alt=""><figcaption></figcaption></figure>

Me llama la atención el directorio /backups

<figure><img src="../../../.gitbook/assets/image (3) (1) (1).png" alt=""><figcaption></figcaption></figure>

Descomprimimos y nos encontramos con la contraseña de developer, asi que voy a loguearme:

<figure><img src="../../../.gitbook/assets/image (5) (1).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (4) (1).png" alt=""><figcaption></figcaption></figure>

Voy a explotar el PoC para injectar una shell

<figure><img src="../../../.gitbook/assets/image (7) (1).png" alt=""><figcaption></figcaption></figure>

Accedo a la ruta donde se encuentra la shell y una vez dentro hacemos una reverseshell hacia nuestra maquina:

<figure><img src="../../../.gitbook/assets/image (9) (1).png" alt=""><figcaption></figcaption></figure>

Configuramos la shell intereactiva y ejecutamos el comando sudo -l

<figure><img src="../../../.gitbook/assets/image (10) (1).png" alt=""><figcaption></figcaption></figure>

Se puede ejecutar el comando find con el usario de rafa, vamos a ver en GTFO como podremos escalar a usuario rafa con find

<figure><img src="../../../.gitbook/assets/image (11) (1).png" alt=""><figcaption></figcaption></figure>

Con este comando nos permite cambiar de usuario, en este caso a rafa

<figure><img src="../../../.gitbook/assets/image (12) (1).png" alt=""><figcaption></figcaption></figure>

Ejecuto de nuevo sudo -l y vemos que ahora el comando que podemos ejecutar es debugfs con el usuario de ruben

<figure><img src="../../../.gitbook/assets/image (13) (1).png" alt=""><figcaption></figcaption></figure>

Buscamos nuevamente en GTFO y vemos que hay opcion a cambiar de usuario con sudo

<figure><img src="../../../.gitbook/assets/image (14) (1).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (15).png" alt=""><figcaption></figcaption></figure>

Ejecuto otra vez sudo -l y veo tenemos permiso de ejecutar un script ubicado en /opt

<figure><img src="../../../.gitbook/assets/image (16).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (17).png" alt=""><figcaption></figcaption></figure>

Ejecutamos una /bin/bash y nos convertimos en el usuario root

<figure><img src="../../../.gitbook/assets/image (18).png" alt=""><figcaption></figcaption></figure>
