# CT007 — Realizar login

**Autor:** Vitor Igor  
**Requisito relacionado:** RF02031 — Realizar login  
**Ator:** Usuário

## Objetivo

Verificar se um usuário consegue autenticar-se com e-mail, senha e perfil ativo associado à conta e se o sistema impede o acesso quando as credenciais, a situação da conta ou o perfil selecionado não atendem às condições definidas.

## Pré-condições

- Existe uma conta cadastrada e ativa com credenciais válidas.
- A conta possui pelo menos um perfil ativo associado.
- O perfil utilizado no fluxo principal possui funcionalidades configuradas.

## [FP] — FLUXO PRINCIPAL

1. O usuário acessa a tela de login.
2. O sistema apresenta os campos de e-mail, senha e seleção de perfil.
3. O usuário informa o e-mail e a senha válidos e seleciona um perfil ativo associado à conta.
4. O usuário confirma o login.
5. O sistema verifica a correspondência das credenciais, o status ativo da conta, a associação do perfil selecionado e o status ativo do perfil. [RN1][RN2]
6. O sistema autentica o usuário, disponibiliza somente as funcionalidades configuradas para o perfil selecionado e encaminha o usuário à tela inicial. [RN3]

## [FA01] — E-MAIL OU SENHA INCORRETOS

1. O usuário informa um e-mail inexistente ou uma senha que não corresponde à conta.
2. O usuário confirma o login.
3. O sistema impede a autenticação e apresenta uma mensagem adequada, sem disponibilizar o acesso ao sistema.

## [FA02] — CONTA INATIVA

1. O usuário informa credenciais válidas de uma conta com status Inativo e seleciona um perfil associado.
2. O usuário confirma o login.
3. O sistema impede a autenticação e informa que a conta não pode acessar o sistema enquanto estiver inativa. [RN1]

## [FA03] — PERFIL INATIVO OU NÃO ASSOCIADO

1. O usuário informa credenciais válidas, mas seleciona um perfil que está Inativo ou que não está associado à conta.
2. O usuário confirma o login.
3. O sistema impede a autenticação com o perfil selecionado e apresenta uma mensagem adequada. [RN2]

## [RN] — REGRAS DE NEGÓCIO

- **RN1:** O e-mail e a senha devem corresponder a uma conta cadastrada e ativa.
- **RN2:** O perfil selecionado deve estar associado à conta e permanecer ativo.
- **RN3:** Após a autenticação, somente as funcionalidades configuradas para o perfil escolhido devem ser disponibilizadas.

## Dados e resultados esperados

| Dados de entrada | Resultado esperado |
|---|---|
| E-mail e senha válidos; conta ativa; perfil ativo e associado. | Autenticação concluída, funcionalidades do perfil disponibilizadas e redirecionamento à tela inicial. |
| E-mail inexistente ou senha incorreta. | Acesso negado. |
| Conta inativa. | Acesso negado, mesmo com credenciais corretas. |
| Perfil inativo ou não associado à conta. | Acesso negado com o perfil selecionado. |
