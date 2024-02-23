Solo se produce dentro de un bucle.

Produce que finalice el bucle.

#### Ejemplo

Escribir un programa que imprimi los numeros enteros impares menores o iguales al 5.

```python
while i<=10:

    i+=1
    if i%2!=0:
        print(i)
    if i==5:
        break
```


Escribir un programa que imprimi los numeros enteros impares menores o iguales al 5. USANDO FOR

```python
numeros= [1,2,3,4,5,6,7,8,9,10]
  
for numero in numeros:
    if numero%2!=0:
        print(numero)
    if i==5:
        break
```
