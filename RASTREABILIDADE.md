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
| H04 | [H] A investigação pode ocorrer sob pressão de tempo e envolver colaboração entre SRE, desenvolvedores e gestores; políticas de acesso e dados sensíveis podem limitar a consulta e o compartilhamento de evidências. Origem: Entrega 1, seção 5.4. | H | Contextualiza as dependências entre profissionais e as restrições de acesso discutidas em C02. | Entrega 7; questões Q3, Q4 e Q6 de C02. | PENDENTE — hipótese documental, sem validação de campo registrada. | aberta | Investigar a continuidade do contexto até a verificação por P03. |
| H05 | [H] Um repasse sem condições de reprodução e evidências relacionáveis ao incidente pode obrigar a QA a reconstruir parte da investigação antes de verificar uma correção. Origem: Entrega 4, C02, a partir das dores e necessidades de P03. | H | Pode explicar retrabalho e demora na verificação. | Entrega 7; questões Q1 e Q3 de C02. | PENDENTE — refinamento analítico da proto-persona, sem coleta de campo. | aberta | Investigar quais informações precisam acompanhar o diagnóstico compartilhado. |
| H06 | [H] Diferenças entre ambientes e limites de acesso ou cobertura da telemetria podem dificultar que a QA diferencie um teste sem erro de evidência suficiente de correção da falha original. Origem: Entrega 4, C02, a partir das restrições e dores de P03. | H | Pode explicar uma conclusão inconclusiva ou uma confirmação prematura. | Entrega 7; questões Q2, Q4 e Q5 de C02. | PENDENTE — refinamento analítico da proto-persona, sem coleta de campo. | aberta | Investigar a compreensão dos limites das evidências; não pressupor confirmação automática da correção. |

## 3. Rastreabilidade entre contribuição técnica, necessidades e artefatos

| ID | Capacidade do TCC utilizada | Necessidade/problema | Persona | Cenário problema | Objetivo/tarefa | HTA/GOMS/CTT | Cenário de interação / signos | MoLIC | Tela(s) Figma | Heurística / problema | Tarefa no teste | Decisão/melhoria |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| R01 | Seleção de evidências de observabilidade e geração de hipóteses diagnósticas. | Reduzir o esforço para localizar, correlacionar e interpretar evidências durante a investigação de um incidente; hipóteses H01 a H04. | [P02 — Lucas](docs/03_personas_contexto_jornada.md#persona-p02--lucas-o-desenvolvedor-sênior) | [C01 — Investigação de falha no checkout após um deploy](docs/04_cenarios_problema/c01.md#cenário-c01--investigação-de-falha-no-checkout-após-um-deploy) | A01 — corrigir bugs; delimitar, investigar e comunicar o diagnóstico inicial. Tarefas da Entrega 5 nesta branch: PENDENTE. | PENDENTE | PENDENTE | PENDENTE | PENDENTE | PENDENTE | PENDENTE | Preservar o contexto entre SRE e desenvolvedor e investigar os critérios usados para distinguir causa de efeitos propagados. |
| R02 | Seleção de evidências de observabilidade e geração de hipóteses diagnósticas; uso por P03 ainda a investigar. | Recuperar contexto e avaliar a suficiência das evidências de um incidente para verificar sua correção; H04, H05 e H06. | [P03 — Mariana](docs/03_personas_contexto_jornada.md#persona-p03--mariana-a-analista-de-qa) | [C02 — O teste passou, mas a correção ainda é incerta](docs/04_cenarios_problema/c02.md#cenário-c02--o-teste-passou-mas-a-correção-ainda-é-incerta) | A03 — classificar se a falha foi resolvida; tarefa da Entrega 5: PENDENTE. | PENDENTE | PENDENTE | PENDENTE | PENDENTE | PENDENTE | PENDENTE | Investigar a preservação do contexto e os limites das evidências no repasse à QA; manter P03 como persona secundária. |

## 4. Rastreabilidade de padrões de interface

Use esta tabela quando o projeto incorporar padrões como dashboard, relatório, histórico, filtros ou administração. O objetivo é **justificar o padrão**, não apenas listar telas.

| ID da tela/fluxo | Padrão de interface | Objetivo/tarefa que justifica | Informação/ação principal | Evidência de necessidade | Artefatos relacionados |
|---|---|---|---|---|---|
| F01 | dashboard | {{T01}} | {{...}} | {{H01/evidência...}} | {{C01/M01}} |
| F02 | histórico com filtros | {{T02}} | {{...}} | {{...}} | {{...}} |
| F03 | administração/CRUD | {{T03}} | {{...}} | {{...}} | {{...}} |

## 5. Registro de mudanças de escopo

| Data | O que mudou | Evidência/feedback que motivou | Artefatos afetados | Responsável |
|---|---|---|---|---|
| {{...}} | {{...}} | {{...}} | {{...}} | {{...}} |
| 17/09/2026 | C02 detalha uma necessidade já prevista em A03/P03 e explicita H05 e H06; mantém o recorte de apoio à compreensão e comunicação do incidente. Não inclui gestão ou execução de testes no escopo. | Orientação para descrever as dificuldades anteriores à solução; base documental em P03 e H04, ainda sem validação de campo. | Entrega 4 (C02), R02 e registro de hipóteses; checklist final. | Willian Verenka Oliveira Silva |

## Como usar

- Use identificadores estáveis (`H01`, `P01`, `C01`, `T01`, `M01`, `F01`, `UT01`).
- Quando uma necessidade/problema tiver origem em hipótese da Entrega 1, cite o ID correspondente.
- Em TCC sem interface original, pelo menos uma linha deve mostrar claramente **como uma capacidade técnica chega até uma tarefa de usuário e uma tela/fluxo**.
- Uma linha pode se desdobrar quando um objetivo possui múltiplos caminhos.
- Não force relação inexistente: se algo ainda não foi modelado, marque `PENDENTE`.
- Ao remover uma funcionalidade, registre a decisão em vez de apagar silenciosamente o histórico.
- Dashboard, CRUD, filtros e relatórios só devem aparecer quando houver objetivo/tarefa que os justifique.
