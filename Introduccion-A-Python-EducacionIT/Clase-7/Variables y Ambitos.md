
El ambito o el alcance (SCOPE) de una variable es el lugar en donde la variable es visible y reconocida como tal para otras porciones del codigo.

Las variables creadas dentro de una funcion se llaman variables locales y su ambito es la funcion donde fueron creadas; o sea que toda referencia por fuera de la funcion producira error.

```python
def prueba():
	a=1

print(a)

```

Ese codigo va a generara error porque la variable "a" solamente puede ser referenciada dentro de la funcion "prueba".

Incluso dos variables con el mismo nombre pueden coexistir si estan en ambitos diferentes.

```python
def prueba():
	a="ESTOY DENTRO DE LA FUNCION"
	print(a)

a="ESTOY FUERA DE LA FUNCION ESTOY EN GLOBAL SCOPE"

prueba()
print(a)

```