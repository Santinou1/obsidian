#### Instruccion Continue

Solo se puede utilizar dentro de un bucle.

Produce que finalice la iteracion actual omitiendo las instrucciones posteriores y continuando el bucle.

##### Ejemplo

**Escribir un programa que imprimi todos los numeros enteros pares menores o igualesal 10.**


```python
i=0

while i<=10:
    i+=1
    if i%2!=0:
        continue
    print(i)
```


##### Ejemplo

**Escribir un programa que imprimi todos los numeros enteros pares menores o igualesal 10. UTILIZANDO FOR**

```python
numeros= [1,2,3,4,5,6,7,8,9,10]

for numero in numeros:
    if numero%2!=0:
        continue
    print(numero)
```
