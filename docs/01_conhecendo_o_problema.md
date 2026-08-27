# Entrega 1 — Conhecendo o projeto, o usuário e o problema

**Data:** 17/08/2026 
**Status:** em andamento 
**Responsabilidade:** 1 solução consolidada por equipe

## Objetivo da atividade

Reinterpretar o tema do TCC sob a perspectiva de Interação Humano-Computador e construir um **entendimento comum entre os integrantes da equipe**.

A disciplina utiliza preferencialmente o tema do TCC para os exercícios de IHC. Isso vale tanto para TCCs que já preveem uma interface quanto para trabalhos cujo resultado principal é algoritmo, modelo, API, biblioteca, análise de dados, infraestrutura, estudo experimental ou outro artefato técnico.

> **Importante:** a interface projetada na disciplina é um artefato de aprendizagem de IHC. Ela **não se torna automaticamente uma obrigação do TCC**. Sua incorporação ao trabalho de conclusão depende de decisão da equipe e do orientador.

Antes de preencher, leia [`../GUIA_ESCOPO_IHC.md`](../GUIA_ESCOPO_IHC.md).

Nesta primeira semana a equipe **não deve começar desenhando telas**. Primeiro deverá compreender:

- o que o TCC realmente produz;
- quem poderia obter valor dessa contribuição;
- quais pessoas interagem, administram, configuram, interpretam ou são afetadas;
- o que essas pessoas precisam alcançar;
- como atividades relacionadas acontecem hoje;
- problemas, limitações e contexto;
- alternativas existentes;
- qual recorte de interação fará sentido para a disciplina.

Ao final desta entrega, a equipe deve diferenciar:

- **tema do TCC** × **escopo formal do TCC** × **escopo de IHC da disciplina**;
- **objetivo do projeto** × **objetivo do usuário**;
- **problema do usuário** × **solução tecnológica**;
- **fato conhecido** × **hipótese** × **lacuna de conhecimento**;
- **capacidade técnica** × **forma de uso dessa capacidade**;
- **funcionalidade** × **atividade/resultado que o usuário precisa alcançar**;
- **usuário direto** × **stakeholders**.

---

## Como classificar as respostas

Sempre que a resposta fizer uma afirmação sobre usuários, problemas, atividades, necessidades, contexto ou mercado, use:

- **[F] Fato conhecido** — existe evidência/fonte.
- **[H] Hipótese** — afirmação plausível que ainda precisa ser investigada.
- **[?] Não sabemos ainda** — lacuna relevante.

Quando usar `[F]`, informe a origem. Hipóteses prioritárias devem receber IDs (`H01`, `H02`...) e também ser registradas em [`../RASTREABILIDADE.md`](../RASTREABILIDADE.md).

> **Exemplo:** `[H] H01 — DBAs considerariam útil comparar automaticamente o plano atual de execução com uma recomendação produzida pelo algoritmo.`

Uma hipótese explicitada é melhor do que uma suposição escondida.

---

# 0. Identificação do TCC e da equipe

## 0.1 Membros

| Nome completo | Matrícula | GitHub |
|---|---:|---|
| Willian Verenka Oliveira Silva | 22.124.081-5 | https://github.com/willianverenka |
| Gabriel Lovato | 22.123.004-8 | https://github.com/gabriellovato7 |
| Théo Zago Zimmermann | 22.123.035-2 | https://github.com/theozago |
| João Vitor Sitta | 22.123.054-3 | https://github.com/JVSittaG |

## 0.2 Título atual do TCC

Diagnóstico de falhas em sistemas distribuídos por pipeline em dois estágios: filtragem estrutural em grafos de observabilidade e geração de hipóteses com LLMs

## 0.3 Orientador(a)

Leonardo Anjoletto Ferreira

## 0.4 Qual é o resultado principal atualmente previsto no TCC?

Marque e descreva:

- [ ] sistema/aplicação interativa;
- [ ] algoritmo;
- [ ] modelo de IA/ML/LLM;
- [ ] biblioteca/API/framework;
- [ ] análise de dataset;
- [ ] estudo/benchmark/avaliação experimental;
- [ x ] infraestrutura/backend;
- [ ] componente embarcado/IoT;
- [ ] outro: {{...}}.

**Descrição:** O TCC prevê um pipeline de diagnóstico de falhas em sistemas distribuídos que, no primeiro estágio, filtra estruturalmente um grafo de observabilidade para selecionar evidências relevantes e, no segundo, utiliza um modelo de linguagem de grande porte para gerar hipóteses plausíveis sobre a origem da falha.

## 0.5 O TCC já previa desenvolvimento de interface com usuário?

- [ ] Sim, a interface já faz parte do TCC.
- [ x ] Parcialmente; existe alguma interação, mas ainda não está bem definida.
- [ ] Não. O TCC é predominantemente técnico e não previa interface.

**Explique o que está formalmente previsto no TCC:** 

Formalmente, o TCC prevê a construção e a avaliação técnica do pipeline de diagnóstico, incluindo os mecanismos necessários para fornecer dados de observabilidade e consultar os resultados produzidos. Existe uma interação técnica parcialmente prevista, mas uma interface completa orientada a um produto ainda não está definida. 

> Esta resposta serve para separar o compromisso do TCC do projeto da disciplina. Mesmo quando a opção for **não**, a equipe irá definir uma interface para exercitar IHC.

---

# 1. Entendendo a contribuição do projeto

## 1.1 Explique o TCC em uma frase, sem citar linguagem de programação, framework ou banco de dados.

Algoritmos para analisar e auxiliar o diagnóstico de problemas em sistemas distribuídos.

## 1.2 Qual situação, atividade ou problema do mundo real motivou o TCC?

[F] Como dois devs participantes no grupo, notamos que diariamente em nosso trabalhos nós nos encontravamos perdendo muito tempo filtrando logs de sistemas, em quantidades massivas, de forma manual distribuídos para formar uma análise diagnóstica, e a motivação foi justamente trabalhar em métodos para fornecer ferramentas que mitiguem este problema. 

## 1.3 Qual é a **capacidade/contribuição central** produzida pelo TCC?

Complete, se ajudar:

> “Nosso TCC produz, melhora, analisa ou permite `{{capacidade}}`.”

Exemplos: otimizar consultas; classificar imagens; detectar anomalias; comparar modelos; identificar padrões; prever demanda; analisar desempenho; gerar resumos; recomendar configurações.

Nosso TCC investiga um pipeline que reduz o espaço de busca em dados de observabilidade por meio de filtragem estrutural em grafos e gera hipóteses plausíveis para apoiar o diagnóstico de falhas em sistemas distribuídos.

## 1.4 O que se espera que esteja diferente **para pessoas, organizações ou processos** se essa contribuição for bem-sucedida?

[H] Espera-se que pessoas que estejam monitorando sistemas distribuídos possam ter maior visibilidade dos erros que estão acontecendo e que consigam entender a causa raíz de forma rápida, a fim de contribuir também para uma ação assertiva adequada.

## 1.5 O que é mérito técnico/científico do TCC e o que seria uma possível aplicação prática?

| Mérito/contribuição técnica | Possível aplicação/valor em uso |
|---|---|
| Filtragem estrutural de grafos de observabilidade e geração de hipóteses diagnósticas com LLM | Apoiar profissionais na investigação de incidentes, concentrando evidências relevantes e oferecendo hipóteses inspecionáveis para orientar o diagnóstico inicial |

---

# 2. Entendendo as pessoas envolvidas

## 2.1 Quem interage diretamente com o produto, se já existe interface prevista?

Se não houver interface prevista no TCC, escreva `NÃO SE APLICA AO ESCOPO ORIGINAL` e prossiga para 2.2.

[F] Desenvolvedores, administradores de sistema, gestores de equipes de tecnologia, DevOps, SRE's (Site Reliability Engineer) e QA's.

## 2.2 Quem poderia **usar, configurar, administrar, operar, interpretar ou tomar decisões** a partir da contribuição técnica?

Considere perfis profissionais e stakeholders, não apenas consumidores finais.

| Perfil | Relação com a contribuição | O que faria | Status/evidência |
|---|---|---|---|
| Desenvolvedor | Responsável por atualizar o código para correções | Utilizaria a telemetria e hipóteses geradas para resolver bugs pela causa raiz no código  | F |
| SRE | Responsável por monitorar infraestrutura | Utilizaria a telemetria para determinar a saúde (a nível de aplicação ou infraestrutura) dos sistemas  | F |
| Gestor de equipe | Alocar recursos (humanos) para manutenção do sistema | Utilizaria as evidências e propagações de erros para priorizar correções de problemas específicos e alocar desenvolvedores para a correção | F |


## 2.3 Existem pessoas afetadas que não usariam a interface diretamente?

| Stakeholder | Como é afetado | Usa interface? | Status/evidência |
|---|---|---|---|
| Representante da empresa (relacionamento com cliente) | Terá insumos para comunicar instabilidades no sistema para clientes e parceiros estratégicos | não | F |

## 2.4 Que características desses perfis podem influenciar a interação?

Considere conhecimento do domínio, experiência tecnológica, frequência de uso, necessidades de acessibilidade, responsabilidade profissional, familiaridade com métricas, linguagem técnica, urgência etc.

[F] O conhecimento técnico da arquitetura dos sistemas, entendimento da temática (domínio) e a familiaridade com telemetria de sistemas distribuídos podem influenciar a interação com a ferramenta, de forma positiva ou negativa. 

---

# 3. Entendendo objetivos e atividades

## 3.1 O que o usuário está tentando conseguir no mundo real?

Não responda “usar o algoritmo”, “clicar no sistema” ou “ver o dashboard”.

[H] Diagnosticar e entender problemas complexos em sistemas distribuídos de forma rápida e com evidências concentradas.

## 3.2 Quais são as atividades mais importantes?

| ID | Atividade/objetivo | Quem realiza | Frequência/criticidade inicial | Status/evidência |
|---|---|---|---|---|
| A01 | Corrigir bugs | Desenvolvedor | Diariamente | {{...}} |
| A02 | Classificar a saúde do sistema | SRE | Diariamente | {{...}} |
| A03 | Classificar se bugs foram realmente resolvidos | QA's | Diariamente | {{...}} |

## 3.3 Qual atividade parece mais frequente? Por quê?

[F] A02 deve ser a mais frequente. O escopo do SRE é mais fechado, e a maior responsabilidade do profissional é justamente entender o estado atual dos sistemas e identificar problemas que podem estar ocorrendo em tempo real. Por conta disso, ele utilizaria a ferramenta o tempo todo como forma de apoio para apontar áreas problemáticas do sistema e poder reportar de forma adequada.

## 3.4 Qual parece mais crítica? Que consequência existe se for mal executada?

[H] A02 deve ser também a mais crítica. Por que engloba o caso que, caso existam áreas do sistema que estejam falhando frequentemente e a ferramenta não reporte de forma evidente, então se enfrenta uma situação que não há visibilidade suficiente de erros para o monitoramento, e é justamente o propósito da ferramenta.

---

# 4. Entendendo o problema ou processo atual

## 4.1 Como essas atividades são realizadas hoje, antes da interface imaginada na disciplina?

Pode existir software concorrente, linha de comando, planilha, notebook, script, painel técnico, processo manual, consulta a logs, análise visual, troca de mensagens, decisão por especialista etc.

[F] Existem softwares concorrentes, como DynaTrace e DataDog. Ainda sim, para diagnóstico de problemas, ainda depende da consulta de logs de partes faltosas e da construção uma relação causal para entender como que um erro aconteceu e qual foi seu impacto.

## 4.2 O que é difícil, demorado, confuso, repetitivo, arriscado ou pouco transparente?

[H] É demorado pra encontrar os logs relevantes para análise técnica, e é difícil construir a relação pra entender qual foi a causa raíz do erro.

## 4.3 Que informações o profissional precisa interpretar para tomar decisão?

Logs, telemetria do sistema, funcionamento da codebase e o conhecimento do domínio para entender o impacto do usuário.

## 4.4 O que acontece quando a atividade falha ou quando o resultado é interpretado incorretamente?

[F] A análise errônea leva a uma ação inadequada, como uma correção de um bug de forma parcial, ou até mesmo a falha em resolver este problema.

## 4.5 Conte uma situação concreta.

Escreva uma pequena narrativa com pessoa, objetivo, atividade, contexto, dificuldade e consequência. **Não descreva ainda a futura solução.**

[F] Um desenvolvedor é comunicado de um erro em certo sistema. Para entender o problema e planejar sua ação de correção, ele utiliza uma plataforma para pesquisar a telemetria e logs produzidos por aquele problema que está procurando. A dificuldade está em encontrar as evidências corretas em tempo hábil para trabalhar em sua solução, e a consequência é a baixa assertividade e a demora para o diagnóstico da causa raiz do problema.

## 4.6 Que evidência existe hoje?

| Evidência/fonte | O que sustenta | Limitação |
|---|---|---|
| {{...}} | {{...}} | {{...}} |

---

# 5. Entendendo o contexto de uso

## 5.1 Onde e em quais situações a interação poderia ocorrer?

[F] Em qualquer local do sistema, momentos após deploys e atualizações no sistema são propícios para aparição de novos erros, e a ferramenta auxilia nestes cenários. Também para a procura de bugs específicos já mapeados.

## 5.2 Em quais dispositivos/equipamentos?

[F] Nos servidores que hospedam os serviços que compõem o sistema. 

## 5.3 Existem condições físicas relevantes?

Considere iluminação, ruído, mobilidade, conexão, privacidade, uso compartilhado, interrupções, pressão de tempo etc.

[F] A pressão de tempo é um fator determinante, alguns usuários, como o desenvolvedor, possuem um prazo máximo estipulado por seus superiores para diagnosticar, planejar e executar a resolução do problema.

## 5.4 Existem fatores sociais ou organizacionais?

Considere papéis, chefias, equipes, permissões, aprovação, responsabilidade profissional, auditoria, turnos e colaboração.

[H] H04: A investigação de incidentes ocorre sob pressão de tempo e pode envolver colaboração entre o SRE de plantão, desenvolvedores responsáveis pelos serviços e gestores. Políticas de acesso, responsabilidade sobre cada serviço e a possível presença de dados sensíveis na telemetria também podem limitar quem consulta, compartilha ou registra evidências.

## 5.5 Existe necessidade de histórico, rastreabilidade ou auditoria?

[F] Existe a necessidade de auditoria e restrição do uso, pois os logs dos sistemas podem revelar informações sensíveis sobre dados de usuários, por exemplo. Portanto, o acesso à esses dados e filtros deve ser limitado e planejado para perfis de usuários específicos.

## 5.6 Um erro pode produzir consequência relevante? Qual?

[F] Pode contribuir para a continuidade de sistemas faltosos e inconfiáveis, prejudicando o fornecimento do produto/software e o relacionamento com os clientes.
---

# 6. Entendendo mercado e alternativas existentes

> Nesta entrega faça apenas um **levantamento inicial**. A análise aprofundada ocorre na Entrega 2.

## 6.1 Como pessoas resolvem problemas semelhantes hoje?

| Alternativa atual | Quem usa | Para quê | Status/evidência |
|---|---|---|---|
| Consulta e filtragem manual de logs, métricas e traces | SREs e desenvolvedores | Localizar sintomas e evidências de um incidente | {{...}} |
| Mapas de serviços e navegação entre sinais de observabilidade | SREs e DevOps | Investigar dependências e propagação da falha | {{...}} |

## 6.2 Existem produtos que atuam na mesma área, mesmo sem serem equivalentes ao TCC?

[F] DataDog, DynaTrace são equivalentes, mas também existem produtos da mesma área como o Grafana, Application Insights, etc.

## 6.3 Quais interfaces profissionais esse público já conhece?

Exemplos possíveis: ferramentas de banco, IDEs, consoles de nuvem, dashboards, plataformas de dados, ferramentas de monitoramento, painéis de IA, sistemas administrativos.

Ferramentas de monitoramento de telemetria de aplicações e logs. 

## 6.4 O que essas soluções parecem fazer bem?

[F] As soluções existentes concentram sinais de observabilidade, oferecem filtros por serviço e período, permitem aprofundamento em logs e traces e apresentam relações entre componentes. Algumas também agrupam anomalias e apresentam candidatos a causa.

## 6.5 O que parecem fazer mal, dificultar ou não atender?

Apresentam dados que são heterogêneos uniformimente, dificulta a formulação de hipóteses de causalidade e, por consequência, um diagnóstico técnico.

## 6.6 Que padrões de interface ou vocabulário parecem familiares a esse público?

[F] São familiares padrões como seleção de intervalo de tempo, filtros por serviço e ambiente, severidade e estado do incidente, mapas de dependências, listas de ocorrências e aprofundamento progressivo do resumo para logs, métricas e traces.

---

# 7. Derivando o escopo de IHC da disciplina

## 7.1 Escolha o caminho do projeto

### Caminho A — TCC já possui interface

Explique qual parte da interface será usada como recorte da disciplina e por que esse fluxo é relevante.

Será explorado o fluxo de investigação de um único incidente: delimitação do serviço e período afetados, acompanhamento do processamento, inspeção do subgrafo de observabilidade, avaliação das hipóteses geradas e consulta às evidências relacionadas. O fluxo é relevante porque apoia diretamente o diagnóstico do usuário.

### Caminho B — TCC não possui interface prevista

Faça o exercício de transferência de uso:

> **Imagine que o TCC foi concluído com sucesso e uma empresa, laboratório ou organização quer transformar a contribuição em algo utilizável. Quem precisaria interagir com ela e para quê?**

Responda:

1. quem poderia contratar/adotar a solução? {{...}}
2. quem seria o usuário direto? {{...}}
3. quem administraria/configuraria? {{...}}
4. quem interpretaria resultados? {{...}}
5. quem tomaria decisões? {{...}}
6. quais dados/entradas seriam necessários? {{...}}
7. quais resultados deveriam ser compreendidos? {{...}}
8. que erros/rupturas seriam possíveis? {{...}}

## 7.2 Qual perfil será priorizado no projeto de IHC?

SRE.

**Por que esse perfil foi escolhido?** 

esse perfil lida diretamente com telemetria, precisa entender rapidamente a propagação das falhas e conecta o resultado do pipeline às decisões operacionais e ao encaminhamento para desenvolvedores.

## 7.3 Qual objetivo desse usuário será priorizado?

Formular e comunicar um diagnóstico inicial fundamentado sobre a provável origem e o impacto de um incidente.

## 7.4 Que interface será explorada na disciplina?

Complete:

> **Para fins da disciplina de IHC, será projetada uma interface que permita a `{{perfil}}` utilizar `{{capacidade/resultado do TCC}}` para `{{objetivo}}`, no contexto de `{{situação}}`.**

Para fins da disciplina de IHC, será projetada uma interface que permita a um SRE de plantão utilizar o subgrafo de observabilidade filtrado e as hipóteses geradas pelo pipeline para formular e comunicar um diagnóstico inicial fundamentado de um incidente, sob pressão de tempo após um alerta ou implantação.

## 7.5 Qual é a relação dessa interface com o TCC?

- [ ] Já fazia parte do TCC.
- [ x ] É um aprofundamento de algo parcialmente previsto.
- [ ] É uma extensão conceitual criada para a disciplina.
- [ ] É um protótipo demonstrativo de aplicação potencial.
- [ ] Outra: {{...}}.

> **Declaração:** a interface desenvolvida nesta disciplina é um artefato de aprendizagem de IHC baseado no tema do TCC. Sua inclusão ou implementação no TCC somente ocorrerá se isso for posteriormente decidido pela equipe e pelo orientador.

---

# 8. Levantando possibilidades de interação — sem desenhar ainda

A equipe pode registrar possibilidades para investigação. **Não significa que todas serão implementadas.**

Marque apenas as que parecem plausíveis e explique o objetivo correspondente.

| Possibilidade | Pode fazer sentido? | Objetivo/tarefa que justificaria | Evidência atual |
|---|---|---|---|
| Dashboard/visão geral | sim | entender a saúde geral da aplicação | {{...}} |
| Configuração/parametrização | sim | configurar a frequência da ingestão e processamento de dados | {{...}} |
| Entrada/upload/seleção de dados | sim | selecionar quais dados serão ingeridos | {{...}} |
| Acompanhamento de processamento | talvez | entender a quantidade de dados que ainda não foram processados, já que são potenciais insumos para análise | {{...}} |
| Relatório/resultados | sim | {{...}} | {{...}} |
| Histórico com busca/filtros | não | {{...}} | {{...}} |
| Comparação de resultados | não | {{...}} | {{...}} |
| Explicabilidade/detalhamento | sim | detalhamento de erros individuais em vértices dos grafos para enriquecer a análise do usuário | {{...}} |
| Administração/configurações globais | não | {{...}} | {{...}} |
| Usuários/perfis/permissões | talvez | restringir o acesso a pessoas autorizadas | {{...}} |
| CRUD de entidade do domínio | não | {{...}} | {{...}} |
| Auditoria/logs | talvez | {{...}} | {{...}} |
| Alertas/ocorrências | sim | alertar sobre erros recorrentes que estão se propagando pelos serviços, também sobre erros e quedas críticas | {{...}} |
| Ajuda/documentação | não | {{...}} | {{...}} |

> **Atenção:** “login + dashboard + CRUD” não é uma solução universal. Cada padrão deve surgir de uma tarefa real.

---

# 9. Benefícios e ações iniciais

## 9.1 Qual benefício concreto o projeto de IHC pretende oferecer?

| Benefício esperado | Problema/necessidade | Usuário | Status/evidência |
|---|---|---|---|
| Reduzir o esforço para reunir e interpretar evidências durante a investigação de um incidente | Telemetria dispersa e dificuldade de estabelecer uma relação provável entre sintomas e origem | SRE | {{...}} |

## 9.2 Que ações o usuário deverá conseguir realizar?

| ID | O usuário precisa conseguir... | Para alcançar... | Prioridade inicial |
|---|---|---|---|
| F01 | Delimitar o incidente por serviço, sintoma e período | Restringir o espaço/amostra de evidências | média |
| F02 | Inspecionar o subgrafo e os componentes afetados | Compreender a propagação da falha | alta |
| F03 | Examinar hipóteses e suas evidências | Formular um diagnóstico fundamentado | alta |

## 9.3 Tecnologias/restrições já definidas no TCC

A tecnologia aparece **agora**, depois do entendimento do uso.

| Tecnologia/restrição | Por que existe | Possível impacto na interação |
|---|---|---|
| {{...}} | {{...}} | {{...}} |

---

# 10. Hipóteses e dúvidas prioritárias

| ID | Hipótese/dúvida | Por que importa | Como poderá ser investigada |
|---|---|---|---|
| H01 | [H] A visualização da estrutura de dependências entre serviços e spans será relevante para que o SRE compreenda a propagação da falha. | O TCC utiliza grafos de spans como representação estrutural e a interface proposta prevê a inspeção do subgrafo. É necessário descobrir quanto dessa estrutura deve ser apresentada ao usuário e em qual nível de detalhe. | Entrega 2/3/7/... |
| H02 | [?] Ainda não sabemos qual quantidade de detalhes deve ser apresentada inicialmente para equilibrar compreensão e redução de sobrecarga cognitiva. | Mostrar o trace completo pode reproduzir o problema original de excesso de informação, enquanto uma filtragem muito agressiva pode ocultar evidências relevantes. | {{...}} |
| H03 | [H] As hipóteses geradas pelo LLM serão mais úteis ao SRE quando apresentadas acompanhadas das evidências estruturais que as sustentam, em vez de apresentadas apenas como uma conclusão textual. | O TCC gera uma hipótese diagnóstica estruturada, mas a utilização profissional depende da capacidade do usuário de avaliar criticamente a resposta. A apresentação das evidências pode ser necessária para que o resultado seja interpretável e confiável. | {{...}} |

Registre em [`../RASTREABILIDADE.md`](../RASTREABILIDADE.md).

---

# 11. Síntese da equipe

| Pergunta | Síntese atual |
|---|---|
| Qual é a contribuição central do TCC? | O TCC utiliza um pipeline em dois estágios para apoiar o diagnóstico de falhas em sistemas distribuídos. O primeiro estágio representa traces como grafos e realiza uma filtragem estrutural por GNN ou heurística; o segundo utiliza um LLM para transformar a evidência selecionada em uma hipótese diagnóstica estruturada. |
| O TCC já previa interface? | Não completamente. O escopo formal prevê a construção e avaliação técnica do pipeline e os mecanismos necessários para fornecer dados de observabilidade e consultar seus resultados, mas não define uma interface completa orientada a um produto. |
| Quem é o usuário prioritário de IHC? | SRE |
| O que ele precisa alcançar? | Identificar e formular uma resolução sobre a provável origem e o impacto de um incidente |
| Qual problema/atividade será estudado? | A investigação de incidentes em sistemas distribuídos, especialmente o processo de localizar evidências relevantes em grandes volumes de telemetria e compreender a propagação de uma falha entre diferentes serviços. |
| Como isso acontece hoje? | O profissional utiliza plataformas de observabilidade para consultar e filtrar logs, métricas e traces. |
| Qual é o contexto de uso? | Após alertas, deploys, atualizações ou durante a procura de bugs específicos. |
| Que interface/recorte será explorado? | {{...}} |
| Como a interface se relaciona ao TCC? | Ela utiliza o subgrafo de observabilidade filtrado e a hipótese diagnóstica gerada pelo LLM, produzido pelo pipeline. |
| Quais pontos ainda são hipóteses? | {{H01...}} |

### Delimitação

**Dentro do escopo de IHC:** Apoiar o diagnóstico inicial de um incidente, disponibilizacao do subgrafo, apresentação das hipóteses, delimitação de serviço, período e sintomas e comunicação de um diagnóstico inicial. 
**Fora do escopo de IHC:** Treinamento da GNN, construção dos grafos, definição dos algoritmos de filtragem,,   
**Dentro do escopo formal do TCC:** Construção e avaliação experimental do pipeline em dois estágios, incluindo a representação dos traces como grafos, filtragem estrutural por GNN e heurística, geração de hipóteses diagnósticas por LLM e comparação entre trace completo, subgrafo GNN e subgrafo heurístico segundo métricas estruturais, diagnósticas e operacionais.  
**Interface da disciplina será implementada no TCC?** Não definido

---

# 12. Como esta entrega alimenta as próximas

- **Entrega 2:** verifica mercado, concorrentes e interfaces profissionais representativas.
- **Entrega 3:** detalha perfis e contexto.
- **Entrega 4:** aprofunda situações problemáticas.
- **Entrega 5:** modela tarefas centrais.
- **Entrega 6:** experimenta alternativas em baixa fidelidade.
- **Entrega 7:** investiga hipóteses com dados.
- **Entrega 8:** define restrições e metas de usabilidade.
- **Entregas 9–11:** transformam o recorte em modelo de interação e protótipo.
- **Entregas 12–14:** avaliam a interface construída na disciplina.

A Entrega 1 é uma **fotografia inicial do conhecimento**. Ela pode e deve ser revisada quando surgirem evidências.

---

# 13. Relação com INOVA e comunicação do projeto

Prepare uma explicação de até três frases:

1. **Problema/atividade humana:** {{...}}
2. **Contribuição técnica do TCC:** {{...}}
3. **Como uma pessoa poderia utilizar essa contribuição:** {{...}}

Essa síntese ajuda a apresentar o projeto para público não especializado sem reduzir seu mérito técnico.

---

# Checklist de qualidade

- [ ] Está clara a diferença entre tema do TCC, escopo formal do TCC e escopo de IHC.
- [ x ] A equipe declarou se o TCC já previa interface.
- [ ] Se não previa, foi derivado um usuário plausível e um objetivo de uso.
- [ x ] A interface de IHC não foi apresentada como obrigação automática do TCC.
- [ x ] A contribuição do TCC foi descrita sem começar por tecnologias de implementação.
- [ x ] Usuários diretos e stakeholders foram diferenciados.
- [ x ] Foram considerados profissionais que configuram, administram, interpretam ou decidem, quando pertinente.
- [ x ] Objetivo do usuário não foi confundido com objetivo do projeto.
- [ x ] Processo/problema atual foi descrito antes da solução.
- [ x ] Existe situação concreta de uso/problema.
- [ x ] Contexto físico, social/organizacional, dispositivos e consequências de erro foram considerados.
- [ x ] Mercado/alternativas existentes foram levantados inicialmente.
- [ x ] Possibilidades como dashboard, relatório, histórico, filtros e CRUD foram tratadas como hipóteses de solução, não como requisitos automáticos.
- [ x ] Cada possibilidade de interface tem um objetivo/tarefa que poderia justificá-la.
- [ x ] Afirmações relevantes estão marcadas `[F]`, `[H]` ou `[?]`.
- [ ] Hipóteses prioritárias receberam IDs e foram para a rastreabilidade.
- [ ] O recorte de IHC é viável para modelar, prototipar e avaliar no semestre.
- [ x ] A equipe consegue explicar problema humano → contribuição computacional → forma de uso.
