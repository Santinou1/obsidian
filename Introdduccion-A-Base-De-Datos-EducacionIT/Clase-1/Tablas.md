
En esta Tabla como podemos observas tenemos 4 columnas y 4 registros.

Columna 1 / Campo 1 = Codigo
Columna 2 / Campo 2 = Nombre
Columna 3 / Campo 3 = Precio
Columna 4 / Campo 4= Stock

Y tenemos 4 registros, que los registros son las FILAS.

Registro 1 / Fila 1= 1 | iPod | 299 | 200
Registro 2 / Fila 2= 2 | Iphone | 399 | 300
Registro 3 / Fila 3= 3 | Ipad | 499 | 250
Registro 4 / Fila 4= 4 | Macbook Pro | 1199 | 150


![[Pasted image 20231219144931.png]]


Una analogia de bases de datos podria ser que...

Vos tenes un registro de ventas en tu local , y registras todo en un cuaderno fisico.
El cuaderno fisico se contempla de columnas y filas.
Columnas que podrian ser el nombre del producto que se vendio y el precio.
Y las filas que serian cada registro de cada producto vendido.

Una vez se llena ese cuaderno, lo almacenamos en una carpeta que almacenaria los cuadernos que a su vez serian las TABLAS.

Una vez que llenas las carpetas, las tenes que guardar en un mueble con otras Carpetas.
Y ahora es donde introducimos las TABLAS RELACIONADAS / TABLAS RELACIONALES.

Por ejemplo, imaginemos que una empresa tiene Tablas de productos y empleados.

Nosotros en la tabla de productos, no vamos a almacenar a los empleados no tiene sentido, entonces hacemos una tabla para cada tipo.

Una vez estan guardadas ambas carpetas / tablas en el mismo Mueble.

Ahi como podemos observar tenemos la tabla generada de los Empleados.

![[Pasted image 20231219150415.png]]


En algun momento en la empresa vamos a tener que generar una factura por un producto y tambien va a tener el codigo del cajero que te atendio , eso lo consultariamos en la tabla de empleados.

Para hacer eso vamos a tener que realizar las consultas a las 2 tablas, a la de producto ( para ver que producto compro ) y a la de los empleados (para ver que cajero atendio esa orden).

Es decir vamos a tener que hacer una RELACION entre ambas TABLAS.

