# Cifrado césar y uso de tr para la traducción de caracteres \[Bandit11]

Encontrar la contraseña en el fichero data.txt, donde todas la minusculas (a-z) y mayusculas (A-Z) estan rotadas 13 posiciones:

<pre><code><strong>bandit11@bandit:~$ cat data.txt | tr '[A-Za-z]' '[N-ZA-Mn-za-m]'
</strong>The password is JVNBBFSmZwKKOP0XbFXOoW8chDz5yVRv
</code></pre>

Tambien se puede desencriptar desde la web

{% embed url="https://rot13.com" %}

### INFORMACION EXTRA SOBRE EL CIFRADO CÉSAR

Para los más curiosos, el cifrado César lleva el nombre de Julio César. Es uno de los tipos de cifrados más antiguos y se basa en el cifrado monoalfabético más simple. Se considera un método débil de criptografía, ya que es fácil decodificar el mensaje debido a sus técnicas de seguridad mínimas.

#### Origen e historia

El gobernante romano Julio César (100 a. C. – 44 a. C.) utilizó un cifrado muy simple para la comunicación secreta. Sustituyó cada letra del alfabeto con una letra tres posiciones más adelante. Más tarde, cualquier cifrado que utilizara este concepto de «desplazamiento» para la creación de un alfabeto cifrado, se denominó cifrado César.

En el siglo XIX, la sección de anuncios personales en los periódicos a veces se usaba para intercambiar mensajes encriptados usando esquemas de cifrado simples. Kahn (1967) describe casos de amantes que participan en comunicaciones secretas cifradas utilizando el cifrado César en The Times.

Incluso ya en 1915, el cifrado César estaba en uso: el ejército ruso lo empleó como reemplazo de cifrados más complicados que habían resultado demasiado difíciles de dominar por sus tropas; Los criptoanalistas alemanes y austriacos tuvieron pocas dificultades para descifrar sus mensajes.

De todos los cifrados de tipo de sustitución, este cifrado de César es el más simple de resolver, ya que solo hay 25 combinaciones posibles.
