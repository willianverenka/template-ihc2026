# Entrega 2 — Público-alvo e análise de concorrência

**Data:** 03/09/2026

**Status:** 🟨 em andamento

**Responsabilidade mínima:** cada integrante analisa pelo menos 1 concorrente/interface representativa; a equipe produz síntese comparativa.

## Objetivo da atividade

Compreender soluções do mesmo domínio **e também interfaces familiares ao público-alvo**. O objetivo não é copiar telas, mas identificar convenções, padrões, affordances percebidas, problemas recorrentes, expectativas e oportunidades de design.

> **Concorrente não precisa ser idêntico ao produto.** Pode atuar na mesma área, resolver objetivo semelhante ou disputar a mesma necessidade. Quando não houver concorrente direto, use produtos análogos e softwares que o público já utiliza.

### Para TCCs que não previam interface

Não procure apenas um “concorrente do algoritmo”. Investigue **interfaces profissionais que materializam atividades semelhantes** às que o usuário escolhido precisaria realizar.

Exemplos:

- TCC de banco de dados → consoles de administração, ferramentas para DBA, monitoramento e análise de consultas;
- TCC de LLM/ML → painéis de experimentos, gestão de modelos/datasets, comparação de métricas, revisão de resultados;
- TCC de análise de dados → dashboards, ferramentas de BI, filtros, relatórios e exploração;
- TCC de infraestrutura/API → portais administrativos, observabilidade, logs, gestão de credenciais e uso;
- TCC de cibersegurança → consoles de alertas, triagem, histórico e auditoria.

A pergunta é: **“que convenções esse perfil já conhece para executar tarefas equivalentes?”**

## Entrada obrigatória da Entrega 1

Retome o mapa inicial de alternativas e produtos citado na Entrega 1. Aqui a equipe deixa de trabalhar apenas com impressão inicial e passa a **investigar sistematicamente** cada solução.

| Item citado na Entrega 1 | Tipo | Por que foi citado | Status inicial | Decisão nesta entrega |
|---|---|---|---|---|
| Consulta e filtragem manual de logs, métricas e traces | processo atual | É a forma de localizar sintomas e evidências antes do apoio proposto pelo TCC | [F] | manter como referência do problema atual |
| Mapas de serviços e navegação entre sinais | padrão de interface profissional | Apoiam a investigação de dependências e da propagação de falhas | [F] | analisar nos concorrentes C01, C02 e C03 |
| Datadog | concorrente/análogo | Reúne observabilidade, filtros, traces, mapas de dependência e investigação de incidentes | [F] | analisar em C01 |
| New Relic | concorrente direto quanto à atividade | Apoia triagem, correlação de sinais e diagnóstico assistido por IA | [F] — incluído durante a Entrega 2 | analisar em C02 |
| Dynatrace | concorrente direto quanto à atividade | Combina topologia, análise causal e apresentação da provável causa raiz | [F] | analisar em C03 |
| Grafana e Azure Application Insights | ferramentas do domínio | Foram citadas como alternativas de observabilidade na Entrega 1 | [F] | PENDENTE — avaliar na análise do quarto integrante ou justificar exclusão |

Se uma hipótese da Entrega 1 for confirmada ou refutada durante esta análise, atualize `H01`, `H02`... em [`../RASTREABILIDADE.md`](../RASTREABILIDADE.md).

## 1. Público-alvo desta análise

[F] Conforme a Entrega 1, o público-alvo prioritário é o **Site Reliability Engineer (SRE)** de plantão. Desenvolvedores também participam da investigação e recebem o diagnóstico inicial para realizar correções. Esses profissionais monitoram sistemas distribuídos, interpretam grandes volumes de telemetria e precisam compreender rapidamente a origem provável, a propagação e o impacto de uma falha, muitas vezes sob pressão de tempo após um alerta ou implantação.

As análises C01–C03 investigam interfaces profissionais que materializam o fluxo priorizado na Entrega 1: **delimitar o incidente → inspecionar o subgrafo e os componentes afetados → examinar hipóteses e evidências → formular e comunicar um diagnóstico inicial**. O objetivo é reconhecer convenções familiares a esse público, sem pressupor que todas devam ser reproduzidas no protótipo.

## 2. Concorrentes diretos/indiretos

### Análise C01 — Datadog

**Autor(a):** Théo Zago Zimmermann — 22.123.035-2

**Tipo:** análogo quanto à interface profissional de observabilidade

**Link oficial:** [https://www.datadoghq.com/](https://www.datadoghq.com/)

**Data de acesso:** 27/08/2026

#### Contexto e proposta

[F] O Datadog é uma plataforma de observabilidade que reúne monitoramento de infraestrutura e aplicações e permite investigar métricas, logs e traces. O *Log Explorer* oferece pesquisa, filtragem, agrupamento e visualização de logs; o *Trace Explorer* permite buscar spans por atributos e relações estruturais; e os mapas representam serviços e dependências observadas.

Para este TCC, o Datadog é mais bem caracterizado como interface profissional análoga do que como concorrente direto do método técnico. O pipeline da equipe realiza uma filtragem estrutural específica e gera hipóteses com LLM, enquanto o Datadog oferece uma plataforma ampla. Sua contribuição para esta entrega é mostrar como uma ferramenta familiar ao SRE materializa as atividades de delimitar uma ocorrência, explorar dependências e aprofundar evidências.

A análise foi documental, baseada na documentação oficial e em avaliações públicas; não foi realizado teste prático em uma conta instrumentada.

#### Funcionalidades relevantes

| Funcionalidade | Como é realizada | Evidência/print | Observação de IHC |
|---|---|---|---|
| Dashboards | Apresentam indicadores e visualizações configuráveis em uma visão consolidada. | [Dashboards — documentação oficial](https://docs.datadoghq.com/dashboards/) | Favorecem uma visão geral antes do aprofundamento, mas só seriam pertinentes ao projeto se apoiassem uma decisão do SRE sobre o incidente. |
| Log Explorer | Permite pesquisar, filtrar, agrupar e inspecionar logs por atributos e período. | [Log Explorer — documentação oficial](https://docs.datadoghq.com/logs/explorer/) | A redução progressiva do conjunto apresentado se relaciona à F01 da Entrega 1: delimitar o incidente por serviço, sintoma e período. |
| Trace Explorer e Trace Queries | Permitem pesquisar spans e traces por tags, atributos e relações entre spans. Os resultados podem ser visualizados em mapa de fluxo. | [Trace Queries — documentação oficial](https://docs.datadoghq.com/tracing/trace_explorer/trace_queries/) | É possível passar de critérios de busca para evidências específicas. O padrão é relevante a H02 porque evita apresentar toda a telemetria simultaneamente. |
| Visualizações de um trace | Um trace pode ser visto como gráfico de chama, lista de spans, *waterfall* ou mapa, com foco em um span e seus descendentes. | [Trace View — documentação oficial](https://docs.datadoghq.com/tracing/trace_explorer/trace_view/) | Oferece diferentes representações e detalhamento sob demanda. A equipe deve selecionar a representação que melhor apoia a compreensão causal, sem impor opções desnecessárias. |
| Mapa de dependências | Apresenta relações a montante e a jusante, taxas de requisição, erro e latência; um painel lateral detalha a dependência selecionada. | [Service Page — documentação oficial](https://docs.datadoghq.com/tracing/services/service_page/) | Relaciona-se a H01 e F02, pois torna visíveis componentes e dependências sem retirar o usuário do contexto do serviço focal. |
| Correlação entre sinais | A partir de um span, o usuário pode consultar logs, processos, infraestrutura e dependências correlacionadas ao mesmo período. | [Trace View — documentação oficial](https://docs.datadoghq.com/tracing/trace_explorer/trace_view/) | Sugere uma trilha entre subgrafo, hipótese e evidências. A presença desse padrão no produto não confirma, por si só, H03 para o público da equipe. |
| Alertas e monitores | Condições configuradas acompanham sinais e geram alertas que podem iniciar uma investigação. | [Monitors — documentação oficial](https://docs.datadoghq.com/monitors/) | Oferecem um ponto de entrada coerente com o cenário da Entrega 1, no qual o SRE começa após um alerta ou implantação. |
| Gestão de incidentes | Incidentes podem reunir contexto, responsáveis, atualizações e comunicação durante a resposta. | [Incident Management — documentação oficial](https://docs.datadoghq.com/service_management/incident_management/) | O incidente funciona como objeto compartilhável e pode apoiar a passagem do diagnóstico inicial do SRE para desenvolvedores. |

#### Experiência do usuário e opiniões

[F] Em consulta realizada em 03/09/2026, o Datadog aparecia no G2 com média de 4,4/5 e centenas de avaliações. Os temas positivos destacados incluíam monitoramento em tempo real, integrações, criação de dashboards e amplitude funcional; entre os temas negativos recorrentes apareciam curva de aprendizagem, complexidade e dificuldade para iniciantes. São relatos de usuários de organizações e papéis distintos e não devem ser tratados como comportamento universal de SREs.

Para o projeto de IHC, a lição não é reproduzir a quantidade de recursos do Datadog, mas preservar o aprofundamento progressivo e selecionar apenas os controles necessários às tarefas F01–F03. A encontrabilidade e a carga cognitiva ainda precisarão ser verificadas com participantes representativos.

#### Padrões e tendências percebidos

- **Visão geral seguida de detalhamento:** o usuário parte de indicadores ou resultados e aprofunda um serviço, trace ou span.
- **Filtragem progressiva e persistência temporal:** consultas combinam serviço, ambiente, atributos e intervalo de tempo; buscas podem ser salvas.
- **Múltiplas representações do trace:** mapa, *waterfall*, lista e gráfico de chama respondem a perguntas distintas.
- **Foco em um subconjunto:** traces grandes podem destacar spans críticos e permitir a recuperação de detalhes adicionais.
- **Dependências com painel contextual:** o mapa mantém a topologia visível enquanto o painel lateral mostra métricas e erros da relação selecionada.
- **Correlação de sinais:** logs, processos, infraestrutura e traces são conectados pelo contexto da investigação.

#### Pontos positivos, limitações e lições

| Ponto | Evidência | Implicação para nosso projeto |
|---|---|---|
| Positivo — filtros restringem e agrupam informações | Log Explorer e Trace Explorer | Oferecer delimitação por serviço, período e sintoma antes de executar ou apresentar o diagnóstico. |
| Positivo — o mapa representa dependências e mantém um serviço focal | Service Page e Flow Map | Usar o subgrafo filtrado como foco, com indicação de direção e acesso a detalhes dos nós e arestas. |
| Positivo — o usuário pode focar um span e seus descendentes | Trace View | Mostrar informação relevante primeiro e permitir expansão sob demanda, contribuindo para investigar H02. |
| Positivo — explorações podem preservar contexto e ser compartilhadas por link | Trace View oferece permalink e buscas salvas | Permitir que o diagnóstico inicial seja comunicado com o mesmo incidente, período, hipótese e evidências examinadas. |
| Limitação — a amplitude funcional pode aumentar a curva de aprendizagem | Temas recorrentes nas avaliações do G2 | Restringir o protótipo às tarefas prioritárias e testar se o SRE encontra evidências sem navegar por funções secundárias. |
| Limitação — flexibilidade de visualização pode aumentar escolhas e carga cognitiva | Um trace admite quatro representações principais e múltiplos agrupamentos | Definir uma visualização inicial coerente com a tarefa e oferecer alternativas somente quando agregarem valor verificável. |

### Análise C02 — New Relic

**Autor(a):** Willian Verenka Oliveira Silva — 22.124.081-5

**Tipo:** direto quanto à atividade de observabilidade e diagnóstico; não equivalente quanto ao método técnico

**Link oficial:** [https://newrelic.com/](https://newrelic.com/)

**Data de acesso:** 27/08/2026

#### Contexto e proposta

[F] A New Relic é uma plataforma de observabilidade que reúne dados de aplicações e infraestrutura, como métricas, eventos, logs, traces e erros, para apoiar monitoramento, investigação e resposta a incidentes. A plataforma concorre diretamente pela mesma necessidade identificada na Entrega 1: permitir que SREs e desenvolvedores encontrem evidências e compreendam falhas em sistemas distribuídos. Ela não é tecnicamente equivalente ao TCC, pois o projeto da equipe investiga um pipeline específico de filtragem estrutural de grafos de observabilidade e geração de hipóteses diagnósticas com LLM.

Para manter a análise coerente com o recorte de IHC, foram examinados principalmente os fluxos de triagem de um incidente, inspeção da propagação entre serviços, aprofundamento em traces e logs e análise assistida por IA. A análise foi documental, baseada nas páginas oficiais que apresentam e ilustram a interface; não foi realizado teste prático em uma conta instrumentada.

#### Funcionalidades relevantes

| Funcionalidade | Como é realizada | Evidência/print | Observação de IHC |
|---|---|---|---|
| Triagem de erros e incidentes | O *Errors inbox* agrupa ocorrências semelhantes e apresenta estado, impacto, frequência, stack trace, traces distribuídos e logs em contexto. O feed de *issues* permite pesquisar, filtrar, reconhecer e encerrar incidentes. | [Errors inbox — documentação oficial](https://docs.newrelic.com/docs/errors-inbox/errors-inbox/) e [Issues & activity — documentação oficial](https://docs.newrelic.com/docs/alerts/alert-event-management/issues-and-alert-event-management-and-response/) | O agrupamento reduz repetição e oferece uma entrada orientada ao problema, em vez de exigir que o SRE comece pela busca manual em toda a telemetria. O estado do incidente e as entidades afetadas ajudam a priorização. |
| Busca e inspeção de traces distribuídos | A lista de traces pode ser refinada por consulta, serviço, presença de erro e duração. No detalhe, as visões de linha do tempo, latência e *waterfall* mostram spans, duração, erros e fronteiras entre entidades. | [Distributed tracing UI](https://docs.newrelic.com/docs/distributed-tracing/ui-data/understand-use-distributed-tracing-ui/) e [trace details](https://docs.newrelic.com/docs/distributed-tracing/ui-data/trace-details/) | O aprofundamento progressivo, da lista ao span, preserva uma visão geral antes de expor detalhes. Para o projeto, isso é uma referência para equilibrar H02: mostrar primeiro o subgrafo filtrado e permitir expansão sob demanda. |
| Mapa de serviços e fluxo dinâmico | O *Maps* apresenta relações entre serviços e infraestrutura, direção das dependências, saúde e agrupamentos. O *Dynamic Flow Map* agrega traces em torno de um serviço focal e destaca anomalias correlacionadas de latência e erro em nós e arestas. | [Maps](https://docs.newrelic.com/docs/service-architecture-intelligence/maps/advanced-maps/) e [Dynamic Flow Map](https://docs.newrelic.com/docs/service-architecture-intelligence/maps/dynamic-flow-map/) | A representação nó-aresta, o foco em uma entidade e o agrupamento de elementos menos relevantes são convenções pertinentes a H01. A evidência é de uso do padrão no domínio, não confirma sozinha que o público da equipe prefira essa visualização. |
| Logs em contexto | Os logs podem ser abertos a partir de um serviço, erro, trace, host, cluster ou entidade. A interface oferece filtros, atributos, padrões, consultas, visualização detalhada e acesso ao log relacionado sem perder o ponto de partida da investigação. | [Logs UI — documentação oficial](https://docs.newrelic.com/docs/logs/ui-data/use-logs-ui/) | A passagem de uma anomalia ou span para a evidência bruta reduz troca de contexto. O projeto deve preservar serviço, período e incidente ao abrir uma evidência, evitando que o usuário refaça filtros. |
| Análise assistida por IA | O *New Relic AI* aceita perguntas em linguagem natural, consulta telemetria, produz explicações, resumos ou gráficos e oferece a ação *Explain this error* em logs e stack traces. | [New Relic AI — documentação oficial](https://docs.newrelic.com/docs/agentic-ai/new-relic-ai/) | A IA aparece integrada ao artefato investigado, não apenas em um chat isolado. Isso se aproxima de H03 e sugere que cada hipótese do TCC seja ligada às evidências que a originaram e a ações de verificação. |
| Correlação, comunicação e acompanhamento | Eventos relacionados podem ser reunidos em um único *issue* por regras de correlação. Os *workflows* encaminham notificações e contexto para a pessoa ou equipe responsável. | [Correlação de alertas](https://docs.newrelic.com/docs/alerts/organize-alerts/change-applied-intelligence-correlation-logic-decisions/) e [Workflows](https://docs.newrelic.com/docs/alerts/get-notified/alert-event-workflows/) | O incidente funciona como objeto compartilhável, com estado e histórico. Para o objetivo definido na Entrega 1, o diagnóstico inicial precisa manter contexto suficiente para ser comunicado a desenvolvedores sem depender de uma explicação oral paralela. |

#### Experiência do usuário e opiniões

[F] Na página consultada em 27/08/2026, o G2 agregava 583 avaliações da New Relic, com nota média de 4,4/5. O resumo da plataforma aponta como temas positivos a observabilidade abrangente, o monitoramento em tempo real, os dashboards e a integração de dados; entre os temas negativos recorrentes aparecem curva de aprendizagem, complexidade e configuração. Esses relatos são compatíveis com uma tensão visível na própria documentação: a integração de muitas capacidades reduz a troca entre ferramentas, mas amplia a quantidade de conceitos, rotas de navegação e opções que o usuário precisa aprender.

Essa evidência não deve ser generalizada como comportamento de todo SRE: avaliações públicas são autorrelatadas, podem ter viés de seleção e incluem organizações, papéis e níveis de experiência distintos. Também não substituem um teste com o público da equipe. Como implicação inicial, o projeto deve priorizar um fluxo estreito, centrado em um incidente, e medir em avaliações futuras se o SRE localiza a provável origem e suas evidências sem se perder em funcionalidades secundárias.

#### Padrões e tendências percebidos

- **Entrada orientada ao incidente:** erros e eventos correlacionados são agrupados antes do aprofundamento na telemetria.
- **Aprofundamento progressivo:** a interface parte de resumo, estado e impacto e permite chegar a serviço, trace, span, stack trace e log.
- **Contexto persistente:** serviço, entidade, período e erro funcionam como elos entre diferentes visões.
- **Topologia focal e redução de ruído:** mapas destacam o serviço investigado, codificam anomalias em nós e arestas e agrupam entidades de menor relevância.
- **IA incorporada ao fluxo:** explicações e perguntas de acompanhamento aparecem junto a logs, stack traces, consultas e dashboards.
- **Colaboração baseada em um objeto compartilhado:** *issues* possuem estado, linha do tempo, entidades impactadas e encaminhamento por workflows.
- **Consulta avançada como camada opcional:** filtros visuais atendem investigações iniciais, enquanto NRQL oferece expressividade a usuários experientes.

#### Pontos positivos, limitações e lições

| Ponto | Evidência | Implicação para nosso projeto |
|---|---|---|
| Positivo — reúne diferentes sinais e permite navegar do incidente à evidência detalhada | Errors inbox, distributed tracing e logs em contexto, conforme documentação oficial | Manter uma trilha navegável entre hipótese, componente do subgrafo, span e log, preservando filtros e período. |
| Positivo — o mapa focal explicita dependências e propagação sem exibir toda a arquitetura com igual destaque | Dynamic Flow Map usa serviço focal, direção das arestas, anomalias e agrupamento de entidades | Apresentar primeiro o subgrafo selecionado pelo pipeline e oferecer expansão para evidências excluídas ou vizinhas quando necessário. |
| Positivo — a explicação por IA é acionada no contexto do erro e admite perguntas de acompanhamento | Ação *Explain this error* em logs e stack traces | Vincular cada hipótese diagnóstica aos dados analisados e permitir que o usuário examine o raciocínio e solicite detalhes, em vez de mostrar apenas uma conclusão. |
| Limitação — respostas de IA podem ser imprecisas, incompletas ou conter erros e a própria New Relic recomenda verificação humana | Seção “Accuracy and security” da documentação do New Relic AI | Tratar a hipótese como apoio à decisão: sinalizar origem automática, incerteza e limitações; nunca apresentar a saída como causa raiz confirmada sem validação. |
| Limitação — amplitude funcional pode gerar curva de aprendizagem e dificuldade de navegação | Temas recorrentes nas 583 avaliações agregadas pelo G2 | Restringir o protótipo ao diagnóstico inicial de um incidente e testar encontrabilidade e carga cognitiva com SREs representativos. |
| Limitação — mapas e traces dependem de instrumentação, amostragem, permissões e cobertura entre serviços | Documentação de tracing e Maps informa obfuscação por falta de acesso e possíveis lacunas por dados ausentes | Exibir estados de dado ausente, acesso restrito e cobertura parcial; não transformar ausência de telemetria em evidência de normalidade. |
| Limitação — o Dynamic Flow Map cobre até três horas de traces agregados | Documentação oficial do Dynamic Flow Map | Tornar o período analisado visível e comunicar quando a hipótese estiver baseada em uma janela incompleta ou inadequada ao incidente. |

### Análise C03 — Dynatrace

**Autor(a):** Gabriel Lovato — 22.123.004-8

**Tipo:** direto quanto à atividade de observabilidade e diagnóstico de causa raiz

**Link oficial:** [https://www.dynatrace.com/](https://www.dynatrace.com/)

**Data de acesso:** 27/08/2026

#### Contexto e proposta

[F] A Dynatrace é uma plataforma de observabilidade *full-stack* para aplicações, microsserviços e infraestrutura. Ela combina traces, logs, métricas e topologia e apresenta, na aplicação *Problems*, o impacto, a causa raiz apontada, as entidades relacionadas e um caminho visual de resolução. O Smartscape representa entidades e dependências do ambiente em um mapa interativo atualizado a partir da telemetria.

A solução concorre diretamente pela atividade humana priorizada no TCC: reduzir o esforço necessário para relacionar sintomas, componentes afetados e provável origem de um incidente. Ainda assim, não é equivalente ao método científico da equipe, que compara filtragem estrutural por GNN ou heurística e usa um LLM para gerar hipóteses diagnósticas a partir do subgrafo selecionado.

A análise foi documental, baseada na documentação oficial e em avaliações públicas; não foi realizado teste prático em um ambiente instrumentado.

#### Funcionalidades relevantes

| Funcionalidade | Como é realizada | Evidência/print | Observação de IHC |
|---|---|---|---|
| Smartscape | Apresenta serviços, infraestrutura e outras entidades como nós conectados, com relações e dependências em tempo real e vistas contextuais. | [Smartscape — documentação oficial](https://docs.dynatrace.com/docs/analyze-explore-automate/smartscape) | A visão espacial pode apoiar H01, mas uma topologia extensa pode sobrecarregar o usuário. O recorte e a hierarquia visual precisam indicar por que cada nó está presente. |
| Problems e análise de causa raiz | Agrupa sinais relacionados em um problema e apresenta impacto, causa raiz, entidades afetadas, automações e *Visual resolution path*. | [Problems app — documentação oficial](https://docs.dynatrace.com/docs/dynatrace-intelligence/problems-app) | Coloca o problema e a provável causa no centro, reduzindo a necessidade de começar por logs crus. O caminho visual oferece rastreabilidade estrutural para a conclusão. |
| Visual resolution path | Mostra graficamente a relação entre frontends, serviços e backends; nós cinza representam entidades usadas na análise, mas não diretamente impactadas. | [Problems app — documentação oficial](https://docs.dynatrace.com/docs/dynatrace-intelligence/problems-app) | A distinção entre “analisado”, “afetado” e “causa apontada” é uma referência útil para explicar seleção e exclusão no subgrafo do TCC. |
| PurePath e traces distribuídos | Permite filtrar traces e aprofundar uma requisição em uma visualização *waterfall*, chegando a serviços, chamadas, atributos, logs, erros e detalhes de código. | [Distributed traces — documentação oficial](https://docs.dynatrace.com/docs/observe/application-observability/distributed-traces/concepts) | O *drill-down* mantém o contexto durante o aprofundamento. Na proposta, corresponde à passagem do subgrafo filtrado para spans e evidências específicas. |
| Filtro temporal | O intervalo de análise pode ser escolhido e preservado durante a navegação entre diferentes visões. | [Timeframe — documentação oficial](https://docs.dynatrace.com/docs/analyze-explore-automate/dashboards-classic/dashboards/dashboard-timeframe) | Como telemetria é cronológica, o período precisa permanecer visível e estável para evitar que o usuário compare evidências de janelas diferentes sem perceber. |

#### Experiência do usuário e opiniões

[F] Avaliações públicas agregadas pelo G2 consultadas em 03/09/2026 mencionam como pontos positivos visibilidade, monitoramento, depuração e amplitude de recursos. Curva de aprendizagem, complexidade da interface e necessidade de melhorias de UX aparecem entre os temas negativos. A documentação do *Problems* mostra que eventos relacionados são reunidos em uma entidade investigável; a hipótese de que esse agrupamento reduza a fadiga de alertas ainda precisa ser verificada com o público da equipe.

Essas opiniões são autorrelatadas e reúnem perfis, organizações e ambientes distintos; não demonstram que todo SRE encontrará as mesmas facilidades ou dificuldades. Para o projeto, elas motivam avaliar se o fluxo incidente → hipótese → caminho estrutural → evidência reduz esforço sem esconder contexto indispensável.

#### Padrões e tendências percebidos

- **Abstração orientada ao problema:** o incidente agregado aparece antes dos sinais brutos.
- **Causa apontada junto ao impacto:** a interface relaciona provável origem, componentes afetados e consequências observadas.
- **Caminho causal visual:** a topologia não é apenas decorativa; ela explica quais entidades participaram da análise e como se relacionam.
- **Aprofundamento contextual:** traces, logs e detalhes de execução podem ser acessados a partir do problema ou serviço investigado.
- **Filtros persistentes:** o intervalo temporal acompanha a navegação entre visões.
- **Cores semânticas e painéis contextuais:** estados e anomalias são destacados, enquanto detalhes aparecem sem eliminar a visão principal.
- **Breadcrumbs e aprofundamento rastreável:** a navegação indica o caminho percorrido entre problema, serviço e evidência detalhada.
- **Painéis laterais:** resumos de entidades podem ser consultados sem substituir imediatamente a visualização principal.

#### Pontos positivos, limitações e lições

| Ponto | Evidência | Implicação para nosso projeto |
|---|---|---|
| Positivo — eventos são sintetizados em um problema investigável | Problems reúne impacto, causa raiz e automações | Usar a hipótese do incidente como ponto de entrada, evitando obrigar o SRE a começar pelo grafo completo ou por logs crus. |
| Positivo — o caminho visual relaciona conclusão e estrutura | Visual resolution path aponta entidades afetadas, relacionadas e a causa indicada | Sustenta a convenção investigada em H03: a hipótese precisa remeter aos nós e evidências usados para formulá-la. |
| Positivo — há detalhamento do problema ao trace e ao código | PurePath combina waterfall, logs, métricas, topologia e detalhes de execução | Permitir expansão progressiva do subgrafo e acesso ao span ou log relevante sem perder o contexto do incidente. |
| Limitação — a quantidade de menus, conceitos e recursos pode elevar a curva de aprendizagem | Temas recorrentes nas avaliações agregadas pelo G2 | Simplificar as vistas do subgrafo e ocultar elementos secundários por padrão, verificando a decisão em testes com SREs. |
| Limitação — automação e causa apontada podem transmitir certeza excessiva | Problems destaca “Root cause” e o caminho usado pela análise | No projeto, usar “hipótese diagnóstica” e comunicar incerteza, cobertura dos dados e necessidade de validação humana. |
| Limitação — dependência de instrumentação e permissões pode produzir evidência parcial | Traces e Smartscape dependem dos sinais disponíveis e de acesso aos respectivos dados | Representar explicitamente lacunas, entidades não instrumentadas e acesso restrito; ausência de dados não deve parecer saúde confirmada. |

## 3. Softwares que o público-alvo usa no cotidiano

Analise interfaces que moldam a expectativa do público, mesmo que não sejam concorrentes.

| Software | Por que o público usa | Padrões relevantes | Prints | O que aprender |
|---|---|---|---|---|
| Datadog | Monitorar aplicações e infraestrutura e investigar logs, métricas e traces | Filtros por atributo e tempo, buscas salvas, mapas, múltiplas visualizações de trace e aprofundamento contextual | PENDENTE | Preservar contexto entre a delimitação do incidente e a evidência detalhada. |
| New Relic | Triar erros e incidentes, correlacionar sinais e explorar entidades afetadas | Errors inbox, issues, mapas focais, logs em contexto e explicações por IA | PENDENTE | Organizar a interface a partir do incidente e ligar hipóteses às evidências verificáveis. |
| Dynatrace | Detectar problemas, compreender impacto e investigar causa raiz | Problems, Smartscape, caminho visual de resolução, PurePath e filtro temporal persistente | PENDENTE | Distinguir visualmente causa apontada, componentes afetados e elementos apenas relacionados. |

## 3.1 Padrões de interface relevantes ao escopo de IHC

Registre somente padrões encontrados nas soluções analisadas e que possam ter relação com objetivos reais da equipe.

| Padrão observado | Produto(s) | Para qual tarefa serve | Vantagem percebida | Risco/limitação | Aplicável ao nosso escopo? |
|---|---|---|---|---|---|
| Visão geral/dashboard | Datadog, New Relic e Dynatrace | Reconhecer estado, impacto e prioridade antes do aprofundamento | Oferece orientação inicial sob pressão de tempo | Pode virar uma coleção de métricas sem decisão associada | talvez — somente como resumo do incidente |
| Resumo/relatório do incidente | New Relic e Dynatrace | Formular e comunicar um diagnóstico inicial | Reúne estado, impacto, entidades, hipótese e histórico | Uma síntese automática pode aparentar certeza indevida | sim |
| Histórico e filtros | Datadog, New Relic e Dynatrace | Delimitar serviço, sintoma, ambiente e período | Reduz o espaço de busca e permite repetir uma investigação | Filtros invisíveis ou inconsistentes podem produzir conclusões erradas | sim |
| Grafo/mapa de dependências | Datadog, New Relic e Dynatrace | Compreender propagação e componentes afetados | Torna relações e direção do fluxo inspecionáveis | Muitos nós, cores ou arestas podem aumentar carga cognitiva | sim — usando o subgrafo filtrado |
| Aprofundamento progressivo | Datadog, New Relic e Dynatrace | Passar de hipótese ou anomalia para trace, span e log | Mantém a visão geral enquanto disponibiliza evidência detalhada | Rupturas de contexto obrigam o usuário a refazer a busca | sim |
| Explicação/causa assistida por IA | New Relic e Dynatrace | Interpretar sinais e formar uma hipótese inicial | Reduz o esforço de síntese e sugere próximos passos | Pode estar errada, incompleta ou baseada em dados parciais | sim — com evidência, incerteza e validação humana |
| Administração/CRUD | Não identificado como parte do fluxo central em C01–C03 | Administrar entidades ou configurações | Pode apoiar governança em um produto completo | Não contribui diretamente para F01–F03 e amplia o escopo | não neste recorte |
| Comparação de resultados | Não observada como padrão central em C01–C03 | Comparar hipóteses, algoritmos ou períodos | Pode apoiar avaliação técnica | Não foi sustentada como tarefa do SRE na Entrega 1 | não neste momento |

> O objetivo não é concluir “todo concorrente tem dashboard, então teremos um”. O padrão só será adotado se apoiar uma tarefa rastreável.

## 4. Síntese comparativa da equipe

| Critério | C01 | C02 | C03 | Oportunidade para o projeto |
|---|---|---|---|---|
| Navegação | Busca e filtros levam a trace, serviço, span e sinais correlacionados | Issue ou erro leva a trace, mapa e logs em contexto | Problema leva a causa apontada, caminho visual e PurePath | Adotar fluxo curto e bidirecional: incidente → hipótese/subgrafo → evidência, preservando período e filtros. |
| Feedback/estado | Métricas, erros e duração aparecem em traces e dependências | Issues possuem estado, prioridade, duração e entidades afetadas | Problems mostram impacto, causa indicada e estado das automações | Tornar processamento, cobertura dos dados e estado da hipótese visíveis, incluindo carregamento, falha e resultado parcial. |
| Prevenção/recuperação de erro | Foco e busca salva reduzem repetição; traces grandes entram em modo de prévia | Agrupamento reduz ruído; respostas de IA exigem verificação humana | Agrupamento e caminho causal orientam a triagem; causa apontada pode transmitir certeza excessiva | Permitir revisar filtros, desfazer foco e acessar evidência excluída; nunca tratar hipótese automática como confirmação. |
| Terminologia | Serviço, ambiente, trace, span, erro e dependência | Issue, entidade, trace, span, logs em contexto e explicação | Problem, impacto, root cause, Smartscape e PurePath | Preferir vocabulário familiar em português, mantendo termos técnicos reconhecidos e definindo “hipótese diagnóstica” claramente. |
| Acessibilidade | [?] Não foi realizada avaliação específica; há forte uso de cor em traces e mapas | [?] Não foi realizada avaliação específica; mapas usam cores para saúde e anomalia | [?] Não foi realizada avaliação específica; estados também usam cores semânticas | Não depender apenas de cor: combinar rótulos, ícones, padrões e texto; avaliar contraste, teclado e leitura do grafo. |
| Eficiência | Filtros estruturais, foco no span e sinais correlacionados reduzem o conjunto analisado | Entrada pelo incidente, agrupamento e IA reduzem troca de contexto | Problems sintetiza eventos e liga causa, impacto e topologia | Exibir primeiro a seleção do pipeline, oferecendo justificativa e expansão sob demanda para reduzir esforço sem ocultar lacunas. |

## 5. Recomendações derivadas

- **RC01:** Estruturar a navegação principal como incidente → hipótese/subgrafo → span/log, preservando serviço, período e filtros durante todo o aprofundamento — derivada de C01, C02 e C03.
- **RC02:** Apresentar inicialmente apenas o subgrafo selecionado pelo pipeline e permitir expansão de nós, arestas e evidências excluídas — derivada dos mapas focais e mecanismos de agrupamento de C01, C02 e C03; relacionada a H01 e H02.
- **RC03:** Vincular cada hipótese diagnóstica aos componentes e sinais que a sustentam, distinguindo evidência observada, interpretação automática e validação humana — derivada de C02 e do *Visual resolution path* de C03; relacionada a H03.
- **RC04:** Exibir explicitamente janela temporal, cobertura de instrumentação, dados ausentes, acesso restrito e processamento parcial — derivada das limitações de tracing e topologia identificadas em C01, C02 e C03.
- **RC05:** Usar “hipótese diagnóstica” em vez de “causa raiz confirmada” e comunicar incerteza e limitações da geração por IA — derivada dos alertas de precisão do New Relic AI em C02 e da apresentação de causa em C03.
- **RC06:** Não incluir administração, CRUD ou um dashboard genérico neste recorte sem uma tarefa rastreável; priorizar encontrabilidade e carga cognitiva no teste com SREs — derivada das críticas de complexidade presentes em C01, C02 e C03.

## Referências

- DATADOG. *Dashboards*. Documentação oficial, s.d. Disponível em: [https://docs.datadoghq.com/dashboards/](https://docs.datadoghq.com/dashboards/). Acesso em: 3 set. 2026.
- DATADOG. *Log Explorer*. Documentação oficial, s.d. Disponível em: [https://docs.datadoghq.com/logs/explorer/](https://docs.datadoghq.com/logs/explorer/). Acesso em: 3 set. 2026.
- DATADOG. *Trace Queries*. Documentação oficial, s.d. Disponível em: [https://docs.datadoghq.com/tracing/trace_explorer/trace_queries/](https://docs.datadoghq.com/tracing/trace_explorer/trace_queries/). Acesso em: 3 set. 2026.
- DATADOG. *Trace View*. Documentação oficial, s.d. Disponível em: [https://docs.datadoghq.com/tracing/trace_explorer/trace_view/](https://docs.datadoghq.com/tracing/trace_explorer/trace_view/). Acesso em: 3 set. 2026.
- DATADOG. *Service Page*. Documentação oficial, s.d. Disponível em: [https://docs.datadoghq.com/tracing/services/service_page/](https://docs.datadoghq.com/tracing/services/service_page/). Acesso em: 3 set. 2026.
- DATADOG. *Monitors*. Documentação oficial, s.d. Disponível em: [https://docs.datadoghq.com/monitors/](https://docs.datadoghq.com/monitors/). Acesso em: 3 set. 2026.
- DATADOG. *Incident Management*. Documentação oficial, s.d. Disponível em: [https://docs.datadoghq.com/service_management/incident_management/](https://docs.datadoghq.com/service_management/incident_management/). Acesso em: 3 set. 2026.
- DYNATRACE. *Smartscape*. Documentação oficial, 2026. Disponível em: [https://docs.dynatrace.com/docs/analyze-explore-automate/smartscape](https://docs.dynatrace.com/docs/analyze-explore-automate/smartscape). Acesso em: 3 set. 2026.
- DYNATRACE. *Problems app*. Documentação oficial, 2026. Disponível em: [https://docs.dynatrace.com/docs/dynatrace-intelligence/problems-app](https://docs.dynatrace.com/docs/dynatrace-intelligence/problems-app). Acesso em: 3 set. 2026.
- DYNATRACE. *Distributed traces concepts*. Documentação oficial, 2026. Disponível em: [https://docs.dynatrace.com/docs/observe/application-observability/distributed-traces/concepts](https://docs.dynatrace.com/docs/observe/application-observability/distributed-traces/concepts). Acesso em: 3 set. 2026.
- DYNATRACE. *Dashboard timeframe and management zone settings*. Documentação oficial, 2017. Disponível em: [https://docs.dynatrace.com/docs/analyze-explore-automate/dashboards-classic/dashboards/dashboard-timeframe](https://docs.dynatrace.com/docs/analyze-explore-automate/dashboards-classic/dashboards/dashboard-timeframe). Acesso em: 3 set. 2026.
- NEW RELIC. *Error tracking*. Documentação oficial, s.d. Disponível em: [https://docs.newrelic.com/docs/errors-inbox/errors-inbox/](https://docs.newrelic.com/docs/errors-inbox/errors-inbox/). Acesso em: 27 ago. 2026.
- NEW RELIC. *Issues and alert event management and response*. Documentação oficial, s.d. Disponível em: [https://docs.newrelic.com/docs/alerts/alert-event-management/issues-and-alert-event-management-and-response/](https://docs.newrelic.com/docs/alerts/alert-event-management/issues-and-alert-event-management-and-response/). Acesso em: 27 ago. 2026.
- NEW RELIC. *Understand and use the distributed tracing UI*. Documentação oficial, s.d. Disponível em: [https://docs.newrelic.com/docs/distributed-tracing/ui-data/understand-use-distributed-tracing-ui/](https://docs.newrelic.com/docs/distributed-tracing/ui-data/understand-use-distributed-tracing-ui/). Acesso em: 27 ago. 2026.
- NEW RELIC. *Understand the trace details UI page*. Documentação oficial, s.d. Disponível em: [https://docs.newrelic.com/docs/distributed-tracing/ui-data/trace-details/](https://docs.newrelic.com/docs/distributed-tracing/ui-data/trace-details/). Acesso em: 27 ago. 2026.
- NEW RELIC. *Use logs UI*. Documentação oficial, s.d. Disponível em: [https://docs.newrelic.com/docs/logs/ui-data/use-logs-ui/](https://docs.newrelic.com/docs/logs/ui-data/use-logs-ui/). Acesso em: 27 ago. 2026.
- NEW RELIC. *Understand and use Maps*. Documentação oficial, s.d. Disponível em: [https://docs.newrelic.com/docs/service-architecture-intelligence/maps/advanced-maps/](https://docs.newrelic.com/docs/service-architecture-intelligence/maps/advanced-maps/). Acesso em: 27 ago. 2026.
- NEW RELIC. *Dynamic Flow Map*. Documentação oficial, s.d. Disponível em: [https://docs.newrelic.com/docs/service-architecture-intelligence/maps/dynamic-flow-map/](https://docs.newrelic.com/docs/service-architecture-intelligence/maps/dynamic-flow-map/). Acesso em: 27 ago. 2026.
- NEW RELIC. *Meet New Relic AI, your observability assistant*. Documentação oficial, 2026. Disponível em: [https://docs.newrelic.com/docs/agentic-ai/new-relic-ai/](https://docs.newrelic.com/docs/agentic-ai/new-relic-ai/). Acesso em: 27 ago. 2026.
- NEW RELIC. *Configure correlation logic with decisions*. Documentação oficial, s.d. Disponível em: [https://docs.newrelic.com/docs/alerts/organize-alerts/change-applied-intelligence-correlation-logic-decisions/](https://docs.newrelic.com/docs/alerts/organize-alerts/change-applied-intelligence-correlation-logic-decisions/). Acesso em: 27 ago. 2026.
- NEW RELIC. *Workflows*. Documentação oficial, s.d. Disponível em: [https://docs.newrelic.com/docs/alerts/get-notified/alert-event-workflows/](https://docs.newrelic.com/docs/alerts/get-notified/alert-event-workflows/). Acesso em: 27 ago. 2026.
- G2. *Datadog reviews 2026*. 2026. Disponível em: [https://www.g2.com/products/datadog/reviews](https://www.g2.com/products/datadog/reviews). Acesso em: 3 set. 2026.
- G2. *Dynatrace reviews 2026*. 2026. Disponível em: [https://www.g2.com/products/dynatrace/reviews](https://www.g2.com/products/dynatrace/reviews). Acesso em: 3 set. 2026.
- G2. *New Relic reviews 2026*. 2026. Disponível em: [https://www.g2.com/products/new-relic/reviews](https://www.g2.com/products/new-relic/reviews). Acesso em: 27 ago. 2026.

## Checklist

- [x] O mapa inicial de alternativas da Entrega 1 foi revisitado e aprofundado.
- [ ] Hipóteses relevantes sobre mercado/padrões foram atualizadas na rastreabilidade quando surgiram evidências.
- [ ] Há pelo menos uma análise completa por integrante.
- [ ] Cada análise contém prints legíveis da interface.
- [ ] Prints mostram telas/estados relevantes, não apenas logos/homepage.
- [x] Foram analisados concorrentes e/ou interfaces representativas ao público.
- [x] Em TCC sem interface original, foram investigadas ferramentas profissionais análogas às atividades do usuário escolhido.
- [x] Padrões como dashboard, relatório, filtros e CRUD foram analisados como soluções para tarefas, não como requisitos automáticos.
- [x] Opiniões de UX têm fonte.
- [x] A síntese compara critérios comuns e produz recomendações.
- [x] Não há “copiar porque o concorrente faz”; há justificativa de adequação ao público/contexto.
