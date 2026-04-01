---
title: "Post de teste: todos os recursos do blog"
description: "Demonstração completa dos elementos disponíveis nos posts do LabEpi — imagens, tabelas, gráficos, código, citações e muito mais."
date: 2026-04-01
author: "Gabriel Olegário"
tags: ["Teste", "Guia", "Markdown"]
cover: "/assets/images/lucas-santos.jpg"
draft: false
---

Este post é um mapa de tudo que você pode usar ao escrever um artigo para o LabEpi. Cada bloco abaixo mostra um recurso diferente com um exemplo real do contexto de epidemiologia.

---

## 1. Formatação de texto

Você pode usar **negrito** para enfatizar termos técnicos como **odds ratio** ou **intervalo de confiança**. Use *itálico* para títulos de estudos como *The Lancet* ou para termos em inglês. Também é possível ~~riscar~~ texto que ficou desatualizado.

Texto normal continua sendo renderizado como parágrafo. Parágrafos são separados por uma linha em branco no arquivo Markdown.

---

## 2. Títulos e hierarquia

O título do post (`title` no frontmatter) vira um `<h1>` automático. No corpo do post, use:

### H3 — subtítulo de seção
Use para dividir seções dentro de um tópico maior.

#### H4 — sub-subtítulo
Use com moderação, apenas quando há muitos níveis necessários.

---

## 3. Listas

### Lista não ordenada

- Transversal
- Coorte prospectiva
- Coorte retrospectiva
- Caso-controle
  - Aninhado em coorte
  - Clássico de base hospitalar
- Ensaio clínico randomizado (ECR)

### Lista ordenada

1. Defina a pergunta de pesquisa (PICO)
2. Escolha o delineamento adequado
3. Calcule o tamanho amostral
4. Submeta ao comitê de ética
5. Colete os dados
6. Analise e interprete

---

## 4. Citação em bloco

> "A epidemiologia é a ciência que investiga a distribuição e os determinantes de estados ou eventos relacionados à saúde em populações específicas e a aplicação desse estudo no controle de problemas de saúde."
>
> — Last JM. *A Dictionary of Epidemiology*, 4ª ed., Oxford University Press, 2001.

---

## 5. Tabela

As tabelas são ótimas para comparar delineamentos ou apresentar resultados resumidos.

| Delineamento | Direção temporal | Medida de associação | Adequado para desfecho raro? |
|---|---|---|---|
| Transversal | Simultânea | Prevalência / RP | Não |
| Coorte prospectiva | Passado → Futuro | RR / IR | Depende |
| Coorte retrospectiva | Retrospectiva | RR / HR | Depende |
| Caso-controle | Retrospectiva | OR | **Sim** |
| ECR | Prospectiva | RR / NNT | Não |

---

## 6. Código

Use `código inline` para comandos curtos, funções ou nomes de variáveis.

Para blocos longos, use código com destaque de sintaxe:

```r
# Regressão logística no R
modelo <- glm(
  desfecho ~ exposicao + idade + sexo,
  data = dados,
  family = binomial(link = "logit")
)

summary(modelo)
exp(coef(modelo))          # OR bruto
exp(confint(modelo))       # IC 95%
```

```python
import pandas as pd
import statsmodels.api as sm

# Teste qui-quadrado
from scipy.stats import chi2_contingency

tabela = pd.crosstab(df['exposicao'], df['desfecho'])
chi2, p, dof, expected = chi2_contingency(tabela)
print(f"χ² = {chi2:.3f}  |  p = {p:.4f}")
```

---

## 7. Imagem com legenda

Imagens inseridas no texto com legenda descritiva usando HTML simples dentro do Markdown:

<figure>
  <img src="/assets/images/lucas-santos.jpg" alt="Foto de Lucas Santos, epidemiologista e fundador do LabEpi" />
  <figcaption>Lucas Santos — epidemiologista, colaborador do Global Burden of Disease (GBD/IHME) e fundador do Laboratório de Epidemiologia.</figcaption>
</figure>

---

## 8. Gráfico inline (SVG)

Para gráficos simples, você pode embutir SVG diretamente. Aqui um gráfico de barras mostrando a proporção de estudantes de saúde no Brasil por área:

<svg class="chart" viewBox="0 0 600 320" fill="none" xmlns="http://www.w3.org/2000/svg" role="img" aria-label="Gráfico de barras: estudantes por área da saúde">
  <!-- Eixo Y -->
  <line x1="60" y1="20" x2="60" y2="260" stroke="#ffffff20" stroke-width="1"/>
  <!-- Eixo X -->
  <line x1="60" y1="260" x2="580" y2="260" stroke="#ffffff20" stroke-width="1"/>
  <!-- Labels eixo Y -->
  <text x="50" y="265" text-anchor="end" fill="#7a85b8" font-size="11" font-family="Outfit, sans-serif">0</text>
  <text x="50" y="195" text-anchor="end" fill="#7a85b8" font-size="11" font-family="Outfit, sans-serif">25%</text>
  <text x="50" y="130" text-anchor="end" fill="#7a85b8" font-size="11" font-family="Outfit, sans-serif">50%</text>
  <text x="50" y="65"  text-anchor="end" fill="#7a85b8" font-size="11" font-family="Outfit, sans-serif">75%</text>
  <!-- Grade horizontal -->
  <line x1="60" y1="195" x2="580" y2="195" stroke="#ffffff08" stroke-width="1" stroke-dasharray="4 4"/>
  <line x1="60" y1="130" x2="580" y2="130" stroke="#ffffff08" stroke-width="1" stroke-dasharray="4 4"/>
  <line x1="60" y1="65"  x2="580" y2="65"  stroke="#ffffff08" stroke-width="1" stroke-dasharray="4 4"/>
  <!-- Barras -->
  <!-- Medicina: 32% → altura 83px -->
  <rect x="80"  y="177" width="68" height="83"  fill="#99ffcd" rx="4" opacity="0.9"/>
  <text x="114" y="270" text-anchor="middle" fill="#7a85b8" font-size="11" font-family="Outfit, sans-serif">Medicina</text>
  <text x="114" y="171" text-anchor="middle" fill="#99ffcd" font-size="12" font-weight="700" font-family="Outfit, sans-serif">32%</text>
  <!-- Enfermagem: 28% → 73px -->
  <rect x="175" y="187" width="68" height="73"  fill="#8cb4ff" rx="4" opacity="0.9"/>
  <text x="209" y="270" text-anchor="middle" fill="#7a85b8" font-size="11" font-family="Outfit, sans-serif">Enfermagem</text>
  <text x="209" y="181" text-anchor="middle" fill="#8cb4ff" font-size="12" font-weight="700" font-family="Outfit, sans-serif">28%</text>
  <!-- Fisioterapia: 14% → 36px -->
  <rect x="270" y="224" width="68" height="36"  fill="#99ffcd" rx="4" opacity="0.6"/>
  <text x="304" y="270" text-anchor="middle" fill="#7a85b8" font-size="11" font-family="Outfit, sans-serif">Fisioterapia</text>
  <text x="304" y="218" text-anchor="middle" fill="#c5cde8" font-size="12" font-weight="700" font-family="Outfit, sans-serif">14%</text>
  <!-- Nutrição: 11% → 29px -->
  <rect x="365" y="231" width="68" height="29"  fill="#ffd36e" rx="4" opacity="0.8"/>
  <text x="399" y="270" text-anchor="middle" fill="#7a85b8" font-size="11" font-family="Outfit, sans-serif">Nutrição</text>
  <text x="399" y="225" text-anchor="middle" fill="#ffd36e" font-size="12" font-weight="700" font-family="Outfit, sans-serif">11%</text>
  <!-- Outras: 15% → 39px -->
  <rect x="460" y="221" width="68" height="39"  fill="#8cb4ff" rx="4" opacity="0.5"/>
  <text x="494" y="270" text-anchor="middle" fill="#7a85b8" font-size="11" font-family="Outfit, sans-serif">Outras</text>
  <text x="494" y="215" text-anchor="middle" fill="#c5cde8" font-size="12" font-weight="700" font-family="Outfit, sans-serif">15%</text>
  <!-- Título -->
  <text x="320" y="305" text-anchor="middle" fill="#7a85b8" font-size="12" font-family="Outfit, sans-serif">Distribuição estimada de estudantes de saúde no Brasil. Fonte: INEP/MEC 2023.</text>
</svg>

---

## 9. Separador horizontal

Use `---` para separar seções visualmente, como feito ao longo deste post.

---

## 10. Callout / nota de destaque

Use HTML direto para caixas de destaque que não existem no Markdown padrão:

<div class="callout">
  <strong>Nota metodológica:</strong> Os dados de prevalência apresentados neste post são estimativas baseadas em inquéritos populacionais. Para fins acadêmicos, sempre consulte as fontes primárias e verifique a data de coleta dos dados.
</div>

---

## 11. Links

Links podem ser [inline como este](/blog/) ou podem levar para páginas externas. Ao citar fontes, sempre prefira o link direto para o artigo no DOI ou PubMed.

---

## O que não é suportado em `.md` puro

Para recursos mais avançados (componentes interativos, animações, gráficos dinâmicos), o Astro suporta arquivos `.mdx`. Nesse formato, você pode importar componentes Astro diretamente dentro do texto. Avise se quiser ativar MDX no projeto.
