# Matriz de rastreabilidade de IHC

A matriz deve ser atualizada ao longo do semestre. Ela ajuda a demonstrar que a interface não surgiu arbitrariamente e registra **como o conhecimento da equipe evoluiu**.

Para projetos cujo TCC não previa interface, esta matriz é especialmente importante: deve ficar visível a passagem da **contribuição técnica do TCC** para um **cenário de uso plausível**, e desse cenário para as decisões de interação.

## 1. Derivação do escopo de IHC a partir do TCC

| Elemento | Registro da equipe | Evidência/justificativa | Estado |
|---|---|---|---|
| Tema do TCC | {{...}} | {{documento/TCC}} | definido |
| Resultado técnico esperado | {{algoritmo, análise, sistema, modelo, API...}} | {{...}} | definido |
| O TCC previa interface? | sim / não / parcialmente | {{...}} | definido |
| Capacidade/contribuição central | {{o que a tecnologia permite}} | {{...}} | definido |
| Possíveis beneficiários/stakeholders | {{...}} | {{fonte ou hipótese}} | F / H / ? |
| Usuário escolhido para IHC | {{...}} | {{por que esse perfil}} | F / H / ? |
| Objetivo principal do usuário | {{...}} | {{...}} | F / H / ? |
| Contexto de uso adotado | {{...}} | {{...}} | F / H / ? |
| Interface/recorte de IHC | {{...}} | {{como deriva dos itens acima}} | proposta / revisada |
| Relação com o TCC | parte prevista / extensão conceitual / protótipo demonstrativo / outra | {{...}} | definido |

> Se o escopo de IHC mudar ao longo do semestre, preserve a decisão anterior no histórico e registre **qual evidência motivou a mudança**.

## 2. Registro de hipóteses e lacunas

Use esta tabela para itens importantes marcados como `[H]` ou `[?]`, indicando a entrega de origem. Preserve o histórico: não apague uma hipótese refutada.

| ID | Afirmação / dúvida inicial | Tipo | Por que importa | Como/onde investigar | Evidência obtida | Estado atual | Impacto no projeto |
|---|---|---|---|---|---|---|---|
| H01 | {{...}} | H / ? | {{...}} | Entrega 2 / 3 / 7 / outra | {{link/fonte ou PENDENTE}} | aberta / sustentada / refutada / refinada | {{...}} |
| H02 | {{...}} | H / ? | {{...}} | {{...}} | {{...}} | aberta | {{...}} |
| H03 | [H] Hipóteses geradas pelo modelo de linguagem podem ser mais úteis ao SRE quando acompanhadas das evidências estruturais que as sustentam. Origem: Entrega 1, seção 10. | H | Permite investigar como o profissional avalia uma explicação antes de comunicá-la. | Entrega 7; questões Q1, Q4 e Q5 de C03. | PENDENTE — sem validação de campo registrada. | aberta | Investigar a sustentação e os limites do diagnóstico comunicado em C03. |
| H04 | [H] A investigação pode ocorrer sob pressão de tempo e envolver colaboração entre SRE, desenvolvedores e gestores; políticas de acesso e dados sensíveis podem limitar a consulta e o compartilhamento de evidências. Origem: Entrega 1, seção 5.4. | H | Contextualiza as dependências entre profissionais e as restrições de acesso discutidas em C02. | Entrega 7; questões Q3, Q4 e Q6 de C02. | PENDENTE — hipótese documental, sem validação de campo registrada. | aberta | Investigar a continuidade do contexto até a verificação por P03. |
| H05 | [H] Um repasse sem condições de reprodução e evidências relacionáveis ao incidente pode obrigar a QA a reconstruir parte da investigação antes de verificar uma correção. Origem: Entrega 4, C02, a partir das dores e necessidades de P03. | H | Pode explicar retrabalho e demora na verificação. | Entrega 7; questões Q1 e Q3 de C02. | PENDENTE — refinamento analítico da proto-persona, sem coleta de campo. | aberta | Investigar quais informações precisam acompanhar o diagnóstico compartilhado. |
| H06 | [H] Diferenças entre ambientes e limites de acesso ou cobertura da telemetria podem dificultar que a QA diferencie um teste sem erro de evidência suficiente de correção da falha original. Origem: Entrega 4, C02, a partir das restrições e dores de P03. | H | Pode explicar uma conclusão inconclusiva ou uma confirmação prematura. | Entrega 7; questões Q2, Q4 e Q5 de C02. | PENDENTE — refinamento analítico da proto-persona, sem coleta de campo. | aberta | Investigar a compreensão dos limites das evidências; não pressupor confirmação automática da correção. |

## 3. Rastreabilidade entre contribuição técnica, necessidades e artefatos

| ID | Capacidade do TCC utilizada | Necessidade/problema | Persona | Cenário problema | Objetivo/tarefa | HTA/GOMS/CTT | Cenário de interação / signos | MoLIC | Tela(s) Figma | Heurística / problema | Tarefa no teste | Decisão/melhoria |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| R01 | Seleção de evidências de observabilidade e geração de hipóteses diagnósticas. | Reduzir o esforço para localizar, correlacionar e interpretar evidências durante a investigação de um incidente; hipóteses H01 a H04. | [P02 — Lucas](docs/03_personas_contexto_jornada.md#persona-p02--lucas-o-desenvolvedor-sênior) | [C01 — Investigação de falha no checkout após um deploy](docs/04_cenarios_problema/c01.md#cenário-c01--investigação-de-falha-no-checkout-após-um-deploy) | A01 — corrigir bugs; [T01 — avaliar uma hipótese diagnóstica](docs/05_analise_tarefas/t01.md). A tarefa termina com a avaliação, antes da correção. | [HTA/GOMS/CTT — T01](docs/05_analise_tarefas/t01.md); diagramas incorporados. | PENDENTE | PENDENTE | PENDENTE | PENDENTE | PENDENTE | Associar a hipótese às evidências e registrar suporte, contradições e limites; proposta ainda a validar. |
| R02 | Seleção de evidências de observabilidade e geração de hipóteses diagnósticas; uso por P03 ainda a investigar. | Recuperar contexto e avaliar a suficiência das evidências de um incidente para verificar sua correção; H04, H05 e H06. | [P03 — Mariana](docs/03_personas_contexto_jornada.md#persona-p03--mariana-a-analista-de-qa) | [C02 — O teste passou, mas a correção ainda é incerta](docs/04_cenarios_problema/c02.md#cenário-c02--o-teste-passou-mas-a-correção-ainda-é-incerta) | A03 — classificar se a falha foi resolvida; [T02 — emitir um parecer sobre a verificação da correção](docs/05_analise_tarefas/t02.md). | [HTA/GOMS/CTT — T02](docs/05_analise_tarefas/t02.md); diagramas incorporados. | PENDENTE | PENDENTE | PENDENTE | PENDENTE | PENDENTE | Preservar contexto e distinguir teste bem-sucedido de correção sustentada. Permitir parecer inconclusivo e recuperação de falha de comunicação; P03 permanece secundária, sem gestão ou execução de testes. |
| R03 | Geração de hipóteses diagnósticas associadas a evidências de observabilidade. | Avaliar explicações concorrentes e comunicar suas limitações antes de encaminhar uma ação; H03 e H04. | [P01 — Rafael](docs/03_personas_contexto_jornada.md#persona-p01--rafael-mendes) / [P02 — Lucas](docs/03_personas_contexto_jornada.md#persona-p02--lucas-o-desenvolvedor-sênior) | [C03 — Dificuldade em distinguir a causa de um incidente de seus efeitos](docs/04_cenarios_problema/c03.md#cenário-c03--dificuldade-em-distinguir-a-causa-de-um-incidente-de-seus-efeitos) | A02 — classificar a saúde do sistema; [T03 — formular um diagnóstico inicial fundamentado](docs/05_analise_tarefas/t03.md). | [HTA/GOMS/CTT — T03](docs/05_analise_tarefas/t03.md); diagramas incorporados. | PENDENTE | PENDENTE | PENDENTE | PENDENTE | PENDENTE | Investigar critérios de sustentação do diagnóstico e comunicação de incerteza; preservar a distinção entre o componente que origina a falha e os que apresentam efeitos. |
| R04 | Filtragem estrutural em grafos de observabilidade para selecionar evidências. | Identificar evidências relevantes de observabilidade, compreender as relações entre serviços e organizar um contexto técnico suficiente para apoiar a investigação de um incidente; H01, H02 e H03. | [P04 — Camila](docs/03_personas_contexto_jornada.md#persona-p04--camila-nunes) | [C04 — Investigação de uma falha propagada entre microsserviços](docs/04_cenarios_problema/c04.md#cenário-c04--investigação-de-uma-falha-propagada-entre-microsserviços) | [T04–T06 — investigar a propagação, confirmar dependências e comunicar o retorno ao SRE](docs/05_analise_tarefas/t04.md) | [HTA — T04; GOMS — T05; CTT — T06](docs/05_analise_tarefas/t04.md); diagramas em imagens externas. | PENDENTE | PENDENTE | PENDENTE | PENDENTE | PENDENTE | PENDENTE |

**Consolidação da Entrega 5 (08/10/2026):** T01 identifica a contribuição de Gabriel, T02 a de Willian e T03 a de Théo. A antiga T01 de Théo passou a T03; sua referência C01 foi corrigida para C03 e Lucas foi alinhado a P02 no trabalho de Gabriel. Veja o [histórico de correspondência](docs/05_analise_tarefas.md#correspondência-de-identificadores). IDs internos de etapas/métodos são locais a cada tarefa. A correção documental não valida as hipóteses. Em 14/10/2026, aplicou-se a regra de uma técnica por integrante: T01/HTA (Gabriel), T02/CTT (Willian) e T03/GOMS (Théo); a técnica de Sitta segue PENDENTE. Em 21/10/2026, a regra foi corrigida para 1 HTA, 1 GOMS e 1 CTT por integrante: T01 e T03 voltaram a ter as três técnicas, e T02 mantém apenas o CTT. Em 22/10/2026, T02 recebeu HTA e GOMS. Em 28/10/2026, a contribuição de Sitta foi incorporada como T04 (HTA), T05 (GOMS) e T06 (CTT).

## 4. Rastreabilidade de padrões de interface

Use esta tabela quando o projeto incorporar padrões como dashboard, relatório, histórico, filtros ou administração. O objetivo é **justificar o padrão**, não apenas listar telas.

| ID da tela/fluxo | Padrão de interface | Objetivo/tarefa que justifica | Informação/ação principal | Evidência de necessidade | Artefatos relacionados |
|---|---|---|---|---|---|
| F01 | Delimitação por serviço, sintoma e período | T03 | Definir e ajustar o recorte do incidente. | Entrega 1, seção 9.2; C03; necessidade ainda a validar. | P01/C03/T03; tela e MoLIC PENDENTE. |
| F02 | Inspeção contextual do subgrafo | T01/T03 | Relacionar componentes e acessar os registros pertinentes. | Entrega 1, seção 9.2; H01/H03; modelagens T01/T03. | P01/P02, C01/C03; tela e MoLIC PENDENTE. |
| F03 | Hipóteses associadas a evidências | T01/T03; contexto de entrada de T02 | Examinar o suporte e os limites da explicação. | Entrega 1, seção 9.2; H03; repasse à QA relacionado a H05/H06. | T01/T02/T03; tela e MoLIC PENDENTE. |
| PENDENTE | Registro e comunicação contextual de parecer | T02; comunicação também presente em T01/T03 | Preservar conclusão, referências, limitações e confirmação de disponibilidade. | P03/C02, H04–H06; proposta de design de T02, sem validação empírica. | R02/T02; signos, tela e MoLIC PENDENTE. |

F01–F03 preservam os identificadores **funcionais da Entrega 1**, não designam telas já produzidas no Figma. As linhas genéricas do template (dashboard, histórico e CRUD) foram substituídas pelos vínculos documentados; não constituíam funcionalidades aprovadas do projeto.

## 5. Registro de mudanças de escopo

| Data | O que mudou | Evidência/feedback que motivou | Artefatos afetados | Responsável |
|---|---|---|---|---|
| {{...}} | {{...}} | {{...}} | {{...}} | {{...}} |
| 17/09/2026 | C02 detalha uma necessidade já prevista em A03/P03 e explicita H05 e H06; mantém o recorte de apoio à compreensão e comunicação do incidente. Não inclui gestão ou execução de testes no escopo. | Orientação para descrever as dificuldades anteriores à solução; base documental em P03 e H04, ainda sem validação de campo. | Entrega 4 (C02), R02 e registro de hipóteses; checklist final. | Willian Verenka Oliveira Silva |
| 08/10/2026 | T02 detalha a interpretação e comunicação do parecer de P03/C02, incluindo conclusão inconclusiva e recuperação de falha de comunicação. Mantém o recorte e não incorpora gestão/execução de testes nem aprovação automática da liberação. | Solicitação de Willian para iniciar sua análise seguindo C02; base documental P03, H04–H06, ainda sem coleta de campo. | Entrega 5, R02, vínculo em C02 e checklist final. | Willian Verenka Oliveira Silva |
| 14/10/2026 | A Entrega 5 passa a exigir uma técnica por integrante. Mantidos o HTA de T01, o CTT de T02 e o GOMS de T03; os demais modelos saem da entrega e permanecem no histórico Git. Tarefas, personas, cenários e recorte de IHC não mudam. | Orientação da disciplina sobre a responsabilidade individual na Entrega 5, repassada por Willian. | Entrega 5 (índice e T01–T03), R01–R03, README, checklist final, C02/C03 e diagramas `ctt_t01`, `hta_t02`, `hta_t03` e `ctt_t03`. | Willian Verenka Oliveira Silva |
| 21/10/2026 | A Entrega 5 volta a exigir 1 HTA, 1 GOMS e 1 CTT por integrante. Restaurados o GOMS e o CTT de T01 e o HTA e o CTT de T03; T02 mantém apenas o CTT. Tarefas, personas, cenários e recorte de IHC não mudam. | A regra de uma técnica por integrante, aplicada em 14/10, foi um equívoco da consolidação; o template da disciplina pede as três técnicas. Correção informada por Willian. | Entrega 5 (índice e T01–T03), R01, R03, README e diagramas `ctt_t01`, `hta_t03` e `ctt_t03`. | Willian Verenka Oliveira Silva |

## Como usar

- Use identificadores estáveis (`H01`, `P01`, `C01`, `T01`, `M01`, `F01`, `UT01`).
- Quando uma necessidade/problema tiver origem em hipótese da Entrega 1, cite o ID correspondente.
- Em TCC sem interface original, pelo menos uma linha deve mostrar claramente **como uma capacidade técnica chega até uma tarefa de usuário e uma tela/fluxo**.
- Uma linha pode se desdobrar quando um objetivo possui múltiplos caminhos.
- Não force relação inexistente: se algo ainda não foi modelado, marque `PENDENTE`.
- Ao remover uma funcionalidade, registre a decisão em vez de apagar silenciosamente o histórico.
- Dashboard, CRUD, filtros e relatórios só devem aparecer quando houver objetivo/tarefa que os justifique.
