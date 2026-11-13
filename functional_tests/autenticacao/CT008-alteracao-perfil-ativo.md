# CT008 — Alterar o perfil ativo durante a sessão

**Autor:** Vitor Igor  
**Requisito relacionado:** RF02032 — Alterar o perfil ativo durante a sessão  
**Ator:** Usuário autenticado com mais de um perfil associado

## Objetivo

Verificar se o usuário autenticado consegue alternar entre perfis ativos associados à própria conta e se o sistema atualiza o contexto e as funcionalidades disponibilizadas após a troca.

## Pré-condições

- O usuário está autenticado no BVApp.
- A conta possui pelo menos dois perfis ativos associados.
- Um dos perfis está selecionado como perfil ativo na sessão.

## [FP] — FLUXO PRINCIPAL

1. O usuário aciona a opção de alteração do perfil ativo.
2. O sistema apresenta os perfis ativos associados à conta.
3. O usuário seleciona outro perfil ativo da lista.
4. O usuário confirma a troca.
5. O sistema atualiza o perfil ativo e as funcionalidades disponíveis de acordo com a configuração do novo perfil. [RN1]
6. O sistema atualiza as informações apresentadas ao usuário e encaminha-o à página inicial do contexto selecionado.
7. O usuário verifica que o novo perfil está ativo e que as funcionalidades exibidas correspondem a esse perfil.

## [FA01] — PERFIL NÃO ASSOCIADO À CONTA

1. O usuário tenta selecionar um perfil que não está associado à sua conta.
2. O sistema recusa a troca e mantém o perfil ativo anteriormente selecionado. [RN2]

## [FA02] — PERFIL INATIVO

1. O usuário tenta selecionar um perfil que está associado à conta, mas possui status Inativo.
2. O sistema recusa a troca e mantém o perfil ativo anteriormente selecionado. [RN1][RN2]

## [RN] — REGRAS DE NEGÓCIO

- **RN1:** A lista de seleção deve apresentar apenas perfis ativos associados à conta; após a troca, as funcionalidades devem corresponder à configuração do novo perfil.
- **RN2:** A troca deve ser recusada quando o perfil escolhido não estiver associado à conta ou estiver inativo.

## Dados e resultados esperados

| Dados de entrada | Resultado esperado |
|---|---|
| Outro perfil ativo associado à conta. | Perfil ativo atualizado; informações e funcionalidades correspondem ao novo contexto; usuário encaminhado à página inicial. |
| Perfil não associado. | Troca recusada; perfil anterior mantido. |
| Perfil inativo. | Troca recusada; perfil anterior mantido. |
