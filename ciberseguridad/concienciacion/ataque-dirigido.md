---
description: Concienciación empleados
---

# Ataque dirigido

## ATAQUE DIRIGIDO CON GOPHISH

El primer ataque que se llevará a cabo contra los empleados es de tipo **phishing**, uno de los mas tipicos de los cibercriminales, estos buscan suplantar a un servicio para obtener información confidencial relacionada con este. El ataque capturará el **usuario y contraseña** de acceso al servicio de los usuarios que piquen en la trampa.&#x20;

{% hint style="info" %}
El objetivo de este tipo de ataque es que los usuarios vean lo fácil que es ser engañados por un correo fraudulento y que se vea comprometida la información confidencial de la empresa o de sus servicios personales.
{% endhint %}

### RECURSOS

#### <mark style="color:blue;">**Manuales**</mark>

**Manual de INCIBE**

{% embed url="https://www.incibe.es/empresas/formacion/kit-concienciacion" %}

**Manual oficial de Gophish**&#x20;

{% embed url="https://docs.getgophish.com/user-guide/documentation/changing-user-settings" %}

#### <mark style="color:blue;">Herramienta</mark>

**Instalador de Gophish**

{% embed url="https://github.com/gophish/gophish/releases" %}

{% hint style="info" %}
Otra plataforma donde se puede poner a pruba los empleado es Microsoft Defender.
{% endhint %}

### PROCESO GODPHISH

#### <mark style="color:blue;">Primeros pasos con Golpish</mark>

* Intalar gophish desde github o la pagina oficial.
* Una vez instalado, por defecto se crear en el servidor local, se puede cambiar la ip al servidor en el fichero .json)

<figure><img src="../../.gitbook/assets/image (9).png" alt="" width="375"><figcaption></figcaption></figure>

* Acceder al portal de gophish con 127.0.0.1:3333 y el usuario y contraseña crespondientes.

<figure><img src="../../.gitbook/assets/image (5).png" alt="" width="375"><figcaption></figcaption></figure>

* Añadir un nuevo perfil desde donde se envia el correo electronico.

<figure><img src="../../.gitbook/assets/image (10).png" alt="" width="342"><figcaption></figcaption></figure>

#### <mark style="color:blue;">Ahora que necesitas para crear tu campaña</mark>

* Email template: plantilla de correo que hemos creado.
* Landing Page: pagina de aterrizaje falsa.
* URL: http://127.0.0.1:80 --> donde esta alojadas las paginas de aterrizaje
  * Cambiar dominio para que sea menos sospechoso
* Crear la Página Web, esta sera una réplica de la web legítima. Buscando la intencion de que ele empleado escriba sus credeenciales. &#x20;

Una vez completado todo el proceso, ya estas listo para realizar tu campaña.
