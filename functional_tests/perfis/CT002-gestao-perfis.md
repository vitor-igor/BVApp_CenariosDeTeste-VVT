# CT002 — Gerenciar perfis de acesso (CRUD)

**Autor:** Vitor Igor  
**Requisito relacionado:** RF02013 — Gestão de perfis de acesso  
**Ator:** Administrador do sistema

## Objetivo

Verificar se o Administrador consegue cadastrar, consultar, pesquisar, atualizar, alterar o status e excluir logicamente perfis de acesso, mantendo as validações e a integridade das informações previstas no requisito.

## Pré-condições

- O Administrador está autenticado no BVApp.
- A funcionalidade de gestão de perfis está disponível para o Administrador.
- Não existe outro perfil com o nome reservado para este cenário.

## [FP] — FLUXO PRINCIPAL

1. O Administrador acessa a área de gestão de perfis de acesso.
2. O sistema apresenta a opção de cadastrar um perfil e os campos Nome, Descrição e Status.
3. O Administrador informa o nome `PERFIL_TESTE_VVT` e a descrição `Perfil criado para validar o gerenciamento de acessos.` e deixa o status sem preenchimento.
4. O Administrador confirma o cadastro.
5. O sistema valida os dados, verifica que o nome ainda não está cadastrado e cria o perfil com status **Ativo**, pois o status não foi informado. [RN1][RN2][RN3]
6. O sistema apresenta uma confirmação do cadastro.
7. O Administrador acessa a consulta de perfis e pesquisa por `PERFIL_TESTE_VVT`.
8. O sistema apresenta o perfil recém-cadastrado entre os resultados.
9. O Administrador seleciona o perfil para edição, altera sua descrição para `Descrição atualizada para o cenário de teste.` e modifica seu status para **Inativo**.
10. O Administrador confirma a atualização.
11. O sistema salva os novos dados e o status do perfil.
12. O Administrador consulta novamente o perfil e verifica que a descrição e o status foram atualizados.
13. O Administrador solicita a exclusão lógica do perfil.
14. O sistema marca o perfil como excluído logicamente, preserva seu registro e deixa de apresentá-lo nas consultas usuais. [RN4]
15. O Administrador pesquisa novamente pelo nome do perfil e verifica que ele não aparece nos resultados usuais.

## [FA01] — NOME DUPLICADO

1. O Administrador inicia o cadastro de outro perfil utilizando um nome que já existe.
2. O sistema identifica a duplicidade e recusa o cadastro, informando o motivo.
3. Nenhum novo perfil é criado.

## [FA02] — CAMPOS FORA DOS LIMITES

1. O Administrador tenta cadastrar ou atualizar um perfil com nome menor que 3 caracteres ou maior que 100 caracteres, ou com descrição menor que 5 caracteres ou maior que 500 caracteres.
2. O sistema recusa a operação e informa quais campos não atendem às validações.
3. Os dados anteriormente salvos permanecem inalterados.

## [FA03] — PESQUISA SEM RESULTADOS

1. O Administrador pesquisa por um nome que não corresponde a nenhum perfil disponível nas consultas usuais.
2. O sistema não apresenta perfis que não correspondam à pesquisa.
3. A mensagem específica para ausência de resultados não é definida no requisito e não deve ser presumida neste cenário.

## [RN] — REGRAS DE NEGÓCIO

- **RN1:** O nome deve possuir entre 3 e 100 caracteres.
- **RN2:** A descrição deve possuir entre 5 e 500 caracteres.
- **RN3:** Não pode haver dois perfis com o mesmo nome; quando o status não for informado no cadastro, o perfil deve ser criado como Ativo.
- **RN4:** A exclusão é lógica: o registro não deve ser apagado fisicamente e deve deixar de aparecer nas consultas usuais.

## Dados e resultados esperados

| Dados de entrada | Resultado esperado |
|---|---|
| Nome `PERFIL_TESTE_VVT`, descrição válida e status não informado. | Perfil cadastrado com status Ativo. |
| Nome já utilizado por outro perfil. | Cadastro recusado por duplicidade. |
| Nome ou descrição fora dos limites definidos. | Cadastro/atualização recusado; dados anteriores preservados. |
| Alteração de descrição e status. | Novos dados exibidos na consulta. |
| Exclusão do perfil. | Perfil ausente das consultas usuais, com registro preservado logicamente. |
