# BVApp — Cenários de Teste

## Apresentação

Este repositório individual organiza a documentação dos cenários de teste funcionais do módulo **Gestão de Pessoas e Controle de Acesso** do BVApp. O material foi preparado para a atividade de Engenharia de Testes.

## Objetivo

Documentar comportamentos funcionais que poderão ser aproveitados em etapas futuras de revisão, verificação, implementação e automação. Esta entrega não implementa nem executa essas verificações.

## Escopo

O mini projeto preserva os dez cenários selecionados, cobrindo:

- autenticação com credenciais válidas e bloqueio de usuário inativo;
- encerramento de sessão e alteração de senha;
- troca de perfil ativo e disponibilização de funcionalidades por perfil;
- atalhos para seleção de permissões;
- expansão e recolhimento da barra lateral;
- painel do usuário por perfil e indicadores da página Overview.

A Feature **Central de Notificações** não faz parte do escopo. Os cenários não são operações CRUD.

## Tecnologias e organização

A pasta `functional_tests/` reúne a documentação dos testes funcionais, seguindo a separação conceitual apresentada no exemplo do professor. A referência utiliza Django; aqui aproveitamos somente a ideia de organização, sem reproduzir arquivos específicos desse framework. A estrutura é compatível com o contexto do BVApp em Flask, mas este repositório contém exclusivamente documentação em Markdown e **não é uma aplicação Flask executável**. Não há implementação, interfaces, scripts ou automação nesta etapa. Os cenários poderão ser aproveitados em etapas futuras de implementação e automação.

## Catálogo de cenários

| ID | Nome do cenário | Funcionalidade | Requisito relacionado | Documento |
|---|---|---|---|---|
| CT001 | Autenticação com credenciais válidas | Autenticação | US 23593 — Realizar login no sistema | [CT001](functional_tests/autenticacao/CT001-autenticacao-credenciais-validas.md) |
| CT002 | Bloqueio de login de usuário inativo | Autenticação | US 23595 — Login de usuário inativo | [CT002](functional_tests/autenticacao/CT002-login-usuario-inativo.md) |
| CT003 | Alteração do perfil ativo durante a sessão | Controle de acesso | US 28720 — Atualizar alteração de perfil ativo durante a sessão; relacionada: US 23604 — Alterar perfil ativo durante a sessão | [CT003](functional_tests/controle_acesso/CT003-alteracao-perfil-ativo.md) |
| CT004 | Encerramento da sessão | Autenticação e sessão | US 23599 — Encerrar sessão do sistema | [CT004](functional_tests/autenticacao/CT004-encerramento-sessao.md) |
| CT005 | Alteração de senha do usuário | Autenticação e credenciais | US 25515 — Alterar senha do usuário | [CT005](functional_tests/autenticacao/CT005-alteracao-senha.md) |
| CT006 | Disponibilização de funcionalidades conforme o perfil ativo | Controle de acesso | CA 23601 — Apresentar apenas funcionalidades autorizadas para o perfil ativo; associada à US 23593 | [CT006](functional_tests/controle_acesso/CT006-funcionalidades-por-perfil.md) |
| CT007 | Atalhos de definição de permissões para perfil | Controle de acesso | US 29269 — Atalhos de definição de permissões para Perfil | [CT007](functional_tests/controle_acesso/CT007-atalhos-permissoes.md) |
| CT008 | Expansão e recolhimento da barra lateral | Interface e navegação | US 29022 — Expandir sidebar geral | [CT008](functional_tests/interface/CT008-expansao-recolhimento-barra-lateral.md) |
| CT009 | Visualização do painel do usuário conforme o perfil ativo | Painéis | US 26973 — Painel do Usuário básico; critérios de aceitação relacionados | [CT009](functional_tests/paineis/CT009-painel-usuario.md) |
| CT010 | Exibição dos indicadores na página Overview | Painéis | US 29672 — Página Overview | [CT010](functional_tests/paineis/CT010-indicadores-overview.md) |

## Estrutura de diretórios

```text
bvapp-cenarios-de-teste/
├── README.md
└── functional_tests/
    ├── README.md
    ├── autenticacao/
    │   ├── CT001-autenticacao-credenciais-validas.md
    │   ├── CT002-login-usuario-inativo.md
    │   ├── CT004-encerramento-sessao.md
    │   └── CT005-alteracao-senha.md
    ├── controle_acesso/
    │   ├── CT003-alteracao-perfil-ativo.md
    │   ├── CT006-funcionalidades-por-perfil.md
    │   └── CT007-atalhos-permissoes.md
    ├── interface/
    │   └── CT008-expansao-recolhimento-barra-lateral.md
    └── paineis/
        ├── CT009-painel-usuario.md
        └── CT010-indicadores-overview.md
```

## Orientações de leitura

Use o catálogo para abrir um cenário. Cada arquivo independente em `functional_tests/` apresenta objetivo, requisitos relacionados, ator, pré-condições, fluxo principal e alternativos, regras de negócio, dados, resultados esperados e pontos a confirmar quando os requisitos deixam dúvidas. O [README de functional_tests](functional_tests/README.md) apresenta a finalidade dessa pasta.

Os documentos descrevem o comportamento requerido; não afirmam que o sistema já o implementa. A fonte de requisitos é a exportação do OpenProject `bvapp_gest_o_de_pessoas_2026-11-05_22-17.pdf`.

## Autoria

Os dez cenários identificam **Vitor Igor** como autor. Curso/Instituição: Engenharia de Software / IFPB.
