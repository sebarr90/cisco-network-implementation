# cisco-network-implementation
configuraciones de Capa 2, Capa 3 y Seguridad con un Firewall ASA y una VPN Site-to-Site.
🛰️ Proyecto de Redes – Implementación en Packet Tracer

Este proyecto consiste en la implementación de una topología de red empresarial simulada en Cisco Packet Tracer, aplicando configuraciones de Capa 2, Capa 3 y Seguridad con un Firewall ASA y una VPN Site-to-Site.

El objetivo principal es integrar conceptos de enrutamiento dinámico, segmentación de red, seguridad en switches, NAT/PAT, DHCP, firewalling y VPNs en un entorno simulado.

📋 Requerimientos Implementados
A. Implementación en Capa 3

Direccionamiento completo con IPv4.

Configuración de OSPF área 0 (backbone) en todos los routers.

Interfaces pasivas configuradas en OSPF donde corresponde.

Implementación de VPN Site-to-Site entre RA y RC para asegurar tráfico entre las LANs Inside (172.16.10.0/24) y DMZ (172.16.250.0/24).

B. Implementación en Capa 2

Reasignación de puertos de switch a VLANs distintas de VLAN1.

Puertos no utilizados → shutdown.

Seguridad en puertos:

Máximo de 2 direcciones MAC por puerto.

Exceso de MACs → puerto se desactiva.

Configuración de STP PortFast + BPDU Guard en interfaces de usuarios.

Storm Control para limitar broadcast al 15%.

DHCP Snooping en SWB con límite de 2 direcciones IP/min para prevenir ataques de hambruna.

C. Implementación de Seguridad

Cisco ASA Firewall configurado con zonas:

Inside → nivel de seguridad 100.

DMZ → nivel de seguridad 40.

Outside → nivel de seguridad 20.

NAT/PAT configurado:

Inside → NAT dinámico hacia Outside.

PC-DMZ → NAT estático hacia Outside (accesible con IP pública interna).

DHCP Server en ASA para la zona Inside (máx. 16 IPs).

ACLs y Telnet:

Telnet permitido desde servidor Servicios (172.16.250.3).

Usuario: admin_telnet, Password: telnet.

MPF (Modular Policy Framework) → inspección de ICMP, FTP, DNS y TFTP.

VPN Site-to-Site implementada entre RA y RC para tráfico seguro entre segmentos.

🖥️ Topología de Red

📌 Componentes principales:

Routers: RA, RB, RC (con OSPF + VPN).

Switches: SWA, SWB, SWC (con VLANs, STP, DHCP Snooping, Seguridad).

Firewall ASA (con NAT, DHCP, ACLs, Zonas y VPN).

Equipos finales: PCs en Inside, DMZ y Servidor de Servicios.

⚠️ Notas Importantes

En Packet Tracer, algunos equipos fueron reemplazados para soportar la configuración:

Routers 2911 → cambiados a 1841 en RA y RC (limitación en VPN).

ASA 5505 → cambiado a ASA 5506 (mejor compatibilidad con NAT, DHCP y VPN).

Todas las configuraciones fueron probadas y validadas con ping e inspección de tráfico.

🚀 Resultados

Conectividad asegurada entre todas las redes vía OSPF.

Seguridad aplicada en switches de acceso.

Control de tormentas broadcast y protección de spanning-tree.

ASA funcionando como firewall perimetral con NAT/PAT y DHCP.

VPN Site-to-Site establecida correctamente, asegurando que el tráfico entre Inside ↔ DMZ viaja por el túnel y no por OSPF.

📂 Archivos del Repositorio

proyecto-redes.pkt → archivo de Packet Tracer con toda la topología.

documentacion.txt → documentación detallada de configuraciones.

README.md → explicación del proyecto.

🔑 Credenciales de Acceso

Telnet al ASA

Usuario: admin_telnet

Password: telnet
