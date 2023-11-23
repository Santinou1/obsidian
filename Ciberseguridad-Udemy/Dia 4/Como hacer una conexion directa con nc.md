Una Conexion Directa es cuando el atacante se conecta a la victima.

Nuestro Kali Linux es nuestro S.O como hacker, la maquina del atacante.

El Windows 7 Es la victima de la victima.

Entonces lo que vamos a hacer es una conexion directa que seria que con nuestro Kali nos conectamos al W7.

Ahora lo que vamos a hacer desde w7 es poner el comando

```sh
#nc -lvvp "puerto"
nc -lvvp 4447

# lo que hace la flag lvvp es poner netcat en escucha en el puerto 4447
```

![[Pasted image 20231123105506.png]]
`Tambien utilice ipconfig para poder saber mi ip para conectarme desde mi kali linux`
Ahi abrimos el puerto 4447 y es la puerta para que el atacante pueda entrar.

Ahora desde Kali linux lo que vamos a hacer es conectarnos mediante netcat.


```sh
#nc ip-victima
nc 192.168.0.45 4447
```

Una vez ejecutemos ese comando va a parecer que no paso nada pero si vamos a la maquina de la victima y hacemos una captura de lo que esta pasando es que tenemos un dispositivo conectado en nuestra maquina.

![[Pasted image 20231123105748.png]]
