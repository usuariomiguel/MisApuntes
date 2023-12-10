# 2. Lectura de archivos especiales \[Bandit1 - Bandit2]

Puede ser que en alguna ocasión te encuentres con algún archivo que empiece por el símbolo ‘**–**‘.

```
// Para ver contenido de un archivo que sea - deberemos indicarle a la 
maquina que no se trata de un parametro si no de un archivo:
 
cat /home/usuario/-
cat ./-
grep -r "\w" 2>/dev/null | tail -n 1 | cut ":" -f 2
grep -r "\w" 2>/dev/null | tail -n 1 | tr ":" " " | rev | awk '{print $1}' | rev

```

Archivo con espacios

```
// la consola va a interpretar despues del espacio que son
varios archivos:

cat 'archivo con espacios'
cat archivo\ con\ espacios
cat arch*

// Si tabulas automaticamente detecta el archivo
```

