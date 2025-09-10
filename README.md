# 🚀 Projeto MultiCloud – VPN Site-to-Site (Azure ↔ AWS)

Este projeto demonstra a configuração de uma **VPN Site-to-Site** entre a **Microsoft Azure** e a **Amazon Web Services (AWS)**, permitindo comunicação segura entre redes virtuais em diferentes provedores de nuvem.  

---

## 📖 Visão Geral
O objetivo é interligar duas redes em provedores diferentes, utilizando **IPSec/IKEv2** para criar um túnel seguro, garantindo que instâncias em ambas as nuvens se comuniquem como se estivessem em uma mesma rede.

---

## 🏗️ Arquitetura

### ☁️ Azure
- **Resource Group:** `RG-MULTICLOUD`  
- **Virtual Network:** `VNET-MULTICLOUD` (172.16.0.0/16)  
- **Subnets:**  
  - `SUBNET-1` → 172.16.1.0/24  
  - `GatewaySubnet` → 172.16.0.0/24  
- **Virtual Network Gateway:** `VpnGw1` (Generation 1, IP Público gerado)  

### ☁️ AWS
- **VPC:** `vpc-multicloud` (192.168.0.0/16)  
- **Subnet:** `subnet-1` (192.168.0.0/24)  
- **Internet Gateway** (associado à VPC)  
- **Route Table** (com rotas configuradas)  
- **Customer Gateway:** (IP público do Azure Gateway)  
- **Virtual Private Gateway**  
- **VPN Connection:** (IKEv2, roteamento estático)  

---

## 🔑 Passos de Configuração

### 🔹 Azure
1. Criar **Resource Group**  
2. Criar **VNET + Subnets**  
3. Criar **Virtual Network Gateway**  
4. Criar **Local Network Gateway** (com IP do túnel AWS)  
5. Criar **Connection** (Site-to-Site IPsec com PSK da AWS)  

### 🔹 AWS
1. Criar **VPC + Subnet**  
2. Criar **Internet Gateway**  
3. Criar **Route Table + Rotas**  
4. Criar **Customer Gateway** (IP do Azure)  
5. Criar **Virtual Private Gateway**  
6. Criar **VPN Connection** (estática, rede Azure)  
7. Baixar **arquivo de configuração** e aplicar no Azure  

---

## 🔐 Regras de Segurança

### ✅ AWS Security Group
- Outbound: liberar tráfego para qualquer rede + rede Azure  
- Inbound: liberar tráfego vindo da rede Azure + SSH  

### ✅ Azure Security Group
- Outbound: liberar tráfego para rede AWS  
- Inbound: liberar tráfego vindo da rede AWS + RDP (instâncias Windows)  

---

## 🧪 Validação
- Criar instâncias em ambos os lados  
- Testar **ping, SSH, RDP** entre as redes  
- Validar que os **túneis VPN estão ativos e estáveis**  

---

## 🛠️ Tecnologias Utilizadas
- Microsoft **Azure**  
- Amazon **AWS**  
- **VPN Site-to-Site (IPSec/IKEv2)**  
- **Security Groups & Route Tables**  

---

## 👤 Autor
Projeto desenvolvido por **Victor Djalma**  
