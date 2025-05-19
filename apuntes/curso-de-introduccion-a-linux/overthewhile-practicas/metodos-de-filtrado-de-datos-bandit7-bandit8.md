# Métodos de filtrado de datos \[Bandit7 - Bandit8]

### Bandit 7

Hay que encontrar la password en el archivo data.txt despues de la palabra millionth

```
// Some code
cat data.txt | grep millionth | awk '{print $2}'
cat data.txt | grep millionth | xargs | cut -d ' ' -f 2
TESKZC0XvTetK0S9xNwm25STk5iWrBvP
```

**Comando AWK**

Los usos básicos que podemos dar al comando Awk son los siguientes:

1. Buscar palabras y patrones de palabras y reemplazarlos por otras palabras y/o patrones.
2. Hacer operaciones matemáticas.
3. Procesar texto y mostrar las líneas y columnas que cumplen con determinadas condiciones.
4. Etc.

XARGS&#x20;

Reporta todo el un mismo espacio, es decir, quita todos los espacios para sobrantes para poder filtar la información

```
echo 'hola      mundo' > prueba
cat prueba 
hola      mundo
cat prueba | xargs 
hola mundo
```

Por aquí te dejo un par de Cheat Sheets para el comando ‘**AWK**‘, en caso de que quieras investigar un poco más:

* AWK Cheat Sheet: [https://www.shortcutfoo.com/app/dojos/awk/cheatsheet](https://www.shortcutfoo.com/app/dojos/awk/cheatsheet)
* AWK Cheat Sheet 2: [https://bl831.als.lbl.gov/\~gmeigs/scripting\_help/awk\_cheat\_sheet.pdf](https://bl831.als.lbl.gov/\~gmeigs/scripting\_help/awk\_cheat\_sheet.pdf)

También te dejo algunos enlaces de interés por si quieres indagar un poco más acerca del uso del comando ‘cut‘:

* &#x20;Cheat Sheet: Cutting Text with cut: [https://bencane.com/2012/10/22/cheat-sheet-cutting-text-with-cut/](https://bencane.com/2012/10/22/cheat-sheet-cutting-text-with-cut/)

### Bandit9

Hay que encontrar la contraseña en el archivo data.txt en una línea de texto que solo ocurre una única vez "que no se repite"

```
// Ordenamos alfabeticamente con el comando sort las filas y luego imprimimos la que sea unica con el parametro -u y -c que cuenta las repeticiones.
sort data.txt | uniq -cu
EN632PlfYiZbn3PhVK3XOGSlNInNE00t
```

Te dejo a continuación unos enlaces de interés para que puedas indagar en el uso de los comandos ‘**sort**‘ y ‘**uniq**‘:

* Tutorial del uso de SORT: [https://www.ibidemgroup.com/edu/tutorial-sort-linux-unix/](https://www.ibidemgroup.com/edu/tutorial-sort-linux-unix/)
* Tutorial del uso de UNIQ: [https://victorhckinthefreeworld.com/2021/10/21/el-comando-uniq-de-gnu/](https://victorhckinthefreeworld.com/2021/10/21/el-comando-uniq-de-gnu/)
