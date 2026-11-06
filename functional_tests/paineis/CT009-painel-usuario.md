# CT009 — Visualização do painel do usuário conforme o perfil ativo

**Autor:** Vitor Igor

## Objetivo

Verificar se o painel do usuário apresenta informações correspondentes ao perfil ativo e não exibe segredos de autenticação.

## Requisitos relacionados

- **Feature 25891 — Visualização dos dados próprios do Usuário**
- **US 26973 — Painel do Usuário básico**
- **CA 35363 — Visualização dos dados próprios do Usuário**
- **CA 35364 — Permitir que o usuário autenticado consulte as informações relacionadas à própria conta**
- **CA 35365 — Apresentar as informações correspondentes ao perfil ativo, respeitando os dados disponíveis para esse perfil**
- **CA 35366 — Permitir a visualização dos dados cadastrais do cooperado, de seu cargo e das usinas e unidades consumidoras associadas**
- **CA 35367 — Não exibir a senha, o hash da senha ou outros segredos de autenticação do usuário**

## Ator

Usuário autenticado no BVApp.

## Pré-condições

- O usuário está autenticado e possui um perfil ativo.
- Para o fluxo COOPERADO, o usuário está associado a um cooperado com dados cadastrais e vínculos disponíveis.
- Para o fluxo administrativo, a conta possui nome, e-mail e perfis vinculados.

## Fluxo principal — Perfil ativo COOPERADO

1. O usuário acessa o Painel do Usuário.
2. O sistema apresenta os dados pessoais, de contato e endereço.
3. O sistema apresenta o cargo, as usinas e as unidades consumidoras associadas ao cooperado.
4. O usuário verifica que não são exibidos senha, hash de senha ou outros segredos de autenticação.

## Fluxos alternativos

### FA01 — Perfil ativo administrativo

1. O usuário autenticado com perfil administrativo ativo acessa o Painel do Usuário.
2. O sistema apresenta nome, e-mail e perfis vinculados.
3. O usuário verifica que não são exibidos senha, hash de senha ou outros segredos de autenticação.

## Regras de negócio

> O painel apresenta informações correspondentes ao perfil ativo e respeita os dados disponíveis para esse perfil. Não deve exibir senha, hash de senha ou outros segredos de autenticação.

## Dados de entrada e resultados esperados

| Dados de entrada | Resultado esperado |
|---|---|
| Conta autenticada com perfil ativo COOPERADO e dados/vínculos associados. | Painel apresenta dados pessoais, de contato e endereço, cargo, usinas e unidades consumidoras associados. |
| Conta autenticada com perfil ativo administrativo e nome, e-mail e perfis vinculados. | Painel apresenta nome, e-mail e perfis vinculados. |
| Em ambos os fluxos. | Nenhum segredo de autenticação é exibido. |

## Dúvida para esclarecimento

- A US descreve as informações para COOPERADO e para perfil administrativo, mas não enumera nominalmente todos os perfis administrativos. Confirmar a classificação caso existam outros tipos de perfil.
