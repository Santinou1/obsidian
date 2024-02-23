VICTIMA= MAQUINA W7

Un usuario, ingresa a una linea de comandos y escribe "nmap".

Recordar que actualmente estamos en la fase 1 y 2 del pentesting.

* Recoleccion de Informacion.
* Escaneo.

Por eso nmap es una de las mejores herramientas para realizar el escaneo y recolectar informacion.


Ahora, imaginemonos que nosotros somos el hacker y tenemos que auditar una empresa.

Nosotros necesitamos saber cuales son los dispositivos, cuales son los host, cuales son las ip , justamente eso es un escaneo y recoleccion de informacion. (PARA HACER ESTO ES OBLIGATORIAMENTE ESTAR EN LA MISMA RED.)


Ahora como hacemos todo eso que te estoy comentando ?

Simple.

Una vez conectado a la red debemos saber cual es nuestra ip. 
Por eso usamos ifconfig.

```sh
ifconfig || ipconfig
```

Porque necesitamos ese comando?
Para poder visualizar el segmento de la red a la que estamos conectados es decir.
Si nosotros escaneamos y visualizamos que tenemos la IP = 192.168.0.36
Quiere decir el segmento de red donde todos los dispositivos estan conectados es "192.168.0.xxx"

Ahora si, sabiendo eso vamos a utilizar nmap.


# -sP

El comando que vamos a ejecutar es  nmap -sP (Scan Ping)

```sh
nmap -sP 192.168.0.0/24
```

Esa flag lo que hace es realizar un barrido de una red pero siempre realizando pings. 
Ahora , porque se utiliza el segmento de red con un "0" al final y / 24.

El 0 al final representa el inicio , y "/24" es una representacion de las subredes, es decir que /24 dice que los primeros 24 bits de la direccion IP son la parte de la RED, y los ultimos 8 bits son la parte del HOST.

En resumen, esta subred incluirá direcciones IP desde 192.168.0.1 hasta 192.168.0.254.

Al ejecutar ese comando, nos devuelve esta informacion (que seria todos los dispositivos conectados que se le pudieron hacer ping).

```sh
root@kali:/home/santitech# nmap -sP 192.168.0.0/24
Starting Nmap 7.80 ( https://nmap.org ) at 2023-12-22 08:13 -03
Nmap scan report for 192.168.0.1
Host is up (0.0032s latency).
MAC Address: 4A:F7:C0:90:2C:4F (Unknown)
Nmap scan report for 192.168.0.24
Host is up (0.14s latency).
MAC Address: 92:9A:4A:0F:3B:5C (Unknown)
Nmap scan report for 192.168.0.25
Host is up (0.047s latency).
MAC Address: D0:C2:4E:30:2D:00 (Unknown)
Nmap scan report for 192.168.0.45
Host is up (0.00047s latency).
MAC Address: 08:00:27:F1:3F:AC (Oracle VirtualBox virtual NIC)                  
Nmap scan report for 192.168.0.97
Host is up (0.11s latency).
MAC Address: 9A:03:A9:C4:F1:78 (Unknown)      
Nmap scan report for 192.168.0.113
Host is up (0.026s latency).
MAC Address: 00:0C:43:58:A2:FB (Ralink Technology)     
Nmap scan report for 192.168.0.116
Host is up (0.00048s latency).
MAC Address: D0:39:57:92:AF:71 (Unknown)   
Nmap scan report for 192.168.0.193
Host is up (0.0020s latency).
MAC Address: 6C:1C:71:7B:2B:96 (Unknown)
Nmap scan report for 192.168.0.208
Host is up (0.094s latency).
MAC Address: F4:02:23:3D:28:8E (Unknown)
Nmap scan report for 192.168.0.254
Host is up (0.0015s latency).
MAC Address: 00:50:F1:64:CB:63 (Intel)
Nmap scan report for 192.168.0.36
Host is up.

```


Como podemos ver en uno de todos los registros que saco , aparece nuestro Windows 7 que seria

```sh
Nmap scan report for 192.168.0.45
Host is up (0.00047s latency).
MAC Address: 08:00:27:F1:3F:AC (Oracle VirtualBox virtual NIC) 
```

Ese seria la flag -sP


# -sn

Ahora veamos la Flag -sn

```sh
nmap -sn 192.168.0.0/24
```

Que hace exactamente "-sN".
El mismo recorrido de toda la red, pero sin la necesidad de hacer PING.

el output de esa ejecucion es

```sh
root@kali:/home/santitech# nmap -sn 192.168.0.0/24
Starting Nmap 7.80 ( https://nmap.org ) at 2023-12-22 08:30 -03
Stats: 0:00:01 elapsed; 0 hosts completed (0 up), 255 undergoing ARP Ping Scan
ARP Ping Scan Timing: About 97.06% done; ETC: 08:30 (0:00:00 remaining)
Nmap scan report for 192.168.0.1
Host is up (0.0031s latency).
MAC Address: 4A:F7:C0:90:2C:4F (Unknown)
Nmap scan report for 192.168.0.25
Host is up (0.053s latency).
MAC Address: D0:C2:4E:30:2D:00 (Unknown)
Nmap scan report for 192.168.0.113
Host is up (0.088s latency).
MAC Address: 00:0C:43:58:A2:FB (Ralink Technology)
Nmap scan report for 192.168.0.116
Host is up (0.00026s latency).
MAC Address: D0:39:57:92:AF:71 (Unknown)
Nmap scan report for 192.168.0.193
Host is up (0.012s latency).
MAC Address: 6C:1C:71:7B:2B:96 (Unknown)
Nmap scan report for 192.168.0.254
Host is up (0.0036s latency).
MAC Address: 00:50:F1:64:CB:63 (Intel)
Nmap scan report for 192.168.0.36
Host is up.
Nmap done: 256 IP addresses (7 hosts up) scanned in 1.38 seconds

```


Ya sabemos que la maquina virtual tiene de ip la "192.168.0.45".
Ahora lo que necesitamos saber nosotros es la cantidad de puertos que tiene abierto.


# -Pn

la flag -Pn

```sh
nmap -Pn 192.168.0.45
```

Esta flag, de lo que se va a encargar es de analizar los 1024 puertos mas conocidos de una direccion IP en especifico.
En este caso nosotros vamos a usar la ip del Windows 7 para asi poder ver los puertos a los cuales podemos entrar.

```sh
root@kali:/home/santitech# nmap -Pn 192.168.0.45
Starting Nmap 7.80 ( https://nmap.org ) at 2023-12-22 08:37 -03
Nmap scan report for 192.168.0.45
Host is up (0.00069s latency).
Not shown: 991 closed ports
PORT      STATE SERVICE
135/tcp   open  msrpc
139/tcp   open  netbios-ssn
445/tcp   open  microsoft-ds
49152/tcp open  unknown
49153/tcp open  unknown
49154/tcp open  unknown
49155/tcp open  unknown
49157/tcp open  unknown
49158/tcp open  unknown
MAC Address: 08:00:27:F1:3F:AC (Oracle VirtualBox virtual NIC)

Nmap done: 1 IP address (1 host up) scanned in 1.55 seconds


```

**(ULTRA IMPORTANTE, PARA REALIZAR UN -Pn EL FIREWALL TIENE QUE ESTAR DESACTIVADO)**

Ahora ya realizado el escaneo de puertos podemos tener un panorama mas amplio por donde atacar, y nuestro caso va a ser el  445.
Es decir, la puerta de entrada para atacar es el puerto 445.


# -sT

Si nosotros utilizamos la flag "-sT" vamos a analizar con nmap SOLAMENTE los puertos TCP

```sh
nmap -sT 192.168.0.45
```

La salida por consola seria esta

```sh
Starting Nmap 7.80 ( https://nmap.org ) at 2023-12-22 09:10 -03
Nmap scan report for 192.168.0.45
Host is up (0.0038s latency).
Not shown: 991 closed ports
PORT      STATE SERVICE
135/tcp   open  msrpc
139/tcp   open  netbios-ssn
445/tcp   open  microsoft-ds
49152/tcp open  unknown
49153/tcp open  unknown
49154/tcp open  unknown
49155/tcp open  unknown
49157/tcp open  unknown
49158/tcp open  unknown
MAC Address: 08:00:27:F1:3F:AC (Oracle VirtualBox virtual NIC)

Nmap done: 1 IP address (1 host up) scanned in 1.61 seconds

```


# -sU

Si nosotros utilizamos la flag "-sT" vamos a analizar con nmap SOLAMENTE los puertos UCP.

```sh
nmap -sU 192.168.0.45
```

La salida por consola seria esta

```sql
Host is up (0.0013s latency).
Not shown: 994 closed ports
PORT     STATE         SERVICE
137/udp  open          netbios-ns
138/udp  open|filtered netbios-dgm
500/udp  open|filtered isakmp
1900/udp open|filtered upnp
4500/udp open|filtered nat-t-ike
5355/udp open|filtered llmnr
MAC Address: 08:00:27:F1:3F:AC (Oracle VirtualBox virtual NIC)
```


Ahora imaginemos que solamente queremos analizar unos puertos especificos.

Como ya sabemos si nosotros hacemos
```sh
nmap -Pn 192.168.0.45
```
Lo que va a hacer es mostrar los 1024 puertos, pero ahora si nosotros queremos analizar un conjunto de ellos o unos cuantos?

Ahora es donde entra la siguiente bandera.

# -p,puerto1,puerto2,etc

Con esa flag, determinamos cuales son los puertos abiertos, obviamente dandole a entender que puertos analizar.

```sh
nmap -p135,139,445 192.168.0.45
```

El output seria este

```sh
Nmap scan report for 192.168.0.45
Host is up (0.0014s latency).

PORT    STATE SERVICE
135/tcp open  msrpc
139/tcp open  netbios-ssn
445/tcp open  microsoft-ds
MAC Address: 08:00:27:F1:3F:AC (Oracle VirtualBox virtual NIC)

Nmap done: 1 IP address (1 host up) scanned in 1.20 seconds

```

Ahora, que pasa si por ejemplo escribimos un puerto que sabemos que no esta abierto?

Por ejemplo

```sh
nmap -p1024 192.168.0.45
```

Como podemos ver el output dice que esta CLOSED.
Es decir que no se esta utilizando

```sh
root@kali:/home/santitech# nmap -p1024 192.168.0.45
Starting Nmap 7.80 ( https://nmap.org ) at 2023-12-22 09:54 -03
Nmap scan report for 192.168.0.45
Host is up (0.0017s latency).

PORT     STATE  SERVICE
1024/tcp closed kdm
MAC Address: 08:00:27:F1:3F:AC (Oracle VirtualBox virtual NIC)
Nmap done: 1 IP address (1 host up) scanned in 0.16 seconds

```




# -sV

Este comando nos va a servir para sacar la Version del Servicio de cada Puerto.

```sh
nmap -sV 192.168.0.45
```

El output de este comando es

```sh
Host is up (0.00077s latency).
Not shown: 991 closed ports
PORT      STATE SERVICE      VERSION
135/tcp   open  msrpc        Microsoft Windows RPC
139/tcp   open  netbios-ssn  Microsoft Windows netbios-ssn
445/tcp   open  microsoft-ds Microsoft Windows 7 - 10 microsoft-ds (workgroup: WORKGROUP)
49152/tcp open  msrpc        Microsoft Windows RPC
49153/tcp open  msrpc        Microsoft Windows RPC
49154/tcp open  msrpc        Microsoft Windows RPC
49155/tcp open  msrpc        Microsoft Windows RPC
49157/tcp open  msrpc        Microsoft Windows RPC
49158/tcp open  msrpc        Microsoft Windows RPC
MAC Address: 08:00:27:F1:3F:AC (Oracle VirtualBox virtual NIC)
Service Info: Host: WINDOWS-7; OS: Windows; CPE: cpe:/o:microsoft:windows

```

Fijense que se agrego una nueva columna "VERSION".



# -O

Con este comando vamos a poder sacar el Sistema Operativo de la victima.
Es importante que cuando analizamos una IP , sepamos que SO Tiene.
Porque?
Porque sabiendo que s.o utiliza podemos buscar y explotar sus vulnerabilidades.

El comando seria asi

```sh
nmap -O 192.168.0.45
```

El output es el siguiente

```sh
Starting Nmap 7.80 ( https://nmap.org ) at 2023-12-22 10:37 -03
Stats: 0:00:00 elapsed; 0 hosts completed (1 up), 1 undergoing SYN Stealth Scan
SYN Stealth Scan Timing: About 0.90% done
Nmap scan report for 192.168.0.45
Host is up (0.0016s latency).
Not shown: 991 closed ports
PORT      STATE SERVICE
135/tcp   open  msrpc
139/tcp   open  netbios-ssn
445/tcp   open  microsoft-ds
49152/tcp open  unknown
49153/tcp open  unknown
49154/tcp open  unknown
49155/tcp open  unknown
49157/tcp open  unknown
49158/tcp open  unknown
MAC Address: 08:00:27:F1:3F:AC (Oracle VirtualBox virtual NIC)
Device type: general purpose
Running: Microsoft Windows 7|2008|8.1
OS CPE: cpe:/o:microsoft:windows_7::- cpe:/o:microsoft:windows_7::sp1 cpe:/o:microsoft:windows_server_2008::sp1 cpe:/o:microsoft:windows_server_2008:r2 cpe:/o:microsoft:windows_8 cpe:/o:microsoft:windows_8.1
OS details: Microsoft Windows 7 SP0 - SP1, Windows Server 2008 SP1, Windows Server 2008 R2, Windows 8, or Windows 8.1 Update 1
Network Distance: 1 hop

OS detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 2.86 seconds

```

Como podemos ver puede ser  Microsoft Windows 7 | 2008 | 8.1



# -sC

Esta flag lo que va a hacer es  una llamada a una serie de scripts extras, que nos van a sacar mas informacion de la que podriamos sacar con un escaneo normal.

Es decir estamos usando herramientas extras de nmap que no son propias, es decir que no son principales, y las estamos mandando a llamar para realizar el escaneo y sacar informacion extra.

Su ejecucion seria asi

```sh
nmap -sC 192.168.0.45
```

Y su output es

```sh
Starting Nmap 7.80 ( https://nmap.org ) at 2023-12-22 10:40 -03
Stats: 0:00:18 elapsed; 0 hosts completed (1 up), 1 undergoing Script Scan
NSE Timing: About 93.99% done; ETC: 10:41 (0:00:01 remaining)
Stats: 0:00:42 elapsed; 0 hosts completed (1 up), 1 undergoing Script Scan
NSE Timing: About 94.09% done; ETC: 10:41 (0:00:03 remaining)
Nmap scan report for 192.168.0.45
Host is up (0.00086s latency).
Not shown: 991 closed ports
PORT      STATE SERVICE
135/tcp   open  msrpc
139/tcp   open  netbios-ssn
445/tcp   open  microsoft-ds
49152/tcp open  unknown
49153/tcp open  unknown
49154/tcp open  unknown
49155/tcp open  unknown
49157/tcp open  unknown
49158/tcp open  unknown
MAC Address: 08:00:27:F1:3F:AC (Oracle VirtualBox virtual NIC)

Host script results:
|_clock-skew: mean: 55m19s, deviation: 1h43m55s, median: -4m41s
|_nbstat: NetBIOS name: WINDOWS-7, NetBIOS user: <unknown>, NetBIOS MAC: 08:00:27:f1:3f:ac (Oracle VirtualBox virtual NIC)
| smb-os-discovery: 
|   OS: Windows 7 Ultimate 7601 Service Pack 1 (Windows 7 Ultimate 6.1)
|   OS CPE: cpe:/o:microsoft:windows_7::sp1
|   Computer name: Windows-7
|   NetBIOS computer name: WINDOWS-7\x00
|   Workgroup: WORKGROUP\x00
|_  System time: 2023-12-22T10:36:16-03:00
| smb-security-mode: 
|   account_used: guest
|   authentication_level: user
|   challenge_response: supported
|_  message_signing: disabled (dangerous, but default)
| smb2-security-mode: 
|   2.02: 
|_    Message signing enabled but not required
| smb2-time: 
|   date: 2023-12-22T13:36:16
|_  start_date: 2023-12-22T11:00:16

Nmap done: 1 IP address (1 host up) scanned in 100.39 seconds

```

La informacion extra que nos trajo es por ejepmlo
El SO
Hay un servidor SMB
Nos muestra el WorkGroup
etc


# -A = -sV -O -sC

La flag -A es la combinacion de -sV -O -sC.
Quiere decir que nos va a sacar versiones de los servicios, sistemas operativos, y scripts de nmap.
Es muy agresivo y muy llamativo por eso hay que tener cuidado cuando realizamos este tipo de comandos.


La ejecucion seria

```sh
nmap -A 192.168.0.45
```

Y el output es

```sh
root@kali:/home/santitech# nmap -A 192.168.0.45
Starting Nmap 7.80 ( https://nmap.org ) at 2023-12-22 10:46 -03
Stats: 0:00:18 elapsed; 0 hosts completed (1 up), 1 undergoing Service Scan
Service scan Timing: About 33.33% done; ETC: 10:47 (0:00:32 remaining)
Nmap scan report for 192.168.0.45
Host is up (0.0013s latency).
Not shown: 991 closed ports
PORT      STATE SERVICE      VERSION
135/tcp   open  msrpc        Microsoft Windows RPC
139/tcp   open  netbios-ssn  Microsoft Windows netbios-ssn
445/tcp   open  microsoft-ds Windows 7 Ultimate 7601 Service Pack 1 microsoft-ds (workgroup: WORKGROUP)
49152/tcp open  msrpc        Microsoft Windows RPC
49153/tcp open  msrpc        Microsoft Windows RPC
49154/tcp open  msrpc        Microsoft Windows RPC
49155/tcp open  msrpc        Microsoft Windows RPC
49157/tcp open  msrpc        Microsoft Windows RPC
49158/tcp open  msrpc        Microsoft Windows RPC
MAC Address: 08:00:27:F1:3F:AC (Oracle VirtualBox virtual NIC)
Device type: general purpose
Running: Microsoft Windows 7|2008|8.1
OS CPE: cpe:/o:microsoft:windows_7::- cpe:/o:microsoft:windows_7::sp1 cpe:/o:microsoft:windows_server_2008::sp1 cpe:/o:microsoft:windows_server_2008:r2 cpe:/o:microsoft:windows_8 cpe:/o:microsoft:windows_8.1
OS details: Microsoft Windows 7 SP0 - SP1, Windows Server 2008 SP1, Windows Server 2008 R2, Windows 8, or Windows 8.1 Update 1
Network Distance: 1 hop
Service Info: Host: WINDOWS-7; OS: Windows; CPE: cpe:/o:microsoft:windows

Host script results:
|_clock-skew: mean: 55m19s, deviation: 1h43m55s, median: -4m41s
|_nbstat: NetBIOS name: WINDOWS-7, NetBIOS user: <unknown>, NetBIOS MAC: 08:00:27:f1:3f:ac (Oracle VirtualBox virtual NIC)
| smb-os-discovery: 
|   OS: Windows 7 Ultimate 7601 Service Pack 1 (Windows 7 Ultimate 6.1)
|   OS CPE: cpe:/o:microsoft:windows_7::sp1
|   Computer name: Windows-7
|   NetBIOS computer name: WINDOWS-7\x00
|   Workgroup: WORKGROUP\x00
|_  System time: 2023-12-22T10:42:36-03:00
| smb-security-mode: 
|   account_used: <blank>
|   authentication_level: user
|   challenge_response: supported
|_  message_signing: disabled (dangerous, but default)
| smb2-security-mode: 
|   2.02: 
|_    Message signing enabled but not required
| smb2-time: 
|   date: 2023-12-22T13:42:36
|_  start_date: 2023-12-22T11:00:16

TRACEROUTE
HOP RTT     ADDRESS
1   1.28 ms 192.168.0.45

OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 67.49 seconds
```

Vamos a analizar detalladamente la salida de Nmap =

```sh
root@kali:/home/santitech# nmap -A 192.168.0.45
Starting Nmap 7.80 ( https://nmap.org ) at 2023-12-22 10:46 -03
Stats: 0:00:18 elapsed; 0 hosts completed (1 up), 1 undergoing Service Scan
Service scan Timing: About 33.33% done; ETC: 10:47 (0:00:32 remaining)

```

- El usuario está ejecutando el comando `nmap` con la opción `-A` (escaneo agresivo) contra la dirección IP `192.168.0.45`.

```sh
Nmap scan report for 192.168.0.45
Host is up (0.0013s latency).
Not shown: 991 closed ports
```

- Nmap ha identificado un host en la dirección IP `192.168.0.45` con una latencia muy baja de `0.0013s`. El resultado también menciona que hay 991 puertos cerrados que no se muestran en los resultados.

```sh
PORT      STATE SERVICE      VERSION
135/tcp   open  msrpc        Microsoft Windows RPC
139/tcp   open  netbios-ssn  Microsoft Windows netbios-ssn
445/tcp   open  microsoft-ds Windows 7 Ultimate 7601 Service Pack 1 microsoft-ds (workgroup: WORKGROUP)
49152/tcp open  msrpc        Microsoft Windows RPC
49153/tcp open  msrpc        Microsoft Windows RPC
49154/tcp open  msrpc        Microsoft Windows RPC
49155/tcp open  msrpc        Microsoft Windows RPC
49157/tcp open  msrpc        Microsoft Windows RPC
49158/tcp open  msrpc        Microsoft Windows RPC

```

- Nmap ha identificado varios puertos abiertos y los servicios correspondientes en la máquina objetivo. Por ejemplo, el puerto `135` está ejecutando Microsoft Windows RPC, el puerto `139` está ejecutando netbios-ssn y el puerto `445` está ejecutando Microsoft Windows 7 Ultimate con el Service Pack 1 y comparte información a través del protocolo microsoft-ds.

```sh
MAC Address: 08:00:27:F1:3F:AC (Oracle VirtualBox virtual NIC)
Device type: general purpose
Running: Microsoft Windows 7|2008|8.1
OS CPE: cpe:/o:microsoft:windows_7::- cpe:/o:microsoft:windows_7::sp1 cpe:/o:microsoft:windows_server_2008::sp1 cpe:/o:microsoft:windows_server_2008:r2 cpe:/o:microsoft:windows_8 cpe:/o:microsoft:windows_8.1
OS details: Microsoft Windows 7 SP0 - SP1, Windows Server 2008 SP1, Windows Server 2008 R2, Windows 8, or Windows 8.1 Update 1

```

- Nmap ha identificado la dirección MAC de la máquina objetivo como `08:00:27:F1:3F:AC`, indicando que se está utilizando la interfaz de red virtual de Oracle VirtualBox. El tipo de dispositivo se identifica como de propósito general y se ejecuta el sistema operativo Microsoft Windows, con varias versiones especificadas.

```sh
Network Distance: 1 hop
Service Info: Host: WINDOWS-7; OS: Windows; CPE: cpe:/o:microsoft:windows

```

- La distancia de red se determina en 1 salto. La información del servicio indica el nombre del host como `WINDOWS-7`, el sistema operativo como Windows y la Notación Común de Plataforma (CPE) como `cpe:/o:microsoft:windows`.

```sh
Host script results:
|_clock-skew: mean: 55m19s, deviation: 1h43m55s, median: -4m41s
|_nbstat: NetBIOS name: WINDOWS-7, NetBIOS user: <unknown>, NetBIOS MAC: 08:00:27:f1:3f:ac (Oracle VirtualBox virtual NIC)
| smb-os-discovery: 
|   OS: Windows 7 Ultimate 7601 Service Pack 1 (Windows 7 Ultimate 6.1)
|   OS CPE: cpe:/o:microsoft:windows_7::sp1
|   Computer name: Windows-7
|   NetBIOS computer name: WINDOWS-7\x00
|   Workgroup: WORKGROUP\x00
|_  System time: 2023-12-22T10:42:36-03:00

```

- Los resultados de los scripts incluyen información sobre la desviación del reloj, detalles de NetBIOS y descubrimiento de OS mediante SMB (Server Message Block). Revela que la máquina objetivo está ejecutando Windows 7 Ultimate con el Service Pack 1, tiene el nombre de computadora `Windows-7`, pertenece al grupo de trabajo `WORKGROUP` y muestra la hora del sistema.

```sh
| smb-security-mode: 
|   account_used: <blank>
|   authentication_level: user
|   challenge_response: supported
|_  message_signing: disabled (dangerous, but default)
| smb2-security-mode: 
|   2.02: 
|_    Message signing enabled but not required
| smb2-time: 
|   date: 2023-12-22T13:42:36
|_  start_date: 2023-12-22T11:00:16

```

- Se proporcionan detalles sobre el modo de seguridad SMB (Server Message Block), indicando que la cuenta utilizada está en blanco, el nivel de autenticación es de usuario, la respuesta al desafío está soportada y la firma de mensajes está desactivada (peligroso, pero predeterminado). También se presenta información sobre el modo de seguridad SMB2, indicando que la firma de mensajes está habilitada pero no es obligatoria. También se incluyen detalles sobre el tiempo SMB2.


```sh
TRACEROUTE
HOP RTT     ADDRESS
1   1.28 ms 192.168.0.45

```

- Un traceroute indica que la máquina objetivo está a un salto de distancia con un tiempo de ida y vuelta (RTT) de 1.28 milisegundos.

```sh
OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 67.49 seconds

```

- Las líneas finales resumen el escaneo de Nmap, indicando que se realizaron la detección de sistema operativo y servicios, y que el escaneo completo de 1 dirección IP con 1 host activo tomó 67.49 segundos.

En resumen, el escaneo de Nmap proporciona información detallada sobre los puertos abiertos, servicios, sistema operativo, detalles de red y varios resultados de scripts relacionados con la seguridad y configuración del objetivo.

# -f

La flag -f se utiliza para FRAGMENTAR la informacion