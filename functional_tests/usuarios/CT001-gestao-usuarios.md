# CT001 — Gerenciar usuários (CRUD)

**Autor:** Vitor Igor  
**Requisito relacionado:** RF02025 — Gestão de usuários  
**Atores:** Administrador do sistema ou Gestor

## Objetivo

Verificar se Administrador e Gestor conseguem cadastrar, consultar, pesquisar, atualizar, alterar o status e excluir logicamente contas de usuários, respeitando as regras de dados obrigatórios, e-mail, senha, perfis e associação com cooperados.

## Pré-condições

- O Administrador ou Gestor está autenticado no BVApp.
- Existem perfis ativos disponíveis para associação às contas.
- Para os testes de associação, existem cooperados cadastrados: um ativo e sem conta vinculada, um inativo e sem conta vinculada e outro que já possui uma conta associada.
- Os e-mails utilizados nos testes ainda não estão associados a outras contas.

## [FP] — FLUXO PRINCIPAL: CADASTRO, CONSULTA, ATUALIZAÇÃO E EXCLUSÃO

1. O ator acessa a área de gestão de usuários.
2. O sistema apresenta a opção de cadastrar usuário e os campos de nome, e-mail, senha, status, perfis associados e CPF, quando houver associação com cooperado.
3. O ator informa nome `Usuário Teste VVT`, e-mail `teste.vvt.01@example.com`, senha `Teste@1234`, seleciona um perfil ativo disponível e deixa o status sem preenchimento.
4. O ator confirma o cadastro.
5. O sistema verifica os campos obrigatórios, a unicidade do e-mail, a complexidade da senha e a existência de pelo menos um perfil ativo selecionado. [RN1][RN2][RN3]
6. Como não foi informado CPF nem status, o sistema cadastra a conta como Ativa e associa o perfil selecionado.
7. O sistema apresenta a confirmação do cadastro.
8. O ator acessa a consulta de usuários e pesquisa pelo nome ou e-mail da conta cadastrada.
9. O sistema apresenta o usuário correspondente nos resultados.
10. O ator seleciona a conta e atualiza o nome e o e-mail, utilizando um e-mail ainda não associado a outra conta.
11. O ator confirma a atualização.
12. O sistema salva os dados e apresenta a conta atualizada na consulta.
13. O ator altera o status da conta para Inativo.
14. O sistema salva a alteração de status.
15. O ator solicita a exclusão lógica da conta.
16. O sistema marca a conta como excluída logicamente, retira-a das consultas usuais e impede sua autenticação. [RN4]
17. O ator pesquisa novamente pelo usuário e verifica que a conta não aparece nos resultados usuais.

## [FA01] — CADASTRO VINCULADO A COOPERADO ATIVO

1. O ator inicia o cadastro de uma conta e informa um CPF correspondente a um cooperado ativo que ainda não possui conta vinculada.
2. O ator informa e-mail, senha válida e seleciona ao menos um perfil ativo.
3. O sistema localiza o cooperado, vincula a conta ao registro encontrado e utiliza na conta o nome cadastrado para esse cooperado.
4. O sistema cria a conta como Ativa, quando o status não tiver sido informado, e conclui o cadastro.

## [FA02] — CADASTRO VINCULADO A COOPERADO INATIVO

1. O ator inicia o cadastro e informa o CPF de um cooperado existente, inativo e ainda não associado a outra conta.
2. O ator informa os demais dados obrigatórios e seleciona ao menos um perfil ativo.
3. O sistema localiza o cooperado, realiza a associação e cria a conta como Inativa, conforme a condição do cooperado. [RN5]

## [FA03] — DADOS INVÁLIDOS OU ASSOCIAÇÃO INDISPONÍVEL

1. O ator tenta cadastrar uma conta sem nome, e-mail ou senha, com e-mail já utilizado, com senha que não atende à complexidade exigida ou sem selecionar ao menos um perfil ativo.
2. O sistema recusa o cadastro e informa o motivo, sem criar a conta.
3. Em outra tentativa, o ator informa CPF inexistente ou pertencente a cooperado que já possui conta vinculada.
4. O sistema recusa a associação e o cadastro, informando o problema e sem criar a conta parcialmente.

## [FA04] — E-MAIL DUPLICADO NA ATUALIZAÇÃO

1. O ator edita uma conta e informa um e-mail que já pertence a outra conta.
2. O sistema recusa a atualização e informa a duplicidade.
3. Os dados anteriores da conta permanecem preservados.

## [RN] — REGRAS DE NEGÓCIO

- **RN1:** Nome, e-mail e senha são obrigatórios; o e-mail deve ser único.
- **RN2:** A senha deve possuir no mínimo 8 caracteres e incluir letras, números e caracteres especiais.
- **RN3:** A conta deve possuir ao menos um perfil ativo selecionado no fluxo administrativo.
- **RN4:** A exclusão é lógica: o registro é preservado, deixa de aparecer nas consultas usuais e não pode mais autenticar-se.
- **RN5:** Quando o CPF corresponder a um cooperado inativo, a conta vinculada deve ser criada como Inativa; quando o status não for informado nos demais casos, a conta deve ser criada como Ativa.
- **RN6:** Quando o CPF for informado, deve existir um cooperado correspondente e ainda não associado a outra conta; o nome utilizado na conta deve ser o nome cadastrado do cooperado.

## Dados e resultados esperados

| Dados de entrada | Resultado esperado |
|---|---|
| Nome, e-mail único, senha válida, perfil ativo e status omitido. | Conta criada como Ativa e associada ao perfil selecionado. |
| CPF de cooperado ativo sem conta. | Conta vinculada ao cooperado e com o nome registrado para ele. |
| CPF de cooperado inativo sem conta. | Conta vinculada e criada como Inativa. |
| CPF inexistente ou de cooperado já associado. | Cadastro recusado, sem conta parcialmente criada. |
| Senha com menos de 8 caracteres ou sem uma das categorias exigidas. | Cadastro recusado. |
| E-mail duplicado ou ausência de perfil ativo. | Cadastro/atualização recusado, sem alteração indevida. |
| Exclusão lógica de conta existente. | Conta ausente das consultas usuais e impedida de autenticar-se. |
