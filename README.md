# BVApp — Cenários de Teste

## Apresentação

Este repositório individual organiza a documentação dos cenários de teste funcionais do módulo **Gestão de Entidades** do BVApp, elaborados para a atividade de Engenharia de Testes.

## Objetivo

Documentar comportamentos funcionais que poderão ser aproveitados em etapas futuras de revisão, verificação, implementação e automação. Esta entrega não implementa nem executa essas verificações.

## Catálogo de cenários

| ID | Cenário | Requisito relacionado | Pasta |
|---|---|---|---|
| CT001 | Gerenciar usuários (CRUD) | RF02025 | `functional_tests/usuarios/` |
| CT002 | Gerenciar perfis de acesso (CRUD) | RF02013 | `functional_tests/perfis/` |
| CT003 | Definir funcionalidades disponíveis por perfil | RF02014 | `functional_tests/perfis/` |
| CT004 | Gerenciar perfis associados a uma conta | RF02026 | `functional_tests/usuarios/` |
| CT005 | Atualizar os próprios dados cadastrais | RF02027 | `functional_tests/usuarios/` |
| CT006 | Alterar a própria senha | RF02028 | `functional_tests/usuarios/` |
| CT007 | Realizar login | RF02031 | `functional_tests/autenticacao/` |
| CT008 | Alterar o perfil ativo durante a sessão | RF02032 | `functional_tests/autenticacao/` |
| CT009 | Encerrar a sessão (logout) | RF02033 | `functional_tests/autenticacao/` |
| CT010 | Visualizar o próprio painel de usuário | RF02029 | `functional_tests/paineis/` |

## Estrutura de diretórios

```text
BVApp_CenariosDeTeste-VVT/
├── README.md
├── functional_tests/
│   ├── README.md
│   ├── perfis/
│   │   ├── CT002-gestao-perfis.md
│   │   └── CT003-definir-funcionalidades-perfil.md
│   ├── usuarios/
│   │   ├── CT001-gestao-usuarios.md
│   │   ├── CT004-perfis-associados-conta.md
│   │   ├── CT005-atualizar-proprios-dados.md
│   │   └── CT006-alterar-propria-senha.md
│   ├── autenticacao/
│   │   ├── CT007-login.md
│   │   ├── CT008-alteracao-perfil-ativo.md
│   │   └── CT009-logout.md
│   └── paineis/
│       ├── CT010-painel-usuario.md
└── docs/
    ├── mapeamento-versao-anterior.md
    └── pontos-de-atencao.md
```

## Organização dos cenários

Cada arquivo apresenta identificador e título, objetivo, requisito relacionado, ator, pré-condições, fluxo principal, fluxos alternativos, regras de negócio, dados e resultados esperados e autoria.

Nos cenários CRUD, as quatro operações são descritas em um mesmo fluxo, sem dividir cadastro, consulta, atualização e exclusão em cenários separados. Quando o requisito não define um comportamento, a documentação registra o ponto para esclarecimento em vez de inventar uma regra.

## Autoria

**Autor:** Vitor Igor  
**Curso:** Engenharia de Software  
**Instituição:** IFPB — Campus João Pessoa
