Vamos a crear la tabla de productos.

```sql
CREATE TABLE categorias(
    idCategoria tinyint not null auto_increment unsigned not null primary key,
    catNombre varchar(45) not null unique
)
  
CREATE TABLE marcas (
    idMarca tinyint unsigned auto_increment not null primary key,
    mkNombre varchar(45) unique not null
)

CREATE TABLE productos
(
idProducto mediumint unsigned auto_increment not null primary key,
prdNombre varchar(45) unique not null,
prdPrecio decimal(8,2) not null unsigned,
idMarca tinyint unsigned  not null,
foreign key (idMarca) references marcas(idMarca),
idCategoria tinyint not null unsigned not null,
foreign key (idCategoria) references categorias(idCategoria),
prdDescripcion varchar(1000) not null,
prdImagen varchar(45) not null,
prdActivo boolean not null
);
```


Ahora vamos a insertarle datos.

Primero vamos a realizar las categorias.

```sql
INSERT INTO `categorias`
	(`idCategoria`, `catNombre`)
    VALUES
    (1,"Smartphone"),
    (2,"Camaras Mirorless"),
    (3, "Lentes"),
    (4, "Parlantes Bluetooth"),
    (5, "Smart TV"),
    (6, "Consolas"),
    (7, "Tablets");
```


Ahora, vamos a hacer las marcas.

```sql
INSERT INTO `marcas`
	(`idMarca`,`mkNombre`)
		VALUES
        (1,"Nikon"),
        (2,"Apple"),
        (3,"Audiostechnica"),
        (4,"Marshall"),
        (5,"Samsung"),
        (6,"Huawei");
```


Y por ultimo los productos.

```sql
INSERT INTO productos
    (prdNombre, prdPrecio, idMarca, idCategoria, prdDescripcion, prdImagen, prdActivo)
VALUES
    ('Galaxy S21', 899.99, 5, 1, 'Potente smartphone de Samsung', 'galaxy_s21.jpg', 1),
    ('Nikon Z6', 1799.99, 1, 2, 'Cámara mirrorless profesional', 'nikon_z6.jpg', 1),
    ('AT-LP120XUSB', 199.99, 3, 3, 'Lente de alta calidad de Audiotechnica', 'at_lp120xusb.jpg', 1),
    ('Marshall Kilburn II', 249.99, 4, 4, 'Parlante Bluetooth con un sonido potente', 'marshall_kilburn_ii.jpg', 1),
    ('Samsung QLED Q90T', 1499.99, 5, 5, 'Smart TV con tecnología QLED', 'samsung_qled_q90t.jpg', 1),
    ('Huawei MateStation X', 599.99, 6, 6, 'Consola de juegos potente de Huawei', 'huawei_matestation_x.jpg', 1);

```


------------------------------------------------------------------------------------------

