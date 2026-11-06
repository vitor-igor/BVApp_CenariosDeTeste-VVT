# CT001 — Autenticação com credenciais válidas

**Autor:** Vitor Igor

## Objetivo

Verificar se um usuário com conta ativa consegue autenticar-se usando e-mail, senha e um perfil associado à conta.

## Requisitos relacionados

- **Feature 23519 — Autenticação (Login)**
- **US 23593 — Realizar login no sistema**
- **CA 23590 — Validar correspondência entre e-mail, senha e usuário cadastrado**
- **CA 23591 — Impedir autenticação com credenciais incorretas**
- **CA 23600 — Permitir selecionar o perfil utilizado a partir do login**

## Ator

Usuário do BVApp com conta ativa.

## Pré-condições

- O usuário possui uma conta cadastrada e ativa.
- O usuário possui credenciais válidas.
- Há pelo menos um perfil associado à conta.

## Fluxo principal

1. O usuário acessa o formulário de login.
2. Informa o e-mail e a senha válidos e seleciona um perfil associado à conta.
3. Pressiona **Entrar**.
4. O sistema valida as credenciais e a associação do perfil selecionado.
5. O sistema permite o acesso e redireciona o usuário para a tela inicial.

## Fluxos alternativos

### FA01 — Credenciais incorretas

1. O usuário informa e-mail ou senha que não corresponde a um usuário cadastrado.
2. Pressiona **Entrar**.
3. O sistema impede a autenticação, conforme a CA 23591. A mensagem não é especificada nos requisitos consultados.

## Regras de negócio

> O e-mail e a senha devem corresponder a um usuário cadastrado, e o perfil selecionado deve estar associado à conta.

## Dados de entrada e resultados esperados

| Dados de entrada | Resultado esperado |
|---|---|
| E-mail e senha válidos de uma conta ativa; perfil associado à conta. | A autenticação é permitida e o usuário é redirecionado para a tela inicial. As funcionalidades conforme o perfil selecionado são verificadas no CT006. |
| E-mail ou senha incorretos. | A autenticação é impedida, sem presumir mensagem específica. |

## Dúvida para esclarecimento

- Qual mensagem ou orientação deve ser apresentada quando o usuário tenta selecionar um perfil não associado à conta?
