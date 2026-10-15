### Actividad 2.1
Practica 1 en CISCO
### Actividad 2.2
Abrir aplicación de wifi para analizar las redes cercanas de frecuencia 2.4 GHz y 5 GHz 

Wifi 2 = 80211.A, vel = 54mbps, año = 1999
Wifi 1 = 80211.B, vel = 11mbps, año = 1999 
Wifi 4 = 80211.N, vel = 11mbps, año = 1999
Wifi 3 = 80211.G, vel = 54mbps, año = 2003
Wifi 5 = 80211.AC, vel = 600mbps, año = 2009
Wifi 6 = 80211.AX, vel = 96gbps, año 2014
### Actividad 2.3

Capas del tcp/ip
1. Capa de Aplicación

- **Qué hace:** Es el punto de contacto directo con el usuario y las aplicaciones (como navegadores web o clientes de correo). Prepara los datos que se van a enviar.
- **Protocolos principales:** HTTP/HTTPS, FTP, SMTP, DNS, SSH
2. Capa de Transporte

- **Qué hace:** Controla la comunicación de extremo a extremo entre los dispositivos. Divide los datos en bloques más pequeños (segmentos) y asegura que lleguen bien.
- **Protocolos principales:**
    - **TCP:** Seguro y ordenado; confirma que todo llegue sin errores.
    - **UDP:** Más rápido, pero sin garantías de entrega o de orden (ideal para streaming o juegos en tiempo real)
3. Capa de Internet (o Red)

- **Qué hace:** Se encarga de direccionar y enrutar los paquetes de datos para que crucen diferentes redes y lleguen a su destino final (utilizando direcciones IP).
- **Protocolos principales:** IP (IPv4 / IPv6), ICMP, ARP
4. Capa de Acceso a la Red (o Enlace)

- **Qué hace:** Maneja la conexión física y lógica con el medio de transmisión. Convierte los paquetes en señales eléctricas, ópticas o de radio para enviarlos por el hardware.
- **Tecnologías y protocolos principales:** Ethernet, Wi-Fi, Bluetooth