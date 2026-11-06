# CT002 — Bloqueio de login de usuário inativo

**Autor:** Vitor Igor

## Objetivo

Verificar que uma conta inativa não consegue autenticar-se, mesmo com credenciais válidas.

## Requisitos relacionados

- **Feature 23519 — Autenticação (Login)**
- **US 23595 — Login de usuário inativo**
- **CA 23592 — Impedir acesso de usuários com status inativo**

## Ator

Usuário com conta cadastrada e status inativo.

## Pré-condições

- Existe uma conta cadastrada com status inativo.
- O usuário conhece o e-mail e a senha válidos dessa conta.

## Fluxo principal

1. O usuário acessa a tela de login.
2. Informa o e-mail e a senha válidos da conta inativa.
3. Pressiona **Entrar**.
4. O sistema impede o acesso e exibe: **“Usuário inativo. Entre em contato com o administrador.”**

## Fluxos alternativos

A US não especifica fluxos alternativos próprios para esta condição. A tentativa com credenciais incorretas é tratada como alternativa da autenticação no CT001.

## Regras de negócio

> Usuários com status inativo não podem acessar o sistema. Inativação não significa exclusão da conta.

## Dados de entrada e resultados esperados

| Dados de entrada | Resultado esperado |
|---|---|
| E-mail e senha válidos de uma conta inativa. | A autenticação não é concluída, o acesso não é permitido e a mensagem especificada na US é exibida. |
