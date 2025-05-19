# Jugando con conexiones \[Bandit20]



```
// Ejecutamos el script con permiso SUID la funcion es que se conecta a un puerto y te proporciona la password Bandit21 si reciber la contraseña de Bandit20

bandit20@bandit:~$ ./suconnect 1112
Read: VxCazJaVykI6W36BkBU0mJTCM8rR95XT
Password matches, sending next password

bandit20@bandit:~$ nc -nlvp 1112
Listening on 0.0.0.0 1112
Connection received on 127.0.0.1 34426
VxCazJaVykI6W36BkBU0mJTCM8rR95XT
NvEJF7oVjkddltPSrdKEFOllh9V1IBcq
```
