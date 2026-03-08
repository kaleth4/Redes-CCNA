# Redes-CCNA
🎓 Redes CCNA: Topologías y Conceptos Fundamentales
La certificación CCNA (Cisco Certified Network Associate) se enfoca en el nivel técnico de configuración y mantenimiento de equipos de redes Cisco (Examen 200-301)
. Estos son sus conceptos más importantes:
📐 Topologías de Red
Las topologías describen cómo se organizan y conectan físicamente o lógicamente los dispositivos en una red
:
Estrella: Todos los dispositivos se conectan a un nodo central (Switch o Hub); es la más común en redes locales
.
Bus: Todos comparten un único cable central; es económica pero riesgosa, ya que si el cable falla, toda la red cae
.
Anillo: Los dispositivos forman un círculo cerrado y los datos viajan en una sola dirección
.
Malla: Cada dispositivo se conecta con todos los demás, ofreciendo alta redundancia y tolerancia a fallos
.
Árbol: Una variante jerárquica de la estrella, ideal para escalabilidad en organizaciones
.
📚 Modelos de Referencia
Modelo OSI: Marco conceptual de 7 capas (Física, Enlace, Red, Transporte, Sesión, Presentación y Aplicación) que estructura la comunicación entre sistemas abiertos
.
Modelo TCP/IP: El modelo práctico de 4 capas (Acceso a la Red, Internet, Transporte y Aplicación) que rige el internet actual
.
🛠️ Configuración y Componentes Clave
Segmentación y VLANs: Las VLANs (Virtual LANs) permiten dividir una red física en varias redes lógicas para mejorar la seguridad y el rendimiento
. La VLAN 1 es la interfaz virtual de administración predeterminada en switches Cisco
.
Router-on-a-Stick: Método para permitir la comunicación entre diferentes VLANs utilizando un router conectado a un switch mediante un enlace troncal (trunk) y configurando subinterfaces para cada VLAN
.
Protocolos Esenciales:
IP: Encargado del direccionamiento y enrutamiento
.
TCP/UDP: TCP es orientado a conexión (confiable, usa el 3-way handshake), mientras que UDP no lo es (más rápido, ideal para streaming)
.
ICMP: Utilizado por herramientas como ping para verificar la conectividad de extremo a extremo
.
DHCP y DNS: DHCP asigna direcciones IP automáticamente
, mientras que DNS traduce nombres de dominio a direcciones IP
.
Subnetting: Técnica para dividir una red IP grande en subredes más pequeñas, optimizando el uso de direcciones.

📍Mi Laboratorio de Cisco
<img width="748" height="765" alt="laboratorio" src="https://github.com/user-attachments/assets/b5559c29-3384-452d-a8ef-f09d3f665e1b" />
<img width="892" height="646" alt="packet" src="https://github.com/user-attachments/assets/bc2b8a59-671d-4bc8-a92c-b15d75dbc491" />

Para completar esta práctica de laboratorio sobre la resolución de problemas de configuración de VLAN emepzaremos con:
Parte 1: Armado de la red y configuración básica
Cableado de la red: Realiza la conexión física de los dispositivos (2 switches, 1 router y las PC) tal como se muestra en el diagrama de la topología
. Utilizo cables Ethernet para las conexiones de red y cables de consola para la configuración de los dispositivos Cisco
.
Configuración de los equipos host: Asigno las direcciones IP, máscaras de subred y gateways predeterminados a cada PC (PC-A, PC-B y PC-C) siguiendo la Tabla de direccionamiento
.
Inicialización de switches: Inicializo y vuelvo a cargar los switches S1 y S2 según sea necesario para comenzar con una configuración limpia
.
Configuración del Router: Se implementa subinterfaces en el Router R1 para permitir la comunicación entre las diferentes VLANs (VLAN 10, 20 y 30)
.
Parte 2 y 3: Resolución de problemas de VLAN
Identificar y corregir errores: Los switches ya cuentan con información de VLAN y enlaces troncales (802.1Q), pero tienen errores de configuración que causan problemas de conectividad
. Se Debe:
Resolver los problemas específicos de la VLAN 10
.
Resolver los problemas específicos de la VLAN 20
.
Asegurarte de que los puertos estén asignados correctamente (F0/1 como enlace troncal, F0/6-12 a VLAN 10, etc.)
.
<img width="747" height="741" alt="Captura de pantalla 2026-03-06 080700" src="https://github.com/user-attachments/assets/90b15991-0d9a-43d8-902d-4a9fe21143db" />



🛡️ Redes en el Pentesting
El hacking ético de redes se basa en identificar y aprovechar vulnerabilidades de forma controlada para mejorar la seguridad
. A continuación, se detallan los pilares y herramientas clave utilizados en estas auditorías:
🔍 Reconocimiento y Escaneo: La herramienta favorita para el descubrimiento de dispositivos y puertos es Nmap, la cual permite realizar "radiografías" de la red para ver qué equipos están activos y qué servicios (como SSH, HTTP o SMB) están corriendo en sus puertos
. Mediante escaneos sigilosos (stealth scans), un atacante puede intentar pasar desapercibido al no completar el saludo de tres vías de TCP
.
📶 Hacking de Redes Wi-Fi: Para vulnerar redes inalámbricas, se suelen capturar los handshakes (apretones de manos entre el router y el dispositivo), los cuales contienen la contraseña cifrada que luego puede ser descifrada mediante ataques de fuerza bruta o diccionarios usando herramientas como Hashcat o Airgeddon
.
🎭 Ingeniería Social y Gemelo Maligno: El ataque de Evil Twin consiste en crear un punto de acceso falso con un portal cautivo que imita uno legítimo para engañar al usuario y que este ingrese su contraseña en texto claro
.
🕵️ Sniffing y Ataques MITM: Mediante el envenenamiento ARP (ARP Spoofing), un pentester puede posicionarse como un "hombre en el medio" (Man-in-the-Middle), interceptando el tráfico entre la víctima y el router
. Herramientas como Bettercap facilitan este proceso y permiten capturar credenciales en sitios no cifrados (HTTP)
.
📊 Análisis de Paquetes: Wireshark es el analizador de protocolos estándar que permite ver detalladamente cada paquete de datos, facilitando la identificación de contraseñas enviadas mediante peticiones POST en formularios web.
