Para crear una tabla utilizamos el comando CREATE TABLE

> Sintaxis:

```sql
CREATE TABLE personas
```

Si ejecutamos ese comando VA A LANZAR ERROR, debido que no se puede crear una TABLA si no esta creada previamente las columnas.

Como generamos columnas?

Entre parentesis en la sintaxis,agregamos la columna.

Ejemplo

```sql
CREATE TABLE nombreDeLaTabla 
					  (nombreColumn1 datatype caracteristica,
					  nombreColumna2 datatype caracteristica,
					  nombreColumna3 datatype caracteristica,
					  nombreColumna4 datatype caracteristica)
```

Primero usamos las palabras reservadas "CREATE TABLE " y posteriormente ponemos el nombre que queremos que se llame la tabla y despues entre parentesis el nombre de las columnas.

Tambien algo muy importante es que se tiene que aclarar que TIPO DE DATO representa cada columna.
Y tambien como podemos visualizar en la primera COLUMNA vemos que el ID es AUTO-INCREMENTABLE, asi que vamos a realizar esos parametros en nuestra creacion de la tabla.

El termino "unsigned" hace referencia a que solamente va a almacenar numeros positivos es decir por ejemplo un **tinyint unsigned** va a almacenar entre 0 a 255, en cambio un **tinyint** va a almacenar entre  -128 a 127

El tipo de dato **char** consume el total de datos puestos por el usuario es decir

char(42) = santino 
esa sentencia va a ser santino____________
y un total de espacios en blancos hasta llegar a 42 que es lo establecido por nosotros.

en cambio varchar(45) = santino
solamente va a usar el texto proporcionado, no va a autocompletar con el maximo que nosotros le dijimos.

Tambien usamos la caracteristica / restriccion "unique" en el campo DNI, debido que el dni es UNICO.


Ahora vamos a realizar esa tabla

![[Pasted image 20231219150415.png]]


```sql
CREATE TABLE personas 
					  (id tinyint unsigned auto_increment,
					  apellido varchar(255) ,
					  nombre varchar(255),
					  dni int unsigned unique ,
					  alta date
);
```

