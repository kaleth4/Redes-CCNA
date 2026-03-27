## Introducción

Una **red virtual** es una red definida por software que permite la comunicación entre máquinas virtuales y recursos físicos.

---

## Ventajas de Redes Virtuales

**Beneficios principales:**

- **Aislamiento** del tráfico
- **Flexibilidad** en configuración
- **Escalabilidad** dinámica
- **Reducción** de costos de hardware

---

## Tipos de Redes Virtuales

### Host-Only Network

**Arquitectura:**

```
[Host] ←→ [VM1] ←→ [VM2] ←→ [VM3]
       ↕
   [vSwitch]
```

**Características:**

- Comunicación entre **host y VMs**
- **Aislamiento** completo de red externa
- Ideal para **laboratorios** seguros

---

**Configuración en VirtualBox:**

```bash
VBoxManage hostonlyif create
VBoxManage hostonlyif ipconfig vboxnet0 --ip 192.168.56.1
```

---

### NAT Network

**Arquitectura:**

```
[Internet] ←→ [NAT Gateway] ←→ [VM1, VM2, VM3]
```

**Características:**

- Acceso a **Internet** desde VMs
- VMs **no accesibles** desde exterior
- **Traducción** de direcciones automática

---

**Configuración en VirtualBox:**

```bash
VBoxManage natnetwork add --netname natnet1 --network "10.0.2.0/24"
VBoxManage natnetwork start --netname natnet1
```

---

### Bridged Network

**Arquitectura:**

```
[Physical Network] ←→ [Bridge] ←→ [VM1, VM2, VM3]
                              ↕
                          [Host NIC]
```

**Características:**

- VMs aparecen como **dispositivos físicos** en la red
- Acceso **completo** a recursos de red
- **Menor seguridad**

---

### Internal Network

**Arquitectura:**

```
[VM1] ←→ [Internal Switch] ←→ [VM2] ←→ [VM3]
```

**Características:**

- Comunicación **solo entre VMs**
- **Aislamiento** completo del host y exterior
- Ideal para **simulaciones** de red

---

## Topologías Complejas

### Red Corporativa Simulada

**Diseño:**

```
[Internet]
    ↓
[pfSense Firewall] (WAN: DHCP, LAN: 192.168.1.1/24)
    ↓
[Internal Switch]
    ├── [Domain Controller] (192.168.1.10)
    ├── [File Server] (192.168.1.20)
    ├── [Web Server] (192.168.1.30)
    └── [Workstations] (192.168.1.100-200)
```

---

### Red DMZ

**Diseño:**

```
[Internet]
    ↓
[External Firewall]
    ↓
[DMZ] (10.0.1.0/24)
    ├── [Web Server] (10.0.1.10)
    ├── [Mail Server] (10.0.1.20)
    └── [DNS Server] (10.0.1.30)
    ↓
[Internal Firewall]
    ↓
[Internal Network] (192.168.1.0/24)
```

---

## Configuración Avanzada

### VLAN

**Configuración:**

```bash
sudo vconfig add eth0 10
sudo ifconfig eth0.10 192.168.10.1 netmask 255.255.255.0
```

---

### Tunneling

**Configuración GRE:**

```bash
sudo ip tunnel add gre1 mode gre remote 10.0.1.1 local 10.0.1.2
sudo ip link set gre1 up
sudo ip addr add 192.168.100.1/24 dev gre1
```

---

### VPN

**Configuración:**

```bash
sudo openvpn --config client.ovpn
```

---

## Herramientas de Gestión

### Wireshark

**Captura de tráfico:**

```bash
sudo tcpdump -i eth0 -w capture.pcap
wireshark capture.pcap
```

---

### Netcat

**Testing de conexiones:**

```bash
# Servidor
nc -l -p 1234

# Cliente
nc 192.168.1.10 1234
```

---

### Nmap

**Escaneo de red:**

```bash
# Descubrimiento de hosts
nmap -sn 192.168.1.0/24

# Escaneo completo
nmap -sS -A 192.168.1.10
```

---

## Seguridad en Redes Virtuales

### Microsegmentación

**Estrategias:**

- **Separación** de servicios
- Políticas de **firewall** específicas
- **Monitoreo** granular

---

### Firewalls

**Ejemplo con pfSense:**

- **LAN:** 192.168.1.1/24
- **DHCP:** 192.168.1.100-200
- **Reglas:** permitir HTTP/HTTPS outbound, bloquear todo lo demás




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
