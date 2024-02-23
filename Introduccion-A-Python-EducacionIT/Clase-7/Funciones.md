
**def funcion ([arg1,arg2,...]):
	bloque instr**

Permite darle un nombre a un bloque de instrucciones.

Cuando se invoca la función se ejecutan las instrucciones del bloque.

Su objetivo principal es evitar la repetición de codigo haciendo que los programas sean mas claros, legibles y faciles de mantener.

Para invocar la ejecucion de una funcion:

funcion([expr1,expr2,...])

***

Nostros por ejemplo en este bloque de codigo estamos saludando al usuario al inicio del programa y al final del programa

```python
print("Hola Mundo")
print("Desde Python")
  

a=5
b=9
c=a*b
print(c)


print("Hola Mundo")
print("Desde Python")
```

Como podemos ver hay una parte en el codigo que se repite. 
Vamos a optimizar ese codigo usando funciones para que quede mucho mas legible.


```python
#Declaracion de la funcion

def imprimirSaludo():
    print("Hola Mundo")
    print("Desde Python")

#Invocacion de la Funcion para saludar
imprimirSaludo()

#Logica x
a=5
b=9
c=a*b
print(c)

#Invocacion nuevamente de la funcion para saludar.
imprimirSaludo()
```

