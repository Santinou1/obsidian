Recordemos que la direccion IP quiere decir "Internet Protocol" , que es similar al dni, sirve para identificar los dispositivos.

Actualmente existen dos versiones de direcciones IP = **IPv4 y IPv6**

La IPv4 tiene un tamaño de 32 bits y esta expresado en BINARIO.

**Por ejemplo mi IP es = 192.168.0.116
Que expresado en binario seria  = 11000000.10101000.00000000.01110100
Esta compuesto por 4 Octetos. Que seria la reunion de 8 bits.
8 Bits * 4 Octetos = 32 bits.**

La direccion IP se divide en  2 partes.

Red y Host.

En mi caso seria

**RED**
	**192.168**

**HOST**
	**0.116*

Usando una analogia podriamos decir que la red es la calle de mi casa y el host el numero.
![[Pasted image 20231121102157.png]]

¿Como el sistema distingue entre la **red y el host**?

Mediante una **Mascara de Subred**

![[Pasted image 20231121102421.png]]

En resumen, la **Mascara de Subred** actúa como un filtro que separa la parte de la dirección IP que identifica la red de la parte que identifica los dispositivos dentro de esa red. Aquí hay un resumen de sus funciones clave:

1. **División de Redes:** La máscara de subred permite dividir una red IP en subredes más pequeñas. Esto es útil para organizar y segmentar la red de manera eficiente.
    
2. **Identificación de Red y Host:** La dirección IP se compone de dos partes: la parte que identifica la red y la parte que identifica un dispositivo específico en esa red. La máscara de subred define dónde termina la identificación de la red y comienza la identificación del host.
    
3. **Notación en Forma de Prefijo:** La máscara de subred se expresa a menudo en notación de prefijo, como "CIDR" (Classless Inter-Domain Routing), que indica cuántos bits se utilizan para la identificación de la red. Por ejemplo, una máscara de subred en notación CIDR podría ser "/24", lo que significa que los primeros 24 bits de la dirección IP se utilizan para la red y los últimos 8 bits se utilizan para identificar dispositivos en esa red.
    
4. **Control del Tráfico:** La máscara de subred también se utiliza para determinar qué dispositivos están en la misma red local y pueden comunicarse directamente entre sí sin pasar por un enrutador. Esto ayuda a controlar el tráfico en una red.

Una analogia seria

Estamos en una gran ciudad dividida en diferentes barrios, y cada barrio tiene sus propias calles numeradas. La ciudad representa toda la red, y cada barrio es como una subred.

1. **División en Barrios (Subredes):** La ciudad (red) se divide en barrios más pequeños (subredes) para organizarla mejor y facilitar la gestión.
    
2. **Dirección de Calles (Dirección IP):** Cada calle en un barrio tiene su propio número, y ese número es como la dirección IP. Parte del número de la calle identifica el barrio (red), y el resto identifica casas individuales (dispositivos) en esa calle.
    
3. **Máscara de Subred (Límites del Barrio):** La máscara de subred sería como las reglas que indican dónde termina un barrio y comienza otro. Define cuántos números de la calle se utilizan para identificar el barrio y cuántos para identificar las casas.
    
4. **Notación de Prefijo (Indicación de Área):** Podríamos usar una notación especial, digamos "/3", para indicar que los primeros tres dígitos del número de la calle se utilizan para identificar el barrio. Así, "/3" sería como decir que los primeros tres bits de la dirección IP se utilizan para la identificación de la red.
    
5. **Tráfico entre Calles y Barrios (Enrutamiento):** Las personas en la misma calle (misma subred) pueden interactuar directamente, pero si quieren ir a otra calle (otra subred), necesitan seguir las reglas de tráfico (enrutamiento) para llegar allí.
    

En resumen, la ciudad, los barrios, las calles y las casas representan la red, las subredes, las direcciones IP y los dispositivos, respectivamente. La máscara de subred establece límites claros entre los barrios, facilitando la organización y el enrutamiento eficiente en la ciudad (red).