###### range([expr_i,]expr_f[expr_incr])

Devuelve una secuencia de numeros enteros desde un valor inicial (Default 0) hasta un valor final -1 con un incremento (default 1).

Uno de sus principales usos es junto a la instruccion for, para definir un bucle sobre el que se itera un numero determinado de veces.

###### Ejemplo

Escribir un programa que imprima los numeros enteros del 1 al 5 utilizando un bucle While.


```python
i=1
while 1<6:
    print(i)
    i+=1
```

Modificar el programa anterior para que imprima los numeros enteros del 1 al 50.


```python
i=1
while 1<51:
    print(i)
    i+=1
```

Ahora hacelo con un for.

```python
for i in [1,2,3,4,5]:
    print(i)
```

Ahora del 1 al 50 con for , se complica no? Bueno, ahora usamos el for range.

```python
for i in range(1,51):
    print(i)
```