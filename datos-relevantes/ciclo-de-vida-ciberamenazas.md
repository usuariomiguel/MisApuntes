---
coverY: 0
---

# Ciclo de vida ciberamenazas

Este es el ciclo de vida de la mayoría de las ciberamenazas, modelo desarrollado por Lockheed Martin y denominado Cyber Kill Chain®12.

<figure><img src="../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

De forma muy resumida, el modus operandi en muchas de las actuales campañas de distribución de malware puede resumirse en:&#x20;

* Fase de intrusión.&#x20;
* Movimiento lateral.&#x20;
* Explotación o colonización.&#x20;

Cada una de estas fases puede modelarse tomando como referencia las matrices de Tácticas, Técnicas y Conocimiento Común de Adversarios de ATT\&CK13 y pueden servir de base para establecer el plan de salvaguardas

### Fase de intrusión

Los principales vectores de entrada que se están observando por parte de los atacantes son el correo electrónico y los servicios no seguros expuestos. Habitualmente, en el caso del correo electrónico, se trata de correos dirigidos a una o varias víctimas con un documento malicioso adjunto (generalmente, haciendo uso de macros para la descarga del código dañino) o persuadiendo al usuario para que visite una web previamente comprometida. Una vez allí, una falsa actualización del navegador, la instalación de complementos o mecanismos similares logran la descarga de la primera etapa del malware. Por su parte, los servicios expuestos a internet son una vía de entrada muy usada por los atacantes. Servicios como RDP o SSH, que permiten acceso directo a la red interna, son analizados en busca de credenciales débiles o vulnerabilidades conocidas.

### Fase de movimiento lateral

Una vez dentro de la organización, los atacantes buscan ganar persistencia y desactivar los sistemas de defensa. Asegurada la persistencia, la propagación del malware dentro de la organización se lleva a cabo utilizando diferentes tácticas/técnicas:&#x20;

* Explotando vulnerabilidades conocidas (EternalBlue, EternalRomance, BlueKeep, etc.) que ayuden al movimiento lateral del atacante, como son las que afectan a protocolos como SMB.&#x20;
* Robando credenciales y creando nuevos usuarios de administración.
* Deshabilitando cualquier sistema de protección implementado. En el caso de que el interés sea distribuir ransomware, los atacantes eliminarán también cualquier copia de seguridad.&#x20;

En esta fase los atacantes suelen usar herramientas de post-explotación o que les faciliten la propagación lateral, como por ejemplo Empire, CobalStrike o Metasploit, además de herramientas nativas de los sistemas como Powershell, Batch Scripts, PSEXEC, etc. La tendencia de los atacantes pasa por el uso de técnicas de Living off the Land (LOL) o el uso de fileless malware.

### Fase de explotación o colonización

Una vez obtenido el control sobre la infraestructura víctima y establecido contacto con su sistema de Comando y Control, el atacante envía las órdenes de descarga y detonación del malware elegido, o bien cualquier otro tipo de acción a realizar sobre la red o sistemas víctima: exfiltración de información, alteración o eliminación de datos, cifrado, etc.

<figure><img src="../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

