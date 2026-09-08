# Compartilhamentos SMB

## Visão geral

Foi configurado um servidor de arquivos utilizando o Windows Server 2025 e o protocolo SMB (Server Message Block).

Os compartilhamentos foram organizados por departamento, permitindo que os usuários acessem os recursos de acordo com suas permissões no Active Directory.

## Estrutura das pastas

As pastas foram criadas no servidor dentro do diretório:

```text
C:\Compartilhamentos\
```

Estrutura:

```text
C:\Compartilhamentos\
├── TI
├── Financeiro
├── Administrativos
└── Diretoria
```

## Compartilhamentos de rede

Foram criados os seguintes compartilhamentos SMB:

| Compartilhamento | Caminho no servidor | Departamento |
|---|---|---|
| TI | `C:\Compartilhamentos\TI` | TI |
| Financeiro | `C:\Compartilhamentos\Financeiro` | Financeiro |
| Administrativo | `C:\Compartilhamentos\Administrativos` | Administrativo |
| Diretoria | `C:\Compartilhamentos\Diretoria` | Diretoria |

## Acesso aos compartilhamentos

Os usuários acessam os compartilhamentos através do endereço de rede do servidor.

Exemplos:

```text
\\192.168.X.XX\TI
\\192.168.X.XX\Financeiro
\\192.168.X.XX\Administrativo
\\192.168.X.XX\Diretoria
```

## Controle de acesso

O acesso aos compartilhamentos foi configurado utilizando grupos de segurança do Active Directory.

A estrutura permite separar os recursos por departamento.

```text
TI
└── Grupo: TI

Financeiro
└── Grupo: Financeiro

Administrativo
└── Grupo: Administrativo

Diretoria
└── Grupo: Diretoria
```

O grupo **Diretoria** possui acesso aos compartilhamentos dos demais departamentos, conforme a configuração definida para o laboratório.

## Permissões

As permissões de acesso foram configuradas nas pastas do servidor através da interface gráfica do Windows Server.

Foram utilizadas as permissões de segurança do Windows para controlar quais grupos podem acessar cada compartilhamento.

Os usuários foram testados individualmente para validar o controle de acesso.

### Resultado dos testes

| Usuário | TI | Financeiro | Administrativo | Diretoria |
|---|---|---|---|---|
| Sabrina | ✅ | ❌ | ❌ | ❌ |
| Maria | ❌ | ✅ | ❌ | ❌ |
| Jose | ❌ | ❌ | ✅ | ❌ |
| Joao | ✅ | ✅ | ✅ | ✅ |

O usuário da Diretoria possui acesso aos compartilhamentos dos demais departamentos.

Os demais usuários possuem acesso somente aos recursos autorizados para seus respectivos grupos.

## Mapeamento das unidades

As pastas compartilhadas são disponibilizadas aos usuários através de unidades de rede configuradas por GPO.

| Unidade | Compartilhamento | Departamento |
|---|---|---|
| T: | `\\192.168.X.XX\TI` | TI |
| F: | `\\192.168.X.XX\Financeiro` | Financeiro |
| A: | `\\192.168.X.XX\Administrativo` | Administrativo |
| G: | `\\192.168.X.XX\Diretoria` | Diretoria |

A unidade `G:` foi utilizada para o compartilhamento da Diretoria porque a letra `D:` já estava ocupada pela unidade de CD/DVD da máquina virtual.

## GPOs utilizadas

O mapeamento das unidades de rede foi realizado através de políticas de grupo:

```text
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
```

## Testes realizados

- [x] Criação das pastas no servidor
- [x] Criação dos compartilhamentos SMB
- [x] Configuração das permissões
- [x] Associação das permissões aos grupos do Active Directory
- [x] Acesso aos compartilhamentos através da rede
- [x] Teste de acesso com usuário do grupo TI
- [x] Teste de acesso com usuário do grupo Financeiro
- [x] Teste de acesso com usuário do grupo Administrativo
- [x] Teste de acesso com usuário do grupo Diretoria
- [x] Mapeamento automático das unidades através de GPO
- [x] Validação do acesso aos recursos compartilhados

## Resultado

O Windows Server 2025 foi configurado com sucesso como servidor de arquivos utilizando o protocolo SMB.

Os compartilhamentos foram organizados por departamento e o controle de acesso foi realizado através de grupos do Active Directory e permissões do Windows.

As unidades de rede são distribuídas automaticamente através de GPO, permitindo que os usuários tenham acesso aos recursos necessários de acordo com sua função.

O ambiente foi validado através de testes individuais de acesso, confirmando o funcionamento do controle de permissões.
