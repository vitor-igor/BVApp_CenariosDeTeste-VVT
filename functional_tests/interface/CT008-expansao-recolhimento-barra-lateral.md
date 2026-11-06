# CT008 — Expansão e recolhimento da barra lateral

**Autor:** Vitor Igor

## Objetivo

Verificar se um usuário autenticado consegue alternar a barra lateral geral entre os modos expandido e compacto, quando aplicável.

## Requisitos relacionados

- **US 29022 — Expandir sidebar geral**

## Ator

Usuário autenticado no BVApp.

## Pré-condições

- O usuário está autenticado.
- A barra lateral geral está disponível.

## Fluxo principal

1. O usuário aciona o controle de expansão da barra lateral.
2. O sistema aumenta a largura da barra lateral e alterna para o modo expandido.
3. O sistema exibe os rótulos dos itens de navegação.
4. O usuário aciona novamente o controle; quando aplicável, o sistema alterna para o modo compacto.

## Fluxos alternativos

A US não especifica comportamentos alternativos adicionais.

## Regras de negócio

> A barra lateral alterna entre os modos expandido e compacto, quando aplicável. Os rótulos dos itens de navegação devem ser exibidos.

## Dados de entrada e resultados esperados

| Dados de entrada | Resultado esperado |
|---|---|
| Usuário autenticado; acionamento do controle de expansão/recolhimento. | A barra lateral aumenta sua largura, exibe os rótulos no modo expandido e pode retornar ao modo compacto, quando aplicável. |
