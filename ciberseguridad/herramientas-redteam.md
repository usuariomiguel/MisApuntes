# Herramientas RedTeam

### Stegseek

La herramienta stegseek es un descifrador de contraseñas para archivos ocultos. Es una bifurcación del proyecto original steghide y es miles de veces más rápida que otros descifradores, pudiendo ejecutar la totalidad de rockyou.txt en menos de 2 segundos. Stegseek también se puede utilizar para extraer metadatos de steghide sin contraseña, lo que se puede utilizar para probar si un archivo contiene datos ocultos.

```sh
apt install stegseek
```

{% embed url="https://github.com/RickdeJager/stegseek" %}

### Steghide&#x20;

Steghide es un programa de esteganografía que oculta bits de un archivo de datos en algunos de los bits menos significativos de otro archivo de tal manera que la existencia del archivo de datos no es visible y no se puede probar.

Steghide está diseñado para ser portátil y configurable y presenta datos ocultos en archivos bmp, jpeg, jpg, wav y au, cifrado Blowfish, hash MD5 de frases de contraseña para claves Blowfish y distribución pseudoaleatoria de bits ocultos en los datos del contenedor.

Steghide es útil en investigaciones forenses digitales.

```bash
apt install steghide
```

{% embed url="https://www.kali.org/tools/steghide/" %}

### Camphish

Camphish es una herramienta con la que puedes conseguir tomar fotos de la camara frontal del movil o la webcam de un PC. Camphish crea una web web falsa con php y alojada en un servidor con ngrok o serveo. Para que funcione se necesita que el usuario permita el acceso a la camara una vez acceda a la web. &#x20;

{% embed url="https://github.com/techchipnet/CamPhish" %}

OhMyQR

Hermienta que crea un servidor donde se aloja una replica de un inicio de sesion de una aplicacion con QR para que cuando la victima escanee este se inicie sesion en nuestra maquina atacante. A este tipo de ataque se le denomina QRLJacking o Quick Response Code Login Jacking.

{% embed url="https://github.com/cryptedwolf/ohmyqr" %}

