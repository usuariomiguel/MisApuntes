# Ejecución de comandos por SSH \[Bandit18]

The password for the next level is stored in a file **readme** in the homedirectory. Unfortunately, someone has modified **.bashrc** to log you out when you log in with SSH.

A través del archivo de configuración ‘**.bashrc**‘ o ‘**.zshrc**‘, es posible definir una serie de acciones a llevar a cabo a la hora de obtener una consola interactiva, en este caso tras ingresar por SSH.

Es por ello que tras ingresar, somos expulsados de forma inmediata, dado que así ha sido definido en el archivo de configuración ‘**.bashrc**‘ para el caso que estamos tratando. Si colamos un comando al final de nuestra línea al aplicar una autenticación por SSH, lograremos que ese comando sea introducido a nivel de sistema antes de que se interprete el archivo de configuración pertinente.

```
// Como no podemos entrar directamente vamos a lanzar comandos remotamente con ssh

ssh bandit18@bandit.labs.overthewire.org -p 2220 cat readme
awhqfNnAbc1naukrpqDYcF95h7HoMTrC

// otra forma mas comodo en abrirnos una bash

ssh bandit18@bandit.labs.overthewire.org -p 2220 bash
ls
readme
cat readme
awhqfNnAbc1naukrpqDYcF95h7HoMTrC
```

