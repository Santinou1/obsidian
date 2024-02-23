Si queremos traer Datos de 2 O mas tablas, tenemos 2 Tecnicas para lograrlo.


1- La primera de estas 2 tecnicas se llama **Table Relation**

En la tenica **Table Relation** se logra mencionando en el listado de Tablas despues del **FROM** las tablas necesarias separadas por ",".

```sql
SELECT prdNombre,prdPrecio, mkNombre
	FROM productos, marcas
```      
Si hacemos eso nos va a generar un error debido que se hace un error recursivo.
Es decir nos va a traer todos los productos una vez y a cada uno de los productos va a poner la primera marca.
Despues vuelve a traer todos los productos y le pone a cada uno de los productos la segunda marca, y asi sucesivamente.
Este es un error de **producto cartesiano.**

Como se puede ver pone apple a todos, audiostechnica a todos y asi.

```sql
|   |   |   |
|---|---|---|
|Galaxy S21|899.99|Apple|
|Nikon Z6|1799.99|Apple|
|AT-LP120XUSB|199.99|Apple|
|Marshall Kilburn II|249.99|Apple|
|Samsung QLED Q90T|1499.99|Apple|
|Huawei MateStation X|599.99|Apple|
|Galaxy S21|899.99|Audiostechnica|
|Nikon Z6|1799.99|Audiostechnica|
|AT-LP120XUSB|199.99|Audiostechnica|
|Marshall Kilburn II|249.99|Audiostechnica|
|Samsung QLED Q90T|1499.99|Audiostechnica|
|Huawei MateStation X|599.99|Audiostechnica|
|Galaxy S21|899.99|Huawei|
|Nikon Z6|1799.99|Huawei|
|AT-LP120XUSB|199.99|Huawei|
|Marshall Kilburn II|249.99|Huawei|
|Samsung QLED Q90T|1499.99|Huawei|
|Huawei MateStation X|599.99|Huawei|
|Galaxy S21|899.99|Marshall|
|Nikon Z6|1799.99|Marshall|
|AT-LP120XUSB|199.99|Marshall|
|Marshall Kilburn II|249.99|Marshall|
|Samsung QLED Q90T|1499.99|Marshall|
|Huawei MateStation X|599.99|Marshall|
|Galaxy S21|899.99|Nikon|
|Nikon Z6|1799.99|Nikon|
|AT-LP120XUSB|199.99|Nikon|
|Marshall Kilburn II|249.99|Nikon|
|Samsung QLED Q90T|1499.99|Nikon|
|Huawei MateStation X|599.99|Nikon|
|Galaxy S21|899.99|Samsung|
|Nikon Z6|1799.99|Samsung|
|AT-LP120XUSB|199.99|Samsung|
|Marshall Kilburn II|249.99|Samsung|
|Samsung QLED Q90T|1499.99|Samsung|
|Huawei MateStation X|599.99|Samsung|
```


Como solucionamos ese error?
Vamos a tener que insertar un filtro para igualar las columnas en **COMUN**.

```sql
	SELECT prdNombre,prdPrecio, mkNombre
		FROM productos, marcas
				WHERE productos.idMarca = marcas.idMarca;
```

**WHERE productos.idMarca = marcas.idMarca**: Esta es la cláusula `WHERE`, que establece la condición para unir las dos tablas. La condición indica que se deben seleccionar solo las filas donde el valor en la columna `idMarca` de la tabla "productos" sea igual al valor en la columna `idMarca` de la tabla "marcas". En otras palabras, se están seleccionando los productos que tienen una correspondencia en términos de la marca a la que pertenecen.

La sintaxis entonces es

```sql
	SELECT colTabla1, colTabla2, colTabla2
		FROM tabla1, tabla2
			WHERE tabla1.fk = tabla2.pk
```

Por ejemplo, si ahora tambien queremos traer el nombre de las categorias de los productos seria.

```sql
SELECT prdNombre,prdPrecio, mkNombre, catNombre
	FROM productos, marcas, categorias
			WHERE productos.idMarca = marcas.idMarca
				AND productos.idCategoria = categorias.idCategoria
```

2- La segunda se llama **Table Join**

En la tecnica **JOIN** no se menciona en el **TABLE LIST** (despues del **FROM**) solo se menciona en la tabla principal.
Y utilizamos la palabra reservada **JOIN** para mencionar las tablas secundarias.
Y finalizamos igualando la columna en comun despues de la palabra **ON**


```sql
SELECT prdNombre,prdPrecio,mkNombre
	FROM productos
    JOIN marcas
		ON productos.idMarca= marcas.idMarca
```


La sintaxis seria

```sql
SELECT colTabla1, colTabla2, colTabla2
	FROM tabla1
	JOIN tabla2
		ON tabla1.fk=tabla2.pk
```


Por ejemplo, si ahora tambien queremos traer el nombre de las categorias de los productos seria.

```sql
SELECT prdNombre, prdPrecio, mkNombre, catNombre
FROM productos
JOIN marcas ON productos.idMarca = marcas.idMarca
JOIN categorias ON productos.idCategoria = categorias.idCategoria;

```
	