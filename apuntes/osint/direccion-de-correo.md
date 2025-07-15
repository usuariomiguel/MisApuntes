# Dirección de correo

### Información de hosting

**MXToolbox**: muestra los MX configurados públicamente, es decir, que si tiene un filtro de seguridad, este será mostrado.  [https://mxtoolbox.com/SuperTool.aspx](https://mxtoolbox.com/SuperTool.aspx)

**Pulsedive**: en el apartado de mal server mostrará el servidor final donde llegan los correos, este se debe a que este software muestra historial de tráfico real o cabeceras asociadas.  [https://pulsedive.com/](https://pulsedive.com/)

**Netlas.io**: puedes encontrar emails asociados al dominio, los MX configurados públicamente y el NS [https://netlas.io/](https://netlas.io/)

### Busqueda de correo

**Hunter**: personalmente la mejor herramienta para busqueda de correo además de tener varias funcionalidades muy utiles como verificación de seguridad de una dirección. **DE PAGO** [**https://hunter.io/dashboard**](https://hunter.io/dashboard)

### Analisis de correo

**Phistool:** Esta herramienta te ahorra mucho trabajo, enseñando una cantidad inmensa de informacion de un correo sospechosos, como cabeceras, seguridad (DKIM - DMARC - SPF), etc.&#x20;

{% embed url="https://app.phishtool.com/" %}

**CMD:** Algunos comandos utilies para analisis de correos son:&#x20;

Verificar el SPF del servidor remoto:

```
nslookup -type=txt dominio.com
```
