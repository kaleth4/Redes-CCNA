###Redes
🎓 Redes CCNA: Topologías, Configuración y Pentesting
Este repositorio es una guía integral sobre los conceptos fundamentales de la certificación Cisco Certified Network Associate (CCNA), incluyendo laboratorios prácticos de configuración y una introducción a la seguridad ofensiva en redes.

📐 1. Topologías de Red
Las topologías describen la organización física o lógica de los dispositivos.
network topologies diagram star mesh ring bus tree, generada por IA
Shutterstock
<img width="748" height="765" alt="laboratorio" src="https://github.com/user-attachments/assets/d2498f97-8322-463a-a1e6-5dea9f0fca39" />

Topología	Características	Caso de Uso
Estrella	Conexión a un nodo central (Switch/Hub).	Redes LAN modernas (la más común).
Malla	Redundancia total; todos conectados entre sí.	Redes críticas y proveedores de Internet.
Bus	Un solo cable central (backbone).	Redes antiguas o de bajo presupuesto.
Árbol	Jerárquica; combinación de estrellas.	Escalabilidad en campus corporativos.
<img width="747" height="741" alt="Captura de pantalla 2026-03-06 080700" src="https://github.com/user-attachments/assets/ee731073-1a21-4e43-baf7-bdea31f3b485" />

📚 2. Modelos de Referencia
Entender cómo se encapsulan los datos es vital para el diagnóstico de fallos.

Modelo OSI: Marco teórico de 7 capas (Física, Enlace, Red, Transporte, Sesión, Presentación, Aplicación).

Modelo TCP/IP: El estándar práctico de Internet (Acceso a Red, Internet, Transporte, Aplicación).

🛠️ 3. Configuración y Componentes Clave
🔹 Segmentación y VLANs
Las VLANs (Virtual LANs) segmentan redes físicas en dominios de difusión más pequeños.

VLAN 1: Interfaz de administración predeterminada.

Trunking (802.1Q): Permite el paso de múltiples VLANs a través de un solo enlace físico.

🔹 Router-on-a-Stick (ROAS)
Permite la comunicación entre VLANs mediante un router y subinterfaces.

Bash
# Ejemplo de configuración de subinterfaz en Router (R1)
R1(config)# interface g0/0.10
R1(config-subif)# encapsulation dot1Q 10
R1(config-subif)# ip address 192.168.10.1 255.255.255.0
📍 4. Laboratorio Práctico: Troubleshooting de VLANs
Este escenario se enfoca en la resolución de problemas de conectividad en una red con múltiples switches y un router.

Parte 1: Implementación Básica
Cableado: Conexión de 2 switches, 1 router y 3 PCs.

Direccionamiento: Configuración de IPs estáticas según la tabla de direccionamiento.

Mantenimiento: Inicialización (write erase / reload) para asegurar configuraciones limpias.

Parte 2 y 3: Resolución de Conflictos
Problema: Error en la asignación de puertos.

Solución: Mover puertos F0/6-12 a la VLAN 10.

Verificación: Asegurar que el enlace entre switches sea Trunk y no Access.

🛡️ 5. Redes en el Pentesting
El hacking ético analiza la red desde la perspectiva de un atacante para fortalecerla.

🔍 Reconocimiento y Escaneo
Nmap: Descubrimiento de hosts y servicios.

Stealth Scans: Uso de paquetes SYN para evitar completar el three-way handshake y pasar desapercibido.

🕵️ Ataques MITM (Man-in-the-Middle)
ARP Spoofing: Envenenamiento de la tabla ARP para interceptar tráfico entre la víctima y el Gateway.

Herramientas: Bettercap, Ettercap.

📶 Seguridad Wi-Fi y Análisis
Aircrack-ng / Hashcat: Captura de handshakes y cracking de contraseñas por fuerza bruta.

Wireshark: Análisis profundo de protocolos (Capa 2 a Capa 7) para detectar credenciales en texto plano (HTTP/FTP).
