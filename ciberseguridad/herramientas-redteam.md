# Herramientas RedTeam

### Esteganografía

#### Stegseek.

1. **Categoría**: **Herramienta de búsqueda de esteganografía**.
2. **Función**: Stegseek se utiliza para **buscar** posibles datos ocultos en archivos. Su enfoque principal es la identificación de archivos que podrían contener datos esteganografiados, a menudo buscando patrones que indican la presencia de información oculta.
3. **Uso**: Se usa principalmente para buscar en grandes conjuntos de archivos o en sistemas de archivos completos para encontrar imágenes que podrían estar ocultando datos. Stegseek es útil en contextos de investigación forense y seguridad para detectar posibles ocultaciones de información.

```sh
apt install stegseek
```

{% embed url="https://github.com/RickdeJager/stegseek" %}

#### Steghide

1. **Categoría**: **Herramienta de esteganografía**.
2. **Función**: Steghide se utiliza para **ocultar** datos dentro de archivos, como imágenes y archivos de audio. También permite extraer datos ocultos de archivos que contienen información esteganográfica.
3. **Uso**: Permite a los usuarios ocultar información dentro de archivos multimedia, como imágenes y archivos de audio, utilizando técnicas de esteganografía. Es útil tanto para ocultar datos de manera segura como para realizar pruebas de esteganografía.

```bash
apt install steghide
```

{% embed url="https://www.kali.org/tools/steghide/" %}

### Phishing

1. **Categoría**: **Herramienta de phishing**.
2. **Función**: Camphish está diseñada para crear y gestionar campañas de phishing. Permite a los usuarios configurar páginas web que imitan sitios legítimos para engañar a los usuarios y recopilar sus credenciales o información sensible.
3. **Uso**: Se utiliza para simular ataques de phishing con fines de prueba de seguridad, auditoría de seguridad o formación. Los profesionales de seguridad la usan para evaluar la vulnerabilidad de los usuarios ante ataques de phishing.

{% embed url="https://github.com/techchipnet/CamPhish" %}

### Ingeniería Social

#### OhMyQR

1. **Categoría**: **Generador de QR Codes con funcionalidades de ingeniería social**.
2. **Función**: OhMyQR es una herramienta que genera códigos QR personalizados. Estos códigos pueden redirigir a páginas web específicas, descargar archivos o realizar otras acciones cuando se escanean con un lector de QR.
3. **Uso**: Aunque puede ser utilizada para diversas aplicaciones benignas como marketing y promociones, también puede ser usada para fines de ingeniería social, como crear códigos QR que dirijan a páginas de phishing o descarguen malware. Es útil para crear campañas de ingeniería social o para realizar pruebas de seguridad.

{% embed url="https://github.com/cryptedwolf/ohmyqr" %}

### Fuzzing

#### FUFF

1. **Categoría**: **Fuzzing de Headers HTTP**.
2. **Función**: fuff está diseñado específicamente para **fuzzing** de headers HTTP. Envía diferentes combinaciones y valores de headers HTTP a un servidor para identificar posibles problemas en cómo el servidor maneja estas entradas.
3. **Uso**: Se usa principalmente para probar aplicaciones web, enfocándose en los headers HTTP para detectar vulnerabilidades en el manejo de estos datos.

{% embed url="https://github.com/ffuf/ffuf" %}

#### ZFUZZ

1. **Categoría**: **Fuzzing**.
2. **Función**: ZFuzz se utiliza para realizar **fuzzing** en aplicaciones y servicios, buscando identificar vulnerabilidades al enviar entradas malformadas o aleatorias. Esta técnica ayuda a descubrir errores en el procesamiento de datos por parte de la aplicación.
3. **Uso**: Es útil para probar la robustez de una aplicación al someterla a una gran cantidad de datos inesperados, ayudando a encontrar fallos de seguridad como desbordamientos de búfer o errores en el manejo de excepciones.

{% embed url="https://github.com/z3pp/ZFuzz" %}

> #### Diferencias entre Fuff y Zfuff
>
> * Ambas herramientas se enmarcan en el ámbito del fuzzing, pero **ZFuzz** tiene un enfoque más general, mientras que **fuff** está especializada en un aspecto particular del fuzzing relacionado con las aplicaciones web.

