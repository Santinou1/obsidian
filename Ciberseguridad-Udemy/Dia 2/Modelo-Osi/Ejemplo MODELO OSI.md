
La parte izquierda representa el dispositivo de origen, puede ser por ejemplo nuestro dispositivo (Pc, Celular etc.)

Por otro lado la parte derecha representa el dispositivo destino.

Lo demas son routers exceptuando el servidor de arriba a la izquierda.

![[Pasted image 20231120114554.png]]

Ahora si podemos empezar con el ejemplo del grafico de arriba.

Imaginemonos que le mandamos un Whatsapp a un amigo.

Consideremos la transmisión de un mensaje a través de las distintas capas del modelo OSI. En la **Capa 7 (Aplicación)**, donde generamos el mensaje en la plataforma "Wsp" a nuestro amigo, se inicia el proceso. Este contenido se transmite a la **Capa 6 (Presentación)**, encargada de formatear la información en un formato de texto coherente, en este caso un "txt".

La **Capa 6** transfiere el mensaje a la **Capa 5 (Sesión)**, que establece la comunicación con el servidor de WhatsApp. La solicitud de envío al destinatario se envía al servidor, que responde con la autorización correspondiente. A continuación, interviene la **Capa 4 (Transporte)**, encargada de dividir la información para envialasa por partes a la **Capa 3 (Red)**. En esta etapa, la información se etiqueta para convertirla en paquetes, incorporando las direcciones IP de origen y destino.

Los paquetes se transmiten a la **Capa 2 (Enlace de Datos)**, que transforma la información a datos binarios y los transmite a la **Capa 1 (Física)**. Esta última capa se encarga de transmitir los datos en formato binario (1 y 0), ya que es la interpretación que los medios de transporte de datos utilizan.

Una vez transmitida, la información llega al primer router, donde la **Capa Física** recibe el mensaje y lo transmite a la **Capa de Enlace de Datos** para su análisis. Luego, se transforma en datos lógicos y se envía a la **Capa de Red**, que interpreta el mensaje. Al darse cuenta de que el paquete no es para su IP, ya que contiene la dirección IP del destinatario, la capa la vuelve a encapsular. A continuación, la información se devuelve a la **Capa de Enlace de Datos**, que vuelve a convertir el paquete en datos binarios y asigna la dirección MAC del próximo salto antes de enviarlo de nuevo a la **Capa Física** para su transmisión.

Este paquete llega eventualmente al servidor de WhatsApp, donde se determina a qué usuario está destinado. Posteriormente, el ciclo se repite para asegurar la entrega del mensaje al destinatario.

Vuelvo a insertar la imagen del ejemplo.

![[Pasted image 20231120114554.png]]