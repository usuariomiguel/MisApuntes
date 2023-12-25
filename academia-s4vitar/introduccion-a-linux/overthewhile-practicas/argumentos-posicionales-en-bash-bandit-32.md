# Argumentos posicionales en Bash \[Bandit 32]

After all this `git` stuff its time for another escape. Good luck!

```
// Solo toma variable de entorno
// $0 = variable que imprime primer argumento 
$0
// ya tenemos una bash y vemos la contraseaña
```

En Bash se pueden usar argumentos desde la línea de comandos, los cuales son enviados a los scripts como variables. Estos quedarían representados de la siguiente forma:

\[$0]: Representa el nombre del script que se invocó desde la terminal.

\[$1]: Es el primer argumento desde la línea de comandos.

\[$2]: Es el segundo argumento desde la línea de comandos y así sucesivamente.

\[$#]: Contiene el número de argumentos que son recibidos desde la línea de comandos.

\[$\*]: Contiene todos los argumentos que son recibidos desde la línea de comandos, guardados todos en la misma variable.
