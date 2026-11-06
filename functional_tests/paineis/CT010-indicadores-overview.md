# CT010 — Exibição dos indicadores na página Overview

**Autor:** Vitor Igor

## Objetivo

Verificar se a página Overview apresenta os indicadores e painéis definidos para o usuário autenticado.

## Requisitos relacionados

- **US 29672 — Página Overview**

## Ator

Usuário autenticado no BVApp.

## Pré-condições

- O usuário está autenticado.
- Há dados disponíveis para alimentar os indicadores e painéis descritos na US.

## Fluxo principal

1. O usuário acessa a página Overview.
2. O sistema apresenta os indicadores de Serviços, Ativos, Cooperados, Ordens de Serviço, Contas e Cobranças.
3. O sistema apresenta os painéis de status dos ativos, geração de energia e fluxo financeiro.
4. O usuário verifica a presença desses indicadores e painéis.

## Fluxos alternativos

A US não especifica mensagens ou estados alternativos para ausência de dados ou falha no carregamento.

## Regras de negócio

> A página Overview deve apresentar os indicadores e painéis listados na US 29672. Não são presumidos cálculos ou valores de referência.

## Dados de entrada e resultados esperados

| Dados de entrada | Resultado esperado |
|---|---|
| Dados de serviços, ativos, cooperados, ordens de serviço, contas, cobranças, geração de energia e fluxo financeiro. | Apresentação dos seis indicadores e dos painéis de status dos ativos, geração de energia e fluxo financeiro, sem inferir valores numéricos. |

## Dúvida para esclarecimento

- Quais valores ou fórmulas devem ser utilizados para validar a correção numérica dos indicadores e painéis? A US lista os componentes, mas não especifica cálculos ou valores esperados.
