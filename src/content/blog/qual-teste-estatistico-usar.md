---
title: "Qual teste estatístico usar? O guia definitivo para pesquisadores em formação"
description: "Qui-quadrado, Mann-Whitney, regressão logística — quando aplicar cada um e como interpretar os resultados."
date: 2026-03-10
author: "Lucas Santos"
tags: ["Estatística", "Metodologia", "Testes"]
draft: false
---

A dúvida sobre qual teste estatístico usar é uma das mais frequentes — e mais paralisantes — para pesquisadores em formação. Este guia mostra o caminho para decidir com segurança.

## A pergunta certa antes de qualquer teste

Antes de abrir o SPSS, R ou qualquer software, responda:

1. **Qual é o tipo da variável desfecho?** (categórica binária, categórica nominal, numérica contínua, numérica ordinal)
2. **Quantos grupos você está comparando?** (dois ou mais de dois)
3. **Os grupos são independentes ou pareados?**
4. **A variável numérica segue distribuição normal?**

## O mapa de decisão

### Desfecho categórico binário
- Dois grupos independentes → **Qui-quadrado** (ou Fisher exato para células com n < 5)
- Medidas repetidas → **McNemar**

### Desfecho numérico contínuo
- Dois grupos independentes, distribuição normal → **Teste t de Student independente**
- Dois grupos independentes, sem normalidade → **Mann-Whitney U**
- Mais de dois grupos, normalidade → **ANOVA one-way**
- Mais de dois grupos, sem normalidade → **Kruskal-Wallis**
- Antes e depois no mesmo grupo → **Teste t pareado** (normal) ou **Wilcoxon** (sem normalidade)

### Associação entre variáveis
- Duas variáveis numéricas com normalidade → **Correlação de Pearson**
- Sem normalidade ou ordinais → **Correlação de Spearman**

## Regressão: quando simples não basta

Quando você precisa controlar por variáveis de confusão ou tem múltiplos preditores:

- Desfecho binário → **Regressão logística binária**
- Desfecho numérico → **Regressão linear múltipla**
- Tempo até evento → **Regressão de Cox**

## O erro mais comum

Pesquisadores iniciantes frequentemente **escolhem o teste antes de verificar a distribuição dos dados**. Isso leva ao uso de testes paramétricos (que assumem normalidade) em dados que não são normais — invalidando as conclusões.

Sempre verifique a normalidade com:
- Histograma visual
- QQ-plot
- Teste de Shapiro-Wilk (para amostras ≤ 50) ou Kolmogorov-Smirnov

## Interpretando o p-valor corretamente

O p-valor < 0,05 não significa que o resultado é "importante" ou "relevante clinicamente". Significa apenas que, **assumindo que a hipótese nula é verdadeira**, a probabilidade de obter um resultado tão ou mais extremo é menor que 5%.

Sempre reporte o **tamanho de efeito** junto com o p-valor:
- Cohen's d para comparação de médias
- Odds Ratio para desfechos binários
- Coeficiente de correlação para associações
