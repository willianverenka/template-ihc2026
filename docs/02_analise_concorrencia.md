# Entrega 2 — Público-alvo e análise de concorrência

**Data:** 27/08/2026  
**Status:** concluída  
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
| Dynatrace | concorrente direto | Líder de mercado em APM e AIOps para análise de causa raiz estrutural e de telemetria | [F] | analisar (foco exclusivo desta etapa) |

Se uma hipótese da Entrega 1 for confirmada ou refutada durante esta análise, atualize `H01`, `H02`... em [`../RASTREABILIDADE.md`](../RASTREABILIDADE.md).

## 1. Público-alvo desta análise

O público-alvo desta análise são **Site Reliability Engineers (SREs)** e **Desenvolvedores** que necessitam investigar incidentes em sistemas distribuídos complexos. Como delimitado na Entrega 1, essas pessoas estão sob pressão de tempo (ex: após alertas de falhas ou deploys instáveis) e buscam reduzir o tempo de diagnóstico. Elas lidam com grandes volumes de telemetria dispersa e necessitam estabelecer uma relação causal rápida entre sintomas de falha, impacto e origem (causa raiz).

## 2. Concorrentes diretos/indiretos

### Análise C03 — Dynatrace

**Autor(a):** Gabriel Lovato — 22.123.004-8  
**Tipo:** direto  
**Link oficial:** https://www.dynatrace.com/  
**Data de acesso:** 27/08/2026

#### Contexto e proposta

Dynatrace é uma plataforma "full-stack" focada em observabilidade corporativa, Application Performance Monitoring (APM) e segurança de aplicações. Seu diferencial de destaque (e o que a aproxima do tema do TCC) é o uso de inteligência artificial determinística e causal (chamada de Davis AI). Em vez de depender do usuário para cruzar logs e traces manualmente, o Dynatrace ingere continuamente os dados, constrói uma topologia de dependências em tempo real (Smartscape) e analisa anomalias na estrutura para identificar e apontar diretamente a causa raiz de incidentes.

#### Funcionalidades relevantes

| Funcionalidade | Como é realizada | Evidência/print | Observação de IHC |
|---|---|---|---|
| Smartscape (Grafo de Dependências) | Apresenta a infraestrutura e os microsserviços como nós interligados em uma rede visual. | - | Ajuda na compreensão espacial de onde o sistema falha, mas pode sobrecarregar se todos os nós aparecerem (Apoia H01 e H02). |
| Problems (Root Cause Analysis) | Agrupa múltiplas anomalias e gera um laudo detalhado descrevendo o que falhou, impacto no negócio e a "Root Cause". | - | O Davis AI entrega uma hipótese textual junto ao caminho visual (Apoia fortemente H03). |
| PurePath (Visualização de Traces) | Inspeção progressiva que permite descer da transação falha até o nível exato do código de execução (spans). | - | Permite um "drill-down" efetivo. Na nossa proposta, esse seria o equivalente à exploração do subgrafo filtrado. |
| Filtro Global de Tempo | Controle permanente no topo da interface que afeta todos os dados e painéis visíveis abaixo dele. | - | Padrão fundamental de usabilidade para profissionais que lidam com telemetria cronológica. |

#### Experiência do usuário e opiniões

Em comunidades de SRE e DevOps (fóruns, Reddit, análises G2), usuários frequentemente elogiam a capacidade do Dynatrace de mitigar a "fadiga de alertas" (alert fatigue). Em vez de receberem milhares de alertas de cada microserviço, recebem apenas um alerta de "Problema" diagnosticado, o que acelera enormemente o tempo de resposta. A maior crítica gira em torno da densidade e da alta curva de aprendizado inicial, além de, em certos casos, navegação confusa devido à vastidão de funcionalidades da plataforma.

#### Preço/modelo de negócio

SaaS Enterprise. Cobra por hora de monitoramento, tamanho de infraestrutura (hosts) e volume de ingestão de logs/traces e de armazenamento. É um produto focado em grandes corporações com orçamentos robustos, não amigável a pequenos projetos indie.

#### Padrões e tendências percebidos

- **Cores semânticas intensas:** Uso proeminente de vermelho para incidentes e verde para componentes saudáveis;
- **Navegação breadcrumb:** Usada extensivamente em aprofundamentos para garantir que o usuário não se perca;
- **Painéis Deslizantes (Drawers):** Abertura lateral de resumos de entidades e spans, sem perder de vista a visualização do grafo principal;
- **Abstração orientada ao problema:** Foco primário na visualização de incidentes agregados, e não em logs "crus".

#### Pontos positivos, limitações e lições

| Ponto | Evidência | Implicação para nosso projeto |
|---|---|---|
| Redução da granularidade e foco na anomalia | A funcionalidade "Problems" agrupa centenas de eventos em apenas uma entidade visível. | A interface deve focar na "Hipótese do Incidente" (gerada pelo LLM) como ponto central, e não forçar o usuário a explorar os grafos crus desde o primeiro momento. |
| Caminho Visual da Causa (Visual Resolution Path) | Apresentação da causa apontando os nós exatos da falha no Smartscape. | Sustenta a H03: apresentar a hipótese do LLM textualmente não basta; ela precisa ter rastreabilidade estrutural visível para passar confiança. |
| Densidade visual | Relatos de usuários e a quantidade maciça de menus na barra esquerda e dados em tela. | Como queremos facilitar um "diagnóstico rápido", precisamos simplificar as vistas dos subgrafos (GNN/heurística), escondendo nós e spans secundários de menor criticidade (relevante para a H02). |

## 3. Softwares que o público-alvo usa no cotidiano

Analise interfaces que moldam a expectativa do público, mesmo que não sejam concorrentes.

| Software | Por que o público usa | Padrões relevantes | Prints | O que aprender |
|---|---|---|---|---|
| {{...}} | {{...}} | {{...}} | {{link local}} | {{...}} |

## 3.1 Padrões de interface relevantes ao escopo de IHC

Registre somente padrões encontrados nas soluções analisadas e que possam ter relação com objetivos reais da equipe.

| Padrão observado | Produto(s) | Para qual tarefa serve | Vantagem percebida | Risco/limitação | Aplicável ao nosso escopo? |
|---|---|---|---|---|---|
| dashboard | {{...}} | {{...}} | {{...}} | {{...}} | sim/não/talvez |
| relatório | {{...}} | {{...}} | {{...}} | {{...}} | {{...}} |
| histórico + filtros | {{...}} | {{...}} | {{...}} | {{...}} | {{...}} |
| administração/CRUD | {{...}} | {{...}} | {{...}} | {{...}} | {{...}} |
| comparação de resultados | {{...}} | {{...}} | {{...}} | {{...}} | {{...}} |

> O objetivo não é concluir “todo concorrente tem dashboard, então teremos um”. O padrão só será adotado se apoiar uma tarefa rastreável.

## 4. Síntese comparativa da equipe

| Critério | C01 | C02 | C03 | Oportunidade para o projeto |
|---|---|---|---|---|
| Navegação |  |  |  |  |
| Feedback/estado |  |  |  |  |
| Prevenção/recuperação de erro |  |  |  |  |
| Terminologia |  |  |  |  |
| Acessibilidade |  |  |  |  |
| Eficiência |  |  |  |  |

## 5. Recomendações derivadas

Liste recomendações com origem explícita.

- **RC01:** {{recomendação}} — derivada de {{C01/C02/evidência}}.
- **RC02:** {{...}}

## Referências

{{fontes dos produtos, avaliações e literatura}}

## Checklist

- [ ] O mapa inicial de alternativas da Entrega 1 foi revisitado e aprofundado.
- [ ] Hipóteses relevantes sobre mercado/padrões foram atualizadas na rastreabilidade quando surgiram evidências.
- [ ] Há pelo menos uma análise completa por integrante.
- [ ] Cada análise contém prints legíveis da interface.
- [ ] Prints mostram telas/estados relevantes, não apenas logos/homepage.
- [ ] Foram analisados concorrentes e/ou interfaces representativas ao público.
- [ ] Em TCC sem interface original, foram investigadas ferramentas profissionais análogas às atividades do usuário escolhido.
- [ ] Padrões como dashboard, relatório, filtros e CRUD foram analisados como soluções para tarefas, não como requisitos automáticos.
- [ ] Opiniões de UX têm fonte.
- [ ] A síntese compara critérios comuns e produz recomendações.
- [ ] Não há “copiar porque o concorrente faz”; há justificativa de adequação ao público/contexto.
