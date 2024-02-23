
##### Las consultas se dividen en.

######              Consultas en SQL

######              Consultas a Server

######              Consultas a Tablas


Las que ya conocemos son.

-- Listar base de datos.

```sql
SHOW databases;
```

-- Listas tablas dentro de la DB Seleccionada.

```sql
SHOW tables;
```

-- Mostrar la estructura de una tabla.

```sql
DESCRIBE *nombre de la tabla*
```

-- La palabra reservada mas Importante o la mas usada es **SELECT**

-- Mostrar la DB Activa

```sql
SELECT database()
```

-- Para realizar consultas a una TABLA utilizamos la palabra reservada SELECT acompañada de la palabra reservada FROM.
-- La palabra FROM es para especificar de que tabla estamos hablando.

```sql
SELECT * FROM *nombre de la tabla*
```

-- Si queremos traer los datos de algunas columnas de una tabla tenemos que mencionar los nombres de las columnas separadas por ",".

Por ejemplo

```sql
SELECT nomColumna1,NomColumna3 FROM nombreDeTabla
```

Ejemplo practico.

```sql
SELECT precio,aeropuerto FROM destinos
```


Es importante aclarar que el orden va a depender de que nombreDeColumna ponemos primero.


