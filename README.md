Projeto DHCP via Roteador
Objetivo

Configurar um roteador Cisco para fornecer IP automático (via DHCP) a PCs conectados através de um switch.

Topologia e Dispositivos
Dispositivo	Modelo Packet Tracer	Quantidade
Roteador	1941 ou 2811	1
Switch	2960	1
PCs	Generic	4

Conexões:

Roteador → Switch: Copper Straight-Through

Switch → PCs: Copper Straight-Through

[PC0]---|
[PC1]---|   
[PC2]---|---[Switch 2960]---[Router 1941]
[PC3]---|


Passo a Passo

Ignorar assistente inicial do roteador:

Digite no quando perguntar se quer entrar no setup.

Configurar hostname:

enable
configure terminal
hostname R1


Configurar senha (opcional):

line console 0
password cisco
login
exit
enable secret cisco123


Configurar interface do roteador:

interface gigabitEthernet0/0
ip address 192.168.1.1 255.255.255.0
no shutdown
exit


Configurar DHCP:

ip dhcp excluded-address 192.168.1.1 192.168.1.5
ip dhcp pool LAN
network 192.168.1.0 255.255.255.0
default-router 192.168.1.1
dns-server 8.8.8.8
exit


Configurar PCs para DHCP:

Desktop → IP Configuration → marque DHCP

Testar conexão:

No PC: ping 192.168.1.1

Verifique IP: ipconfig

Resumo

PCs recebem IP automaticamente do roteador.

DHCP pool definido no roteador com gateway e DNS.

Senhas opcionais para proteger o roteador.