# 1

Escribir un programa que permita ingresar un número entero mayor a 0 e
imprima todos los números enteros desde 1 hasta el número ingresado
inclusive.


```python
numero = int(input("Ingrese un número entero mayor a 0: "))

while numero <= 0:

    print("Por favor, ingrese un número entero mayor a 0.")

    numero = int(input("Ingrese un número entero mayor a 0: "))

actual = 1

while actual <= numero:

    print(actual)

    actual += 1
``` 

# 2

Definir una variable que tenga los puntos cardinales y recorre la lista de indice a fin imprimendo todo el contenido en pantalla.

```python
puntosCardinales= ["n","s","e","o"]

i=0

while (len(puntosCardinales)-1)>=i:
    print(puntosCardinales[i])
    i=i+1
```

# 3

Escribir un programa que tenga la siguiente lista de nombres
nombres = ["Alejandro","Fabio","Roberto"]
insertar entre Alejandro y Fabio a Claudia
al final agregar a cristina
por ultimo recorrer la lista

```python
nombres = ["Alejandro","Fabio","Roberto"]
nombres.insert(1,"Claudia")
nombres.append("Cristina")

i=0

while len(nombres)>i:
    print(nombres[i])
    i=i+1
```

# 4

Escribir un programa que tenga una lista de nombres y recorrerlos con for

```python
nombres=["claudia","marisa","jorge","pinocho"]

for nombre in nombres:
    print(nombre)
```

# 5

Escribir un programa que tenga la siguiente lista de números enteros distintos de 0.
numeros = [1,-3,-4,7,8,2]
Se deben generar dos listas: una para los positivos y otra para los negativos.

```python
numeros = [1,-3,-4,7,8,2]
positivos=[]
negativo=[]

  

for numero in numeros:
    if numero<0:
        positivos.append(numero)
    if numero>0:
        negativo.append(numero)

print("La lista con los numeros positivos son" + positivos)
print("La lista con los numeros negativos son" + negativo)
```
