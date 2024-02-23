Para insertar datos en una Tabla hay 6 maneras.

Pero las mas conocidas son 3.


La primera manera es usando la palabra reservada **SET**.

La segunda manera es usando la sintaxis completa. (Se mencionan las columnas / campos)

La tercera manera es usando la sintaxis simplifcada. (NO se mencionan las columnas)


---

EJEMPLO DE COMO SE PUEDE INSERTAR DATOS DE LA PRIMERA MANERA

Como podemos observar este modo de insertar datos, es similar a un objeto/diccionario, debido que se trabaja con key value.
Nosotros primero usamos la palabra reservada SET y porteriormente ingresamos el nombreDeLaColumna y la igualamos al valor que querramos.

```sql
INSERT INTO nombreDeLaTabla
	SET
		nombreDeLaColumna = valor,
		nombreDeLaColumna2 = valor2,
		nombreDeLaColumna3= valor3;
```

EJEMPLO PRACTICO 1

```sql
INSERT INTO personas
	SET 
    id=DEFAULT,
    apellido="Romero",
	nombre="Paula",
    dni=22696280,
    alta="2023-12-20";
```


EJEMPLO DE COMO SE PUEDE INSERTAR DATOS DE LA SEGUNDA MANERA

Como podemos observar este modo de insertar datos , tenemos que aclarar primeramente en unos parentesis todos los campos a los que queremos agergar informacion, y posteriormente con la palabra reservada "VALUES" tenemos que poner que datos queremos agregar a esas columnas.



```sql
INSERT INTO nombreDeLaTabla
		(nombreCampo, nombreCampo2, nombreCampo3 )
		VALUES
		(valorCampo, valorCampo2, valorCampo3)
```


EJEMPLO PRACTICO 2

 ```sql
 INSERT INTO personas
	(id,apellido,nombre,dni,alta)
VALUES
    (DEFAULT,"Ursino","Fabian",21848036,"2023-12-20");
```



EJEMPLO DE COMO SE PUEDE INSERTAR DATOS DE LA TERCERA MANERA

Como podemos observar este modo de insertar datos, es de manera implicita sin mencionar las columnas..
Lo que pasa es que de esta manera no podes por ejemplo seleccionar que datos quereres ingresar en una columna especifica.
SI O SI tenes que ingresar datos en todas las columnas

```sql
INSERT INTO nombreDeLaTabla
	VALUES
		(
		DEFAULT,
		"Romero",
		"Paula",
		22696280,
		"2023-12-21"
		)
```


EJEMPLO PRACTICO 3

```sql
INSERT INTO personas
	VALUES
		(
		DEFAULT,
		"Romero",
		"Paula",
		22696280,
		"2023-12-21"
		)
```


