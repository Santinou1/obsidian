
Filtrar Registros significa , traer solamente los registros que cumplan con una condicion brindada.

Puede ser que traiga solamente los que tengan id Pares, etc.

Para implementar un filtro utilizamos la palabra reservada **WHERE** seguida de una condicion.

Podemos realizar por ejemplo.

Traer todos los destinos con un precio hasta 8000.

```sql
SELECT aeropuerto, precio
	FROM destinos
		WHERE precio <=8000
```

Por ejemplo si queremos traer el de mayor precio podemos utilizar la funcion "MAX".

```sql
SELECT aeropuerto,MAX(precio)
FROM destinos
```

Y si queremos ordenar los resultados filtrados de manera ascendente como hacemos?


```sql
SELECT aeropuerto, precio
	FROM destinos
		WHERE precio <=8000
			ORDER BY precio;
```

Ahora, como podemos hacer para traer TODOS los destinos con un precio entre 6600 y 8000

```sql
SELECT aeropuerto, precio
	FROM destinos
		WHERE precio >=6600 
		AND precio<=8000
```

Para realizar mas de una condicion usamos la palabra reservada **"AND"**.

Como hacemos para traer todos los destinos de la region 5.

```sql
SELECT aeropuerto, precio
	FROM destinos
		WHERE idRegion=5 
```


Ahora, para traer todos los destinos de la region 3 y  de la region 5.

```sql
SELECT aeropuerto, precio
	FROM destinos
		WHERE idRegion=5
        OR idRegion=3
```

Como podemos ver para realizar esa consulta usamos la palabra reservada "**OR**".

Porque no usamos AND?

Porque AND, es un operador que anida al where, es decir primero va a filtrar todos los que tienen idRegion 5 , y despues tambien va a buscar los que tienen idRegion 5 y ademas idRegion 3.
Es imposible anidar esas 2 operaciones.

Ahora por eso se utiliza OR, debido que OR funciona para uno u otro.


Tambien podemos utilizar la funcion  **"IN"**.

La funcion IN, hace referencia a que podes meter mas de una opcion en la misma consulta es decir.

```sql
SELECT aeropuerto, precio
	FROM destinos
		WHERE idRegion IN (3,5)
```

 