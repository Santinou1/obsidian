Imaginemos que tenemos una Base de Datos que tiene 1 tabla de productos.

```sql
TABLE productos
	(
		nombre primary key,
		precio decimal(10,2),
		proveedor 
	)
```

Ahora, el campo proveedor, no es propio de la Tabla porductos.

No es necesario ? 
En nuestra tabla de productos es mala practica tener la informacion del proveedor, como el cuil, telefono etc.

Entonces que hacemos? A proveedor, lo obtenemos de otra table en donde ahi si van a estar todos los proveedores.

Y en esa tabla donde estan todos los proveedores vamos a buscar al proveedor de nuestro producto y lo vamos a unir mediante su key.

Y para que quisieramos los datos del proveedor en nuestra tabla? 
Porque queremos vincular campos de nuestros productos un campo de su tabla, (SU ID)

por ejemplo

Imaginemos que el proveedor que nos trae todos los congelados nos aumento un 5%.
Si nosotros utilizamos este codigo...

```sql
UPDATE productos
	SET precios=precio * 1.05
```

Estamos diciendo que todos los precios de nuestros productos aumenten un 5% y no tiene sentido, porque solamente aumento los productos del proveedor de congelados.

Entonces en ese caso SI vamos a necesitar saber que proveedor es el que nos esta aumentando e identificarlo con el where.

Entonces el codigo correcto quedaria...

-- Imaginemos que el proveedor tiene id 6

```sql
UPDATE productos
	SET precio=precio*1.05
	WHERE idProveedor= 6
	-- el id lo conseguiriamos mediante la foreign key, en la tabla de proveedores el proveedor de congelados tiene un id, y lo vamos a unir a nuestra tabla productos mediante la foreign key.
```

Eso es el concepto de Foreign Key.

Ahora vamos a hacer todo lo comentado de manera correcta y en codigo.

Primero creamos la tabla productos.


```sql
TABLE productos
	(
		idProductos auto_increment primary key
		nombre varchar(55),
		precio decimal(10,2),
		idProveedor tinyint unsigned  not null, 
		foreign key (idProveedor) references proveedores(idProveedor),	
	)
```

Posteriormente creamos la tabla de proveedores


```sql
TABLE proveedores
	(
		idProveedor tinyint unsigned auto_increment not null,
		nombre varchar(55),
		cuit unique bigint ,
	)
```

La sintaxis del foreign key es

**foreign key (nombreDelCampo) references nombreDeLaTabla(nombreDelCampo)**

