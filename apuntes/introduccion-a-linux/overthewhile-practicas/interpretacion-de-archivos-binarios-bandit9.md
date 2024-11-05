# Interpretación de archivos binarios \[Bandit9]

Encontrar la contraseña en el archivo data.txt que sea human-readable strings, precedida de un caracter '='

```
// filtramos por strings(cadenas de caracteres imprimibles), buscamos el '= ' y imprimimos la 2 columna
strings data.txt | grep "=" | tail -n 1 | awk '{print $2}'
G7w8LIi6J3kTb8A7j9LgrywtEUlyyp6s
```

