# Topologia de Rede

## Visão geral

Este laboratório foi desenvolvido utilizando máquinas virtuais no Oracle VirtualBox, simulando uma pequena infraestrutura corporativa.

A rede do laboratório utiliza uma interface **Host-Only** para comunicação entre o servidor e as estações, enquanto o servidor possui uma segunda interface **NAT** para acesso à Internet.

## Endereçamento IP

| Equipamento | Função | IP |
|---|---|---|
| Windows Server 2025 | Domain Controller / DNS / File Server | `192.168.X.XX` |
| Windows 10 Pro | Estação de trabalho | `192.168.X.XX` |

## Rede do laboratório

```text
Rede: 192.168.X.XX
Servidor: 192.168.X.XX
Cliente: 192.168.X.XX
