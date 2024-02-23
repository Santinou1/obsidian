**¿Que es un script?**

Es una sucesion de pasos  a traves de las cuales nosotros damos unas instrucciones a traves de un archivo, y a traves de estas instrucciones lo que hacemos es "automatizar" nuestro trabajo

**¿Como visualizar todos los SCRIPTS que tiene nmap?**

Sencillo, nos dirigimos a la carpeta donde estan guardados y hacemos un ls

```sh
cd /usr/share/nmap/script
```

**¿Como guardamos un registro en nmap?**

# -oN

Con esa flag, estamos diciendo que se nos guarden los resultados en ese archivo. 

```sh
nmap -sV 192.168.0.45 -oN resultados.txt
```

output

```sh
/home/santitech/Escritorio/resultados.txt
```

**¿Donde encontrar mas scripts de nmap?**

En su pagina oficial
https://nmap.org/nsedoc/scripts/

# -sC

Lo que hace el -sC es en la categoria "default" es aplicar todos los scripts que estan en la categoria default los va a aplicar en base a los servicios que va a obtener del escaneo.

A que me refiero?
Es decir si encuentra una vulnerabilidad, va a buscar los scripts en la categoria default para explotar la vulnerabilidad.

# -vv

La flag -vv se utiliza para dar informacion mas detallada , con informacion adicional sobre el progreso de explotacion.

**Uso de scripts de la categoria Default**

```sh
nmap -sC 192.168.0.45 -vv
```

output

```sh
Starting Nmap 7.80 ( https://nmap.org ) at 2023-12-22 13:34 -03
NSE: Loaded 121 scripts for scanning.
NSE: Script Pre-scanning.
NSE: Starting runlevel 1 (of 2) scan.
Initiating NSE at 13:34
Completed NSE at 13:34, 0.00s elapsed
NSE: Starting runlevel 2 (of 2) scan.
Initiating NSE at 13:34
Completed NSE at 13:34, 0.00s elapsed
Initiating ARP Ping Scan at 13:34
Scanning 192.168.0.45 [1 port]
Completed ARP Ping Scan at 13:34, 0.02s elapsed (1 total hosts)
Initiating Parallel DNS resolution of 1 host. at 13:34
Completed Parallel DNS resolution of 1 host. at 13:34, 0.14s elapsed
Initiating SYN Stealth Scan at 13:34
Scanning 192.168.0.45 [1000 ports]
Discovered open port 445/tcp on 192.168.0.45
Discovered open port 139/tcp on 192.168.0.45
Discovered open port 135/tcp on 192.168.0.45
Discovered open port 49153/tcp on 192.168.0.45
Discovered open port 49157/tcp on 192.168.0.45
Discovered open port 49155/tcp on 192.168.0.45
Discovered open port 49154/tcp on 192.168.0.45
Discovered open port 49152/tcp on 192.168.0.45
Discovered open port 49158/tcp on 192.168.0.45
Completed SYN Stealth Scan at 13:34, 2.29s elapsed (1000 total ports)
NSE: Script scanning 192.168.0.45.
NSE: Starting runlevel 1 (of 2) scan.
Initiating NSE at 13:34
NSE Timing: About 93.99% done; ETC: 13:35 (0:00:02 remaining)
NSE Timing: About 95.10% done; ETC: 13:35 (0:00:03 remaining)
NSE Timing: About 95.60% done; ETC: 13:36 (0:00:04 remaining)
Completed NSE at 13:36, 98.46s elapsed
NSE: Starting runlevel 2 (of 2) scan.
Initiating NSE at 13:36
Completed NSE at 13:36, 0.01s elapsed
Nmap scan report for 192.168.0.45
Host is up, received arp-response (0.0013s latency).
Scanned at 2023-12-22 13:34:46 -03 for 101s
Not shown: 991 closed ports
Reason: 991 resets
PORT      STATE SERVICE      REASON
135/tcp   open  msrpc        syn-ack ttl 128
139/tcp   open  netbios-ssn  syn-ack ttl 128
445/tcp   open  microsoft-ds syn-ack ttl 128
49152/tcp open  unknown      syn-ack ttl 128
49153/tcp open  unknown      syn-ack ttl 128
49154/tcp open  unknown      syn-ack ttl 128
49155/tcp open  unknown      syn-ack ttl 128
49157/tcp open  unknown      syn-ack ttl 128
49158/tcp open  unknown      syn-ack ttl 128
MAC Address: 08:00:27:F1:3F:AC (Oracle VirtualBox virtual NIC)

Host script results:
|_clock-skew: mean: 55m19s, deviation: 1h43m55s, median: -4m40s
| nbstat: NetBIOS name: WINDOWS-7, NetBIOS user: <unknown>, NetBIOS MAC: 08:00:27:f1:3f:ac (Oracle VirtualBox virtual NIC)
| Names:
|   WINDOWS-7<20>        Flags: <unique><active>
|   WINDOWS-7<00>        Flags: <unique><active>
|   WORKGROUP<00>        Flags: <group><active>
|   WORKGROUP<1e>        Flags: <group><active>
|   WORKGROUP<1d>        Flags: <unique><active>
|   \x01\x02__MSBROWSE__\x02<01>  Flags: <group><active>
| Statistics:
|   08 00 27 f1 3f ac 00 00 00 00 00 00 00 00 00 00 00
|   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
|_  00 00 00 00 00 00 00 00 00 00 00 00 00 00
| p2p-conficker: 
|   Checking for Conficker.C or higher...
|   Check 1 (port 41236/tcp): CLEAN (Couldn't connect)
|   Check 2 (port 54197/tcp): CLEAN (Couldn't connect)
|   Check 3 (port 35338/udp): CLEAN (Timeout)
|   Check 4 (port 13285/udp): CLEAN (Failed to receive data)
|_  0/4 checks are positive: Host is CLEAN or ports are blocked
| smb-os-discovery: 
|   OS: Windows 7 Ultimate 7601 Service Pack 1 (Windows 7 Ultimate 6.1)
|   OS CPE: cpe:/o:microsoft:windows_7::sp1
|   Computer name: Windows-7
|   NetBIOS computer name: WINDOWS-7\x00
|   Workgroup: WORKGROUP\x00
|_  System time: 2023-12-22T13:30:08-03:00
| smb-security-mode: 
|   account_used: <blank>
|   authentication_level: user
|   challenge_response: supported
|_  message_signing: disabled (dangerous, but default)
| smb2-security-mode: 
|   2.02: 
|_    Message signing enabled but not required
| smb2-time: 
|   date: 2023-12-22T16:30:08
|_  start_date: 2023-12-22T11:00:16

NSE: Script Post-scanning.
NSE: Starting runlevel 1 (of 2) scan.
Initiating NSE at 13:36
Completed NSE at 13:36, 0.00s elapsed
NSE: Starting runlevel 2 (of 2) scan.
Initiating NSE at 13:36
Completed NSE at 13:36, 0.00s elapsed
Read data files from: /usr/bin/../share/nmap
Nmap done: 1 IP address (1 host up) scanned in 102.01 seconds

```


Fijense en una sentencia tan simple como la que escribi arriba, fijense TODO la informacion que se obtiene.


Podriamos hacer un ataque de fuerza bruta con nmap.

```sh
nmap --script ftp-brute -p 21 192.168.0.247
```

Para mas informacion acerca el script ftp-brute [https://nmap.org/nsedoc/scripts/ftp-brute.html]

