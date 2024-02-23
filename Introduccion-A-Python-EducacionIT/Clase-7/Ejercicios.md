
# 1

Escribir un programa que tenga una lista de nombres, permita ingresar un nombre e imprima un mensaje indicando si el nombre ingresado se encuentra en la lista.

```python
nombres=["Santino","Paula","Fabian"]
newName=str(input("Decime un nombre... "))
  

if newName in nombres:
    print("Ese nombre ya esta en la lista prueba con otro")

else:
    nombres.append(newName)
    print("Nombre agregado con exito! la lista actualizada es {}".format(nombres))
```

# 2

Escribir un programa que tenga un diccionario de vendedores, permita ingresar un nombre e imprima un mensaje indicando si el nombre ingresado se encuentra en el diccionario.

```python
vendedores={1:"Luis",2:"Monica",3:"Juan",4:"Agustin",5:"Luis"}
newName=str(input("Decime un nombre... "))
nombresDeLosVendedores=[]

for keys in vendedores:
    nombresDeLosVendedores.append(vendedores[keys])  

if newName in nombresDeLosVendedores:
    print("Ese nombre esta en la lista.")
else:
    print("El nombre ingresado no se encuentra en la lista, recuerda que los vendedores que estan en el sistema son: {}".format(nombresDeLosVendedores))
```


# 3

Escribir un programa que permita ingresar 2 numeros y escriba la suma utilizando una funcion.

```python
a=int(input("Decime el primer valor..."))
b=int(input("Decime el segundo valor..."))

def suma(a,b):
    print(a+b)
suma(a,b)
```

# 4

Escribir un programa que permita ingresar 2 numeros y escriba la resta utilizando una funcion.

```python
a=int(input("Decime el primer valor..."))
b=int(input("Decime el segundo valor..."))

def resta(a,b):
    print(a-b)
resta(a,b)
```

# 5

Utilizando la funcion sumar escribir un programa que permita ingresar tres numeros e imprima si la suma de los dos primeros es mayor que al tercero.

```python
def sumar(n1,n2):
    return n1+n2

a=int(input("Decime el primer valor..."))
b=int(input("Decime el segundo valor..."))
c=int(input("Decime el tercer valor..."))

  

if sumar(a,b)>c:
    print("es mayor")
else:
    print("es menor")
```

# 6

Modificar el programa del ejercicio anterior para validar que se ingresen numeros enteros, en caso contrario volver a pedirlos.

```python
def sumarV2(n1,n2):
    return n1+n2

  

a=input("Decime el primer valor...")
while not a.isdecimal():
    print("Error , ingresa un numero entero")
    a=input("Decime el primer valor...")


b=input("Decime el segundo valor...")
while not b.isdecimal():
    print("Error , ingresa un numero entero")
    b=input("Decime el segundo valor...")

c=input("Decime el tercer valor...")
while not c.isdecimal():
    print("Error , ingresa un numero entero")
    c=input("Decime el segundo valor...")


if sumarV2(a,b)>c:
    print("es mayor")
else:
    print("es menor")
```

# 7

Optimiza el codigo nuevamente para no repetir tantos "while not"

```python
def validar(x):
    while not x.isdecimal():
        print("Error , ingresa un numero entero")
        x = input("Decime el primer valor...")


def sumarV2(n1, n2):
    return n1 + n2
  
a = input("Decime el primer valor...")
validar(a)
  
b = input("Decime el segundo valor...")
validar(b)

c = input("Decime el tercer valor...")
validar(c)
  
if sumarV2(a, b) > c:
    print("es mayor")
else:
    print("es menor")
```


# 8

Escribir un programa que permita ingresar un precio e imprima si correpsonde un descuento (cuando el precio con IVA es mayor a $1500) utiilzando una funcion.

```python
  
def aplicarIva(precio):
    return precio*1.21


precio=int(input("Ingrese el precio"))
if aplicarIva(precio)>1500:
    print("Corresponde al descuento")

else:
    print("No corrsponde al descuento")
```

