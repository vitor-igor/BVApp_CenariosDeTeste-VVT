# CT006 — Alterar a própria senha

**Autor:** Vitor Igor  
**Requisito relacionado:** RF02028 — Alterar a própria senha  
**Ator:** Usuário autenticado

## Objetivo

Verificar se o usuário consegue alterar a senha da própria conta mediante informação da senha atual, definição de uma nova senha que atenda aos requisitos de complexidade e confirmação idêntica.

## Pré-condições

- O usuário está autenticado no BVApp.
- O usuário conhece a senha atual da conta.
- A conta está ativa.

## [FP] — FLUXO PRINCIPAL

1. O usuário acessa a opção de alteração de senha.
2. O sistema apresenta os campos Senha Atual, Nova Senha e Confirmação da Nova Senha.
3. O usuário informa a senha atual correta.
4. O usuário informa uma nova senha com pelo menos 8 caracteres, contendo letras, números e caracteres especiais.
5. O usuário repete a nova senha no campo de confirmação.
6. O usuário confirma a alteração.
7. O sistema valida a senha atual, a complexidade da nova senha e a igualdade entre a nova senha e sua confirmação. [RN1][RN2]
8. O sistema atualiza a senha e apresenta uma mensagem de sucesso.

## [FA01] — SENHA ATUAL INCORRETA

1. O usuário informa uma senha atual diferente da cadastrada.
2. Preenche a nova senha e sua confirmação com valores válidos e iguais.
3. Confirma a operação.
4. O sistema recusa a alteração, informa que a senha atual está incorreta e mantém a senha cadastrada anteriormente. [RN3]

## [FA02] — NOVA SENHA FORA DA COMPLEXIDADE

1. O usuário informa a senha atual correta.
2. Informa uma nova senha com menos de 8 caracteres ou sem letras, números ou caracteres especiais.
3. Repete o valor no campo de confirmação e confirma a operação.
4. O sistema recusa a alteração, informa o problema e mantém a senha anterior. [RN1][RN3]

## [FA03] — CONFIRMAÇÃO DIFERENTE DA NOVA SENHA

1. O usuário informa a senha atual correta e uma nova senha válida.
2. Informa no campo de confirmação um valor diferente da nova senha.
3. Confirma a operação.
4. O sistema recusa a alteração e mantém a senha anterior. [RN2][RN3]

## [RN] — REGRAS DE NEGÓCIO

- **RN1:** A nova senha deve possuir no mínimo 8 caracteres e incluir letras, números e caracteres especiais.
- **RN2:** A confirmação deve ser idêntica à nova senha.
- **RN3:** A senha atual deve corresponder à senha cadastrada; quando qualquer validação falhar, a senha não deve ser alterada e o sistema deve informar o motivo.

## Dados e resultados esperados

| Dados de entrada | Resultado esperado |
|---|---|
| Senha atual correta; nova senha `NovaSenha@123`; confirmação idêntica. | Senha alterada e mensagem de sucesso. |
| Senha atual incorreta. | Alteração recusada; senha anterior preservada. |
| Nova senha com menos de 8 caracteres ou sem uma categoria exigida. | Alteração recusada; senha anterior preservada. |
| Confirmação diferente da nova senha. | Alteração recusada; senha anterior preservada. |
