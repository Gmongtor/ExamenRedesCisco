# Examen de Redes II  

https://github.com/Gmongtor/ExamenRedesCisco.git

---

# Parte I: Conceptos y Teoría

---

## Pregunta 1: El Mural de las Siete Capas

**¿Qué representa el mural de las siete capas en términos de las redes de comunicación modernas? Identifica brevemente cada capa y explica cómo se relaciona este antiguo “modelo” con el proceso de comunicación de datos actual.**

El mural de las siete capas es una representación del Modelo OSI (Open Systems Interconnection), un marco conceptual que divide el proceso de comunicación en redes en siete capas distintas. Este modelo es fundamental para entender cómo se estandariza la comunicación entre diferentes sistemas y tecnologías en el ámbito de las redes modernas. A continuación, se describen brevemente cada una de las capas y su relación con el proceso de comunicación de datos actual.

| Capa | Nombre             | Función principal                                                              |
|------|--------------------|--------------------------------------------------------------------------------|
| 1    | Física             | Transmisión de bits a través del medio físico.                                |
| 2    | Enlace de Datos    | Control de acceso al medio, detección/corrección de errores, direcciones MAC. |
| 3    | Red                | Enrutamiento de paquetes entre redes (ej. IP).                                |
| 4    | Transporte         | Segmentación, control de flujo, fiabilidad (TCP/UDP).                         |
| 5    | Sesión             | Establecimiento, gestión y terminación de sesiones.                           |
| 6    | Presentación       | Formato, compresión y cifrado de datos.                                       |
| 7    | Aplicación         | Interfaz entre usuario y red (ej. HTTP, FTP, DNS).                            |


![Interpretación moderna_ Las 7 capas del Modelo OSI - visual selection](https://github.com/user-attachments/assets/376fdb0a-9c46-481b-b6a0-111c10c8c3e8)

---

## Pregunta 2: Los Dos Pergaminos del Mensajero

**¿A qué protocolos de comunicación actuales equivalen el mensajero confiable y el mensajero veloz? Compara sus características, explicando las ventajas y desventajas de cada enfoque en redes modernas.**

- **Mensajero confiable**: equivale a **TCP (Transmission Control Protocol)**  
- **Mensajero veloz**: equivale a **UDP (User Datagram Protocol)**

| Característica        | TCP                                  | UDP                               |
|-----------------------|---------------------------------------|-----------------------------------|
| Tipo de conexión      | Orientado a conexión                  | No orientado a conexión           |
| Fiabilidad            | Alta (uso de ACK, control de errores) | Baja                              |
| Orden de entrega      | Garantizado                           | No garantizado                    |
| Velocidad             | Menor                                 | Mayor                             |
| Aplicaciones típicas  | Web, email, FTP, SSH                  | Streaming, VoIP, juegos online    |

Ventajas y Desventajas

#### Ventajas de TCP

Fiabilidad en la entrega: TCP asegura que los datos lleguen correctamente al destino mediante el uso de acuses de recibo (ACK) y mecanismos de control de errores. Esto es crucial para aplicaciones donde la integridad de los datos es fundamental, como en la transferencia de archivos o en correos electrónicos.

#### Desventajas de TCP

Mayor sobrecarga y latencia: Debido a sus características de fiabilidad y control, TCP introduce una mayor sobrecarga en la red, lo que puede resultar en latencias más altas. Esto puede ser un inconveniente en aplicaciones que requieren una respuesta rápida.

#### Ventajas de UDP

Bajo retardo: UDP permite una transmisión más rápida de datos al no requerir la confirmación de entrega ni el control de errores. Esto lo hace ideal para aplicaciones en tiempo real como streaming de video, VoIP y juegos en línea, donde la velocidad es más crítica que la fiabilidad.

#### Desventajas de UDP

No garantiza entrega ni orden: A diferencia de TCP, UDP no asegura que los paquetes lleguen a su destino ni que lo hagan en el orden correcto. Esto puede ser problemático en aplicaciones donde la secuenciación de los datos es importante.

  ![Comparación de Protocolos de Comunicación_ TCP y UDP - visual selection](https://github.com/user-attachments/assets/0c47532b-f9cd-4dcd-9e92-2c3d48056682)


---

## Pregunta 3: El Enigma de las Subredes

**Si la antigua red usaba la dirección 192.168.50.0 como base y necesitaba dividirse en 4 subredes de igual tamaño, ¿qué máscara de subred habrían utilizado los antiguos para lograrlo? ¿Cuántas direcciones de host (utilizables) tendría cada subred resultante?**

- Red base: `192.168.50.0/24`  
- Se requieren 4 subredes → se usan 2 bits más → nueva máscara: **/26**  
- Cada subred /26 tiene: 2⁶ - 2 = **62 hosts utilizables**

| Subred | Rango IP                  | Hosts utilizables |
|--------|---------------------------|-------------------|
| 1      | 192.168.50.0 – 63         | 62                |
| 2      | 192.168.50.64 – 127       | 62                |
| 3      | 192.168.50.128 – 191      | 62                |
| 4      | 192.168.50.192 – 255      | 62                |

**Máscara utilizada:** `255.255.255.192` (**/26**)

---

## Pregunta 4: La Encrucijada de las Rutas

**¿Qué concepto moderno de redes representa el tótem con flechas de la encrucijada? Explica qué es una tabla de enrutamiento y cómo funciona en un router actual. Además, interpreta la diferencia entre las flechas talladas en piedra y las flechas móviles en términos de enrutamiento estático vs. enrutamiento dinámico en redes.**

#### Tabla de Enrutamiento

- Una tabla de enrutamiento es una estructura fundamental en el funcionamiento de los routers. Esta tabla contiene rutas que indican al router por qué interfaz debe enviar un paquete de datos, dependiendo de su dirección IP de destino. La correcta configuración y mantenimiento de esta tabla son esenciales para garantizar que los datos se transmitan de manera eficiente y efectiva a través de una red.


| Tipo de enrutamiento | Descripción                               |
|----------------------|--------------------------------------------|
| Estático             | Rutas configuradas manualmente. Estables. |
| Dinámico             | Rutas aprendidas automáticamente (RIP, OSPF). Se actualizan ante cambios. |

#### Enrutamiento Estático vs Enrutamiento Dinámico

- **Flechas talladas en piedra:** Representan el enrutamiento estático, donde las rutas son configuradas manualmente por un administrador de red. Estas rutas son estables y no cambian a menos que se realice una intervención manual. Esto puede ser beneficioso en entornos donde las rutas son predecibles y no cambian con frecuencia.

- **Flechas móviles:** Simbolizan el enrutamiento dinámico, donde las rutas son aprendidas automáticamente por el router a través de protocolos de enrutamiento como RIP (Routing Information Protocol) o OSPF (Open Shortest Path First). Estas rutas se actualizan automáticamente en respuesta a cambios en la topología de la red, lo que permite una mayor flexibilidad y adaptabilidad en entornos de red más complejos.

 ![La Encrucijada de las Rutas_ Un Análisis del Enrutamiento en Redes Modernas - visual selection](https://github.com/user-attachments/assets/0bb8efd5-f347-4cb9-829f-5998a0eb8dac)

---

## Pregunta 5: El Guardián de la Máscara Única

**¿Qué técnica de redes moderna se refleja en la leyenda del Guardián de la Máscara? Nombra y describe brevemente este mecanismo, explicando cómo permite que múltiples dispositivos internos de una red compartan una única identidad (dirección) al comunicarse con el exterior, y menciona dos beneficios que brinda esta estrategia a las redes actuales.**

En este documento, exploraremos la técnica de redes conocida como NAT (Network Address Translation) y su relación con la leyenda del Guardián de la Máscara Única. NAT es un mecanismo que permite que múltiples dispositivos dentro de una red privada compartan una única dirección IP pública al comunicarse con el exterior. A través de esta técnica, se logran importantes beneficios que son esenciales para la gestión de redes en la actualidad.

### Descripción de NAT:

NAT es un proceso que permite que varios dispositivos en una red privada, como las que utilizan direcciones IP en el rango 192.168.x.x, compartan una sola dirección IP pública cuando acceden a Internet. Este proceso es gestionado por un router que actúa como intermediario. Cuando un dispositivo interno envía una solicitud a Internet, el router reemplaza la dirección IP privada del dispositivo con su propia dirección IP pública. Además, el router mantiene una tabla de traducción que le permite redirigir las respuestas de vuelta al dispositivo correcto dentro de la red privada.

![El Guardián de la Máscara Única_ NAT en la Era de las Redes Modernas - visual selection](https://github.com/user-attachments/assets/8659b61b-d422-4629-b8c8-8820e649b20e)


### Beneficios:
1. **Conservación de direcciones IPv4 públicas:** Dado que las direcciones IPv4 son limitadas y escasas, NAT permite que múltiples dispositivos utilicen una sola dirección IP pública, lo que ayuda a conservar el espacio de direcciones disponibles.
2. **Ocultamiento de la red interna, mejorando la seguridad:** Al utilizar NAT, las direcciones IP internas no son visibles desde el exterior, lo que añade una capa de seguridad a la red. Esto dificulta que los atacantes puedan identificar y dirigirse a dispositivos específicos dentro de la red privada.

![El Guardián de la Máscara Única_ NAT en la Era de las Redes Modernas - visual selection (1)](https://github.com/user-attachments/assets/2960d37e-53eb-48a8-b874-51cbd8480f12)

---

# Parte II: Cisco Packet Tracer

---

## Ejercicio 1 - Reconstrucción de Enlace Entre Ciudades

### Introducción

En este primer ejercicio del examen de redes, se reconstruyó la conexión entre dos ciudades (Ciudad A y Ciudad B), unidas por un enlace serial punto a punto. Se configuraron direcciones IP y rutas estáticas para garantizar la conectividad total entre los dispositivos de ambas redes.

---

### Topología

![image](https://github.com/user-attachments/assets/819517a1-b20c-45a0-9137-57ad11a90969)

---

### Direccionamiento IP

| Dispositivo | Interfaz        | Dirección IP     | Máscara           | Ciudad   |
|-------------|------------------|------------------|-------------------|----------|
| RouterA     | Gig0/0           | 192.168.1.1      | 255.255.255.0     | Ciudad A |
| RouterA     | Serial0/0/0      | 10.0.0.1         | 255.255.255.252   | -        |
| RouterB     | Gig0/0           | 192.168.2.1      | 255.255.255.0     | Ciudad B |
| RouterB     | Serial0/0/0      | 10.0.0.2         | 255.255.255.252   | -        |
| PC0         | -                | 192.168.1.10     | 255.255.255.0     | Ciudad A |
| PC1         | -                | 192.168.1.11     | 255.255.255.0     | Ciudad A |
| PC2         | -                | 192.168.2.10     | 255.255.255.0     | Ciudad B |
| PC3         | -                | 192.168.2.11     | 255.255.255.0     | Ciudad B |

---

### Configuración de Router A

```bash
enable
configure terminal

interface GigabitEthernet0/0
 ip address 192.168.1.1 255.255.255.0
 no shutdown

interface Serial0/0/0
 ip address 10.0.0.1 255.255.255.252
 clock rate 64000
 no shutdown

ip route 192.168.2.0 255.255.255.0 10.0.0.2

end
write memory
```
### Configuración de Router B

```bash
enable
configure terminal

interface GigabitEthernet0/0
 ip address 192.168.2.1 255.255.255.0
 no shutdown

interface Serial0/0/0
 ip address 10.0.0.2 255.255.255.252
 no shutdown

ip route 192.168.1.0 255.255.255.0 10.0.0.1

end
write memory
```
---

## Ejercicio 2 - "Los Canales Secretos de la Red Perdida" 🌐

### Introducción

En esta misión, se ha reconstruido la antigua red de la ciudad utilizando VLANs para segmentar a los distintos gremios. El router central ha retomado el control de los canales secretos (redes) mediante subinterfaces, lo que ha permitido unir de nuevo a los Arquitectos, Escribas y al Servidor del Consejo.

---

### Topología

![image](https://github.com/user-attachments/assets/8541e58e-9cfc-4540-b9e3-d2e79df3df2b)

---

**Dispositivos y VLANs configuradas:**

| Dispositivo       | VLAN  | IP Address        | Función         |
|-------------------|-------|-------------------|-----------------|
| PC1, PC2, PC3      | 10    | 192.168.10.10-12  | Arquitectos     |
| PC4, Smartphone0, Tablet0 | 20    | 192.168.20.10-21  | Escribas        |
| Server0           | 99    | 192.168.99.10     | Servidor DHCP   |
| Router0           | -     | Subinterfaces para cada VLAN | Router-on-a-stick |
| Switch0           | -     | Trunk + Access Ports configurados | Switch central |
---

### Configuración de VLANs en el Switch

```bash
enable
configure terminal

vlan 10
 name Arquitectos
vlan 20
 name Escribas
vlan 99
 name Servidor

interface range fa0/1 - 3
 switchport mode access
 switchport access vlan 10

interface range fa0/5, fa0/7
 switchport mode access
 switchport access vlan 20

interface range fa0/4, fa0/6
 switchport mode access
 switchport access vlan 99

interface gigabitEthernet0/1
 switchport mode trunk
```
### Configuración del Router
```bash
enable
configure terminal

interface GigabitEthernet0/0
 no shutdown

interface GigabitEthernet0/0.10
 encapsulation dot1Q 10
 ip address 192.168.10.1 255.255.255.0
 ip helper-address 192.168.99.10

interface GigabitEthernet0/0.20
 encapsulation dot1Q 20
 ip address 192.168.20.1 255.255.255.0
 ip helper-address 192.168.99.10

interface GigabitEthernet0/0.99
 encapsulation dot1Q 99
 ip address 192.168.99.1 255.255.255.0

exit
write memory

```
