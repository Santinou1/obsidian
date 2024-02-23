
Creemos 2 tablas que tengan el siguiente diagrama.

```sql
CREATE TABLE destinos
(
idDestino smallint unsigned auto_increment not null primary key,
aeropuerto varchar(50) unique not null,
precio decimal(10,2) unsigned not null,
idRegion tinyint unsigned not null,
foreign key (idRegion) references regiones(idRegion),
activo boolean not null
);
```


```sql
CREATE TABLE regiones
(
idRegion tinyint unsigned auto_increment not null primary key,
nombre varchar(45) unique not null
);
```

Insertar datos en la tabla destinos

 ```sql
INSERT INTO regiones
VALUES

( DEFAULT, "America del Sur"),

( DEFAULT, "America Central"),

( DEFAULT, "Caribe y Mexico"),

( DEFAULT, "America del Norte"),

( DEFAULT, "Europa Occidental"),

( DEFAULT, "Europa del Este"),

( DEFAULT, "Asia"),

( DEFAULT, "Oceania")
``` 

Insertar datos en la tabla Destinos

```sql
INSERT INTO destinos

    VALUES

    (1, "Londres (Heathrow)",  9711,5,  1),

    (2, "Amsterdam (Schiphol)", 6231,5, 1),

    (3, "Miami (Wilcox Field)",  6517, 4, 1),

    (4, "Tokio (Narita)", 8704,7,1),

    (5, "Kuala Lumpur (KLIA)",  8570,8, 1),

    (6, "Bangkok (Suvarnabhumi)", 8469,8 ,1),

    (7, "Paris (Charles de Gaulle)",7713,5,1),

    (8, "Cancun (Cancun)",  6494,3, 1 ),

    (9, "Milan (Malpensa)",6756,5,1)
```


Es decir de la tabla DESTINOS, vamos a relacionarnos con la tabla regiones, mediante la Foreign Key "idRegion" hacia la primary key "idRegion".

La sintaxis quedaria

**foreign key (idRegion) references regiones(idRegion),**


Ahora el ejercicio va a ser cambiar las Aerolineas incorrectas, que serian BangKok y Kuala, debido que estan en la region de Oceania y deberian de estar en la Region de Asia.

```sql
UPDATE DESTINOS
    SET idRegion=7
    WHERE idDestino IN (5,6)
```

