##### HACER RECONOCIMIENTO DE 2 IP MEDIANTE UN TXT

Para realizar esta practica vamos a necesitar 2 Ips.

Para eso vamos a realizar un escaneo de red

```sh
nmap -sP 192.168.0.0/24
```

Almacenamos las 2 ip en un archivo.

```txt
192.168.0.45
192.168.0.25
```

Ahora, vamos a ver un comando de Nmap que nos permite hacer un escaneo de IP, a partir de un documento de texto.

El comando seria

```sh
nmap -Pn -iL /home/santitech/Escritorio/ip.txt
```

el output de eso seria

```sh
Starting Nmap 7.80 ( https://nmap.org ) at 2023-12-22 10:24 -03
Nmap scan report for 192.168.0.45
Host is up (0.00083s latency).
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
Nmap scan report for 192.168.0.25                                                                                                                                                           
Host is up (0.0060s latency).                         
Not shown: 996 closed ports                                                          
PORT     STATE SERVICE
7000/tcp open  afs3-fileserver
8001/tcp open  vcom-tunnel   
8002/tcp open  teradataordbms       
8080/tcp open  http-proxy    
MAC Address: D0:C2:4E:30:2D:00 (Unknown)

Nmap done: 2 IP addresses (2 hosts up) scanned in 1.76 seconds  
```
