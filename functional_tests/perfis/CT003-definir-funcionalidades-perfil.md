# CT003 — Definir funcionalidades disponíveis por perfil

**Autor:** Vitor Igor  
**Requisito relacionado:** RF02014 — Definir funcionalidades disponíveis por perfil  
**Ator:** Administrador do sistema

## Objetivo

Verificar se o Administrador consegue configurar as funcionalidades disponíveis para um perfil, substituir integralmente uma configuração anterior e preservar a configuração salva quando ocorrer uma falha.

## Pré-condições

- O Administrador está autenticado no BVApp.
- Existe um perfil de acesso que pode ser configurado.
- Existem funcionalidades cadastradas/disponíveis para seleção.

## [FP] — FLUXO PRINCIPAL

1. O Administrador acessa a configuração de funcionalidades de um perfil existente.
2. O sistema apresenta as funcionalidades existentes no sistema e a seleção atualmente salva para o perfil.
3. O Administrador seleciona as funcionalidades `Funcionalidade A` e `Funcionalidade B`.
4. O Administrador confirma o salvamento.
5. O sistema salva a seleção e apresenta uma confirmação.
6. O Administrador abre novamente a configuração do mesmo perfil.
7. O sistema apresenta `Funcionalidade A` e `Funcionalidade B` como o conjunto habilitado.
8. O Administrador substitui a seleção, removendo `Funcionalidade A` e adicionando `Funcionalidade C`, de modo que a seleção final seja `Funcionalidade B` e `Funcionalidade C`.
9. O Administrador confirma novamente o salvamento.
10. O sistema atualiza a configuração para corresponder exatamente à nova seleção: mantém `Funcionalidade B`, habilita `Funcionalidade C` e deixa de disponibilizar `Funcionalidade A`. [RN1]
11. O Administrador consulta novamente a configuração e verifica que não restaram funcionalidades da seleção anterior que tenham sido removidas.

## [FA01] — FALHA AO SALVAR A CONFIGURAÇÃO

1. O Administrador abre a configuração de um perfil cuja seleção salva contém `Funcionalidade A` e `Funcionalidade B`.
2. O Administrador altera a seleção para `Funcionalidade B` e `Funcionalidade C` e confirma o salvamento.
3. Ocorre uma falha durante a operação de persistência.
4. O sistema informa o motivo da falha.
5. O Administrador consulta novamente a configuração.
6. O sistema apresenta integralmente a configuração anterior (`Funcionalidade A` e `Funcionalidade B`), sem manter parte da nova seleção. [RN2]

## [RN] — REGRAS DE NEGÓCIO

- **RN1:** Após a confirmação bem-sucedida, o conjunto de funcionalidades habilitadas deve corresponder exatamente à seleção realizada pelo Administrador; funcionalidades removidas deixam de estar disponíveis para o perfil.
- **RN2:** Em caso de falha, o sistema deve informar o motivo e preservar integralmente a configuração anterior, sem persistência parcial.
- **RN3:** A seleção deve ser formada por funcionalidades existentes no sistema.

## Dados e resultados esperados

| Dados de entrada | Resultado esperado |
|---|---|
| Seleção inicial A + B. | A e B ficam habilitadas para o perfil. |
| Substituição da seleção por B + C. | A configuração final contém somente B e C. |
| Falha durante o salvamento de B + C, tendo A + B sido a última configuração válida. | A configuração A + B permanece integralmente salva; nenhuma alteração parcial é aplicada. |
