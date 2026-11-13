# CT004 — Gerenciar perfis associados a uma conta

**Autor:** Vitor Igor  
**Requisito relacionado:** RF02026 — Gerenciar perfis associados a uma conta  
**Atores:** Administrador do sistema ou Gestor

## Objetivo

Verificar se Administrador e Gestor conseguem substituir o conjunto de perfis associados a uma conta, mantendo somente perfis ativos, impedindo duplicidades e garantindo ao menos um perfil ativo, com atualização integral ou preservação da configuração anterior em caso de falha.

## Pré-condições

- O ator está autenticado no BVApp.
- Existe uma conta de usuário cadastrada.
- Existem pelo menos três perfis ativos e um perfil inativo.
- A conta possui inicialmente um ou mais perfis ativos associados.
- Para verificar a invalidação de token, a conta alvo está autenticada em outra sessão com o conjunto de acessos anterior.

## [FP] — FLUXO PRINCIPAL

1. O ator acessa a gestão de usuários e seleciona a conta que terá seus perfis alterados.
2. O sistema apresenta os perfis atualmente associados à conta.
3. O ator seleciona um novo conjunto de perfis ativos, por exemplo `Financeiro` e `Gestor`, removendo da seleção um perfil anteriormente associado.
4. O ator confirma a alteração.
5. O sistema verifica que os perfis selecionados estão ativos e não estão duplicados, e que a conta continuará com pelo menos um perfil ativo. [RN1][RN2]
6. O sistema substitui os vínculos anteriores pelo conjunto selecionado, sem manter perfis removidos.
7. O sistema atualiza os acessos da conta de acordo com os perfis selecionados e invalida o token da sessão que esteja utilizando permissões desatualizadas. [RN3]
8. O sistema apresenta a confirmação da alteração.
9. O ator consulta novamente os perfis associados e verifica que a lista corresponde exatamente à seleção confirmada.
10. Na sessão da conta afetada, o usuário tenta continuar utilizando o token anterior.
11. O sistema impede o uso do token invalidado; após autenticar-se novamente, o usuário passa a utilizar o contexto de acesso atualizado.

## [FA01] — TENTATIVA DE ASSOCIAR PERFIL INATIVO

1. O ator seleciona um perfil que está com status Inativo.
2. O ator tenta confirmar a alteração.
3. O sistema recusa a associação e informa o motivo.
4. Os vínculos anteriores permanecem inalterados.

## [FA02] — TENTATIVA DE DEIXAR A CONTA SEM PERFIL ATIVO

1. O ator remove da seleção todos os perfis ativos atualmente associados ou seleciona apenas perfis inativos.
2. O ator confirma a alteração.
3. O sistema recusa a operação, pois a conta deve manter ao menos um perfil ativo.
4. Os vínculos anteriores permanecem preservados.

## [FA03] — FALHA DURANTE A SUBSTITUIÇÃO

1. O ator seleciona um novo conjunto válido de perfis e confirma a alteração.
2. Ocorre uma falha durante o salvamento.
3. O sistema informa o problema.
4. O ator consulta novamente os vínculos.
5. O sistema apresenta integralmente o conjunto anterior, sem adicionar ou remover parcialmente perfis. [RN4]

## [RN] — REGRAS DE NEGÓCIO

- **RN1:** Uma conta pode possuir um ou mais perfis associados.
- **RN2:** Não são permitidas associações duplicadas; somente perfis ativos podem ser vinculados e a conta deve manter ao menos um perfil ativo.
- **RN3:** Após a confirmação, os perfis associados devem corresponder exatamente à seleção realizada e os acessos devem refletir a nova configuração. Tokens com permissões desatualizadas devem ser invalidados.
- **RN4:** Em caso de falha, o sistema deve informar o problema e preservar integralmente os vínculos anteriores, sem atualização parcial.

## Dados e resultados esperados

| Dados de entrada | Resultado esperado |
|---|---|
| Seleção válida de dois perfis ativos. | A conta fica associada exatamente aos dois perfis selecionados. |
| Perfil inativo incluído na seleção. | Alteração recusada e vínculos anteriores preservados. |
| Seleção sem nenhum perfil ativo. | Alteração recusada e a conta mantém pelo menos um perfil ativo. |
| Falha durante a substituição. | Nenhuma associação parcial é persistida. |
| Token anterior da conta afetada. | Token invalidado; o usuário precisa estabelecer uma nova autenticação para usar os acessos atualizados. |
