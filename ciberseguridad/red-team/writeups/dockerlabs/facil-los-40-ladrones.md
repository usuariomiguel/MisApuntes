# \[Facil] Los 40 ladrones

Empezamos con la tipica, un escaneo de los puestos y servicios y una fuerza bruta para ver los directorios en la web

<figure><img src="../../../../.gitbook/assets/image (45).png" alt=""><figcaption></figcaption></figure>

No vemos gran cosa mas que la pagina por defecto de apache. Voy a probar a buscar con la herramienta gobuster a parte de directorios, archivos como php,py y txt

<figure><img src="../../../../.gitbook/assets/image (48).png" alt=""><figcaption></figcaption></figure>

<div align="left">

<figure><img src="../../../../.gitbook/assets/image (47).png" alt="" width="485"><figcaption></figcaption></figure>

</div>

Encontramos un archivo .txt vamos a visualizarlo en la web

<div align="left">

<figure><img src="../../../../.gitbook/assets/image (49).png" alt="" width="416"><figcaption></figcaption></figure>

</div>

Con esta informacion nos podemos hacer una idea de que toctoc es un usuario de ssh y los codigos de abajo son puertos que utilizados con las herramienta de knock estan securizando el servidor ssh por lo que vamos a probar a lanzar el siguiente comando

```
// Intalacion de knock
apt install knockd
```

<div align="left">

<figure><img src="../../../../.gitbook/assets/image (52).png" alt="" width="390"><figcaption></figcaption></figure>

</div>

Efectivamente estaba securizado el servicio de ssh con la herramienta de knock con los puertos 7000,8000,9000 por lo que vamos a realizar un nmap para comprobar que ya podemos ver el servicio de ssh

<figure><img src="../../../../.gitbook/assets/image (50).png" alt=""><figcaption></figcaption></figure>

Una vez tenemos conectividad con el servicio ssh lo que se me ocurre es hacer un ataque de fuerza bruta con la herramienta de hydra al usuario toctoc

```
hydra -l toctoc -P {Wordlist} ssh://IP -v
```

<div align="left">

<figure><img src="../../../../.gitbook/assets/image (53).png" alt="" width="563"><figcaption></figcaption></figure>

</div>

<div align="left">

<figure><img src="../../../../.gitbook/assets/image (54).png" alt="" width="563"><figcaption></figcaption></figure>

</div>

Si vemos que comandos podemos ejecutar con otros privelegio vemos lo siguiente

```
sudo -l 
```

<figure><img src="../../../../.gitbook/assets/image (55).png" alt=""><figcaption></figcaption></figure>

Si inspeccionamos el fichero /opt vamos a ver que esta vacio, por lo que intuimos que puede estar capado con knock, si leemos el fichero .bashrc encontramos los puertos de knock.

<div align="left">

<figure><img src="../../../../.gitbook/assets/image (57).png" alt="" width="563"><figcaption></figcaption></figure>

</div>

Ejecutamos siguiente comando en nuestra maquina atacante para desbloquear el fichero

<div align="left">

<figure><img src="../../../../.gitbook/assets/image (56).png" alt=""><figcaption></figcaption></figure>

</div>

Ya podemos ejecutar el comando como root

<div align="left">

<figure><img src="../../../../.gitbook/assets/image (58).png" alt="" width="534"><figcaption></figcaption></figure>

</div>
