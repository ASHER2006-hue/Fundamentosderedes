### Glosario
**Capa física**

- Bit:
- Señal:
- Ancho de banda:
- Rendimiento (throughput):
- Latencia:
- Medio de transmisión:

**Cables y medios**

- Par trenzado (UTP / STP):
- Conector RJ-45:
- Cable directo y cable cruzado:
- Fibra óptica:
- Fibra monomodo y multimodo:
- Interferencia electromagnética (EMI):
- Wi-Fi (IEEE 802.11):
- Bandas de 2.4 GHz y 5 GHz:
- Bluetooth:

**Señalización**

- Codificación:
- Señalización:
- Sincronización:
- Código Manchester:

**Ethernet y LAN**

- Ethernet (IEEE 802.3):
- Tarjeta de red (NIC):
- Switch:
- Hub:
- Tabla de direcciones MAC:
- Dúplex (half y full):
- Colisión:

**Direccionamiento**

- Dirección MAC:
- OUI:
- Hexadecimal:
- Unicast:
- Multicast:
- Broadcast:

**Enlace de datos**

- Trama (frame)
- Encabezado y tráiler:
- FCS / CRC:
- Subcapa LLC:
- Subcapa MAC:
- CSMA/CD:
- CSMA/CA:


# Actividad 3.1
Hacer una figura explicando porque los cables van en pares
## conceptos:
1. Capa Fisica y de enlace de datos: 
	- transporta bitscomo señales electricas, luz u ondas de radio.
2. Se compone de 3 elementos:
	- medios fisicos (conectores, cables, dispositivos)
	- codificacion de datos
	- señalización
3. Errores comunes: 
	- Medios fisicos: malas conexiones
	- Señalización: esatica por cables blindados con aluminio y fibra optica.
	- codificación: no son muy comunes.
4.  Como se mide el desempeño? 
	- Ancho de banda
	- Rendimiento
	- Latencia
5. Tipos de cables:
	- Cobre: UTP, envia señales electricas y necesita conectores de tipo R1-45, tiene un alcance de 110 metros maximo.



# Actividad 3.2
### Capa Fisica
Transporta bits como señales electricas, luz y ondas.
se copone de tres elementos: medios fisicos (cables, conectores y dispositivos), la codificacion de datos y la señalizacion que la transmite.
#### Señales de comunicacion
Una señal es una variacion de una propiedad fisica que representa bits: cambios de voltaje en cobre, pulsos de luz en fibra u ondas de radio en el aire.
#### parametros
El rendimiento se mide con tres parametros: el ancho de banda, el rendimiento y la latencia.

#### Señalizacion y codificacion fisica
La codificacion convierte los bits en un patron predefinido que facilita la sincronia y la deteccion de errores; la señalizacion define como se representa ese patron en el medio.

### Ethernet capa 1 y 2

Ethernet (IEEE 802.3) es el estandar dominante en LAN y trabaja en dos capas: la capa 1 define medios y señalizacion, y en la capa 2 define las tramas y las direcciones MAC

### Tipos de cables
#### Tipos de cables: cobre
El cable de par trenzado (UTP) transmite señales electricas con conector RJ-45, alcanza hasta 100 metros y es el mas usado en lan; el trenzado reduce la interferencia.

##### UTP: por que los cables van en pares?
Los 8 hilos del UTP forman 5 pares trenzados. Cada par envia la señal con polaridad opuesta en sus dos hilos; la interferencia afecta a ambos por igual y el receptor la cancela al comparar los dos.

Cada par tiene un trenzado distinto para reducir la diafonia entre pares vecinos.

#### Tipos de cable: fibra optica
La fibra optica transmite pulsos de liz: llega a mayores distancias y es inmune a la interferencia electromagnetica, pero es mas costosa y delicada de instalar.

### por que los puntos de intercambio reducen la latencia?
Porque incrementan la cantidad de saltos que se deben de tomar, por ende reduciendo la eficiencia.

### Medios inalambricos
Transmiten por ondas de radio (wi-fi, bluetooth, celular); dan movilidad, pero el medio es compartido, sufre interferencia y requiere medidas de seguridad.

### ARP: de direcciom ip a doreccion MAC
El protocolo ARP permite descubrir la direccion mac de un dispositivo a partir de su direccion ip. Envia una peticion que solo el dueño puede responder.

# Actividad packet tracer 
## Práctica 3: Tabla de direcciones MAC del switch
**Unidad 3:** Capa física y de enlace de datos
**Herramienta:** Cisco Packet Tracer
**Duración aproximada:** 25 a 30 minutos
## Objetivo

Observar cómo un switch aprende las direcciones MAC de los dispositivos conectados y las asocia con sus puertos.
## Material

- 1 switch 2960
- 4 PCs (PC0 a PC3)
## Desarrollo
### Paso 1. Arma la red

1. Coloca un switch 2960 y 4 PCs (PC0 a PC3).
2. Conecta cada PC al switch con cable directo (*Copper Straight-Through*):

   | PC | Puerto del switch |
   |---|---|
   | PC0 | Fa0/1 |
   | PC1 | Fa0/2 |
   | PC2 | Fa0/3 |
   | PC3 | Fa0/4 |
3. Espera a que los enlaces se pongan en verde.
### Paso 2. Asigna las IPs
En cada PC, entra a **Desktop → IP Configuration** y escribe:
| PC | IP | Máscara |
|---|---|---|
| PC0 | 192.168.1.1 | 255.255.255.0 |
| PC1 | 192.168.1.2 | 255.255.255.0 |
| PC2 | 192.168.1.3 | 255.255.255.0 |
| PC3 | 192.168.1.4 | 255.255.255.0 |

> Las IPs solo sirven para poder hacer ping. Lo que se analiza en esta práctica son las direcciones MAC.
### Paso 3. Anota la MAC de cada PC
1. En cada PC, abre **Desktop → Command Prompt**.
2. Escribe `ipconfig /all`.
3. Copia la **Physical Address** de cada PC en una tabla con estas columnas: PC, puerto del switch y MAC.
### Paso 4. Revisa la tabla del switch antes de enviar tráfico

1. Haz clic en el switch y abre la pestaña **CLI**.
2. Presiona Enter, escribe `enable` y presiona Enter.
3. Escribe:
   ```

   show mac address-table

   ```
   Si el comando no se reconoce, usa `show mac-address-table`.
4. Toma una captura de pantalla. La tabla debería estar vacía o casi vacía, porque el switch todavía no ha visto tramas.
5. ![[Pasted image 20261020204031.png]]
### Paso 5. Genera tráfico entre dos PCs
1. En PC0, abre **Command Prompt** y ejecuta:
   ```

   ping 192.168.1.2

   ```
2. El primer ping puede fallar con "Request timed out". Es normal: PC0 primero necesita conocer la MAC de PC1 mediante ARP.
3. Ejecuta el ping otra vez hasta que responda.
### Paso 6. Revisa la tabla otra vez
1. Regresa al CLI del switch y ejecuta `show mac address-table`.
2. Deben aparecer las MAC de PC0 y PC1, cada una asociada a su puerto (Fa0/1 y Fa0/2), con tipo **DYNAMIC** y VLAN 1.
3. Toma otra captura de pantalla.
4. ![[Pasted image 20261020204142.png]]
### Paso 7. Completa la tabla
1. Desde PC2, haz ping a PC3:
   ```

   ping 192.168.1.4

   ```
2. Revisa la tabla del switch una tercera vez.
3. Ahora deben aparecer las 4 MAC, cada una en su puerto.
4. Compara contra las MAC que anotaste en el paso 3: deben coincidir. Toma una captura.
### Paso 8 (opcional). Borra la tabla y observa cómo se aprende de nuevo
1. En el CLI del switch, ejecuta:
   ```

   clear mac address-table dynamic

   ```
2. Ejecuta `show mac address-table`: la tabla debe estar vacía otra vez.
3. Haz un ping entre dos PCs y consulta la tabla de nuevo: el switch vuelve a aprender las MAC.
## Entregable
1. Capturas de pantalla de la tabla del switch en tres momentos: paso 4 (antes del ping), paso 6 (después del primer ping) y paso 7 (con las 4 MAC).
2. La tabla escrita con PC, puerto del switch y MAC.
3. Respuestas breves a estas preguntas:
   4. ¿De dónde aprende el switch las direcciones MAC?
   5. ¿Por qué falló el primer ping?: En mi caso el primer ping no falló
   6. ¿Qué tipo de entrada (dinámica o estática) tiene cada MAC y qué significa?
7. Guarda tu archivo de Packet Tracer (`.pkt`) y entrégalo junto con lo anterior.



# Actividad 3.3
### switch de capa 2
Decide por donde reenviar usando solo la direccion mac de la trama y sutabla de direcciones mac; trabaja dentro de una sola red (o una VLAN).

### Switch de capa 3
Ademas de conmutar por mac, puede enrutar usando la direccion ip del paquete y su tabla de rutas, y conecta varias redes o VLAN entre si.

### Capa 2 frente a capa 3
**Capa 2:** lee la mac, trabaja en una sola red, necesita un router para comunicar redes distintas y cuesta menos.

**Capa 3:** Lee la mac e ip, conecta varias redes o 

**Ejemplo: de una red a otra**
Un equipo de la red 192.168.1.0/24 quiere hablar con la 192.168.2.0/24. Con un switch de capa 2 hace falta un router; un switch de capa 3 mira la ip de destino y crea una trama central.

### Reemplazar un router?
No del todo: el router sigue siendo la mejor opcion para conectar con el exterior (WAN, internet) y para funciones como NAT. el switcj de capa 3 se usa en campus y centros de datos para enrutar entre VLAN a alta velocidad.
![[Tabla comparativa Switch 2 y Switch 3]]
ººººººººººººººººººººººººººººººººººººººººººººººººººººººººººººººººººººººººººººººººººººººººººººººººººººº

## Fibra optica: que es?
Es un cable de vidrio o plastico muy delgado que transmite los datos como pulsos de luz en lugar de señales electricas.

La luz viaja por el nuvleo y rebotan en sus paredes por reflexion total interna, porque el revestimiento que lo rodea desvoa la luz de la vuelta hacia adentro

### Partes del cable de fibra
De adentro hacia afuera: el nucleo que condice la luz; el revestimiento, que la mantiene adentro;
el recubrimiento, que protege el vidrio; y la cubierta exterior.

### Fibra multimodo
Tiene un nucleo mas grueso )50 o 62.5 micras) por donde viajan varios haces a la vez, generados con LED; sirven para distancias cortas, como dentro de un edificio o un campus.

### Componentes de un enlace de fibra
Se necesita el cablle de fibra con conectores en sus extremos y un transceptor que convierte la señal electrica en luz; un convertidor de medios une equipos de cobre con la fibra

### Transceptores
Es un modulo intercambiable que se inserta en el puerto del switch o router y convierte la señal electrica; se elige segun el tipo de fibra, la distancia y la velocidad.


### Tipos de transceptores
Por velocidad: SFP 1gbps, SFP+ 10gbps, SFP28 25gbps, QSFP+ 40gbps, QSFP28 100gbps
Por fibra: SX para multimodo y LX para monomodo.

### Ventajas de la fibra optica
Pfrece mucho mas ancho de banda, llega a nayires distancias, es inmune a las interferencias electromagneticas y es mas dificil de intervenir sin ser detectado.

### Desventajas de la fibra optica
Los equipos y los conectores cuestan mas, la instalacion y los empalmes requieren herramientas especializadas y el cable es mas fragil si se dobla demasiado.


### Donde se usa la fibra optica
En el backbone de internet, en los cables submarinos, en los enlaces entre edificios de un campus y en los centros de datos.

### UTP frente a la fibra optica
UTP: señal electrica, hasta 100m, econocimo, sensible a la interferencia.

Fibra: pulsos de luz, desde cientos de metros hasta decenas de kilometros, mas costosa, inmune a la interferencia.


### unicast, multicas y broadcast
segun a cuentos equipos va dirigida, una comunicacion puede ser unicast (a uno), multicast(aun grupo), o broadcast (a todos).

### Unicast: de uno a uno
La trama va a un solo destinatario, identificado por su mac especifica; es el tipo de trafico mas comun, como abrir una pagina wev o copiar un archivo

### Unicast en el switch
El switch busca la mac de destino en su tabla de direcciones  envia la trama solo por el puerto donde esta ese equipo; si no lo conoce, la inunda por todos los puertos.

### Multicast: de uno a un grupo
La trama va a un grupo de equipos que se unieron a el; los demas la ignoran. En IPv4 usa direcciones de 244.0.0.0 q 239.255.255.255 y mac que empiezan con 01:00:5E


### Broadcast: de uno a todos
La trama llega a todos los equipos de la red, con MAC de destino FF:FF:FF:FF:FF:FF; todos la reciben y la procesan.

# Actividad 3.4

## Capa 3: Red y transporte

### IPv4
Es el protocolo de la capa de red que direccione y enruta los paquetes entre redes, usando direcciones de 32 bits (unos 4,300 millones en total).

### Como se agotaron las direcciones ip
las 4,300 millones de direcciones parecian suficientes, pero se repartieron en bloques por clases: una clase A daba mas de 16 millones a una sola organizacion. Ademas, los dispositivos conectados crecieron sin parar

En 2011 la IANA entrego sus ultimos bloques a los registros regionales. se alargo la vida de IPv4 con CIDR, las direcciones privadas y NAT; la solucion definitiva es la IPv6.

### Caracteristicas del IPv4
Es sin conexion (cada paquete viaja por separado), de mejor esfuerzo (no garantiza la entrega) e independiente del medio (funciona sobre cobre, wifi o fibra).

### Encabezado IPv4
El encabezado mide 20 bytes como minimo y lleva la IP de origen, la IP de destino, el TTL (limite de saltos) y el campo protocolo (TCP,UDP o ICMP).

### IPv6
Usa direcciones de 128 bits y se creo porque las direcciones IPv4 se agotaron; permite un numero practicamente ilimitado de dispositivos.

### Ventajas de IPv6
Ofrece un espacio de direcciones enorme, un encabezado simplificado de 40 bytes, autoconfiguracion de direcciones y no usa broadcast: lo reemplaza con multicast.

### Division de la red en grupos
Una red grande se divide en subredes que son grupos de dispositivos organizados por ubicacion, funcion o departamento, cada uno con su propio rango de direcciones.

### Red y host
Toda direccion tiene dos partes: la parte de red, igual para todos los equipos del grupo y la parte del host, que identifica a cada equipo.

La direccion sola no dice donde termina una y empieza la otra.

### Direcciones publicas
Las direcciones publicas son unicas en todo internet y las asigna el proveedor de servicio (ISP).

Un equipo con direccion publica es alcanzable desde internet; las privadas no.

### Direcciones privadas
Se usan solo dentro de una red y no se enrutan en internet: 10.0.0.0/8, 172.16.0.0/12 y 192.168.0.0/16. Para salir a internet usan NAT.

### Direcciones especiales
127.0.0.1 es el loopback (el propio equipo) y 169.254.0.0/16 es la asignacion automatica (APIPA) cuando falla el DHC

0.0.0.0/0 es la ruta predeterminada.

### Direcciones IPv4 
Una direccion IPv4 tiene 32 bits escritos en 4 octetos decimales separados por puntos, como 192.1681.10; una parte identifica la red y otra el host.

### Una direccion IPv4 en binario
![[tabla.jpg]]


## Actividad 3.5
