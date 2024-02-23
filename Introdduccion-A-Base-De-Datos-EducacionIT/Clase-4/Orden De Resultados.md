
Para ordenar los resultados de una consulta usamos la palabra reservada **ORDER BY**.

Como podemos ver los resultados cuando nosotros hacemos el clasico.

```sql
SELECT idRegion,aeropuerto,precio FROM destinos;
```

Los resultados se muestran mediante el criterio de orden el ID.

Ahora, si hacemos por ejemplo

```sql
SELECT * FROM regiones
```

Se va a ordenar de manera ALFABETICAMENTE, no por el ID.

Ahora, como hacemos para ordenarlo de otra manera?


Utilizando la palabra reservada **ORDER BY**

```sql
SELECT aeropuerto, precio
	FROM destinos
		ORDER BY precio;
```

Como podemos ver ahi, vamos a ordenarlo por el criterio del PRECIO, es decir de menor a mayor.

Como vimos por default ordena de menor a mayor, pero, como hacemos si queremos ordenar de MAYOR a MENOR?

Utilizamos la palabra reservada **DESC** (Descendente)

```sql
SELECT aeropuerto, precio
	FROM destinos
		ORDER BY precio DESC;
```


Ahora, si lo queremos traer de manera alfabeticamente podriamos hacer-

```sql
SELECT aeropuerto, precio
	FROM destinos
		ORDER BY aeropuerto;
```


Tambien podemos ordenarlo por un campo que no fue llamado previamente , es decir que no fue seleccionado en el SELECT.
Por ejemplo

```SQL
SELECT aeropuerto, precio
	FROM destinos
		ORDER BY idRegion;
        
```

Como se ve, podemos usar como CRITERIO de orden una columna que no estamos pidiendo mostrar.


Ahora, como hacemos si por ejemplo ordenar de menor a mayor los previamente ordenados por el criterio de idRegion?

Porque nosotros ordenamos por idRegion , pero estan todos juntos los de **idRegion 4** , pero no estan ordenados por precio por ejemplo.

Eso se logra separando por "," el criterio de orden.

```sql
SELECT aeropuerto, precio
	FROM destinos
		ORDER BY idRegion, precio;
```

