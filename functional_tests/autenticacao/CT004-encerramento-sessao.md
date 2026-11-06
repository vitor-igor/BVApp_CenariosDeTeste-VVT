# CT004 — Encerramento da sessão

**Autor:** Vitor Igor

## Objetivo

Verificar se o usuário consegue encerrar sua sessão ativa, que deve ser invalidada, e se é redirecionado à tela de login.

## Requisitos relacionados

- **Feature 23520 — Logout**
- **US 23599 — Encerrar sessão do sistema**
- **CA 23596 — Permitir encerrar a sessão ativa**
- **CA 23597 — Invalidar a sessão após o logout**
- **CA 23598 — Redirecionar para a tela de login**

## Ator

Usuário autenticado com sessão ativa.

## Pré-condições

- O usuário está autenticado no BVApp.
- Há uma sessão ativa para o usuário.

## Fluxo principal

1. O usuário clica no botão **Sair**.
2. O sistema encerra a sessão do usuário e invalida a sessão atual.
3. O sistema redireciona o usuário para a tela de login.

## Fluxos alternativos

A US não especifica fluxos alternativos para o encerramento da sessão.

## Regras de negócio

> Após o logout, a sessão ativa deve ser invalidada e o usuário deve ser redirecionado à tela de login.

## Dados de entrada e resultados esperados

| Dados de entrada | Resultado esperado |
|---|---|
| Usuário autenticado com sessão ativa; ação **Sair**. | Sessão encerrada e invalidada; tela de login apresentada ao usuário. |
