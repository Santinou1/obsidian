
**expr [not] in coleccion**

Devuelve verdadero si la expresion pertenece a la coleccion.

Para el caso de las tuplas y listas se utiliza el valor; en cambio para los diccionarios se utiliza la clave

###### Ejemplos

```python
diccionario= {"name":"santi",
              "edad":19,
              }

numeros= [1,2,3,4,5]

print("name" in diccionario) # True
print(5 in numeros) # True
print(6 in numeros) # False
```

