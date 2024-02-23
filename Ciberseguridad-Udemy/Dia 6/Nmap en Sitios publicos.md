Como ya vimos anteriormente, usamos NMAP para hacer escaneos de ips locales.
Cuando estabamos en la misma red.
Pero tambien podemos hacer escaneos de ip´s publicas, es decir ip´s de paginas web.

Por ejemplo

Si quisieramos hacer un escaneo a la pagina web "achirou.com" , podriamos hacerlo.

Primero tendriamos que obtener su ip publica que se realiza haciendole un ping.

```sh
ping achirou.com
```

output

```sh
PING achirou.com (89.116.213.103) 56(84) bytes of data.
64 bytes from 89.116.213.103 (89.116.213.103): icmp_seq=1 ttl=48 time=84.5 ms
64 bytes from 89.116.213.103 (89.116.213.103): icmp_seq=2 ttl=48 time=105 ms
64 bytes from 89.116.213.103 (89.116.213.103): icmp_seq=3 ttl=48 time=127 ms
64 bytes from 89.116.213.103 (89.116.213.103): icmp_seq=4 ttl=48 time=147 ms

```

Como podemos ver, ahi obtenemos la ip publica de la web Achirou.com (89.116.213.103).

Ahora podriamos hacerle un escaneo

```sh
nmap 89.116.213.103
```

outpout
```sh
Nmap scan report for 89.116.213.103
Host is up (0.081s latency).
Not shown: 998 filtered ports
PORT    STATE SERVICE
80/tcp  open  http
443/tcp open  https

```


Igualmente cuando hablamos de una pagina web la mejor manera para realizar un escaneo es con las siguientes flags

```sh
nmap -sn --packet-trace --send-ip -v achirou.com
```

output

```sh
root@kali:/home/santitech# nmap -sn --packet-trace --send-ip -v achirou.com
Starting Nmap 7.80 ( https://nmap.org ) at 2023-12-22 12:48 -03
Initiating Ping Scan at 12:48
Scanning achirou.com (149.100.143.86) [4 ports]
SENT (0.3496s) ICMP [192.168.0.36 > 149.100.143.86 Echo request (type=8/code=0) id=16965 seq=0] IP [ttl=41 id=9510 iplen=28 ]
SENT (0.3510s) TCP 192.168.0.36:57517 > 149.100.143.86:443 S ttl=38 id=43242 iplen=44  seq=3978835663 win=1024 <mss 1460>
SENT (0.3518s) TCP 192.168.0.36:57517 > 149.100.143.86:80 A ttl=52 id=49558 iplen=40  seq=0 win=1024 
SENT (0.3525s) ICMP [192.168.0.36 > 149.100.143.86 Timestamp request (type=13/code=0) id=3055 seq=0 orig=0 recv=0 trans=0] IP [ttl=40 id=7017 iplen=40 ]
RCVD (0.4385s) TCP 149.100.143.86:443 > 192.168.0.36:57517 SA ttl=48 id=0 iplen=44  seq=415807744 win=64240 <mss 1460>
Stats: 0:00:00 elapsed; 0 hosts completed (0 up), 1 undergoing Ping Scan
Ping Scan Timing: About 100.00% done; ETC: 12:48 (0:00:00 remaining)
Completed Ping Scan at 12:48, 0.09s elapsed (1 total hosts)
NSOCK INFO [0.4400s] nsock_iod_new2(): nsock_iod_new (IOD #1)
NSOCK INFO [0.4400s] nsock_connect_udp(): UDP connection requested to 181.30.140.132:53 (IOD #1) EID 8
NSOCK INFO [0.4400s] nsock_read(): Read request from IOD #1 [181.30.140.132:53] (timeout: -1ms) EID 18
NSOCK INFO [0.4400s] nsock_iod_new2(): nsock_iod_new (IOD #2)
NSOCK INFO [0.4400s] nsock_connect_udp(): UDP connection requested to 181.30.140.199:53 (IOD #2) EID 24
NSOCK INFO [0.4400s] nsock_read(): Read request from IOD #2 [181.30.140.199:53] (timeout: -1ms) EID 34
Initiating Parallel DNS resolution of 1 host. at 12:48
NSOCK INFO [0.4400s] nsock_write(): Write request for 45 bytes to IOD #1 EID 43 [181.30.140.132:53]
NSOCK INFO [0.4400s] nsock_trace_handler_callback(): Callback: CONNECT SUCCESS for EID 8 [181.30.140.132:53]
NSOCK INFO [0.4400s] nsock_trace_handler_callback(): Callback: WRITE SUCCESS for EID 43 [181.30.140.132:53]
NSOCK INFO [0.4400s] nsock_trace_handler_callback(): Callback: CONNECT SUCCESS for EID 24 [181.30.140.199:53]
NSOCK INFO [0.8460s] nsock_trace_handler_callback(): Callback: READ SUCCESS for EID 18 [181.30.140.132:53] (103 bytes)
NSOCK INFO [0.8460s] nsock_read(): Read request from IOD #1 [181.30.140.132:53] (timeout: -1ms) EID 50
NSOCK INFO [0.8460s] nsock_iod_delete(): nsock_iod_delete (IOD #1)
NSOCK INFO [0.8460s] nevent_delete(): nevent_delete on event #50 (type READ)
NSOCK INFO [0.8460s] nsock_iod_delete(): nsock_iod_delete (IOD #2)
NSOCK INFO [0.8460s] nevent_delete(): nevent_delete on event #34 (type READ)
Completed Parallel DNS resolution of 1 host. at 12:48, 0.41s elapsed
Nmap scan report for achirou.com (149.100.143.86)
Host is up (0.089s latency).
Other addresses for achirou.com (not scanned): 2a02:4780:18:328e:6cd9:f10:1b81:4485
Read data files from: /usr/bin/../share/nmap
Nmap done: 1 IP address (1 host up) scanned in 0.85 seconds
           Raw packets sent: 4 (152B) | Rcvd: 1 (44B)

```

Fijense que nos brinda mucha mas informacion pero lo mas importante es que hace un escaneo a ambos puertos abiertos.

```sh
SENT (0.0074s) TCP 192.168.0.36:64800 > 89.116.213.103:443 S ttl=54 id=29859 iplen=44  seq=2303210335 win=1024 <mss 1460>
SENT (0.0082s) TCP 192.168.0.36:64800 > 89.116.213.103:80 A ttl=55 id=22621 iplen=40  seq=0 win=1024 
```