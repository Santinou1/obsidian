### Append

Agrega un elemento al final de la lista.

lista.append(dato)

```python
numeros=[1,2,3,4,5]
numeros.append(6) #[1,2,3,4,5,6]
print(numeros)
```

### Insert

Agrega un elemento  en una posicion especifica de la lista.

lista.insert(posicion,valor)

```python
numeros=[10,20,30,40,50]
numeros.insert(2,100)
print(numeros)

"""
numeros.insert(2,100)

el 2 representa que va a estar en el indice 

numeros=[10,20,30,40,50]

en indices esa lista quedaria numeros=[0,1,2,3,4]
y si agregamos el 100 se agregaria en el indice 2 osea
numeros=[10,20,100,30,40,50]

"""

```

### Cambiar dato de una lista

Para cambiar de nombre un elemnto podemos renombrarlo entrando en su indice.

Por ejemplo

```python
alumnos=["santi","juan","chile"]

#Si quisieramos renombrar a chile seria

alumnos[2]="jorge"
```

### Del
  
Permite eliminar un elemento en una posicion especifica de la lista

del lista[indice]

```python
alumnos=["santi","juan","chile"]

#supongamos que queremos eliminar a santi
del alumnos[0]

print(alumnos)
```

