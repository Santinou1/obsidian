
Los tipos de escaneos son:

* -sT (sondeo TCP connect())
* -sS (sondeo TCP SYN)
* -sN / -sP (sondeo ping)
* -sU (sondeo UDP)

1. **SYN (Synchronize):** Esta bandera se utiliza para iniciar una conexión entre dos dispositivos. Cuando un dispositivo (por ejemplo, un cliente) quiere establecer una conexión TCP con otro dispositivo (por ejemplo, un servidor), envía un paquete TCP con la bandera SYN activada. Este paquete indica que el dispositivo quiere iniciar una conexión y está solicitando que el otro dispositivo responda.
    
2. **ACK (Acknowledgment):** Esta bandera se utiliza para confirmar que se ha recibido un paquete correctamente. Cuando el dispositivo que recibe el paquete SYN acepta la solicitud de conexión, responde con un paquete que tiene las banderas SYN y ACK activadas. Esto indica que ha recibido la solicitud (SYN) y está aceptando la conexión (ACK).

**Escaneo TCP Connect (-sT)**

* Es el escaneo por defecto cuando no se puede utilizar el escaneo SYN.
* De lo mas completos debido que realiza una conexion con sus objetivos.
* Es muy efectiva con la determinacion del estado de los puertos.
* Es muy detectable por IDS o Firewall.
* El Cliente Manda una FLAG SYN hacia el target, y el target le envia la flag SYNC/ACK, y depsues el Cliente le envia un ACK


**Escaneo TCP SYN (-sS)**

* Es el utilizado por Omision y el mas popular.
* Es Rapido.
* Es sigiloso y poco molesto.
* Muestra una clara y fiable diferenciacion entre los estados abiertos, cerrado, y filtrado.
* Conocida como sondeo medio abierto (half-open).
* Requiere privilegio de SuperUsuario.
* El Cliente Manda una FLAG SYN hacia el target, y el target le envia la flag SYNC/ACK, y depsues el Cliente le envia un RST


**Escaneo ping (-sn / -sP)**

* Una forma de detectar host vivos dentro de un segmento de red.
* -sN le dice a Nmap que no escanee ningun puerto, solo descubra hosts activos.
* Hay algunos equipos que no responden a peticiones ICMP.
* Por lo general los equipos microsoft filtran los paquetes ICMP, por lo cual habria que cambiarnos a -Pn


**Escaneo UDP (-sU)**

* Generalmente mas lento y mas dificil que TCP.
* Muchos auditores lo ignoran, pero es importante realizarlo.
* Stateless (sin estado), no realiza el handshake.
* Es muy detectable por IDS o firewall.