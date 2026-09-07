# Compartilhamentos SMB

## Visão geral

Foi configurado um servidor de arquivos utilizando o Windows Server 2025 e o protocolo SMB (Server Message Block).

Os compartilhamentos foram organizados por departamento, permitindo que os usuários acessem os recursos de acordo com suas permissões no Active Directory.

## Estrutura das pastas

As pastas foram criadas no servidor dentro do diretório:

```text

C:\Compartilhamentos\
├── TI
├── Financeiro
├── Administrativos
└── Diretoria
\\192.168.X.XX\TI
\\192.168.X.XX\Financeiro
\\192.168.X.XX\Administrativo
\\192.168.X.XX\Diretoria

TI
└── Grupo: TI

Financeiro
└── Grupo: Financeiro

Administrativo
└── Grupo: Administrativo

Mapeamento TI
        ↓
T: → \\192.168.X.XX\TI

Mapeamento Financeiro
        ↓
F: → \\192.168.X.XX\Financeiro

Mapeamento Administrativo
        ↓
A: → \\192.168.X.XX\Administrativo

Mapeamento Diretoria
        ↓
G: → \\192.168.X.XX\Diretoria

Diretoria
└── Grupo: Diretoria
