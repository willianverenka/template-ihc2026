# Entrega 2 — Público-alvo e análise de concorrência

**Data:** {{dd/mm/aaaa}}  
**Status:** ⬜ não iniciada  
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
| Datadog | análogo | Plataforma de observabilidade utilizada para monitoramento, logs, métricas e traces | [F] | analisar |

Se uma hipótese da Entrega 1 for confirmada ou refutada durante esta análise, atualize `H01`, `H02`... em [`../RASTREABILIDADE.md`](../RASTREABILIDADE.md).

## 1. Público-alvo desta análise

[F] O público alvo principal definido é o SRE. Responsável pelo monitoramento, disponibilidade, confiabilidade e investigação de problemas em sistemas.
O DataDog é uma referência pois é utilizado por equipes de desenvolvimento e operações para monitoramento e observabilidade de aplicações e infraestruturas. Profissionais como Software Engineers e DevOps Engineers estão entre os usuários do produto.
O objetivo desta análise é compreender quais convenções de interface um SRE pode encontrar em uma ferramenta profissional de observabilidade e quais delas podem ser relevantes para o fluxo definido na Entrega 1:

Delimitar um incidente → inspecionar o subgrafo → avaliar evidências → analisar hipóteses → comunicar um diagnóstico inicial.

## 2. Concorrentes diretos/indiretos

### Análise C01 — {{produto}}

**Autor(a):** Théo Zago Zimmermann 22.123.035-2 
**Tipo:** análogo   
**Link oficial:** [{{URL}}](https://www.datadoghq.com/dg/monitor/free-trial-b/?utm_source=google&utm_medium=paid-search&utm_campaign=dg-coreplatform-multi-ww-en-brand&utm_keyword=datadog&utm_matchtype=e&igaag=198192973844&igaat=&igacm=23852702120&igacr=808951976832&igakw=datadog&igamt=e&igant=g&utm_campaignid=23852702120&utm_adgroupid=198192973844&gad_source=1&gad_campaignid=23852702120&gbraid=0AAAAADFY9Nm7Gbuts42odNhbqKdYLKqvl&gclid=EAIaIQobChMIxaz1i_bBlgMVxUdIAB2qFDx1EAAYASAAEgKo0vD_BwE)  
**Data de acesso:** 27/08/2026

#### Contexto e proposta

[F] O Datadog é uma plataforma de observabilidade que reúne recursos para monitoramento de infraestrutura, aplicações e diferentes sinais de telemetria, incluindo métricas, logs e traces.

[F] A documentação oficial apresenta o Log Explorer como um ambiente para pesquisa, filtragem, agrupamento, visualização e exportação de logs. (Datadog Monitoramento)

[F] O Trace Explorer permite pesquisar spans utilizando tags e outros atributos, possibilitando a investigação de traces em diferentes níveis. (Datadog Monitoramento)

[F] O Service Map representa os serviços da aplicação e as dependências observadas entre eles, permitindo compreender como os dados fluem pela arquitetura e identificar possíveis áreas problemáticas. (Datadog Monitoramento)

Para este TCC, o Datadog é mais bem caracterizado como interface profissional análoga do que como concorrente direto do algoritmo desenvolvido. O TCC propõe um pipeline específico de filtragem estrutural e geração de hipóteses com LLM, enquanto o Datadog oferece uma plataforma ampla de observabilidade.

A principal contribuição desta análise, portanto, é entender como uma ferramenta profissional materializa as atividades de observabilidade e investigação de incidentes que o SRE já precisa realizar.

#### Funcionalidades relevantes

| Funcionalidade | Como é realizada | Evidência/print | Observação de IHC |
|---|---|---|---|
| Dashboard	 | Apresenta informações de monitoramento em uma visão consolidada, permitindo acompanhar diferentes indicadores. | `-` | [F] Favorece uma visão geral antes do aprofundamento. Para o projeto, pode apoiar a tarefa de compreender rapidamente o estado do incidente. |
| Log Explorer | Permite pesquisar, filtrar, agrupar e visualizar logs. | `-` | [F] O filtro reduz o conjunto de informações apresentado. É diretamente relacionado à tarefa F01 da Entrega 1 |
| Trace Explorer | Permite pesquisar spans por tags e atributos e explorar traces. | `-` | [F] Permite passar de uma visão de busca para a inspeção de evidências específicas. Isso é relevante para H02. |
| Service Map | Representa serviços e suas dependências observadas. | `-` | [F] É diretamente relacionado à H01, pois apresenta visualmente relações entre componentes do sistema. |
| Correlação entre sinais | Permite relacionar diferentes informações de observabilidade durante a investigação. | `-` | [H] Esse padrão pode reduzir a necessidade de analisar sinais completamente isolados e pode inspirar a relação entre hipóteses e evidências do TCC. |
| Alertas/monitores | Monitores acompanham condições definidas e podem sinalizar ocorrências. | `-` | [F] Pode funcionar como ponto inicial para uma investigação de incidente. |
| Investigação de incidentes | A plataforma possui recursos voltados ao acompanhamento e resposta a incidentes. | `-` | {{...}} |

#### Experiência do usuário e opiniões

[F] No G2, o Datadog apresenta atualmente avaliação média de 4,4/5, baseada em centenas de avaliações. (G2)

[F] Avaliações públicas destacam positivamente a capacidade de monitorar diferentes aplicações e infraestruturas, a visualização de logs e métricas e a possibilidade de obter informações para identificar problemas. Uma avaliação recente também descreve a plataforma como útil para monitoramento de diferentes ambientes e redução do esforço humano na identificação de erros. (G2)

[F] Em avaliações agregadas, a plataforma apresenta pontuação de 8,2/10 em facilidade de uso e 8,3/10 em facilidade de configuração. (G2)

[H] Ao mesmo tempo, avaliações públicas apontam uma curva de aprendizado elevada e percepção de excesso de recursos para alguns usuários. Também aparecem críticas relacionadas ao custo e à complexidade da plataforma. Essas opiniões não devem ser interpretadas como problemas universais, mas são evidências relevantes de possíveis dificuldades de interação. (G2)

Para o projeto de IHC, essa observação é especialmente relevante. O objetivo não deve ser reproduzir a quantidade de funcionalidades do Datadog, mas selecionar somente as informações necessárias para o SRE executar as tarefas definidas na Entrega 1.


#### Padrões e tendências percebidos

A análise do Datadog identificou os seguintes padrões relevantes:

1. Visão geral → detalhamento

[F] O usuário pode começar com uma visão mais ampla dos dados e posteriormente aprofundar uma ocorrência, log, span ou serviço.

Relação com o TCC: esse padrão é relevante para H02, pois evita obrigar o SRE a visualizar todos os dados disponíveis simultaneamente.

2. Filtragem progressiva

[F] O Log Explorer permite pesquisar e filtrar logs, além de agrupá-los e visualizá-los de diferentes formas. (Datadog Monitoramento)

Relação com o TCC: corresponde diretamente à necessidade F01 de delimitar o incidente por serviço, período e outros critérios.

3. Visualização de dependências

[F] O Service Map apresenta serviços e suas dependências observadas em tempo real. (Datadog Monitoramento)

Relação com o TCC: possui relação direta com H01 e com a necessidade F02 de inspecionar o subgrafo de observabilidade.

4. Correlação de evidências

[F] A plataforma permite trabalhar com diferentes sinais de observabilidade e navegar entre informações relacionadas.

Relação com o TCC: reforça H03, pois uma hipótese diagnóstica deve idealmente poder ser analisada em conjunto com as evidências que a sustentam.

5. Investigação orientada por ocorrência

[F] A plataforma oferece mecanismos de monitoramento e investigação que permitem partir de uma ocorrência e aprofundar sua análise.

Relação com o TCC: aproxima-se do cenário escolhido para a disciplina, no qual o SRE recebe um alerta e inicia a investigação.

#### Pontos positivos, limitações e lições

| Ponto | Evidência | Implicação para nosso projeto |
|---|---|---|
| Concentração de informações | Logs, traces e outros sinais podem ser investigados dentro da plataforma. | Adotar como referência. Evitar que o SRE precise procurar evidências em fontes completamente separadas. |

| Filtros	 | O Log Explorer permite restringir e agrupar informações. (Datadog Monitoramento)	Adotar. |  Relaciona-se diretamente à F01 |

| Visualização de dependências | O Service Map apresenta relações entre serviços. | Adotar como referência. O subgrafo do TCC pode utilizar representação visual das relações relevantes. |

| Aprofundamento progressivo | O Trace Explorer permite pesquisar spans e investigar informações específicas.  | Adotar. Mostrar inicialmente apenas informações relevantes e permitir detalhamento sob demanda. |

| Grande quantidade de recursos | Avaliações apontam curva de aprendizado e complexidade para alguns usuários.  | Evitar copiar. O protótipo deve apresentar apenas informações relacionadas às tarefas prioritárias. |

| Integração de sinais | A plataforma trabalha com diferentes fontes de telemetria. | Adotar. Relacionar hipótese, subgrafo e evidências relevantes. |

| Visualizações configuráveis | Logs podem ser visualizados e transformados em diferentes representações.  | Adotar parcialmente. A flexibilidade pode ser útil, mas não deve aumentar desnecessariamente a carga cognitiva. |

| Compartilhamento	 | Explorações podem ser salvas e compartilhadas com colegas. | Considerar. Pode apoiar a comunicação do diagnóstico inicial entre SRE e desenvolvedores. |




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
