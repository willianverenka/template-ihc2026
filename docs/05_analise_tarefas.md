# Entrega 5 — Análise de tarefas: HTA, GOMS e CTT

[← Início do projeto](../README.md) · [Entrega 4 — Cenários](04_cenarios_problema.md) · [Entrega 6 — Prototipação em papel](06_prototipacao_papel.md)

**Data:** 08/10/2026

**Status:** 🟩 concluída

**Responsabilidade:** cada integrante modela pelo menos 1 HTA, 1 GOMS e 1 CTT. As três técnicas podem abordar a mesma tarefa, conforme a orientação da disciplina.

**Consolidação:** Willian Verenka Oliveira Silva — 22.124.081-5. A autoria dos modelos individuais está identificada em cada arquivo.

## Objetivo e entradas

Modelar tarefas humanas relacionadas à investigação e à comunicação de um incidente. A **HTA** (*Hierarchical Task Analysis*) decompõe a tarefa e explicita seus planos; o **GOMS** (*Goals, Operators, Methods and Selection Rules*) descreve metas, operadores, métodos e regras de seleção; o **CTT** (*ConcurTaskTrees*) representa categorias e relações temporais entre tarefas.

As entradas são a contribuição técnica e as atividades da [Entrega 1](01_conhecendo_o_problema.md), as [personas da Entrega 3](03_personas_contexto_jornada.md) e os [cenários da Entrega 4](04_cenarios_problema.md). Os vínculos estão nas linhas R01–R04 da [matriz de rastreabilidade](../RASTREABILIDADE.md).

## Soluções individuais e seleção de tarefas

| ID | Tarefa | Persona / cenário | Autor(a) | Situação |
|---|---|---|---|---|
| [T01](05_analise_tarefas/t01.md) | Avaliar uma hipótese diagnóstica e decidir se as evidências a sustentam | P02 — Lucas / C01 | Gabriel Lovato — 22.123.004-8 | 🟩 concluída |
| [T02](05_analise_tarefas/t02.md) | Emitir um parecer fundamentado sobre a verificação da correção | P03 — Mariana / C02 | Willian Verenka Oliveira Silva — 22.124.081-5 | 🟩 concluída |
| [T03](05_analise_tarefas/t03.md) | Formular um diagnóstico inicial fundamentado sobre um incidente | P01 — Rafael Mendes / C03 | Théo Zago Zimmermann — 22.123.035-2 | 🟩 concluída |
| [T04](05_analise_tarefas/t04.md#hta--t04-investigar-a-propagação-de-uma-falha-entre-serviços-e-entregar-um-retorno-ao-sre) | Investigar a propagação de uma falha entre serviços e entregar um retorno ao SRE | P04 — Camila / C04 | João Sitta Giopatto — 22.123.054-3 | 🟩 concluída |
| [T05](05_analise_tarefas/t04.md#goms--t05-confirmar-de-quais-serviços-o-serviço-afetado-depende-durante-um-incidente) | Confirmar de quais serviços o serviço afetado depende durante um incidente | P04 — Camila / C04 | João Sitta Giopatto — 22.123.054-3 | 🟩 concluída |
| [T06](05_analise_tarefas/t04.md#ctt--t06-comunicar-o-retorno-ao-sre-e-acompanhar-a-decisão) | Comunicar o retorno ao SRE e acompanhar a decisão | P04 — Camila / C04 | João Sitta Giopatto — 22.123.054-3 | 🟩 concluída |

[H] T01 e T03 são críticas pelo risco de orientar a investigação para o componente errado; T02, pelo risco de concluir que uma correção foi verificada sem evidência suficiente.

## Modelos e arquivos

| Tarefa | HTA | GOMS | CTT |
|---|---|---|---|
| T01 | [Diagrama](../assets/05_tarefas/hta_t01.svg) e planos no [texto individual](05_analise_tarefas/t01.md#2-hta--avaliar-uma-hipótese-diagnóstica) | [Modelo textual](05_analise_tarefas/t01.md#3-goms--avaliar-uma-hipótese-diagnóstica) | [Diagrama](../assets/05_tarefas/ctt_t01.svg) e [interpretação](05_analise_tarefas/t01.md#4-ctt--avaliar-uma-hipótese-diagnóstica) |
| T02 | [Diagrama](../assets/05_tarefas/hta_t02.svg) e planos no [texto individual](05_analise_tarefas/t02.md#3-hta--recuperar-avaliar-e-comunicar) | [Modelo textual](05_analise_tarefas/t02.md#4-goms--métodos-para-produzir-o-mesmo-parecer) | [Diagrama](../assets/05_tarefas/ctt_t02.svg) e [interpretação](05_analise_tarefas/t02.md#5-ctt--dependências-entre-consulta-julgamento-e-comunicação) |
| T03 | [Diagrama](../assets/05_tarefas/hta_t03.png) e planos no [texto individual](05_analise_tarefas/t03.md#2-hta--formular-um-diagnóstico-inicial) | [Modelo textual](05_analise_tarefas/t03.md#3-goms--formular-um-diagnóstico-inicial) | [Diagrama](../assets/05_tarefas/ctt_t03.png) e [interpretação](05_analise_tarefas/t03.md#4-ctt--formular-um-diagnóstico-inicial) |
| T04 | Diagrama e [planos](05_analise_tarefas/t04.md#hta--t04-investigar-a-propagação-de-uma-falha-entre-serviços-e-entregar-um-retorno-ao-sre) | — | — |
| T05 | — | [Modelo textual](05_analise_tarefas/t04.md#goms--t05-confirmar-de-quais-serviços-o-serviço-afetado-depende-durante-um-incidente) | — |
| T06 | — | — | Diagrama e [legenda](05_analise_tarefas/t04.md#ctt--t06-comunicar-o-retorno-ao-sre-e-acompanhar-a-decisão) |

Os SVGs dos diagramas são também suas fontes editáveis.

## Síntese da equipe

T03 acompanha a formulação do diagnóstico pelo SRE. T01 aprofunda a avaliação de uma hipótese pelo desenvolvedor antes de orientar uma correção. T02 acompanha o repasse à QA, que precisa distinguir o resultado observado de um teste da conclusão sobre a falha original. Há sobreposição na consulta a evidências, mas os objetivos e os critérios de conclusão são diferentes.

Essa relação é uma proposta de continuidade entre os papéis, não uma sequência obrigatória validada com usuários.

| Achado da modelagem | Decisão inicial de design | Origem | Avaliação proposta |
|---|---|---|---|
| Uma hipótese convincente pode ter suporte insuficiente. | Associar explicação e evidências; separar fatos, hipótese e interpretação humana. | T01/T03; H03 | Observar se a pessoa reconhece evidência contraditória antes de comunicar sua conclusão. |
| Recorte incompleto pode excluir informação relevante. | Manter serviço e período visíveis e permitir consulta contextual aos registros. | T01/T03; H01–H03 | Observar se a pessoa identifica a lacuna e busca o registro necessário. |
| O repasse pode perder condições essenciais da falha. | Preservar a origem dos registros e os limites da verificação. | T02; H04–H06 | Observar se a pessoa relaciona incidente e verificação e reconhece diferenças entre ambientes. |
| A comunicação pode precisar terminar com incerteza explícita. | Permitir conclusão limitada ou inconclusiva com justificativa e pendências. | T02/T03; H04/H06 | Observar se a pessoa comunica o que falta sem transformar ausência de dados em certeza. |
| Registrar o parecer não garante que ele ficou disponível à equipe. | Informar sucesso ou falha e preservar o rascunho para recuperação. | T02; H04/H05 | Observar reconhecimento da falha e retomada sem perda do parecer. |

[H] São decisões propostas para o protótipo. O protótipo deve priorizar consulta, interpretação e comunicação de um incidente. Execução de correções, gestão ou execução de testes e avaliação científica do algoritmo não são incorporadas por esta entrega. A implementação da interface no TCC continua dependendo da equipe e do orientador.

**Próximas entregas:** T01, T02 e T03 são candidatas à prototipação e à avaliação.

## Checklist

- [x] Cada integrante produziu ao menos 1 HTA, 1 GOMS e 1 CTT.
- [x] Cada artefato identifica autor e tarefa.
- [ ] Diagramas são legíveis e possuem fonte editável quando possível.
- [x] HTA contém planos, não apenas árvore de tópicos.
- [x] GOMS distingue Goals, Operators, Methods e Selection Rules.
- [ ] CTT usa operadores temporais e tipos de tarefa coerentes.
- [x] Há texto explicando cada diagrama.
- [x] Tarefas estão ligadas a cenários/personas na rastreabilidade.
- [ ] Em TCC técnico, as tarefas descrevem o que a pessoa faz com a contribuição/resultados, não passos internos do código.
- [x] CRUDs, relatórios, filtros e atividades administrativas foram escolhidos por relevância ao objetivo do usuário.
