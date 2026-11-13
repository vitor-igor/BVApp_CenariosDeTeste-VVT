# CT010 — Visualizar o próprio painel de usuário

**Autor:** Vitor Igor  
**Requisito relacionado:** RF02029 — Visualizar o próprio painel de usuário  
**Ator:** Usuário autenticado

## Objetivo

Verificar se o painel apresenta a identificação do usuário autenticado, o cabeçalho e a barra lateral geral, além das informações correspondentes ao perfil ativo e à existência de associação com cooperado.

## Pré-condições

- O usuário está autenticado no BVApp.
- Para o fluxo de Cooperado, a conta possui o perfil Cooperado ativo e está associada a um registro de cooperado com dados relacionados cadastrados.
- Para o fluxo administrativo, a conta utiliza um perfil administrativo.

## [FP] — FLUXO PRINCIPAL: PERFIL COOPERADO

1. O usuário acessa o painel da própria conta com o perfil Cooperado ativo.
2. O sistema identifica o usuário autenticado e apresenta o cabeçalho e a barra lateral geral.
3. O sistema verifica que a conta está associada a um registro de cooperado.
4. O sistema apresenta os dados pessoais, de contato e endereço do cooperado, seu cargo e as usinas e unidades consumidoras associadas. [RN1]
5. O usuário confere se as informações apresentadas correspondem ao cooperado associado à sua conta.

## [FA01] — PERFIL ADMINISTRATIVO

1. Um usuário autenticado acessa o próprio painel utilizando um perfil administrativo.
2. O sistema apresenta a identificação do usuário, o cabeçalho e a barra lateral geral.
3. O sistema apresenta nome, e-mail e perfis vinculados à conta, conforme previsto para os perfis administrativos. [RN2]
4. O usuário confere se os dados apresentados correspondem à própria conta.

## [FA02] — PERFIL COOPERADO SEM ASSOCIAÇÃO

1. Um usuário autenticado utiliza o perfil Cooperado, mas sua conta não possui associação com um registro de cooperado.
2. O usuário acessa o painel.
3. O requisito condiciona a exibição dos dados do cooperado à existência de associação, mas não define qual conteúdo ou mensagem deve ser apresentado na ausência dela.
4. A condição deve ser registrada para esclarecimento, sem presumir dados de outro cooperado ou uma mensagem específica.

## [RN] — REGRAS DE NEGÓCIO

- **RN1:** Quando o perfil ativo for Cooperado e houver associação com um registro de cooperado, o painel deve apresentar os dados pessoais, de contato e endereço desse cooperado, seu cargo e as usinas e unidades consumidoras associadas.
- **RN2:** Para perfis administrativos, o painel deve apresentar nome, e-mail e perfis vinculados à conta.
- **RN3:** O painel deve identificar o usuário autenticado e apresentar o cabeçalho e a barra lateral geral.

## Dados e resultados esperados

| Dados de entrada | Resultado esperado |
|---|---|
| Conta autenticada com perfil Cooperado ativo e cooperado associado. | São exibidos dados pessoais, contato, endereço, cargo, usinas e unidades consumidoras do cooperado associado. |
| Conta autenticada com perfil administrativo. | São exibidos nome, e-mail e perfis vinculados, além da identificação, cabeçalho e barra lateral. |
| Perfil Cooperado sem cooperado associado. | Comportamento não especificado; registrar dúvida sem presumir uma resposta. |
