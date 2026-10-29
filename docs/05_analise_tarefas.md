# Entrega 5 — Análise de tarefas: HTA, GOMS e CTT

[← Início do projeto](../README.md) · [Entrega 4 — Cenários](04_cenarios_problema.md) · [Entrega 6 — Prototipação em papel](06_prototipacao_papel.md)

**Data:** 08/10/2026

**Última revisão:** 28/10/2026

**Status:** 🟨 em andamento

**Responsabilidade:** cada integrante modela pelo menos 1 HTA, 1 GOMS e 1 CTT. As três técnicas podem abordar a mesma tarefa, conforme a orientação da disciplina.

**Consolidação:** Willian Verenka Oliveira Silva — 22.124.081-5. A autoria dos modelos individuais está identificada em cada arquivo.

## Objetivo e entradas

Modelar tarefas humanas relacionadas à investigação e à comunicação de um incidente. A **HTA** (*Hierarchical Task Analysis*) decompõe a tarefa e explicita seus planos; o **GOMS** (*Goals, Operators, Methods and Selection Rules*) descreve metas, operadores, métodos e regras de seleção; o **CTT** (*ConcurTaskTrees*) representa categorias e relações temporais entre tarefas.

As entradas são a contribuição técnica e as atividades da [Entrega 1](01_conhecendo_o_problema.md), as [personas da Entrega 3](03_personas_contexto_jornada.md) e os [cenários da Entrega 4](04_cenarios_problema.md). Os vínculos estão nas linhas R01–R04 da [matriz de rastreabilidade](../RASTREABILIDADE.md).

[F] Os quatro trabalhos abaixo estão disponíveis nesta consolidação. [H] Seus fluxos são propostas derivadas das entregas anteriores, ainda sem validação de campo. Modelar uma tarefa não comprova o comportamento do público nem a precisão técnica do pipeline.

## Soluções individuais e seleção de tarefas

| ID | Tarefa | Persona / cenário | Autor(a) | Situação |
|---|---|---|---|---|
| [T01](05_analise_tarefas/t01.md) | Avaliar uma hipótese diagnóstica e decidir se as evidências a sustentam | P02 — Lucas / C01 | Gabriel Lovato — 22.123.004-8 | 🟨 em andamento — modelos e diagramas integrados; revisão conjunta pendente |
| [T02](05_analise_tarefas/t02.md) | Emitir um parecer fundamentado sobre a verificação da correção | P03 — Mariana / C02 | Willian Verenka Oliveira Silva — 22.124.081-5 | 🟨 em andamento — HTA, GOMS e CTT integrados, com diagramas; revisão conjunta pendente |
| [T03](05_analise_tarefas/t03.md) | Formular um diagnóstico inicial fundamentado sobre um incidente | P01 — Rafael Mendes / C03 | Théo Zago Zimmermann — 22.123.035-2 | 🟨 em andamento — modelos textuais; diagramas ainda são placeholders |
| [T04](05_analise_tarefas/t04.md#hta--t04-investigar-a-propagação-de-uma-falha-entre-serviços-e-entregar-um-retorno-ao-sre) | Investigar a propagação de uma falha entre serviços e entregar um retorno ao SRE | P04 — Camila / C04 | João Sitta Giopatto — 22.123.054-3 | 🟨 em andamento — HTA com diagrama em imagem externa |
| [T05](05_analise_tarefas/t04.md#goms--t05-confirmar-de-quais-serviços-o-serviço-afetado-depende-durante-um-incidente) | Confirmar de quais serviços o serviço afetado depende durante um incidente | P04 — Camila / C04 | João Sitta Giopatto — 22.123.054-3 | 🟨 em andamento — GOMS textual |
| [T06](05_analise_tarefas/t04.md#ctt--t06-comunicar-o-retorno-ao-sre-e-acompanhar-a-decisão) | Comunicar o retorno ao SRE e acompanhar a decisão | P04 — Camila / C04 | João Sitta Giopatto — 22.123.054-3 | 🟨 em andamento — CTT com diagrama em imagem externa |

[?] A frequência das tarefas precisa ser investigada. [H] T01 e T03 são críticas pelo risco de orientar a investigação para o componente errado; T02, pelo risco de concluir que uma correção foi verificada sem evidência suficiente. Essa criticidade é uma interpretação do projeto, não uma medida obtida com participantes.

## Modelos e arquivos

| Tarefa | HTA | GOMS | CTT |
|---|---|---|---|
| T01 | [Diagrama](../assets/05_tarefas/hta_t01.svg) e planos no [texto individual](05_analise_tarefas/t01.md#2-hta--avaliar-uma-hipótese-diagnóstica) | [Modelo textual](05_analise_tarefas/t01.md#3-goms--avaliar-uma-hipótese-diagnóstica) | [Diagrama](../assets/05_tarefas/ctt_t01.svg) e [interpretação](05_analise_tarefas/t01.md#4-ctt--avaliar-uma-hipótese-diagnóstica) |
| T02 | [Diagrama](../assets/05_tarefas/hta_t02.svg) e planos no [texto individual](05_analise_tarefas/t02.md#3-hta--recuperar-avaliar-e-comunicar) | [Modelo textual](05_analise_tarefas/t02.md#4-goms--métodos-para-produzir-o-mesmo-parecer) | [Diagrama](../assets/05_tarefas/ctt_t02.svg) e [interpretação](05_analise_tarefas/t02.md#5-ctt--dependências-entre-consulta-julgamento-e-comunicação) |
| T03 | [Placeholder preservado](../assets/05_tarefas/hta_t03.svg); [modelo textual](05_analise_tarefas/t03.md#2-hta--formular-um-diagnóstico-inicial) | [Modelo textual](05_analise_tarefas/t03.md#3-goms--formular-um-diagnóstico-inicial) | [Placeholder preservado](../assets/05_tarefas/ctt_t03.svg); [modelo textual](05_analise_tarefas/t03.md#4-ctt--formular-um-diagnóstico-inicial) |
| T04 | Diagrama em imagem externa e [planos](05_analise_tarefas/t04.md#hta--t04-investigar-a-propagação-de-uma-falha-entre-serviços-e-entregar-um-retorno-ao-sre) | — | — |
| T05 | — | [Modelo textual](05_analise_tarefas/t04.md#goms--t05-confirmar-de-quais-serviços-o-serviço-afetado-depende-durante-um-incidente) | — |
| T06 | — | — | Diagrama em imagem externa e [legenda](05_analise_tarefas/t04.md#ctt--t06-comunicar-o-retorno-ao-sre-e-acompanhar-a-decisão) |

Os SVGs dos diagramas são também suas fontes editáveis. Os placeholders de T03 não contam como diagramas concluídos e foram mantidos a pedido de Willian para ajuste posterior. Os diagramas de T04 e T06 são imagens anexadas no GitHub, sem arquivo no repositório.

## Síntese inicial da equipe

T03 acompanha a formulação do diagnóstico pelo SRE. T01 aprofunda a avaliação de uma hipótese pelo desenvolvedor antes de orientar uma correção. T02 acompanha o repasse à QA, que precisa distinguir o resultado observado de um teste da conclusão sobre a falha original. Há sobreposição na consulta a evidências, mas os objetivos e os critérios de conclusão são diferentes.

Essa relação é uma proposta de continuidade entre os papéis, não uma sequência obrigatória validada com usuários. A revisão conjunta deve verificar a sobreposição entre T01 e T03, conferir a notação de cada técnica com o material da aula e incorporar a esta síntese as contribuições de Sitta (T04–T06).

| Achado da modelagem | Decisão inicial de design | Origem | Avaliação proposta |
|---|---|---|---|
| Uma hipótese convincente pode ter suporte insuficiente. | Associar explicação e evidências; separar fatos, hipótese e interpretação humana. | T01/T03; H03 | Observar se a pessoa reconhece evidência contraditória antes de comunicar sua conclusão. |
| Recorte incompleto pode excluir informação relevante. | Manter serviço e período visíveis e permitir consulta contextual aos registros. | T01/T03; H01–H03 | Observar se a pessoa identifica a lacuna e busca o registro necessário. |
| O repasse pode perder condições essenciais da falha. | Preservar a origem dos registros e os limites da verificação. | T02; H04–H06 | Observar se a pessoa relaciona incidente e verificação e reconhece diferenças entre ambientes. |
| A comunicação pode precisar terminar com incerteza explícita. | Permitir conclusão limitada ou inconclusiva com justificativa e pendências. | T02/T03; H04/H06 | Observar se a pessoa comunica o que falta sem transformar ausência de dados em certeza. |
| Registrar o parecer não garante que ele ficou disponível à equipe. | Informar sucesso ou falha e preservar o rascunho para recuperação. | T02; H04/H05 | Observar reconhecimento da falha e retomada sem perda do parecer. |

[H] São decisões propostas para o protótipo, ainda a investigar. O protótipo deve priorizar consulta, interpretação e comunicação de um incidente. Execução de correções, gestão ou execução de testes e avaliação científica do algoritmo não são incorporadas por esta entrega. A implementação da interface no TCC continua dependendo da equipe e do orientador.

**Próximas entregas:** T01, T02 e T03 são candidatas à prototipação e à avaliação. Os vínculos com signos, MoLIC, telas do Figma e tarefas formais de teste permanecem **PENDENTE**. A proposta de avaliação de T02 já define instrução neutra e critérios de sucesso no documento individual, sem registrar resultados fictícios.

## Correspondência de identificadores

| Origem | Identificador anterior | Identificador consolidado | Motivo |
|---|---|---|---|
| Gabriel, branch `entega2-lovato` | Lucas como P01 | P02 | Alinhar à persona consolidada na Entrega 3. |
| Gabriel, branch `entega2-lovato` | T01 | T01 | Preservar a tarefa de avaliação de hipótese. |
| Théo, branch `Entrega2_Théo` | T01; C01 citado no texto da Entrega 5 | T03; C03 | Eliminar colisão de tarefa e vincular ao cenário individual já integrado. |
| Théo, branch `Entrega2_Théo` | `hta_t01.svg`; `ctt_t03.svg` | `hta_t03.svg`; `ctt_t03.svg` | Separar o HTA do arquivo de Gabriel e manter os placeholders. |
| Willian | Nova tarefa derivada de P03/C02 | T02; `hta_t02.svg`; `ctt_t02.svg` | Reservar identificadores próprios para o parecer da QA. |
| Sitta, branch `entrega-05-sitta` | T10; T11; T12 | T04; T05; T06 | Substituir a numeração provisória pela sequência da equipe. |

IDs de etapas e métodos internos a um modelo são locais à tarefa: `T02/CTT/I1` e `T03/GOMS/METHOD 2`, por exemplo. Não são novos IDs globais de atividade, MoLIC ou tela.

## Histórico de consolidação

| Data | Alteração | Responsável |
|---|---|---|
| 08/10/2026 | Primeira versão de T02, importação das contribuições T01/T03 com autoria preservada, correção P02/C03, resolução de colisões e síntese inicial. Placeholders de Théo mantidos por solicitação de Willian. | Willian Verenka Oliveira Silva |
| 14/10/2026 | Integração ao histórico Git dos commits de origem de Gabriel e Théo. Aplicação da regra de uma técnica por integrante: T01 mantém o HTA, T02 o CTT e T03 o GOMS; os demais modelos e os placeholders de T03 saíram da entrega e permanecem nos commits de origem (2f91011 e a98ccf9) e no histórico da branch. | Willian Verenka Oliveira Silva |
| 14/10/2026 | Checklist restaurada ao texto do template da disciplina, apenas com marcação; checklists individuais de T01–T03 removidas. Pendências de revisão movidas para a síntese. | Willian Verenka Oliveira Silva |
| 15/10/2026 | CTT de T02 revisado: repetições encerradas por desabilitação (`[>`), com a nova tarefa A3 e o reconhecimento U4. | Willian Verenka Oliveira Silva |
| 21/10/2026 | Correção da regra de 14/10: a disciplina pede 1 HTA, 1 GOMS e 1 CTT por integrante. Restaurados o GOMS e o CTT de T01 e o HTA e o CTT de T03, com `ctt_t01.svg` e os placeholders `hta_t03.svg` e `ctt_t03.svg`. T02 mantém apenas o CTT. | Willian Verenka Oliveira Silva |
| 22/10/2026 | HTA e GOMS de T02 retomados da versão de 08/10 (commit 532bc38) e alinhados ao CTT revisado em 15/10, com `hta_t02.svg` refeito. | Willian Verenka Oliveira Silva |
| 28/10/2026 | Incorporação da contribuição de Sitta (commit 73433ac) em `t04.md`: HTA de T04, GOMS de T05 e CTT de T06, renumerados de T10–T12. Removidas a checklist individual e a nota inicial. | Willian Verenka Oliveira Silva |
| 28/10/2026 | Nomes dos operadores do CTT alinhados aos slides da disciplina em T01, T02 e T04, incluindo as legendas de `ctt_t01.svg` e `ctt_t02.svg`. Planos do HTA de T03 escritos com `>` no lugar de `→`. | Willian Verenka Oliveira Silva |

As referências e os commits de origem estão nos arquivos individuais. Orientações gerais: [Guia de uso](../GUIA_DE_USO.md), [Guia de escopo](../GUIA_ESCOPO_IHC.md) e [Bibliografia](../BIBLIOGRAFIA.md).

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
