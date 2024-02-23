# 1

Escribir un programa que tenga una lista de numeros enteros e imprima los numeros enteros impares de esa listas hasta encontrar el numero 0.

```python
numeros = [1,2,3,4,5,0,6,7,8,9,10]
  
for numero in numeros:
     if numero%2!=0:
        print(numero)
     if numero==0:
        break
```

# 2

  
 Escribir un programa que tenga una lista vacia y la vaya llenando con nombres de personas.
 El programa debe tener un menu:

 1- Agregar
 2- Listar.
 3- Salir.

 La opcion de agregar inserta a una persona.
 La opcion de listar imprime el contenido de una lista.

```python
personas= []
dato= 0

while True:
    print("Menu")
    print("1-Agregar")
    print("2-Listar")
    print("3-Salir")
    dato= int(input("Elegi una opcion... "))
    if dato==1:
        persona=input("Que nombre desea agregar... ")
        personas.append(persona)
        print("Nombre agregado correctamente.")
    elif dato==2:
        print(personas)
    elif dato==3:
        break
    else:
        print("No ingresaste una opcion correcta, volve a intentarlo.")
```


# 3

Escribir un programa que tenga la siguiente matriz.

```python
matriz=[[3.3,6.1,4.0],
		[4.9,5.7,6.4]]
```

Permita ingresar un numero de fila y un numero de columna e imprima el numero en esa posicion, validando que los numeros de la fila y columna ingresados sean validos.

Por ejemplo

Fila: 1
Columna: 2
6.1


```python
matriz=[[3.3,6.1,4.0],
        [4.9,5.7,6.4]]

  
fila = int(input("Ingrese el número de fila (entre 0 y {}): ".format(len(matriz) - 1)))
columna = int(input("Ingrese el número de columna (entre 0 y {}): ".format(len(matriz[0]) - 1)))
  
if 0 <= fila < len(matriz) and 0 <= columna < len(matriz[0]):
    valor = matriz[fila][columna]
    print(f"El valor en la posición ({fila}, {columna}) es: {valor}")
else:
    print("Posición inválida. Por favor, ingrese números de fila y columna válidos.")
```
