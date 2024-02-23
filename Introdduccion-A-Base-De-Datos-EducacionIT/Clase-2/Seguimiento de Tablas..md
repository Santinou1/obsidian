
Hasta ahora habiamos creado esta porcion de tabla

```sql
CREATE TABLE personas 
					  (id tinyint unsigned auto_increment,
					  apellido varchar(255) ,
					  nombre varchar(255),
					  dni int unsigned unique ,
					  alta date
);
``` 

Que se componia en=

```sql
- CREATE : Palabra Reservada de SQL
- TABLE : Palabra Reservada de SQL
- personas : Nombre que tendra nustra tabla
	- id : Nombre del campo 
	- tinyint : DataType
	- unsigned : Caracteristica
	- not null : Caracteristica
	- auto_increment : Caracteristica
	- primary key : Primary Key
		- apellido : Nombre del campo
		- varchar(255) : DataType
		-  not null : Caracteristica
			- nombre: Nombre del campo
			- varchar(255): DataType
			-  not null : Caracteristica
				- dni : Nombre del Campo
				- int : DataType
				- unsigned: Caracteristica
				- unique: Caracteristica
				-  not null : Caracteristica
					- alta: Nombre del Campo
					- date: DataType
					-  not null : Caracteristica
	
```

```sql
CREATE TABLE nombreDeLaTabla 
					  (nombreColumn1 datatype caracteristica, primary key
					  nombreColumna2 datatype caracteristica,
					  nombreColumna3 datatype caracteristica,
					  nombreColumna4 datatype caracteristica)
```


Ahora en esta clase vamos a seguir trabajando con la creacion de tablas.

Vamos a agregarle a cada uno la Caracteristica not null.
Que nos va a ayudar es que no tengamos datos erroneos en el datatype que nosotros brindamos por ejemplo.

```sql
Ejemplos de not nulls.

tinyint --- "Hola"
varchar --- vacio
date --- 25
dni --- "String"
```


```sql
CREATE TABLE personas 
					  (id tinyint unsigned auto_increment not null primary key,
					  apellido varchar(255) not null ,
					  nombre varchar(255) not null,
					  dni int unsigned unique not null ,
					  alta date not null
);
``` 



Y el ultimo concepto que vamos a ver ahora, es que la primera columnas tiene que tener una "primary_key", que eso va a identificar a que cada campo es unico.
Y eso nos va a ayudar a cuando querramos filtrar por ejemplo, vamos a buscar por primary key.
Solamente se puede tener una primary key por tabla.
  

Asi que en resumen la tabla creada quedaria de esta manera

```sql
CREATE TABLE personas 
					  (id tinyint unsigned auto_increment not null primary key,
					  apellido varchar(255) not null ,
					  nombre varchar(255) not null,
					  dni int unsigned unique not null ,
					  alta date not null
);
```

Y sus componentes y cada una de sus palabras significa

```sql
- CREATE : Palabra Reservada de SQL
- TABLE : Palabra Reservada de SQL
- personas : Nombre que tendra nustra tabla
	- id : Nombre del campo 
	- tinyint : DataType
	- unsigned : Caracteristica
	- not null : Caracteristica
	- auto_increment : Caracteristica
	- primary key : Primary Key
		- apellido : Nombre del campo
		- varchar(255) : DataType
		-  not null : Caracteristica
			- nombre: Nombre del campo
			- varchar(255): DataType
			-  not null : Caracteristica
				- dni : Nombre del Campo
				- int : DataType
				- unsigned: Caracteristica
				- unique: Caracteristica
				-  not null : Caracteristica
					- alta: Nombre del Campo
					- date: DataType
					-  not null : Caracteristica
```


 