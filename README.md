# 🖥️ Laboratório Windows Server 2025 — Active Directory

Laboratório prático de infraestrutura desenvolvido para estudos e simulação de um ambiente corporativo utilizando Windows Server 2025, Active Directory, DNS, Group Policy, compartilhamentos SMB e controle de acesso.

## 🎯 Objetivo

Este projeto tem como objetivo demonstrar, na prática, a implantação e administração de uma infraestrutura de rede baseada em Windows Server, simulando um ambiente empresarial com usuários, departamentos, grupos, compartilhamentos de arquivos e políticas de grupo.

## 🏗️ Tecnologias utilizadas

- Windows Server 2025
- Windows 10 Pro
- Oracle VirtualBox
- Active Directory Domain Services (AD DS)
- DNS
- SMB / File Server
- Group Policy (GPO)
- Rede Host-Only
- NAT

## 🌐 Estrutura do ambiente

O laboratório é composto por um servidor Windows Server 2025 e uma estação cliente Windows 10, utilizando máquinas virtuais no Oracle VirtualBox.

### Servidor

- Sistema: Windows Server 2025
- Função: Domain Controller
- Active Directory
- DNS
- Servidor de arquivos
- IP da rede do laboratório: `192.168.56.10`

### Cliente

- Sistema: Windows 10 Pro
- Função: Estação de trabalho
- IP da rede do laboratório: `192.168.56.20`
- Ingressado no domínio `clickti.local`

## 🏢 Domínio

```text
Domínio: clickti.local
NetBIOS: CLICKTI
