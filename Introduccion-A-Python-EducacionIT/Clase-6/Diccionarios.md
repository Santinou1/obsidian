Al igual que las listas son colecciones de objetos, PERO a diferencia de estas, sus elementos no estan ordenados por un indice , si no que estan referenciadas por una llave y valor.

Entonces decimos que los elementos de un diccionario son pares de clave-valor.

```python
usuario={"edad":19,"nick":"santino"}
```

Los valores de un diccionario pueden ser de cualquier tipo de dato, incluidos otros diccionarios y listas.
Las claves, en cambio, tienen ciertas restricciones: No pueden repetirse y generalmente, son cadenas o bien números enteros.

Al añadir un valor al diccionario, hay que especificar el valor de clave unica con la que luego se podra acceder a el (pues la posicion ya no es un determinante.)


#### Como accedemos a los valores?

Al no tener un indice, no se accede con el indice perse, se va a acceder y a referir con la clave. 
Por ejemplo

```python
usuario["edad"] #19
usuario["nick"] #santino
```


Ademas de acceder a los elementos del diccionario podemos realizar otras operaciones.

**Obtener la longitud de un Diccionario**

```python
len(usuario) #2
```

**Agregar un elemento al Diccionario**

```python
usuario["altura"]=180
```

**Modificar un elemento del Diccionario**

```python
usuario["edad"]=20
```

**Eliminar un elemento del Diccionario**

```python
del usuario["edad"]
```

**Recorrer los elementos del Diccionario**

El bucle for sobre un diccionario permite acceder a cada una de las claves.

```python
usuarios={"name1":"Santi","name2":"Santino","name3":"Santitiino"}
for keys in usuarios:
	print(keys)

# name1
# name2
# name3
```

Ahora si por ejemplo en vez de las clave quisieramos el nombre seria

```python
usuarios={"name1":"Santi","name2":"Santino","name3":"Santitiino"}
for keys in usuarios:
	print(usuarios[keys])

# Santi
# Santino
# Santitiino
```

Y si quisieramos imprimir la clave y valor seria 

```python
usuarios={"name1":"Santi","name2":"Santino","name3":"Santitiino"}
for keys in usuarios:
	print(keys,usuarios[keys])

# name1 Santi
# name2 Santino
# name3 Santitiino
```

Otro uso frecuente de los diccionarios es para SIMULAR un tipo de datos.

 Por ejemplo podemos tener un cliente

```python
cliente=[100,"Santino","Ursino","9 De Julio",[2226999,2226999],350]
```

Ahora supongamos que queremos imprimir el apellido

```python
cliente[2]
```

Ahora quiero imprimir el ultimo de los telefonos del cliente

```python
cliente[4][1]
```

Se complica identificar elementos del cliente si usamos matriz, asi que vamos a utilizar a un diccionario para crear un cliente.

```python
newCliente= {"id":100,
             "nombre":"Santino",
             "apellido":"Ursino",
             "domicilio":"9 De Julio",
             "telefonos":[22226999,22269999],
             "sueldo":350
             }
```

Ahora por ejemplo si queremos obtener cualquier tipo de dato es mas facil.

```python
newCliente["nombre"]
newCliente["sueldo"]
newCliente["telefonos"][1]
```