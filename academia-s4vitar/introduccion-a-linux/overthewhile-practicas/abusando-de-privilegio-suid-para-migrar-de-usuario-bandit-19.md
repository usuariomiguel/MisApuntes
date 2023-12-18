# Abusando de privilegio SUID para migrar de usuario \[Bandit 19]

{% hint style="info" %}
To gain access to the next level, you should use the setuid binary in the homedirectory. Execute it without arguments to find out how to use it. The password for this level can be found in the usual place (/etc/bandit\_pass), after you have used the setuid binary.
{% endhint %}

**SUID** es un permiso de archivo especial para archivos ejecutables que permite a otros usuarios ejecutar el archivo con los permisos efectivos del propietario del archivo. **SGID**, por el contrario, es un permiso de archivo especial que también se aplica a los archivos ejecutables y permite a otros usuarios heredar el GID efectivo del propietario del grupo de archivos.

SUID significa “establecer ID de usuario” (Set owner User ID) y SGID significa “establecer ID de grupo” (Set Group ID up on execution).

```
// Ya que tenemos permiso de ejecucion del archivo dentro de bandit19 lo ejecutamos
./bandit20-do cat /etc/bandit_pass/bandit20
VxCazJaVykI6W36BkBU0mJTCM8rR95XT
```





