**Ejercicio 1**
Descubrir si un numero es Par O Impar

```python
num= 10

if num%2==0:
 print("es par")
else:
 print("es impar")
```

  
**Ejercicio 2**
Tomas rindio 3 examenes y obtuvo los siguientes notas
- Nota 1 = 9
- Nota 2 = 6
- Nota 3 = 8
Escibir un programa e imprime el promedio y comenta si aprobo o no (se aprueba con 6 o mas)

```python
nota1=9
nota2=6
nota3=8

resultadoFinal= (nota1+nota2+nota3)/3
if resultadoFinal>=6:
 print("aprobo")
else:
 print("desaprobo")
```

  
**Ejercicio 3**
Un banco tiene la siguiente politica para la otorgacion de prestamos  
- Si el cliente tiene entre 30 y 50 años y gana mas de $1000000 : Otorgado
- Si el cliente tiene entre 30 y 50 años y no gana mas de $1000000 : A Revisar
- Si el cliente no tiene entre 30 y 50 años : Rechazado
Escribe un programa para identificar si el prestamo es otorgado a revisar o rechazado.

```python
edadCliente= 29
sueldoCliente= 100000000

if edadCliente>=30 and edadCliente<=50:
 if sueldoCliente > 1000000:
  print("Prestamo Otorgado")
 else:
  print("Prestamo A Revisar")
else:
 print("Prestamo Rechazado")
```
  
**Ejercicio 4**
Escribe un programa que imprimira el nivel salarial en funcion del sueldo.}
- Si el sueldo es menor a $50000 el nivel es Bajo
- Si el sueldo esta entre $50000 y $100000 el nivel es Medio
- Si el sueldo esta entre $100000 y $200000 el nivel es Bueno
- Si el sueldo es mayor a $200000 el nivel es Excelente


```python
sueldo= 200000

if sueldo<=50000:
 print("Sueldo Bajo")
elif sueldo<=100000 and sueldo>50000:
  print("Sueldo Intermedio")
elif sueldo>100000 and sueldo<=200000:
   print("Sueldo Bueno")
else:
 print("Sueldo Excelente")

```


**Ejercicio 5**

 Realice un programa que le pida al usuario ingresar 2 cadenas de textos y posteriormente a eso que verifique si las 2 variables son iguales

```python
texto1= input("ingrese un texto: ")
texto2= input("ingrese otro texto: ")

if texto1==texto2:
 print("son iguales")
else:
 print("son diferentes")
```


**Ejercicio 6**

Escribir un programa que permita ingresar el nombre de un alumno, y luego chequee que no este vacio.
En caso de estarlo, debe imprimir un mensaje de error; en caso contrario, imprimir un mensaje indicando que se ingreso correctamente.

```python
nombreDelAlumno= input("Ingrese el nombre de un alumno: ")

if bool(nombreDelAlumno):
 print("Se ingreso correctamente")
else:
 print("No puede ingresar un campo vacio")


### Otra solucion.

nombreDelAlumno= input("Ingrese el nombre de un alumno: ")

if nombreDelAlumno=="":
 print("No puede ingresar un campo vacio")
else:
 print("Se ingreso correctamente")


```


**Ejercicio 6**

Escribir un programa que ingrese el siguiente numero ingresado por el usuario.
por ejemplo si el usuario ingreso 1 que aparezca 2 en la consola.

```python
numero= int(input("decime un numero"))

print(numero+1)

```

**Ejercicio 7**

Redondea un numero en caso de que sea igual o menor a 50 con el numero que este, y en el caso que sea mayora a 50 con el numero siguiente

ejemplo
3.49 = 3
3.50=3
3.88=4

```python
numero=input("ingrese un numero ")
print(round(numero))
```

**Ejercicio 8**

Agregarle el cuit al dni

```python
dni= 44264552
cuit= 20
cuit+str(dni)

```