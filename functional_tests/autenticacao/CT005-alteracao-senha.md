# CT005 — Alteração de senha do usuário

**Autor:** Vitor Igor

## Objetivo

Verificar se um usuário autenticado pode alterar a senha informando a senha atual correta, uma nova senha que atenda à complexidade e confirmação idêntica.

## Requisitos relacionados

- **Feature 23524 — Atualização de dados cadastrais de Usuários**
- **CA 25514 — Regras para alteração de senha do usuário**
- **US 25515 — Alterar senha do usuário**

## Ator

Usuário autenticado no BVApp.

## Pré-condições

- O usuário está autenticado e conhece sua senha atual.
- O usuário está na tela de alteração de senha.
- Os requisitos não indicam uma permissão específica além da autenticação.

## Fluxo principal

1. O usuário preenche **Senha Atual** com a senha correta.
2. Preenche **Nova Senha** com valor de pelo menos 8 caracteres, incluindo letras, caracteres especiais e números.
3. Preenche **Confirmação da Nova Senha** com o mesmo valor.
4. Clica em **Salvar**.
5. O sistema valida a senha atual, a complexidade da nova senha e a igualdade entre nova senha e confirmação.
6. O sistema atualiza a senha e exibe **“Senha alterada com sucesso”**.

## Fluxos alternativos

- **FA01 — Senha atual incorreta:** o usuário informa senha atual diferente da cadastrada; a alteração não é permitida.
- **FA02 — Nova senha fora da complexidade:** a nova senha tem menos de 8 caracteres ou não inclui pelo menos um elemento de cada grupo exigido; a alteração não é permitida.
- **FA03 — Confirmação divergente:** a confirmação difere da nova senha; o sistema exibe uma mensagem de erro e não conclui a alteração. O texto da mensagem não está especificado.

## Regras de negócio

> A senha atual deve corresponder à cadastrada. A nova senha deve ter no mínimo 8 caracteres e conter letras, caracteres especiais e números. Nova senha e confirmação devem ser idênticas.

## Dados de entrada e resultados esperados

| Dados de entrada | Resultado esperado |
|---|---|
| Senha atual válida; nova senha de teste com pelo menos 8 caracteres e letras, caracteres especiais e números; confirmação idêntica. | Senha atualizada e mensagem **“Senha alterada com sucesso”** exibida. |
| Senha atual incorreta, nova senha fora dos requisitos ou confirmação divergente. | A alteração não é concluída. Mensagens exatas não são presumidas, exceto a de erro para confirmação divergente, cujo texto não é fornecido. |

> Use credenciais de teste, não uma senha real. A US não especifica o texto de erro para senha atual incorreta ou complexidade inválida.
