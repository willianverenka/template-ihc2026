# Entrega 5 — Análise de tarefas: HTA, GOMS e CTT

[← Início do projeto](../README.md) · [Entrega 4 — Cenários](04_cenarios_problema.md) · [Entrega 6 — Prototipação em papel](06_prototipacao_papel.md)

**Data:** 08/10/2026

**Status:** 🟨 em andamento

**Responsabilidade:** cada integrante modela uma única técnica (HTA, GOMS ou CTT) sobre uma tarefa própria, conforme orientação da disciplina. Distribuição: Gabriel — HTA (T01); Willian — CTT (T02); Théo — GOMS (T03); Sitta — técnica a escolher, sobre tarefa própria derivada de P04.

**Consolidação:** Willian Verenka Oliveira Silva — 22.124.081-5. A autoria dos modelos individuais está identificada em cada arquivo.

## Objetivo e entradas

Modelar tarefas humanas relacionadas à investigação e à comunicação de um incidente. A **HTA** (*Hierarchical Task Analysis*) decompõe a tarefa e explicita seus planos; o **GOMS** (*Goals, Operators, Methods and Selection Rules*) descreve metas, operadores, métodos e regras de seleção; o **CTT** (*ConcurTaskTrees*) representa categorias e relações temporais entre tarefas.

As entradas são a contribuição técnica e as atividades da [Entrega 1](01_conhecendo_o_problema.md), as [personas da Entrega 3](03_personas_contexto_jornada.md) e os [cenários da Entrega 4](04_cenarios_problema.md). Os vínculos estão nas linhas R01–R03 da [matriz de rastreabilidade](../RASTREABILIDADE.md).

[F] Os três trabalhos abaixo estão disponíveis nesta consolidação. [H] Seus fluxos são propostas derivadas das entregas anteriores, ainda sem validação de campo. Modelar uma tarefa não comprova o comportamento do público nem a precisão técnica do pipeline.

## Soluções individuais e seleção de tarefas

| ID | Tarefa | Persona / cenário | Técnica | Autor(a) | Situação |
|---|---|---|---|---|---|
| [T01](05_analise_tarefas/t01.md) | Avaliar uma hipótese diagnóstica e decidir se as evidências a sustentam | P02 — Lucas / C01 | HTA | Gabriel Lovato — 22.123.004-8 | 🟨 em andamento — diagrama, planos e tabela integrados; revisão conjunta pendente |
| [T02](05_analise_tarefas/t02.md) | Emitir um parecer fundamentado sobre a verificação da correção | P03 — Mariana / C02 | CTT | Willian Verenka Oliveira Silva — 22.124.081-5 | 🟨 em andamento — primeira versão com diagrama e interpretação |
| [T03](05_analise_tarefas/t03.md) | Formular um diagnóstico inicial fundamentado sobre um incidente | P01 — Rafael Mendes / C03 | GOMS | Théo Zago Zimmermann — 22.123.035-2 | 🟨 em andamento — modelo textual; revisão conjunta pendente |
| PENDENTE | Tarefa ainda não incorporada | P04 — Camila; vínculo com cenário PENDENTE nesta entrega | A escolher | João Vitor Sitta — 22.123.054-3 | ⬜ não iniciada nesta consolidação — contribuição ainda não incorporada |

[?] A frequência das tarefas precisa ser investigada. [H] T01 e T03 são críticas pelo risco de orientar a investigação para o componente errado; T02, pelo risco de concluir que uma correção foi verificada sem evidência suficiente. Essa criticidade é uma interpretação do projeto, não uma medida obtida com participantes.

## Modelos e arquivos

| Tarefa | Técnica | Modelo | Diagrama |
|---|---|---|---|
| T01 | HTA | [Planos e tabela detalhada](05_analise_tarefas/t01.md#2-hta--avaliar-uma-hipótese-diagnóstica) | [hta_t01.svg](../assets/05_tarefas/hta_t01.svg) |
| T02 | CTT | [Tarefas, expressão e relações temporais](05_analise_tarefas/t02.md#3-ctt--dependências-entre-consulta-julgamento-e-comunicação) | [ctt_t02.svg](../assets/05_tarefas/ctt_t02.svg) |
| T03 | GOMS | [Métodos, operadores e regras de seleção](05_analise_tarefas/t03.md#2-goms--formular-um-diagnóstico-inicial) | Não se aplica: modelo textual |

Os SVGs dos diagramas são também suas fontes editáveis. Os modelos que excediam a regra de uma técnica por integrante saíram da entrega em 14/10/2026 e continuam no histórico Git (veja o [histórico de consolidação](#histórico-de-consolidação)).

## Síntese inicial da equipe

T03 acompanha a formulação do diagnóstico pelo SRE. T01 aprofunda a avaliação de uma hipótese pelo desenvolvedor antes de orientar uma correção. T02 acompanha o repasse à QA, que precisa distinguir o resultado observado de um teste da conclusão sobre a falha original. Há sobreposição na consulta a evidências, mas os objetivos e os critérios de conclusão são diferentes.

Como cada tarefa é analisada por uma técnica diferente, os modelos mostram aspectos complementares do recorte: a decomposição e os planos (HTA de T01), as dependências entre ações do usuário e respostas do sistema (CTT de T02) e a escolha entre métodos (GOMS de T03). Não são três visões da mesma tarefa.

Essa relação é uma proposta de continuidade entre os papéis, não uma sequência obrigatória validada com usuários. A revisão conjunta deve verificar a sobreposição entre T01 e T03 e integrar a contribuição ainda pendente de Sitta.

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
| Equipe, regra de uma técnica por integrante | HTA, GOMS e CTT em T01–T03 | T01/HTA; T02/CTT; T03/GOMS | Aplicar a orientação da disciplina; `ctt_t01.svg`, `hta_t02.svg`, `hta_t03.svg` e `ctt_t03.svg` excluídos. |

IDs de etapas e métodos internos a um modelo são locais à tarefa: `T02/CTT/I1` e `T03/GOMS/METHOD 2`, por exemplo. Não são novos IDs globais de atividade, MoLIC ou tela.

## Histórico de consolidação

| Data | Alteração | Responsável |
|---|---|---|
| 08/10/2026 | Primeira versão de T02, importação das contribuições T01/T03 com autoria preservada, correção P02/C03, resolução de colisões e síntese inicial. Placeholders de Théo mantidos por solicitação de Willian. | Willian Verenka Oliveira Silva |
| 14/10/2026 | Integração ao histórico Git dos commits de origem de Gabriel e Théo. Aplicação da regra de uma técnica por integrante: T01 mantém o HTA, T02 o CTT e T03 o GOMS; os demais modelos e os placeholders de T03 saíram da entrega e permanecem nos commits de origem (2f91011 e a98ccf9) e no histórico da branch. | Willian Verenka Oliveira Silva |

As referências e os commits de origem estão nos arquivos individuais. Orientações gerais: [Guia de uso](../GUIA_DE_USO.md), [Guia de escopo](../GUIA_ESCOPO_IHC.md) e [Bibliografia](../BIBLIOGRAFIA.md).

## Checklist da equipe

- [ ] Cada integrante produziu exatamente uma técnica (HTA, GOMS ou CTT) sobre uma tarefa própria; falta a contribuição de Sitta.
- [x] Os três trabalhos incorporados identificam autor, tarefa e origem.
- [x] O HTA de T01 apresenta planos, além da decomposição.
- [x] O GOMS de T03 distingue metas, operadores, métodos e regras de seleção.
- [x] O CTT de T02 identifica categorias de tarefa e relações temporais.
- [ ] Conferir a legibilidade dos diagramas (HTA de T01 e CTT de T02) e sua correspondência com o texto; o CTT de T02 já foi conferido.
- [ ] Conferir a notação de cada técnica com o material da aula.
- [x] As tarefas incorporadas estão vinculadas a personas/cenários em R01–R03.
- [x] Modelagens tratam de tarefas humanas, sem incorporar etapas internas do algoritmo.
- [x] Hipóteses, lacunas e limites do escopo permanecem explícitos.
- [ ] Revisar a síntese com a equipe, incluindo a contribuição pendente e a sobreposição T01/T03.
- [ ] Definir a cobertura final do protótipo e dos testes nas entregas correspondentes.
