# Detección de diferencias entre archivos \[Bandit17]

Hay dos archivos en el homedirectory: password.old y passwords.new. La contraseña esta en passwords.new y en la unica linea que es diferente con el passwords.old&#x20;

```
// Con el comando diff vemos las difencias entre archivos
diff passwords.old passwords.new
42c42
< hga5tuuCLF6fFzUpnagiMN8ssu9LFrdg
---
> p6ggwdNHncnmCNxuAt0KtKVq185ZU7AW

```

Aquí tienes algunos ejemplos del uso del comando ‘diff‘:

* &#x20;Comparar las diferencias con el comando diff: [https://eltallerdelbit.com/comando-diff-ejemplos/](https://eltallerdelbit.com/comando-diff-ejemplos/)
