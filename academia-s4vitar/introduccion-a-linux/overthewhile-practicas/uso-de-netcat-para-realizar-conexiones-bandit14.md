# Uso de netcat para realizar conexiones \[Bandit14]

La contraseña debe de ser encontrada en el puerto 30000 del localhost

```
// Vamos a usar netcat en escucha por el puerto 30000 y escribimos la contraseña de bandit 14
nc localhost 30000
fGrHPx402xGC7U7rXKDaxiWFTOiF0ENq
Correct!
jN2kgmIXJ6fShzhT2avhotn4Zcka6tnt
```

<div align="left">

<figure><img src="../../../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

</div>

Gracias a su universalidad, a Netcat se la llama “la navaja suiza del TCP/IP”. Puede utilizarse, por ejemplo, para diagnosticar errores y problemas que afecten a la funcionalidad y la seguridad de una red. Netcat también puede escanear puertos, hacer streaming de datos o simplemente transferirlos. Además, permite configurar servidores de chat y de web e iniciar consultas por correo. Este software minimalista, desarrollado a mediados de los 90, puede operar en modo servidor y cliente.

```
// Con netcat podemos investigar que puertos hay abiertos remotamente
nc IP -h
// Para ver puertos abiertos localmente en linux podemos usar:
ss -nltp
// Para ver un puerto especifico
lsof -i:port
// Para ver todos los procesos del sistemas
ps -faux
// Para listar los comandos que se ejecutan en el sistema
ps -eo command
```

Netcat es una herramienta de línea de comandos que sirve para escribir y leer datos en la red. Para la transmisión de datos, Netcat usa los protocolos de red TCP/IP y UDP. La herramienta proviene originalmente del mundo de Unix; desde entonces, se ha expandido a todas las plataformas.

