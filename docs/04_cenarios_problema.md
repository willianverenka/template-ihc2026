# Entrega 4 — Cenários de análise/problema

**Data:** 16/09/2026  
**Status:** 🟨 em andamento  
**Responsabilidade:** 1 solução completa por integrante

## Objetivo da atividade

Descrever situações atuais em que o usuário tenta alcançar um objetivo e encontra dificuldades. O cenário de análise/problema deve tornar visível **o contexto, os atores, as ações e as rupturas**, sem antecipar a interface que será projetada.

> **Regra central:** cenário de problema é a “história do problema”. Se o texto já diz “o sistema mostra”, “o aplicativo resolve” ou descreve botões/telas futuras, provavelmente está misturando problema com solução.

Sempre que possível, o cenário deve aprofundar uma **situação concreta já registrada na Entrega 1**.

### Quando o TCC não possuía interface

O cenário continua sendo uma história de **problema/atividade humana**, não uma história do futuro sistema. Descreva como o profissional realiza hoje uma atividade semelhante ou como lida atualmente com dados, resultados, configurações, logs, decisões e limitações que o tema do TCC pretende apoiar.

Exemplo: em vez de “o DBA abre o novo dashboard e executa o algoritmo”, descreva “o DBA precisa investigar uma consulta lenta, reúne informações em ferramentas distintas, compara planos manualmente e tem dificuldade para estimar o impacto de uma mudança”.

A interface da disciplina aparecerá somente depois, nos cenários de interação.

Se o integrante escolher um novo problema/situação, explique por que ele passou a ser relevante e indique a evidência que motivou sua inclusão.

## Cenário C04 — Investigação de uma falha propagada entre microsserviços

**Autor(a):** João Sitta Giopatto — 22.123.054-3  
**Persona(s) relacionada(s):** P04 - Especialista em Observabilidade
**Necessidade relacionada:** Identificar evidências relevantes de observabilidade, compreender as relações entre serviços e organizar um contexto técnico suficiente para apoiar a investigação de um incidente.  
**Situação concreta da Entrega 1 relacionada:**  Consulta e filtragem manual de logs, métricas e traces; mapas de serviços e navegação entre sinais de observabilidade; dificuldade de estabelecer relações entre sintomas e origem do problema. 
**Hipóteses ainda presentes:** H01, H02, H03

### 1. Cenário inicial

Especialista em Observabilidade recebe informações sobre uma falha em um sistema de microsserviços e precisa investigar sua origem. Para isso, consulta logs, métricas e traces em diferentes ferramentas, tentando identificar quais serviços e componentes estão relacionados ao problema.

O grande volume de dados e a necessidade de correlacionar manualmente essas informações dificultam a identificação das evidências mais relevantes e a compreensão de como a falha se propagou.

### 2. Questões de refinamento

Use os tipos de questões/taxonomia definidos na aula. As perguntas devem revelar informações **ainda ausentes** do cenário, não repetir o que já foi respondido.

| # | Questão | Por que precisa ser respondida | Fonte/forma de obter resposta |
|---|---|---|---|
| Q1 | Quais dados são mais relevantes para iniciar a investigação? | Identifica as principais evidências utilizadas | Entrevista com profissionais. |
| Q2 | Como o profissional relaciona os diferentes serviços envolvidos? | Entende como a propagação da falha é analisada | Entrevista e observação. |
| Q3 | Quais dificuldades surgem com o grande volume de telemetria? | Identifica problemas de seleção e interpretação das informações | Entrevista e observação. |
| Q1 | O que acontece quando os dados disponíveis são insuficientes? | Identifica como o profissional lida com limitações da telemetria | Entrevista com profissionais. |

### 3. Cenário refinado

Reescreva o cenário incorporando as respostas. Marque o conteúdo novo de forma consistente (por exemplo, `**[NOVO: ...]**`).

{{narrativa refinada}}

### 4. Elementos extraídos

| Elemento | Evidência no cenário |
|---|---|
| Ator(es) | {{...}} |
| Objetivo(s) | {{...}} |
| Contexto | {{...}} |
| Recursos/informações | {{...}} |
| Ações | {{...}} |
| Problemas/rupturas | {{...}} |
| Consequências | {{...}} |

### 5. Implicações para as próximas entregas

Quais tarefas merecem análise? Quais informações precisam ser coletadas? **Não desenhe a solução ainda.**

> Repita para C02, C03... com autoria individual.

## Checklist

- [ ] Há um cenário completo por integrante.
- [ ] Cada cenário tem título, ator, objetivo, contexto e problema.
- [ ] O cenário possui origem rastreável na Entrega 1 ou justifica claramente a inclusão de uma nova situação.
- [ ] O texto descreve a situação atual, sem antecipar a solução.
- [ ] Para TCC sem interface original, o cenário descreve uma prática humana plausível relacionada à contribuição técnica, e não “a falta de uma tela”.
- [ ] Questões de refinamento acrescentam informação nova.
- [ ] O refinamento mostra claramente o que foi adicionado/alterado.
- [ ] Cenários são diferentes o suficiente para cobrir objetivos/problemas relevantes.
- [ ] Cada cenário está ligado a persona/necessidade na matriz de rastreabilidade.
