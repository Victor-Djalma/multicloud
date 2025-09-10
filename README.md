🌐 Projeto MultiCloud – VPN Site-to-Site (Azure ↔ AWS)

Este projeto demonstra a configuração de uma VPN Site-to-Site entre a Microsoft Azure e a Amazon Web Services (AWS), permitindo comunicação segura entre redes virtuais em diferentes provedores de nuvem.

📖 Visão Geral

O objetivo deste projeto é interligar duas redes distintas em provedores diferentes (Azure e AWS), utilizando IPSec/IKEv2 para criar um túnel seguro.

A arquitetura garante que instâncias em ambas as nuvens possam se comunicar como se estivessem em uma mesma rede corporativa.

🏗️ Arquitetura

Azure

Resource Group: RG-MULTICLOUD

Virtual Network: VNET-MULTICLOUD (172.16.0.0/16)

Subnets:

SUBNET-1 (172.16.1.0/24)

GatewaySubnet (172.16.0.0/24)

Virtual Network Gateway (VpnGw1, Generation 1)

AWS

VPC: vpc-multicloud (192.168.0.0/16)

Subnet: subnet-1 (192.168.0.0/24)

Internet Gateway

Route Table configurada

Customer Gateway (IP público do Azure Gateway)

Virtual Private Gateway

VPN Connection (IKEv2, estática)

🔑 Etapas de Configuração
🔹 Azure

Criar Resource Group

Criar VNET e Subnets

Criar Virtual Network Gateway (gerar IP público)

Criar Local Network Gateway apontando para o túnel da AWS

Criar Connection (site-to-site IPsec com PSK fornecida pela AWS)

🔹 AWS

Criar VPC e Subnet

Criar Internet Gateway e associar à VPC

Criar Route Table e configurar rotas

Criar Customer Gateway (IP público do Azure)

Criar Virtual Private Gateway e associar à VPC

Criar VPN Connection (estática, com rede da Azure)

Baixar configuração e aplicar parâmetros no Azure

🔐 Regras de Segurança

AWS Security Group

Outbound: liberar tráfego para qualquer rede e rede Azure

Inbound: liberar tráfego vindo da rede Azure + SSH

Azure Security Group

Outbound: liberar tráfego para rede AWS

Inbound: liberar tráfego vindo da rede AWS + RDP (instâncias Windows)

✅ Validação

Criar instâncias em ambas as nuvens.

Testar conectividade entre redes (ping, SSH, RDP).

Confirmar que os túneis VPN estão ativos e estáveis em ambos os lados.

📌 Tecnologias Utilizadas

Microsoft Azure

Amazon Web Services (AWS)

VPN Site-to-Site (IPSec/IKEv2)

Segurança com Security Groups e Regras de Rota


👤 Autor

Projeto desenvolvido por Victor Djalma 🎯
