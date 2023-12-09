# Lian\_Yu

<figure><img src="../../../.gitbook/assets/1 NNcKSqF30pmMNp37KbwC7A.png" alt=""><figcaption></figcaption></figure>

Identificacion de puertos y servicios

```
nmap IP -Pn -p- -v -n --min-rate 3000
```

<div align="left">

<figure><img src="../../../.gitbook/assets/image (1) (1).png" alt=""><figcaption></figcaption></figure>

</div>

Vamos a hacer un gobuster en busca de directorios web

```
gobuster dir -u URL -w Diccionary -x .php,.html,.txt
```

<figure><img src="../../../.gitbook/assets/image (2) (1).png" alt=""><figcaption></figcaption></figure>

En el código de la página de island vemos una palabra secreta -> **vigilante**; este pobablemente sea el nombre de usuario del servidor ftp o ssh.

<figure><img src="../../../.gitbook/assets/image (3) (1).png" alt=""><figcaption></figcaption></figure>

Vamos a buscar directorios dentro de **island** con nuestra herramienta gobuster; encontraremos el directorio **2100:**

<figure><img src="../../../.gitbook/assets/image (5).png" alt=""><figcaption><p>Resultado de Gobuster</p></figcaption></figure>

<div align="left">

<figure><img src="../../../.gitbook/assets/image (6).png" alt="" width="375"><figcaption><p>Página 2100</p></figcaption></figure>

</div>

<div align="left">

<figure><img src="../../../.gitbook/assets/image (7).png" alt=""><figcaption><p>Código fuente de la web en 2100</p></figcaption></figure>

</div>

En el comentario de la pagina de 2100 dice que hay un archivo .ticket, por lo que vamos a hacer una fuerza bruta de ficheros/directorios con **gobuster** dentro del directorio **2100:**

<figure><img src="../../../.gitbook/assets/image (8).png" alt=""><figcaption></figcaption></figure>

Encontramos el token **green\_arrow.ticket:**

<div align="left">

<figure><img src="../../../.gitbook/assets/image (9).png" alt=""><figcaption></figcaption></figure>

</div>

El token esta en **base58** , vamos a desencriptarlo para sacar la contraseña real

<div align="left">

<figure><img src="../../../.gitbook/assets/image (11).png" alt="" width="563"><figcaption><p><strong>http://gchq.github.io/Cyberchef/</strong></p></figcaption></figure>

</div>

Ya tenemos la contraseña para aceder al servidor ftp con el usuario vigilante y nos descargamos los archivos guardados en el usuario vigilante; podemos ver que hay una carpeta para un usuario llamado **slade** posiblemente dentro de estos archivos este la contraseña para conectarnos a este mediante ssh y si no la encontramos realizaremos una fuerza bruta:

<div align="left">

<figure><img src="../../../.gitbook/assets/image (12).png" alt=""><figcaption></figcaption></figure>

</div>

<div align="left">

<figure><img src="../../../.gitbook/assets/image (13).png" alt="" width="563"><figcaption></figcaption></figure>

</div>

Probamos a encontrar la **contraseña** del usuario **slade** del servidor **ssh** por medio de fuerza bruta

```
hydra -l slade -P dictionary -IP ssh -t4 -v
```

