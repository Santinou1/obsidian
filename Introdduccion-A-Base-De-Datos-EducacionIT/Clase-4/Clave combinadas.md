Una clave combinada es un campo que se puede formar a partir de 2  o mas campos/columnas.

Entonces trae informacion de 2 columnas, trae 2 datos.

Por ejemplo

Nosotros podemos crear un codigo de avion a partir de  2 campos.

Por ejemplo, si nosotros quisieramos saber el N° De Vuelo seria.

El nombre de la Aerolinea + la Ruta Aerea = N° de Vuelo 

Nombre de la aerolinea = IB
Ruta Aerea= 6856

N° De vuelo= IB + 6856 = IB6856


Mas detalladamente seria:

Tenemos las 2 tablas.

```sql
CREATE TABLE aerolineas(
id smallint unsigned auto_increment not null primary key,
nombre varchar(50) unique not null,
identificador varchar(10) not null unique
)
```

```sql
CREATE TABLE rutas(
id smallint unsigned auto_increment not null primary key,
origen varchar(50)  not null,
destino varchar(50)  not null,
codigo smallint unsigned not null
)
```

Entonces, en la tabla aerolineas tendriamos los datos de 

ID = 1
Nombre = Iberia
Identficador= IB


Y en la tabla rutas tendriamos los datos de

ID = 1
Origen = España
Destino = Londres
Codigo = 6856

Ahora sabemos de donde salen = **El identificador de la Aerolinea + Codigo de la Ruta Aerea = N° de Vuelo** 

