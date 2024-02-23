
# 1
 
 Creacion de tabla productos_apple

![[Pasted image 20231220124510.png]]

```sql
CREATE TABLE productos_apple
(
Codigo smallint unsigned auto_increment not null primary key,
Nombre varchar(255) unique not null,
precio decimal unsigned not null,
stock smallint unsigned not null
);
```

