# Abusando de tareas Cron \[Bandit22]

Sacar la password de bandit23, fijandonos en las tareas crontab /etc/cron.d

```
// Vemos que cronjob_bandit23 ejecuta un script
// vemos que este script copian la contraseña en un temporal
// para ver que temporal tenemos que entender el siguiente comando

myname=$(whoami)
mytarget=$(echo I am user $myname | md5sum | cut -d ' ' -f 1)

// Veamos la contraseña

cat /tmp/8ca319486bfbbc3663ea0fbe81326349
QYw0Y2aiA672PsMmh9puTQuhoz8SyR2G
```
