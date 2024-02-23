Al igual que las listas son colecciones ordenadas de los objetos pero a diferencia de estas, son INMUTABLES.

Es decir, que una vez asignado los elementos, no pueden ser alterados.

Se accede por el indice, al igual que en las listas.

En terminos funcionales, podria decirse que las TUPLAS son un subconjunto de las listas, por cuanto soportan las operaciones con indices para acceeder a sus elementos, pero no asi las de asignacion.

A grandes rasgos podriamos pensar las TUPLAS como una lista CONSTANTE, que no cambia.


##### Ejemplo de Tuplas

```python
# TUPLA DE COLORES RGB
color_rgb = (255, 0, 0)  # Rojo

# TUPLA DE PUNTOS CARDINALES
puntosCardinales= ("Norte","Sur","Este","Oeste")

# TUPLA CON DIFERENTES ELEMENTOS

datos=("Hola Soy un String",1,True,False,[1,2,3],("Otra Tupla"), puntosCardinales)

# Al ser una lista ordenada podemos acceder a cada indice.

puntosCardinales[0] #"Norte"
puntosCardinales[1] #"Sur"
puntosCardinales[2] #"Este"
puntosCardinales[3] #"Oeste"
```


