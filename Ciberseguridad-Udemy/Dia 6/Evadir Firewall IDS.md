
Como sabemos, nmap funciona de manera perfecta para escanear redes donde no tienen activado el firewall, o no tienen proteccion IDS.

Ahora, que hacemos cuando si lo tiene?
Bueno en este bloque vamos a aprender a evadir esas medidas de seguridad.

Existe una herramienta que se llama nping que sirve para mandarles paquetes icmp.

```sh
nping -c 3 192.168.0.45
```
output
```sh

Starting Nping 0.7.80 ( https://nmap.org/nping ) at 2023-12-22 12:41 -03
SENT (0.0176s) ICMP [192.168.0.36 > 192.168.0.45 Echo request (type=8/code=0) id=14786 seq=1] IP [ttl=64 id=44531 iplen=28 ]
RCVD (0.0224s) ICMP [192.168.0.45 > 192.168.0.36 Echo reply (type=0/code=0) id=14786 seq=1] IP [ttl=128 id=11414 iplen=28 ]
SENT (1.0228s) ICMP [192.168.0.36 > 192.168.0.45 Echo request (type=8/code=0) id=14786 seq=2] IP [ttl=64 id=44531 iplen=28 ]
RCVD (1.0251s) ICMP [192.168.0.45 > 192.168.0.36 Echo reply (type=0/code=0) id=14786 seq=2] IP [ttl=128 id=11415 iplen=28 ]
SENT (2.0258s) ICMP [192.168.0.36 > 192.168.0.45 Echo request (type=8/code=0) id=14786 seq=3] IP [ttl=64 id=44531 iplen=28 ]
RCVD (2.0281s) ICMP [192.168.0.45 > 192.168.0.36 Echo reply (type=0/code=0) id=14786 seq=3] IP [ttl=128 id=11416 iplen=28 ]
 
Max rtt: 3.117ms | Min rtt: 0.297ms | Avg rtt: 1.638ms
Raw packets sent: 3 (84B) | Rcvd: 3 (138B) | Lost: 0 (0.00%)
Nping done: 1 IP address pinged in 2.03 seconds

```


Ahora, porque no usamos la flag -sn de nmap?
Es decir porque no hacemos esto

```sh
nmap -sn -v 192.168.0.45
```

output

```sh
Starting Nmap 7.80 ( https://nmap.org ) at 2023-12-22 12:42 -03
Initiating ARP Ping Scan at 12:42
Scanning 192.168.0.45 [1 port]
Completed ARP Ping Scan at 12:42, 0.00s elapsed (1 total hosts)
Initiating Parallel DNS resolution of 1 host. at 12:42
Completed Parallel DNS resolution of 1 host. at 12:42, 0.08s elapsed
Nmap scan report for 192.168.0.45
Host is up (0.0015s latency).
MAC Address: 08:00:27:F1:3F:AC (Oracle VirtualBox virtual NIC)
Read data files from: /usr/bin/../share/nmap
Nmap done: 1 IP address (1 host up) scanned in 0.11 seconds
           Raw packets sent: 1 (28B) | Rcvd: 1 (28B)

```

Bueno, no usamos la sentencia de nmap debido que nmap envia trazas arp es decir, envia solicitudes solamente a REDES LOCALES.
En cambio nping no, porque envia trazas ismp.

**ISMP , ARP SON PROTOCOLOS.**


Ahora vamos a escanear una web en donde tienen los puertos filtrados.

```sh
nmap -Pn -n -v nmap.scanme.org
```

output
```sh
Starting Nmap 7.80 ( https://nmap.org ) at 2023-12-22 12:53 -03
Initiating SYN Stealth Scan at 12:53
Scanning nmap.scanme.org (45.33.32.156) [1000 ports]
Discovered open port 22/tcp on 45.33.32.156
Discovered open port 80/tcp on 45.33.32.156
Discovered open port 9929/tcp on 45.33.32.156
Discovered open port 31337/tcp on 45.33.32.156
Completed SYN Stealth Scan at 12:53, 14.46s elapsed (1000 total ports)
Nmap scan report for nmap.scanme.org (45.33.32.156)
Host is up (0.23s latency).
Other addresses for nmap.scanme.org (not scanned): 2600:3c01::f03c:91ff:fe18:bb2f
Not shown: 993 closed ports
PORT      STATE    SERVICE
22/tcp    open     ssh
80/tcp    open     http
135/tcp   filtered msrpc
139/tcp   filtered netbios-ssn
445/tcp   filtered microsoft-ds
9929/tcp  open     nping-echo
31337/tcp open     Elite

Read data files from: /usr/bin/../share/nmap
Nmap done: 1 IP address (1 host up) scanned in 14.93 seconds
           Raw packets sent: 1087 (47.828KB) | Rcvd: 1065 (42.616KB)

```

Como podemos ver tiene los puertos FILTRADOS, es decir que esta bajo proteccion de un firewall.

Aunque intentemos visualizar informacion como la version de los puertos o lo que sea no va a aparecer nada porque estan seguros via firewall.

Como sorteamos el firewall?

Si vamos a la documentacion de nmap nos da algo de informacion.

```sh
nmap -h
```

en todo la informacion da la documentacion, hay una seccion que habla de firewalls.

```sh
FIREWALL/IDS EVASION AND SPOOFING:
  -f; --mtu <val>: fragment packets (optionally w/given MTU)
  -D <decoy1,decoy2[,ME],...>: Cloak a scan with decoys
  -S <IP_Address>: Spoof source address
  -e <iface>: Use specified interface
  -g/--source-port <portnum>: Use given port number
  --proxies <url1,[url2],...>: Relay connections through HTTP/SOCKS4 proxies
  --data <hex string>: Append a custom payload to sent packets
  --data-string <string>: Append a custom ASCII string to sent packets
  --data-length <num>: Append random data to sent packets
  --ip-options <options>: Send packets with specified ip options
  --ttl <val>: Set IP time-to-live field
  --spoof-mac <mac address/prefix/vendor name>: Spoof your MAC address
  --badsum: Send packets with a bogus TCP/UDP/SCTP checksum

```

Asi que teniendo en cuenta eso, la peticion que le vamos a hacer a la pagina con los puertos segurizados con firewall va a ser.

# -f

La flag de -f lo que realiza es que fragmenta los paquetes.
Eso nos sirve porque aveces fragmentando la informacion puede hacer que evada el firewall.

# -sS

La flag de -sS lo que realiza es enviar un paquete TCP SYN.
En donde espera una respuesta ACK en caso de que el puerto este abierto, y si recibe la respuesta RST significa que el puerto esta cerrado
Este escaneo no es tan intrusivo.


```sh
nmap -n -sS -v -f nmap.scanme.org
```

 output

```sh
Starting Nmap 7.80 ( https://nmap.org ) at 2023-12-22 13:07 -03
Initiating Ping Scan at 13:07
Scanning nmap.scanme.org (45.33.32.156) [4 ports]
Completed Ping Scan at 13:07, 0.21s elapsed (1 total hosts)
Initiating SYN Stealth Scan at 13:07
Scanning nmap.scanme.org (45.33.32.156) [1000 ports]
Discovered open port 22/tcp on 45.33.32.156
Discovered open port 80/tcp on 45.33.32.156
Discovered open port 31337/tcp on 45.33.32.156
Discovered open port 9929/tcp on 45.33.32.156
Completed SYN Stealth Scan at 13:08, 11.09s elapsed (1000 total ports)
Nmap scan report for nmap.scanme.org (45.33.32.156)
Host is up (0.21s latency).
Other addresses for nmap.scanme.org (not scanned): 2600:3c01::f03c:91ff:fe18:bb2f
Not shown: 993 closed ports
PORT      STATE    SERVICE
22/tcp    open     ssh
80/tcp    open     http
135/tcp   filtered msrpc
139/tcp   filtered netbios-ssn
445/tcp   filtered microsoft-ds
9929/tcp  open     nping-echo
31337/tcp open     Elite

Read data files from: /usr/bin/../share/nmap
Nmap done: 1 IP address (1 host up) scanned in 11.52 seconds
           Raw packets sent: 1042 (45.824KB) | Rcvd: 1033 (41.324KB)

```

Como podemos ver siguen filtrados los puertos, asi que vamos a probar con otra alternativa.

```sh
nmap -n -Pn -v -sV nmap.scanme.org
```

output

```sh
Starting Nmap 7.80 ( https://nmap.org ) at 2023-12-22 13:09 -03
NSE: Loaded 45 scripts for scanning.
Initiating SYN Stealth Scan at 13:09
Scanning nmap.scanme.org (45.33.32.156) [1000 ports]
Stats: 0:00:00 elapsed; 0 hosts completed (1 up), 1 undergoing SYN Stealth Scan
SYN Stealth Scan Timing: About 0.55% done
Discovered open port 22/tcp on 45.33.32.156
Discovered open port 80/tcp on 45.33.32.156
Discovered open port 31337/tcp on 45.33.32.156
Discovered open port 9929/tcp on 45.33.32.156
Completed SYN Stealth Scan at 13:09, 7.68s elapsed (1000 total ports)
Initiating Service scan at 13:09
Scanning 4 services on nmap.scanme.org (45.33.32.156)
Completed Service scan at 13:09, 6.43s elapsed (4 services on 1 host)
NSE: Script scanning 45.33.32.156.
Initiating NSE at 13:09
Completed NSE at 13:09, 0.93s elapsed
Initiating NSE at 13:09
Completed NSE at 13:09, 0.86s elapsed
Nmap scan report for nmap.scanme.org (45.33.32.156)
Host is up (0.21s latency).
Other addresses for nmap.scanme.org (not scanned): 2600:3c01::f03c:91ff:fe18:bb2f
Not shown: 993 closed ports
PORT      STATE    SERVICE      VERSION
22/tcp    open     ssh          OpenSSH 6.6.1p1 Ubuntu 2ubuntu2.13 (Ubuntu Linux; protocol 2.0)
80/tcp    open     http         Apache httpd 2.4.7 ((Ubuntu))
135/tcp   filtered msrpc
139/tcp   filtered netbios-ssn
445/tcp   filtered microsoft-ds
9929/tcp  open     nping-echo   Nping echo
31337/tcp open     tcpwrapped
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

Read data files from: /usr/bin/../share/nmap
Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 16.81 seconds
           Raw packets sent: 1024 (45.056KB) | Rcvd: 1015 (40.616KB)

```

Como podemos ver, los puertos siguen filtrados.

Asi que vamos a ejecutar otra sentencia.

Ya que sabemos cuales son los puertos que estan filtrados vamos a anotarlos

-135
-139
-445

```sh
nmap -p 135,139,445 -f -sN nmap.scanme.org
```

output

```sh
Starting Nmap 7.80 ( https://nmap.org ) at 2023-12-22 13:12 -03
Nmap scan report for nmap.scanme.org (45.33.32.156)
Host is up (0.20s latency).
Other addresses for nmap.scanme.org (not scanned): 2600:3c01::f03c:91ff:fe18:bb2f
rDNS record for 45.33.32.156: scanme.nmap.org

PORT    STATE         SERVICE
135/tcp open|filtered msrpc
139/tcp open|filtered netbios-ssn
445/tcp open|filtered microsoft-ds

Nmap done: 1 IP address (1 host up) scanned in 3.36 seconds

```

Ahora como podemos visualizar aparece que estan abiertos y ademas nos dicen que servicio estan corriendo en esos puertos.

Eso se debe a la flag -sN

# -sN

La flag -sN lo que hace es que no active ningun flag en la cabecera TCP de los paquetes que estamos enviando.
Al hacer eso contra un firewall (en algunas circunstancias funcionan en otras no), lo podemos evadir.
