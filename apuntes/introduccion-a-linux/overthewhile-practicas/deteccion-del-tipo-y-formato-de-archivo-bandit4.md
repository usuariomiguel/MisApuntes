# Detección del tipo y formato de archivo \[Bandit4]

Muchos formatos de archivo no están pensados para leerse como texto. Si dicho archivo se ve accidentalmente como un archivo de texto, su contenido será ininteligible. Sin embargo, a veces la firma del archivo se puede reconocer cuando se interpreta como texto.

Por aquí te dejo una lista de firmas de archivos. La columna correspondiente a ‘**Firma Hexadecimal**‘ está directamente relacionada a los primeros bytes que en comparación a los primeros bytes del archivo con el que estamos tratando nos permitirán saber el tipo de formato al que nos estamos enfrentando:

* &#x20;Lista de firmas de archivos: [https://en.wikipedia.org/wiki/List\_of\_file\_signatures](https://en.wikipedia.org/wiki/List\_of\_file\_signatures)

**Solución**&#x20;

```
// filtramos archivos y el tipo de contenido
find . -type f | grep '-file' | xargs file
// cateamos desde el directorio del usuario bandit4
cat ./inhere/-file07
```
