# Escaneo de puertos en Bash \[Bandit16]

The credentials for the next level can be retrieved by submitting the password of the current level to **a port on localhost in the range 31000 to 32000**. First find out which of these ports have a server listening on them. Then find out which of those speak SSL and which don’t. There is only 1 server that will give the next credentials, the others will simply send back to you whatever you send to it.

### **Solución**

```
// Primero detectamos que puertos tenemos abiertos 31000 - 32000 con nmap

nmap -p31000-32000 -Pn -n -v --min-rate 30000 localhost
PORT      STATE SERVICE
31046/tcp open  unknown
31518/tcp open  unknown
31691/tcp open  unknown
31790/tcp open  unknown
31960/tcp open  unknown

// Descubrimos que puerto es despues de probar a conectarnos con ncat 

bandit16@bandit:~$ ncat localhost 31790 --ssl
JQttfApK4SeyHwDlI9SXGR50qclOAil1
Correct!
-----BEGIN RSA PRIVATE KEY-----

// Nos proporciona una clave privada rsa por lo que probamos a conectarnos por ssh

echo "Clave_rsa" > id_rsa
chmod 600 id_rsa
ssh -i id_rsa bandit17@bandit.labs.overthewire.org -p 2220

// Completado 
```

Te comparto por aquí los 2 scripts que nos hemos creado para esta clase, por si los quieres tener a mano y estudiarlos más cómodamente:

* Script ‘hostScan.sh‘: [https://hack4u.io/wp-content/uploads/2022/05/hostScan.sh](https://hack4u.io/wp-content/uploads/2022/05/hostScan.sh)
* Script ‘portScan.sh‘: [https://hack4u.io/wp-content/uploads/2022/05/portScan.sh](https://hack4u.io/wp-content/uploads/2022/05/portScan.sh)
