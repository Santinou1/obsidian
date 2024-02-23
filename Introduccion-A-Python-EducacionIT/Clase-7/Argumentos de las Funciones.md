
Al definir una Función se pueden especificar uno o mas argumentos que pueden ser utilizados, solamente, dentro del bloque de instrucciones de la función.

Al ser invocada la ejecución de la función se deberá especificar un valor o expresión para cada argumento de la función.

**def nombre_de_la_funcion(ARGUMENTO):**

```python
def saludo(nombre):
    print("Hola, todo bien {}".format(nombre))

saludo("Santino")
```



Cuando se invoca la ejecucion de una funcion con argumentos se debe proporcionar un valor para cada argumento, lo que puede realizarse en dos formas:

**Por nombre o por posicion**.


```python
a=int(input("Decime el primer valor..."))
b=int(input("Decime el segundo valor..."))
  

def resta(num1,num2):
 print(num1-num2)
 
resta(num1=a,num2=b)

```
