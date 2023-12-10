# Directorio y archivos ocultos \[Bandit3]

Todo lo que empieza por ‘**.’** es oculto en el sistema. Los archivos ocultos (también llamados archivos dot) en los sistemas operativos Unix, son archivos que se utilizan para ejecutar ciertos scripts o para almacenar la configuración de algunos servicios del host.

Esto no tiene por qué ser del todo así, dado que también puedes crearte tus propios archivos y directorios ocultos.

```
// Para ver estos archivos ocultos existe la opcion en el comando ls
o con el comando find 
ls -la
find . 
find . -type f
```

