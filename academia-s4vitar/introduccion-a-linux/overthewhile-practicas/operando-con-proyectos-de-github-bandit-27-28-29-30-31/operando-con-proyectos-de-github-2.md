# Operando con proyectos de Github

Clonamos el repositorio y encontrar la contraseña

```
// vemos los logs
git log
git show <log>
// no vemos nada
// vamos a ver las ramas -> las ramas son difurcaciones del estado de codigo
git branch -a
git checkout <rama>
// hasta que demos con la rama donde se aloje la contraseña
```

El comando ‘git branch‘ nos permite crear, enumerar y eliminar ramas, así como cambiar sus nombres. Es importante recalcar que no nos permite cambiar entre ramas o volver a unir un historial bifurcado. Por este motivo, ‘git branch‘ está estrechamente integrado con los comandos ‘git checkout‘ y ‘git merge‘.
