# Escapando del contexto de un comando \[Bandit25-26]

¡A veces el tamaño sí que importa!, aislado a esto que hemos visto, el comando ‘more‘ lo que te permite es mostrar el resultado de la ejecución de un comando en la terminal de a una página a la vez. Esto es especialmente útil para casos en los que se ejecutan comandos que puedan llegar a causar un gran desplazamiento.

Para pasar a la página siguiente, tienes que presionar la barra espaciadora en el teclado.

Puedes continuar presionando espacio hasta llegar al final del resultado o puedes presionar la tecla “q” directamente para salir.

```
// 
ssh -i bandit26.sshkey.bandit26@localhost
// Viendo la terminal minimizada vemos el modo more y ejecutamos comando
// Ejecutamos ESC+Shift y escribimos 
:set shell=/bin/bash
:shell
// ejecutamos el script y mandamos un comando para ver la contraseña bandit27
./bandit27 cat /etc/bandit_pass/bandit27
```
