# Privilegios especiales - Capabilities

{% embed url="http://www.etl.it.uc3m.es/Linux_Capabilities" %}

Los permisos capabilities permiten a los procesos realizar tareas específicas sin tener que ejecutarse con privilegios de superusuario.

En Linux, el comando sudo se utiliza para otorgar permisos de superusuario a los usuarios. Sin embargo, esto puede ser peligroso, ya que los usuarios pueden tener acceso completo al sistema. Las capabilites, por otro lado, permiten a los procesos realizar tareas específicas sin tener que ejecutarse con privilegios de superusuario.

```
//ver capabilities
getcap -r / 2>/dev/null
//asignar capabilitie
setcap --options
```

{% hint style="info" %}
En GTFOBins se pueden filtrar por capabilites para escalada de privilegios.
{% endhint %}
