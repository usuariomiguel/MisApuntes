# Uso de conexiones encriptadas \[Bandit15]

Conseguimos la contraseña proporcionando contraseña del nivel actual por el puerto 30001 en el localhost por ssl

```
// usamos netcat con el parametro --ssl
ncat localhost 30001 --ssl
jN2kgmIXJ6fShzhT2avhotn4Zcka6tnt
Correct!
JQttfApK4SeyHwDlI9SXGR50qclOAil1
```

<div align="left">

<figure><img src="../../../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

</div>

Ncat al contrario de nc puede encriptar el tráfico usando SSL. En el modo de conexión, basta con añadir la opción ‘–ssl‘.
