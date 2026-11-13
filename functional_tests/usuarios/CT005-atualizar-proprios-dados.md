# CT005 — Atualizar os próprios dados cadastrais

**Autor:** Vitor Igor  
**Requisito relacionado:** RF02027 — Atualizar os próprios dados cadastrais  
**Ator:** Usuário autenticado

## Objetivo

Verificar se o usuário consegue atualizar o nome e o e-mail da própria conta e, quando ainda não possui associação com cooperado, vincular-se opcionalmente a um cooperado por meio de CPF, sem substituir uma associação existente.

## Pré-condições

- O usuário está autenticado no BVApp.
- A conta ainda não possui associação com cooperado para o fluxo principal.
- Existe um cooperado ativo, ainda não associado a outra conta, disponível para o teste de CPF.
- O e-mail utilizado na atualização não está associado a outra conta.

## [FP] — FLUXO PRINCIPAL

1. O usuário acessa a área de atualização dos próprios dados cadastrais.
2. O sistema apresenta os dados atuais de nome e e-mail e a opção de informar CPF quando ainda não existe associação com cooperado.
3. O usuário altera o nome e informa um novo e-mail válido.
4. O usuário informa o CPF de um cooperado existente e disponível para associação.
5. O usuário confirma a atualização.
6. O sistema verifica que nome e e-mail estão preenchidos, que o e-mail não pertence a outra conta e que o CPF corresponde a um cooperado disponível. [RN1][RN2]
7. O sistema atualiza os dados e associa a conta ao cooperado localizado.
8. O sistema apresenta uma mensagem de sucesso.
9. O usuário consulta novamente os próprios dados e verifica a atualização.

## [FA01] — ATUALIZAÇÃO SEM INFORMAR CPF

1. O usuário altera nome e e-mail válidos e deixa o CPF sem preenchimento.
2. O sistema atualiza os dados cadastrais, mantendo a conta sem associação com cooperado.
3. O sistema apresenta uma confirmação de sucesso.

## [FA02] — E-MAIL DUPLICADO OU CAMPO OBRIGATÓRIO VAZIO

1. O usuário tenta salvar a atualização com nome ou e-mail vazio, ou informa um e-mail já associado a outra conta.
2. O sistema recusa a atualização e informa o motivo.
3. Os dados anteriores da conta são preservados. [RN3]

## [FA03] — CPF INVÁLIDO OU COOPERADO INDISPONÍVEL

1. O usuário informa um CPF que não corresponde a um cooperado cadastrado ou que corresponde a um cooperado já associado a outra conta.
2. O usuário confirma a atualização.
3. O sistema recusa a associação e informa o problema.
4. Os dados e vínculos anteriores permanecem preservados. [RN3]

## [FA04] — CONTA JÁ ASSOCIADA A UM COOPERADO

1. O usuário que já possui associação com cooperado acessa a atualização dos próprios dados.
2. O usuário tenta informar outro CPF para substituir o vínculo existente.
3. O sistema não permite substituir a associação por esse fluxo.
4. O vínculo anterior permanece inalterado. [RN4]

## [RN] — REGRAS DE NEGÓCIO

- **RN1:** Nome e e-mail devem permanecer preenchidos.
- **RN2:** O e-mail deve ser único. O CPF é opcional apenas quando a conta ainda não possui associação com cooperado; quando informado, deve corresponder a um cooperado existente e disponível.
- **RN3:** Em caso de erro, os dados anteriores devem ser preservados.
- **RN4:** Uma associação existente com cooperado não pode ser substituída por meio da atualização dos próprios dados.

## Dados e resultados esperados

| Dados de entrada | Resultado esperado |
|---|---|
| Nome e e-mail válidos; CPF de cooperado disponível. | Dados atualizados e conta associada ao cooperado. |
| Nome e e-mail válidos; CPF não informado. | Dados atualizados sem criar associação. |
| Nome ou e-mail vazio, ou e-mail de outra conta. | Atualização recusada; dados anteriores preservados. |
| CPF inexistente ou associado a outra conta. | Associação recusada; dados anteriores preservados. |
| Conta já vinculada e tentativa de informar outro CPF. | Substituição do vínculo não permitida. |
