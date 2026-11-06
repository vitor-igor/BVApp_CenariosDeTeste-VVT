# CT006 — Disponibilização de funcionalidades conforme o perfil ativo

**Autor:** Vitor Igor

## Objetivo

Verificar quais funcionalidades são apresentadas ao usuário de acordo com as permissões do perfil ativo, sem repetir a autenticação coberta no CT001.

## Requisitos relacionados

- **Feature 23519 — Autenticação (Login)**
- **US 23593 — Realizar login no sistema**
- **CA 23601 — Apresentar apenas funcionalidades autorizadas para o perfil ativo**

## Ator

Usuário autenticado com um perfil ativo.

## Pré-condições

- O usuário está autenticado e possui um perfil ativo.
- O perfil tem permissões associadas conhecidas para a verificação.

## Fluxo principal

1. O usuário consulta a área de navegação e as funcionalidades disponibilizadas.
2. Verifica se são apresentadas as funcionalidades autorizadas para o perfil ativo.
3. Verifica se não são apresentadas funcionalidades não autorizadas para esse perfil.

## Fluxos alternativos

O requisito não detalha mensagens ou telas específicas para esta apresentação.

## Regras de negócio

> A apresentação deve conter somente funcionalidades autorizadas para o perfil ativo, conforme a CA 23601. O requisito não especifica bloqueio de acesso direto a URLs ou endpoints.

## Dados de entrada e resultados esperados

| Dados de entrada | Resultado esperado |
|---|---|
| Usuário autenticado; perfil ativo e conjunto de permissões conhecido. | Funcionalidades autorizadas são apresentadas; funcionalidades não autorizadas não são apresentadas. |
