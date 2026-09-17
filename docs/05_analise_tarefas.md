# Entrega 5 — Análise de tarefas: HTA, GOMS e CTT

**Data:** 10/09/2026

**Status:** 🟨 em andamento

**Responsabilidade:** cada integrante modela pelo menos 1 HTA, 1 GOMS e 1 CTT. As três técnicas podem abordar a mesma funcionalidade ou funcionalidades distintas, conforme a orientação da disciplina.

## Objetivo da atividade

Modelar tarefas importantes sob perspectivas complementares: decomposição hierárquica (HTA), estrutura de metas/métodos/operações (GOMS) e relações temporais entre tarefas (CTT). O diagrama deve ser acompanhado de interpretação textual.

## Para projetos cujo TCC não previa interface

Modele **tarefas humanas relacionadas ao uso da contribuição técnica**, e não a implementação interna do algoritmo. Exemplos de boas tarefas para análise:

- investigar uma consulta de baixo desempenho;
- configurar uma análise e selecionar parâmetros;
- submeter um dataset e verificar sua validade;
- acompanhar uma execução demorada;
- comparar dois resultados/modelos;
- interpretar uma recomendação e decidir se a aceita;
- localizar uma execução anterior usando busca/filtros;
- gerar e compartilhar um relatório;
- administrar papéis/permissões quando isso for parte do trabalho real;
- revisar um alerta e registrar uma decisão.

Um CRUD pode gerar tarefas relevantes, mas “cadastrar usuário” só merece modelagem se tiver significado no domínio (papéis, validações, riscos, permissões, dependências).

## Seleção das tarefas

| ID | Tarefa | Persona/cenário de origem | Frequência/criticidade | Autor responsável |
|---|---|---|---|---|
| T01 | Avaliar uma hipótese diagnóstica e decidir se ela é sustentada pelas evidências | P01 / C01 / H03 | Recorrente durante diagnósticos; criticidade alta por influenciar a ação corretiva | Gabriel Lovato |

> Priorize tarefas necessárias para que o usuário alcance objetivos centrais. Não desperdice a modelagem em ações triviais isoladas, como “clicar em login”, se o objetivo relevante é maior. Da mesma forma, não modele o funcionamento interno do algoritmo como se fosse uma tarefa humana.

---

## HTA — T01 Avaliar uma hipótese diagnóstica e suas evidências

**Autor(a):** Gabriel Lovato — 22.123.004-8

### Descrição da tarefa

O objetivo de Lucas é avaliar criticamente uma hipótese diagnóstica produzida pelo pipeline do TCC e decidir se ela pode orientar a ação corretiva. A tarefa começa quando uma hipótese apresenta uma causa provável e termina quando Lucas a classifica como sustentada, parcialmente sustentada ou não sustentada, registrando sua justificativa. Para isso, ele precisa compreender a afirmação, inspecionar as evidências estruturais associadas, confrontá-las com o contexto operacional e preservar contradições e incertezas. Essa tarefa deriva diretamente de H03 e não pressupõe que a resposta do LLM esteja correta.

### Diagrama

![HTA T01](../assets/05_tarefas/hta_t01.svg)

*Figura 1 — HTA da tarefa T01. Fonte: elaboração do autor.*

### Decomposição e planos

| ID | Objetivo/operação | Plano/ordem | Problema ou decisão de design observada |
|---|---|---|---|
| 0 | Avaliar uma hipótese diagnóstica e decidir se ela é sustentada | Plano 0: executar 1 > 2 > 3 > 4; se houver lacunas relevantes, retornar a 2 ou 3; depois executar 5. | A conclusão do LLM não pode ser aceita automaticamente; o usuário precisa conseguir revisar o raciocínio. |
| 1 | Compreender a hipótese apresentada | Plano 1: executar 1.1 > 1.2. | Termos vagos ou excesso de confiança podem induzir uma interpretação incorreta. |
| 1.1 | Identificar a causa e o serviço apontados | — | A afirmação principal precisa ser distinguível das explicações secundárias. |
| 1.2 | Identificar impacto, propagação e grau de incerteza | — | A ausência de limites e incertezas pode fazer a hipótese parecer conclusiva. |
| 2 | Inspecionar as evidências associadas | Plano 2: executar 2.1; repetir 2.2 e 2.3 para cada componente relevante. | H03 indica que a utilidade da hipótese depende da possibilidade de inspecionar o que a sustenta. |
| 2.1 | Examinar o caminho destacado no subgrafo | — | O usuário precisa compreender quais relações foram consideradas relevantes. |
| 2.2 | Aprofundar spans, logs e metadados citados | — | Detalhes em excesso podem reproduzir a sobrecarga registrada em H02. |
| 2.3 | Marcar evidências favoráveis, ausentes ou contraditórias | — | Contradições não devem desaparecer sob uma explicação textual convincente. |
| 3 | Confrontar a hipótese com o contexto operacional | Plano 3: executar 3.1 > 3.2; executar 3.3 somente se permanecer uma lacuna importante. | A correlação estrutural ou temporal, isoladamente, não prova causalidade. |
| 3.1 | Comparar horários, arquitetura e mudanças recentes | — | Um deploy coincidente pode ser relevante ou apenas uma correlação enganosa. |
| 3.2 | Verificar se a ordem dos eventos é compatível com a causa alegada | — | Um efeito posterior não deve ser tratado como evento originador. |
| 3.3 | Consultar telemetria adicional quando necessário | — | A revisão precisa permitir buscar evidência fora do conjunto inicialmente filtrado. |
| 4 | Decidir o resultado da avaliação | Plano 4: escolher 4.1, 4.2 ou 4.3 de acordo com a suficiência e a consistência das evidências. | A decisão não deve ser reduzida a aceitar ou rejeitar quando apenas parte da hipótese é sustentada. |
| 4.1 | Classificar como sustentada | — | Aplicável quando a causa alegada é compatível com as evidências relevantes. |
| 4.2 | Classificar como parcialmente sustentada e refiná-la | — | Preserva elementos úteis sem aceitar trechos não comprovados. |
| 4.3 | Classificar como não sustentada | — | Evita que uma explicação plausível, mas contraditória, oriente a correção. |
| 5 | Registrar e comunicar a decisão | Plano 5: executar 5.1 > 5.2. | A justificativa deve permitir revisão posterior por SREs e desenvolvedores. |
| 5.1 | Registrar classificação, justificativa e incertezas | — | Sem justificativa, a decisão humana perde rastreabilidade. |
| 5.2 | Compartilhar a avaliação com a equipe envolvida | — | O destinatário precisa distinguir a hipótese original da conclusão revisada. |

**Verificação do HTA:**

- O objetivo 0 representa uma meta do usuário?
- As subtarefas são necessárias e suficientes?
- Os **planos** indicam ordem, alternativa, repetição ou condição?
- A decomposição parou em nível útil para projeto de interação?

---

## GOMS — T01 Avaliar uma hipótese diagnóstica e suas evidências

**Autor(a):** Gabriel Lovato — 22.123.004-8

### Goal

`G0: decidir se uma hipótese diagnóstica é sustentada pelas evidências do incidente.`

### Métodos, operadores e regras de seleção

- **Method M1 — revisão guiada pelas evidências citadas:** ler a hipótese; identificar a causa alegada; localizar os nós e spans citados; examinar cada evidência; verificar a ordem dos eventos; comparar evidências favoráveis e contraditórias; classificar a hipótese; registrar a justificativa.
  - **Operators:** perceber; ler; localizar; selecionar; navegar; inspecionar; comparar; interpretar; decidir; registrar.
- **Method M2 — revisão orientada pelo subgrafo:** examinar o caminho anômalo; identificar o primeiro componente com desvio relevante; consultar a hipótese associada; aprofundar os spans desse componente; comparar o caminho observado com a explicação; classificar a hipótese; registrar a justificativa.
  - **Operators:** examinar; reconhecer; selecionar; seguir relações; ler; comparar; interpretar; decidir; registrar.
- **Method M3 — revisão diante de contradição:** identificar a evidência contraditória; ampliar o período ou o conjunto de serviços; consultar telemetria adicional; reavaliar a ordem causal; refinar ou rejeitar a hipótese; registrar a divergência e as incertezas restantes.
  - **Operators:** reconhecer conflito; definir critérios; ajustar escopo; buscar; comparar; julgar; editar; decidir; registrar.
- **Selection Rule SR1:** usar M1 quando a hipótese trouxer evidências estruturais explicitamente relacionadas; usar M2 quando Lucas preferir partir do caminho anômalo para conferir a explicação; usar M3 quando uma evidência relevante contrariar ou não estiver coberta pela hipótese.
- **Selection Rule SR2:** classificar como sustentada quando a causa alegada for compatível com as evidências relevantes; como parcialmente sustentada quando somente parte da explicação resistir à revisão; e como não sustentada quando houver contradição importante ou ausência de suporte.

> Não chame qualquer passo de “método”. Em GOMS, métodos são sequências alternativas capazes de atingir uma meta; regras de seleção explicam quando escolher entre eles.

---

## CTT — T01 Avaliar uma hipótese diagnóstica e suas evidências

**Autor(a):** Gabriel Lovato — 22.123.004-8

### Descrição

A modelagem CTT representa a revisão humana de uma hipótese gerada pelo pipeline. Depois de acessar e interpretar a afirmação principal, Lucas inspeciona de forma intercalada o subgrafo, os spans e os logs relacionados. Ele confronta essas evidências com o contexto operacional. Caso encontre uma lacuna ou contradição importante, amplia a evidência consultada e repete a comparação. Quando possui base suficiente, escolhe entre sustentar, refinar ou rejeitar a hipótese, registra a justificativa e compartilha a avaliação.

### Diagrama

![CTT T01](../assets/05_tarefas/ctt_t01.svg)

*Figura 2 — CTT da tarefa T01. Fonte: elaboração do autor.*

### Legenda e relações temporais usadas

| Operador/relação | Significado no diagrama | Exemplo no modelo |
|---|---|---|
| `>>` (habilitação) | A tarefa da esquerda deve terminar antes do início da tarefa da direita. | Interpretar a hipótese `>>` inspecionar suas evidências. |
| `|||` (intercalação) | As tarefas podem progredir de forma alternada, sem exigir uma ordem fixa. | Examinar o subgrafo `|||` aprofundar spans `|||` consultar logs. |
| `[]` (escolha) | Apenas um dos caminhos é seguido de acordo com a condição encontrada. | Sustentar `[]` refinar `[]` rejeitar a hipótese. |
| `*` (iteração) | A tarefa pode ser repetida enquanto a condição de saída não for atingida. | Ampliar e comparar evidências enquanto houver lacunas relevantes. |

Identifique, quando aplicável, tarefas de usuário, sistema, interação e tarefas abstratas. Verifique se concorrência, escolha, habilitação, desabilitação e repetição estão representadas corretamente segundo a notação adotada em aula.

---

## Síntese da contribuição individual

As três modelagens mostram que a revisão de uma hipótese diagnóstica não equivale a simplesmente aceitá-la ou rejeitá-la. Lucas precisa localizar o suporte estrutural da afirmação, reconhecer contradições, buscar contexto adicional e registrar por que chegou à sua decisão. A categoria “parcialmente sustentada” é necessária para preservar partes úteis de uma explicação sem validar trechos sem evidência.

Para as próximas etapas, devem ser priorizadas a ligação entre afirmação e evidência, a comparação entre sinais favoráveis e contraditórios, a consulta progressiva de detalhes e o registro da decisão humana com suas incertezas. No protótipo e no teste de usabilidade, a T01 deve incluir uma hipótese plausível com pelo menos uma evidência ambígua, permitindo observar se o participante revisa criticamente o resultado em vez de confiar automaticamente no texto gerado.

## Checklist

- [ ] Cada integrante produziu ao menos 1 HTA, 1 GOMS e 1 CTT. *(Pendente: este arquivo contém somente a contribuição individual de Gabriel.)*
- [x] Cada artefato identifica autor e tarefa.
- [x] Diagramas são legíveis e possuem fonte editável quando possível.
- [x] HTA contém planos, não apenas árvore de tópicos.
- [x] GOMS distingue Goals, Operators, Methods e Selection Rules.
- [x] CTT usa operadores temporais e tipos de tarefa coerentes.
- [x] Há texto explicando cada diagrama.
- [ ] Tarefas estão ligadas a cenários/personas na rastreabilidade. *(T01 ainda precisa ser consolidada pela equipe na matriz.)*
- [x] Em TCC técnico, as tarefas descrevem o que a pessoa faz com a contribuição/resultados, não passos internos do código.
- [x] CRUDs, relatórios, filtros e atividades administrativas foram escolhidos por relevância ao objetivo do usuário.
