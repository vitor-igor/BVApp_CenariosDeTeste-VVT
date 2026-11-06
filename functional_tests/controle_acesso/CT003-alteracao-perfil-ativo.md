# CT003 — Alteração do perfil ativo durante a sessão

**Autor:** Vitor Igor

## Objetivo

Verificar se a troca de perfil atualiza o perfil ativo da sessão, as permissões correspondentes e os dados do usuário, e retorna à página inicial.

## Requisitos relacionados

- **Feature 23519 — Autenticação (Login)**
- **US 28720 — Atualizar alteração de perfil ativo durante a sessão** (referência principal)
- **US 23604 — Alterar perfil ativo durante a sessão** (comportamento relacionado: usuário autenticado com mais de um perfil seleciona outro perfil associado e confirma a troca)
- **CA 23602 — Permitir alterar o perfil ativo durante a sessão**

## Ator

Usuário autenticado que possui mais de um perfil associado à conta.

## Pré-condições

- O usuário está autenticado no BVApp.
- A conta possui mais de um perfil associado.
- Um perfil está ativo na sessão.

## Fluxo principal

1. O usuário abre a opção de troca de perfil.
2. Seleciona outro perfil disponível e associado à conta.
3. Confirma a alteração.
4. O sistema atualiza o perfil ativo da sessão e as permissões correspondentes.
5. O sistema atualiza os dados do usuário e retorna à página inicial.

## Fluxos alternativos

Os requisitos não especificam o comportamento ou mensagens para falha na troca de perfil. Não são definidos passos adicionais.

## Regras de negócio

> A troca é realizada para outro perfil associado à conta. As permissões correspondentes ao novo perfil ativo são atualizadas.

## Dados de entrada e resultados esperados

| Dados de entrada | Resultado esperado |
|---|---|
| Usuário autenticado com mais de um perfil associado; perfil atualmente ativo; outro perfil disponível e associado. | O perfil ativo e as permissões correspondentes são atualizados; os dados do usuário são atualizados e a navegação retorna à página inicial. |
