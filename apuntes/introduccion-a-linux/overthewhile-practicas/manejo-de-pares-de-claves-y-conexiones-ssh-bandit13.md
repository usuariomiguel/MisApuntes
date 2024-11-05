# Manejo de pares de claves y conexiones SSH \[Bandit13]

La siguiente password se encuentra solo puede leerse por el usuario Bandit14, en la direccion  **/etc/bandit\_pass/bandit14**, hay guardada una clave privada de ssh en el usuario bandit13.

**Solucion**

```
// Guardamos la clave privada en nuestra maquina local y le damos permisos de lectura y escritura a root
echo "La_Clave_Privada" > id_rsa
chmod 600 id_rsa
// Nos conectamos al usuario bandit14 por ssh
ssh -i id_rsa bandit14@bandit.labs.overthewire.org -p 2220
// Ya podemos leer la password en la direccion /etc/bandit_pass/bandit14
cat /etc/bandit_pass/bandit14
fGrHPx402xGC7U7rXKDaxiWFTOiF0ENq
```

{% hint style="info" %}
Para conectarte por el servicio ssh sin que te pida contraseña, puedes guardar una copia de la clave publica 'id\_rsa.pub' con el nombre de authorized\_keys

Para crear claves criptograficas usamos el comando -> ssh-keygen \[automaticamente se guardaran en /.ssh/id\_rsa/ del directorio del usuario] &#x20;
{% endhint %}



Los pares de claves SSH son dos claves criptográficamente seguras que pueden usarse para autenticar a un cliente a un servidor SSH. Cada par de claves está compuesto por una clave pública y una clave privada.

El cliente mantiene la clave privada y debe mantenerla en absoluto secreto. Poner en riesgo la clave privada puede permitir a un atacante no autorizado iniciar sesión en los servidores que están configurados con la clave pública asociada sin autenticación adicional. Como medida de precaución adicional, es recomendable cifrar la clave en el disco con una frase de contraseña.

La clave pública asociada puede compartirse libremente sin ninguna consecuencia negativa. La clave pública puede usarse para cifrar mensajes que sólo la clave privada puede descifrar. Esta propiedad se emplea como forma de autenticación mediante el uso del par de claves.
