#### El **Modelo OSI** consta de 7 capas.

Se lee de la **capa superior hacia la inferior** cuando el mensaje va a salir.
Y de la **capa inferior a la superior** cuando el mensaje llega.

#### Capa 7 (Aplicacion)

Es la capa que todo el mundo ve, por ejemplo puede llegar a ser Youtube, Whatsapp.
Es la aplicacion/programa que realiza la comunicacion a las otras capas.
Por ejemplo cuando envias un mensaje por whatsapp usted esta interactuando con la capa aplicacion.

**Las vulnerabilidades en esta capa incluyen**:

- **Inyección de código**: Un atacante puede inyectar código malicioso en aplicaciones web o sistemas, lo que puede resultar en la ejecución de acciones no autorizadas o la exposición de datos sensibles.

- **Ataques de phishing**: Un atacante puede engañar a los usuarios para que revelen sus credenciales de acceso o información personal mediante el uso de sitios web o correos electrónicos falsificados.

- **Vulnerabilidades en el software**: Las aplicaciones y sistemas pueden tener vulnerabilidades de seguridad no parcheadas que pueden ser explotadas por un atacante para comprometer la seguridad de la red.

![[Pasted image 20231120112210.png]]

#### Capa 6 (Presentacion)

Esta capa se encarga de traducir el formato al que usted esta solicitando, si usted desea descargar un archivo/una foto/un video.

Esas extensiones del archivo es manejado por la capa de presentacion, la cual se le mostrara a usted en esta capa.


**Las vulnerabilidades en esta capa incluyen**:

- **Ataques de criptoanálisis**: Un atacante puede intentar descifrar datos cifrados mediante técnicas de criptoanálisis, lo que podría permitir el acceso no autorizado a la información.

- **Ataques de manipulación de datos**: Un atacante puede alterar los datos durante su transmisión, lo que puede resultar en la corrupción de datos o la ejecución de acciones no autorizadas.

![[Pasted image 20231120112401.png]]

#### Capa 5 (Sesion)

Esta Capa es la que maneja la Comunicacion / conversacion entre su dispositivo y el dispositivo remoto.

Tambien facilita los mecanismos de gestion de sesion entre la comunicacion de capas superiores.

Es decir cuando usted solicita un archivo que se encuentra en otro equipo , la capa 5 es la que abre esta comunicacion.

**La seguridad es lo que caracteriza a la capa de sesion, ya que dentro de sus capacidades es la de gestionar la autenticacion y autorizacion del envio o recepcion de informacion a traves de metodos criptograficos**

**Las vulnerabilidades en esta capa incluyen**:

- **Secuestro de sesión**: Un atacante puede robar tokens de sesión o cookies para hacerse pasar por un usuario legítimo y acceder a recursos protegidos.
-
- **Fugas de información**: La información sensible almacenada en variables de sesión puede ser expuesta a través de errores de programación o ataques dirigidos.

![[Pasted image 20231120112623.png]]

#### Capa 4 (Transporte)

La funcionalidad de esta Capa es un sistema para enviar información sin errores a las capas superiores.

Esta Capa tiene 2 elementos principales.

En primer lugar esta Capa es la que segmenta los datos, por ejemplo si descargas una cancion que tiene de peso 30MB esta capa divide estos 30MB en pequeños trozos (paquetes).
Le pone la etiqueta TCP O UDP .
Que TCP es la que permite que cuando se pierda un paquete la capa transporte lo detecte y solicite el reenvio de ese paquete.
En cambio la UDP no, la UDP es por ejemplo cuando estas viendo un vivo en twitch no hay una solicitud para reconstruir el paquete perdido, el paquete ya se perdio.

**La seguridad en esta capa se aplica desde:**
- **El cifrado de los datos**
- **Autenticación de todas las partes**
- **Prevenir la manipulación que atente contra la integridad de los datos**
- **Evasión de ataques de reinyección**

**Las vulnerabilidades en esta capa incluyen**:

- **Ataques de secuestro de sesión**: Un atacante puede interceptar y manipular la comunicación entre dos partes, lo que le permite controlar la sesión y ejecutar acciones no autorizadas.

- **Ataques de inyección de paquetes**: Un atacante puede inyectar paquetes maliciosos en una comunicación, lo que puede provocar fallos en las aplicaciones o la ejecución de código malicioso.

- **Ataques de fuerza bruta**: Un atacante puede intentar adivinar claves de cifrado o contraseñas mediante el uso de técnicas de fuerza bruta, lo que puede permitir el acceso no autorizado a la comunicación.

![[Pasted image 20231120113022.png]]

### Capa 3 (Red)

Esta capa es una de la mas importante.

Permite la comunicación entre dispositivos que se encuentren en redes distintas. De esta forma estos dispositivos se pueden comunicar por mas que no haya una comunicación directa.

Esta capa es la de redireccionamiento.

**Como hablamos de Router o servidor las medidas de seguridad son el control no autorizado de ingreso a traves de contaseñas fuertes y la configuracion de protocolos de administracion a traves de conexiones cifradas**

**Las vulnerabilidades en esta capa incluyen**:

- **Ataques de enrutamiento**: Un atacante puede manipular la información de enrutamiento para desviar el tráfico hacia una ubicación controlada por él o para interrumpir el flujo normal de la comunicación.
- **Ataques de denegación de servicio (DoS)**: Un atacante puede inundar una red con paquetes de datos, lo que provoca una sobrecarga en los dispositivos y la interrupción del servicio.
- **Ataques de suplantación de IP**: Un atacante puede falsificar direcciones IP para ocultar su identidad o para acceder a recursos protegidos.



![[Pasted image 20231120113142.png]]

#### Capa 2 (Enlace de datos)

La capa Enlace de datos es la que toma toda la informacion recopilada en las capas superiores y la traduce a informacio Binaria, para a su vez la capa fisica envie esa informacion.

**La inutilizacion logica de los puertos sin utilizar es clave en esta capa , evita la conexiones fraudulentas o Ataques de envenenamiento de ARP**

**El Envenenamiento de ARP es cuando tenes al atacante en el medio entre la informacion, y puede leer todo**

**Las vulnerabilidades en esta capa incluyen**:

- **Ataques de repetición**: Un atacante puede interceptar y retransmitir paquetes de datos, lo que puede provocar una denegación de servicio (DoS) o la ejecución de acciones no autorizadas.

- **Ataques de suplantación de identidad (spoofing):** Un atacante puede falsear direcciones MAC o cambiarlas dinámicamente para acceder a recursos protegidos o evadir controles de acceso.

- **Inundación de tráfico**: Un atacante puede inundar la red con tráfico no deseado, lo que podría provocar una sobrecarga en la red y posibles interrupciones en la comunicación.


![[Pasted image 20231120113307.png]]

### Capa 1 (Fisica)

Esta capa es la encargada de transmitir la informacion inicial, ya sea por medio de cables de cobre, o fibra optica , radiofrecuencia etc.

La informacion se envia en formato BITS  que se traducen en 0 y 1 y puede varias segun que medio se utilice para enviar la informacion.

Por ejemplo los cables de cobre envia su informacion utilizando 0 y 1 , y hace referencia a que si tiene 0 voltios es 0 y si hace una suma o resta de 5v es un 1.

Al igual que la fibra optica, si esta la luz prendida es un 1 y si esta apagada seria un 0

En esta capa encontramos protocolos como el : 
- PPP 
- Frame Relay
- Ethernet

**Desde la perspectiva de Seguridad Informatica aqui se debe impedir el acceso a terceros, es decir a accesos no autorizados.**

**Las vulnerabilidades en esta capa incluyen:**

- **Intercepción de señales**: Las señales inalámbricas pueden ser interceptadas por un atacante, lo que permite el acceso no autorizado a la información transmitida.

- **Daño físico**: El daño físico a los componentes de la red, como cables y dispositivos, puede provocar interrupciones en la comunicación y la pérdida de datos.
	
- **Manipulación de hardware**: Un atacante puede instalar dispositivos de monitoreo o modificar componentes de hardware para comprometer la seguridad de la red.



![[Pasted image 20231120113457.png]]



Como se puede observar las capas  7,6,5 son capas de **aplicacion**, en cambio las capas 4,3,2,1 son capas de **Flujos de Datos**.


