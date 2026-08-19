# Rede Corporativa Completa

Projeto de infraestrutura de rede corporativa desenvolvido no Cisco Packet Tracer, simulando uma empresa com diferentes setores, servidores, gerenciamento centralizado e conexão com um provedor de Internet.

## Estrutura da Rede

A infraestrutura é composta por um Switch Layer 3 central (SW-CORE), switches de acesso para cada setor, um roteador de borda (R-EDGE), um provedor de Internet (ISP) e um Data Center.

### Setores

* TI — VLAN 10
* RH — VLAN 20
* Financeiro — VLAN 30
* Administrativo — VLAN 40
* Visitantes — VLAN 50
* Gerenciamento — VLAN 99
* Data Center — VLAN 100

## Endereçamento

Cada setor possui uma rede IPv4 /24 independente:

* VLAN 10 — 192.168.10.0/24
* VLAN 20 — 192.168.20.0/24
* VLAN 30 — 192.168.30.0/24
* VLAN 40 — 192.168.40.0/24
* VLAN 50 — 192.168.50.0/24
* VLAN 99 — 192.168.99.0/24
* VLAN 100 — 192.168.100.0/24

O SW-CORE atua como gateway das VLANs através de interfaces virtuais (SVIs).

## Serviços de Rede

O projeto utiliza um servidor DHCP centralizado no Data Center, responsável pela distribuição automática de endereços IP para as diferentes VLANs através de DHCP Relay (`ip helper-address`).

Também foram implementados:

* Servidor DNS — 192.168.100.21
* Servidor DHCP — 192.168.100.20
* Servidor Web — 192.168.100.22

## Switching

A comunicação entre o SW-CORE e os switches de acesso utiliza links trunk 802.1Q, permitindo o transporte das VLANs necessárias.

A VLAN 99 é utilizada para gerenciamento da infraestrutura, enquanto a VLAN 100 é destinada aos servidores do Data Center.

O Spanning Tree Protocol (STP) foi utilizado para controlar a topologia de camada 2 e evitar loops na rede.

## Conectividade

A infraestrutura possui um roteador de borda (R-EDGE) responsável pela comunicação entre a rede corporativa e o ISP.

O projeto foi testado com comunicação entre diferentes VLANs, acesso aos servidores, obtenção automática de endereços via DHCP, resolução DNS e conectividade com a rede externa.

## Objetivo

O objetivo do projeto é demonstrar, de forma prática, a implementação e integração de uma infraestrutura de rede corporativa utilizando segmentação por VLAN, switching, roteamento entre redes, serviços de rede, Data Center, gerenciamento e conectividade externa.

Projeto desenvolvido para fins de estudo e demonstração de conhecimentos em redes de computadores e infraestrutura.
