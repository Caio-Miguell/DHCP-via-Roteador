Projeto DHCP via Roteador
Descrição

Este projeto mostra como configurar um roteador Cisco para fornecer endereços IP automaticamente a PCs em uma rede local usando DHCP.
Com isso, os computadores não precisam de configuração manual de IP, gateway ou DNS — tudo é distribuído automaticamente pelo roteador. Ideal para prática de CCNA.

Topologia

1 Roteador: Cisco 1941

1 Switch: Cisco 2960

4 PCs: Genéricos do Packet Tracer

Conexões:

[PC0]---|
[PC1]---|   
[PC2]---|---[Switch 2960]---[Router 1941]
[PC3]---|

Objetivo

Aprender a configurar DHCP em um roteador Cisco.

Garantir que PCs recebam IP automaticamente.

Testar conectividade básica da rede.

Passo a Passo (Resumo)

Ignorar assistente inicial do roteador

Digite no quando o setup automático aparecer.

Configurar hostname e senhas (opcional, prática CCNA):

enable
configure terminal
hostname R1
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


Configurar PCs para DHCP

Desktop → IP Configuration → marque DHCP

Testar a rede:

ping 192.168.1.1 para verificar conectividade

ipconfig nos PCs para ver o IP atribuído

O que você aprende com este projeto

Configuração básica de roteadores Cisco via CLI.

Criação de pools DHCP e exclusão de endereços.

Conectividade básica entre PCs em uma LAN.

Boas práticas de CCNA (hostnames, senhas, interfaces).
