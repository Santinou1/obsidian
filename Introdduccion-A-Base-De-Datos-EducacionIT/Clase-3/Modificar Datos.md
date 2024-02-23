
Lo que vamos a ver ahora es como modificar los datos de una Tabla.

Para modificar los datos de una tabla utilizamos el comando **UPDATE**

##### Sintaxis.

```sql
UPDATE nombreTable
	SET nombreColumna = Valor
	WHERE colId= valorId

```

##### Ejemplo Practico

```sql
UPDATE personas
    SET apellido= "Ursino",
        nombre= "Mauricio",
        dni= 38859910,
        alta= "2023-12-21"
    WHERE id=3
```

Cabe destacar que si queremos solamente modificar un  elemento se podria hacer


