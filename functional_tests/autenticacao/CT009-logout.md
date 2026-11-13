# CT009 — Encerrar a sessão (logout)

**Autor:** Vitor Igor  
**Requisito relacionado:** RF02033 — Encerrar a sessão (logout)  
**Ator:** Usuário autenticado

## Objetivo

Verificar se o usuário consegue encerrar a sessão ativa, se o token utilizado é invalidado e se o usuário é encaminhado à tela de login.

## Pré-condições

- O usuário está autenticado no BVApp.
- Existe uma sessão ativa e um token de autenticação válido.

## [FP] — FLUXO PRINCIPAL

1. O usuário aciona a opção **Sair**.
2. O sistema encerra a sessão ativa.
3. O sistema invalida o token de autenticação utilizado, impedindo sua reutilização. [RN1]
4. O sistema encaminha o usuário à tela de login.

## [FA01] — TENTATIVA DE REUTILIZAR O TOKEN INVALIDADO

1. Após o logout, o usuário ou cliente tenta realizar uma operação autenticada reutilizando o token anterior.
2. O sistema rejeita a requisição por se tratar de token invalidado.
3. O acesso a recursos protegidos não é concedido.

## [RN] — REGRAS DE NEGÓCIO

- **RN1:** O logout deve encerrar a sessão ativa e invalidar o token utilizado, impedindo sua reutilização.
- **RN2:** Após o encerramento, o usuário deve ser encaminhado à tela de login.

## Dados e resultados esperados

| Dados de entrada | Resultado esperado |
|---|---|
| Usuário autenticado seleciona Sair. | Sessão encerrada, token invalidado e usuário encaminhado à tela de login. |
| Token utilizado antes do logout. | Requisições posteriores com esse token são rejeitadas. |
