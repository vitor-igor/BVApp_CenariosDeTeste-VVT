# CT007 — Atalhos de definição de permissões para perfil

**Autor:** Vitor Igor

## Objetivo

Verificar se os atalhos de selecionar todas as permissões e limpar a seleção atualizam a seleção do formulário sem persistir alterações antes da confirmação do salvamento.

## Requisitos relacionados

- **Feature 23552 — Definição de Permissões (Roles) do Perfil**
- **US 29269 — Atalhos de definição de permissões para Perfil**
- **CA 33900 — Atalhos para limpar associações e selecionar todas as permissões**
- **CA 33901 — Permissão PERFIL_EDITAR para definir ou alterar permissões**

## Ator

Usuário autenticado com a permissão `PERFIL_EDITAR`.

## Pré-condições

- O usuário está autenticado e possui a permissão `PERFIL_EDITAR`.
- Existe um perfil cuja definição de permissões pode ser editada.
- O perfil possui permissões associadas e há permissões ativas disponíveis.

## Fluxo principal

1. O usuário acessa a tela de definição de permissões de um perfil.
2. Aciona o atalho para selecionar todas as permissões disponíveis.
3. O sistema atualiza a seleção do formulário conforme a ação indicada pelo atalho.
4. O usuário aciona o atalho para limpar a seleção.
5. O sistema limpa a seleção apresentada no formulário.
6. O usuário encerra a interação sem confirmar o salvamento.
7. O usuário verifica que as associações persistidas anteriormente não foram alteradas.

## Fluxos alternativos

A US não especifica mensagens de feedback para cada atalho; nenhum texto de mensagem é presumido.

## Regras de negócio

> Os atalhos atualizam a seleção do formulário. As alterações não são persistidas até que o usuário confirme o salvamento. Definir ou alterar permissões requer `PERFIL_EDITAR`.
>
> Conforme a regra da Feature 23552 registrada na documentação anterior, somente permissões ativas podem ser associadas ao perfil.

## Dados de entrada e resultados esperados

| Dados de entrada | Resultado esperado |
|---|---|
| Perfil existente com permissões associadas; permissões ativas disponíveis; usuário autenticado com `PERFIL_EDITAR`. | Selecionar todas atualiza a seleção do formulário; limpar remove a seleção apresentada; sem confirmação, as associações persistidas permanecem inalteradas. |
