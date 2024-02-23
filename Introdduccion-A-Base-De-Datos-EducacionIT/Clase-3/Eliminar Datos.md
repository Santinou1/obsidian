###### Eliminacion de datos de una Tabla.

La sintaxis para eliminar un elemento de una tabla se compone con la palabra reservada **DELETE**.

**Sintaxis**

```sql
DELETE FROM nombreDeLaTabla
```

Ejemplo practico

```sql
DELETE FROM personas;
```

Si utilizaríamos esa sintaxis el problema es que eliminaríamos todo el contenido de la tabla, quedaría la tabla vacía. Es decir si tuviésemos 1000 nombres y usamos  **DELETE FROM personas** estaríamos eliminando todo el contenido de la tabla y nos quedariamos sin esos 1000 nombres.

Ahora para evitar eso se utiliza la palabra reservada **WHERE** , para poder buscar el ID especifico de la persona / producto que querramos borrar.

```sql
DELETE FROM personas
		WHERE id=3
```

