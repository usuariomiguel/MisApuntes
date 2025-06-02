# Cross-Site Request Forgery (CSRF)

El **Cross-Site Request Forgery** (**CSRF**) es una vulnerabilidad de seguridad en la que un atacante **engaña** a un usuario legítimo para que realice una acción no deseada en un sitio web sin su conocimiento o consentimiento.

En un ataque CSRF, el atacante engaña a la víctima para que haga clic en un enlace malicioso o visite una página web maliciosa. Esta página maliciosa puede contener una solicitud HTTP que realiza una acción no deseada en el sitio web de la víctima.



Ejemplo:

**Lab Setup**: [https://seedsecuritylabs.org/Labs\_20.04/Files/Web\_CSRF\_Elgg/Labsetup.zip](https://seedsecuritylabs.org/Labs_20.04/Files/Web_CSRF_Elgg/Labsetup.zip)

Sabiendo el identificador único de un usuario y enviando un post con ese identificador por el método GET con los cambios, en este caso campos del perfil del usuario, una vez el usuario acceda a este por y se ejecute la petición, automáticamente se actualizaran dichos campos.

1. Inspeccionar petición con burpsuite

<div align="left"><figure><img src="../../../.gitbook/assets/image (106).png" alt="" width="563"><figcaption></figcaption></figure></div>



<div align="left"><figure><img src="../../../.gitbook/assets/image (1) (1).png" alt="" width="563"><figcaption></figcaption></figure></div>

<div align="left"><figure><img src="../../../.gitbook/assets/image (2) (1) (1).png" alt=""><figcaption></figcaption></figure></div>

2. Enviamos la peticion al repeater y cambiamos a metodo GET

<div align="left"><figure><img src="../../../.gitbook/assets/image (3) (1) (1).png" alt=""><figcaption></figcaption></figure></div>

3. Eliminamos los campos que no son necesarios y cambiamos el uid por el del usuario victima

<figure><img src="../../../.gitbook/assets/image (4) (1) (1).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (5) (1).png" alt=""><figcaption></figcaption></figure>

4. Copiamos toda la peticion y la escribimos a traves de un mensaje en una imagen (el campo acepta el formato HTML)

<div align="left"><figure><img src="../../../.gitbook/assets/image (6) (1).png" alt="" width="563"><figcaption></figcaption></figure></div>

5. Nos logueamos con samy, y vemos que si abre el mensaje que hemos enviado automaticamente se ejecuta la peticion y se cambian los campos&#x20;

<div align="left"><figure><img src="../../../.gitbook/assets/image (7).png" alt="" width="563"><figcaption></figcaption></figure></div>

<div align="left"><figure><img src="../../../.gitbook/assets/image (8).png" alt="" width="563"><figcaption></figcaption></figure></div>

<div align="left"><figure><img src="../../../.gitbook/assets/image (105).png" alt="" width="563"><figcaption></figcaption></figure></div>
