# Validação do Ambiente

## Visão geral

Após a implantação do Windows Server 2025, Active Directory, DNS, compartilhamentos SMB, permissões e GPOs, foram realizados testes para validar o funcionamento do ambiente.

Os testes foram realizados utilizando as contas de usuários criadas no domínio e uma estação Windows 10 Pro ingressada no domínio `clickti.local`.

## Validação do domínio

A estação Windows 10 foi ingressada com sucesso no domínio:

```text
clickti.local
```

Foi realizado login utilizando contas do domínio, confirmando o funcionamento da autenticação centralizada.

## Validação do DNS

A resolução de nomes foi testada utilizando o servidor DNS do laboratório.

Exemplo:

```text
nslookup clickti.local
```

Também foi validada a resolução do nome do Domain Controller.

```text
nslookup win-03g9i8nug4b.clickti.local
```

Os testes confirmaram que a estação consegue resolver os nomes utilizados pelo domínio.

## Validação das GPOs

As políticas de grupo foram verificadas utilizando:

```text
gpresult /r
```

O comando foi utilizado para identificar as GPOs aplicadas ao usuário.

Foram validadas as seguintes políticas:

- `Mapeamento TI`
- `Mapeamento Financeiro`
- `Mapeamento Administrativo`
- `Mapeamento Diretoria`

## Validação do mapeamento de unidades

Após o login dos usuários, as unidades de rede foram verificadas no Explorador de Arquivos.

| Usuário | Unidades esperadas |
|---|---|
| Sabrina | T: |
| Maria | F: |
| Jose | A: |
| Joao | A:, F:, T:, G: |

A unidade `G:` foi utilizada para o compartilhamento da Diretoria porque `D:` estava ocupada pela unidade de CD/DVD da máquina virtual.

## Validação das permissões

Foram realizados testes de acesso aos compartilhamentos utilizando cada usuário.

### Sabrina

Usuária do grupo TI.

Resultado:

```text
TI → Acesso permitido
Demais departamentos → Acesso negado
```

### Maria

Usuária do grupo Financeiro.

Resultado:

```text
Financeiro → Acesso permitido
Demais departamentos → Acesso negado
```

### Jose

Usuário do grupo Administrativo.

Resultado:

```text
Administrativo → Acesso permitido
Demais departamentos → Acesso negado
```

### Joao

Usuário do grupo Diretoria.

Resultado:

```text
TI → Acesso permitido
Financeiro → Acesso permitido
Administrativo → Acesso permitido
Diretoria → Acesso permitido
```

## Teste de segurança

Os testes confirmaram que os usuários não conseguem acessar os compartilhamentos para os quais não possuem autorização.

O controle é realizado através da combinação de:

- Active Directory
- Grupos de segurança
- Permissões NTFS
- Permissões de compartilhamento SMB
- GPOs

## Resultado geral

O ambiente foi validado com sucesso.

Os principais componentes da infraestrutura estão funcionando conforme planejado:

- [x] Windows Server 2025
- [x] Active Directory
- [x] DNS
- [x] Windows 10 ingressado no domínio
- [x] Usuários e grupos
- [x] Compartilhamentos SMB
- [x] Permissões de acesso
- [x] GPOs
- [x] Mapeamento automático de unidades
- [x] Autenticação de usuários
- [x] Testes de acesso

## Conclusão

A validação demonstrou o funcionamento integrado dos principais serviços de uma infraestrutura Windows corporativa.

O laboratório reproduz um cenário de pequena empresa, permitindo praticar administração de domínio, gerenciamento de usuários, controle de acesso, compartilhamento de arquivos e aplicação de políticas centralizadas.

Este ambiente servirá como base para futuras implementações e melhorias no laboratório.
