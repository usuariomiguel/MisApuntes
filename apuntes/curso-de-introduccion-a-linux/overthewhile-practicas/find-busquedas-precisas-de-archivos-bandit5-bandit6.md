# FIND - Búsquedas precisas de archivos \[Bandit5 - Bandit6]

AYUDA - ¿Cómo buscar y encontrar archivos en Linux?: [https://www.ionos.es/digitalguide/servidores/configuracion/comando-linux-find/](https://www.ionos.es/digitalguide/servidores/configuracion/comando-linux-find/)

**Bandit5**&#x20;

Encontrar la contraseña en un fichero con las siguientes características:

* human-readable
* 1033 bytes in size
* not executable

**Solución**&#x20;

<pre><code><strong>find . -type f ! -executable -size 1033c | xargs cat | xargs
</strong>P4L4vucdmLnm8I7Vl7jG1ApGSfjYKqJU
</code></pre>

**Bandit6**

**Encontrar la contraseña en un fichero con las siguientes características:**

* owned by user bandit7
* owned by group bandit6
* 33 bytes in size

```
// Some code
find / -type f -user bandit7 -group bandit6 -size 33c 2>/dev/null | xargs cat
z7WtoNQU2XfjmMtWA8u5rN4vzqu4v99S
```
