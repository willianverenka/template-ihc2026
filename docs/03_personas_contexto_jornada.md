# Entrega 3 — Personas, mapa de empatia, contexto de uso e jornada

**Data:** 03/09/2026
**Status:** ⬜ não iniciada  
**Responsabilidade:** 1 persona por integrante; 1 mapa de empatia, 1 contexto de uso consolidado e 1 jornada por equipe (salvo orientação diferente do docente).

## Objetivo da atividade

Representar grupos de usuários de forma útil para decisões de design. Persona não é personagem decorativo: suas características devem alterar requisitos, prioridades, linguagem, fluxos ou critérios de avaliação.

## Atenção a projetos técnicos

Em TCCs sem interface original, a persona pode representar um **profissional que se apropria da contribuição técnica**: DBA, analista, cientista de dados, administrador, pesquisador, técnico, operador, gestor ou especialista de domínio.

Não escolha um perfil apenas porque “parece combinar” com a tecnologia. Explique **qual objetivo esse perfil teria e qual parte da contribuição do TCC produziria valor para ele**. Se ainda for hipótese, mantenha como hipótese/proto-persona a validar.

Também considere papéis diferentes quando houver tarefas distintas, por exemplo:

- operador que executa análises;
- administrador que configura e gerencia permissões;
- especialista que interpreta resultados;
- gestor que consulta relatórios e decide;
- auditor que revisa histórico.

## Entradas da Entrega 1

Antes de criar personas, retome os tipos de usuários, características relevantes, objetivos e hipóteses registradas na Entrega 1. A persona **não deve transformar uma hipótese inicial em fato por meio de uma história fictícia**.

| Item da Entrega 1 | Status inicial | Evidência disponível agora | Como será tratado nesta entrega |
|---|---|---|---|
| SRE como usuário prioritário | F | Definido pela equipe na Entrega 1 | Incorporar como persona primária |
| Desenvolvedor como usuário | F | Identificado como profissional que utiliza evidências para correção de problemas | Incorporar como persona secundária |
| QA como usuário | F | Identificado como profissional que pode utilizar informações de telemetria para verificar problemas | Incorporar como persona secundária |
| Gestor de equipe | F | Identificado como stakeholder que pode utilizar informações para priorização e alocação | Incorporar como persona secundária |
| H01 — relevância da visualização das dependências | H | O TCC utiliza grafos de observabilidade e ferramentas como Datadog apresentam mapas de serviços | Manter como hipótese e investigar |
| H02 — quantidade adequada de detalhes | ? | Ainda não existe evidência suficiente para determinar o nível ideal de detalhamento | Manter como lacuna |
| H03 — hipóteses acompanhadas de evidências | H | O pipeline produz hipóteses e ferramentas de observabilidade correlacionam diferentes sinais | Manter como hipótese e investigar |


## 1. Personas

### Persona P01 — Rafael Mendes

**Autor(a):** Théo Zago Zimmermann 22.123.035-2
**Tipo:** primária
**Base de evidências:** proto-persona a validar, construída a partir da Entrega 1 e da análise de interfaces profissionais de observabilidade.  
**Hipóteses da Entrega 1 relacionadas:** H01, H02, H03

![Persona P01](../assets/03_personas/persona_p01.svg)

| Campo | Descrição |
|---|---|
| Faixa etária / contexto relevante | Adulto em contexto profissional de tecnologia. A idade específica não é relevante para o projeto. |
| Ocupação/papel | SRE (Site Reliability Engineer), podendo atuar em regime de plantão para acompanhamento de sistemas. |
| Conhecimento do domínio | [H] Alto conhecimento de sistemas distribuídos, observabilidade, infraestrutura, métricas, logs e traces. |
| Experiência tecnológica | [H] Alta familiaridade com ferramentas profissionais de monitoramento e observabilidade. |
| Objetivos | Identificar rapidamente a origem provável de um incidente, compreender seu impacto e encaminhar uma ação adequada. |
| Necessidades | Visualizar informações relevantes, entender relações entre serviços e verificar as evidências que sustentam uma hipótese. |
| Dores/frustrações | [H] Grande volume de telemetria, necessidade de consultar diferentes sinais e dificuldade para estabelecer relações causais entre sintomas e origem do problema. |
| Motivadores | Reduzir o tempo de diagnóstico, aumentar a confiança na análise e diminuir o impacto dos incidentes. |
| Restrições/acessibilidade | [H] Pode utilizar a interface sob pressão de tempo, com interrupções e necessidade de interpretar informações técnicas rapidamente. |
| Ambiente típico de uso | Ambiente profissional de operações/engenharia, normalmente utilizando computador e ferramentas de observabilidade.  |
| Comportamentos relevantes | [H] Começa pela identificação do incidente, restringe o período e os serviços envolvidos, procura evidências e consulta outros profissionais quando necessário. |

**Decisões de design influenciadas por P01:**

Priorizar informações relevantes para o incidente em vez de apresentar toda a telemetria disponível.

Permitir delimitação por serviço, período e sintomas.

Apresentar o subgrafo de forma compreensível.

Permitir aprofundamento nas evidências.

Apresentar hipóteses juntamente com as evidências relacionadas.

Deixar claro o estado do processamento e da análise.

Evitar excesso de informações simultâneas.


### Síntese das personas

Explique diferenças entre os perfis e qual persona é prioritária. Evite personas duplicadas que só mudam nome/foto.

A P01 — SRE é a persona prioritária para o projeto de IHC porque é o perfil que mais diretamente realiza a atividade de investigação que a interface pretende apoiar.

As demais personas são importantes como participantes secundários do fluxo, principalmente na etapa de comunicação e encaminhamento do diagnóstico.

## 2. Mapa de empatia — equipe

**Persona escolhida:** P01 — Rafael Mendes (SRE)
**Justificativa:** o SRE foi definido na Entrega 1 como usuário prioritário e realiza diretamente a atividade de investigação de incidentes que constitui o recorte principal de IHC.

![Mapa de empatia](../assets/03_personas/mapa_empatia.svg)

Documente também em texto: o que vê; ouve; diz/faz; pensa/sente; dores; ganhos. Diferencie **evidência** de **hipótese**.

O que vê

[F] Ferramentas de observabilidade apresentam dashboards, métricas, logs, traces, alertas e mapas de dependências.

[H] Durante um incidente, o SRE precisa lidar com diferentes sinais de telemetria e identificar quais informações são relevantes para o problema atual.

O que ouve

[H] Pode receber alertas de monitoramento, relatos de desenvolvedores, outros profissionais de tecnologia ou usuários sobre comportamentos anormais.

[H] Durante incidentes, pode receber informações de diferentes membros da equipe simultaneamente.

O que diz e faz

[H] Procura delimitar o incidente por período, serviço e sintomas.

[H] Consulta logs, métricas e traces e tenta estabelecer uma relação entre os diferentes eventos.

[H] Pode comunicar um diagnóstico inicial para desenvolvedores e gestores.

O que pensa e sente

[H] Precisa determinar rapidamente se uma ocorrência representa um problema real e qual componente provavelmente está relacionado.

[H] Pode ter preocupação com a confiabilidade das informações utilizadas para tomar decisões.

[H] Uma hipótese sem evidências suficientes pode gerar desconfiança ou exigir investigação adicional.

Dores
[F] Grande volume de dados de observabilidade pode precisar ser analisado.
[H] Localizar rapidamente evidências relevantes pode ser difícil.
[H] Estabelecer relações causais entre diferentes eventos pode exigir conhecimento especializado.
[H] A pressão de tempo pode aumentar a dificuldade de investigação.
Ganhos
[H] Redução do tempo necessário para encontrar evidências relevantes.
[H] Maior clareza sobre os componentes envolvidos no incidente.
[H] Capacidade de avaliar uma hipótese diagnóstica juntamente com suas evidências.
[H] Comunicação mais objetiva do diagnóstico para outras equipes.
Síntese do mapa

A principal necessidade identificada para P01 é reduzir o esforço cognitivo e operacional necessário para transformar grande quantidade de telemetria em uma investigação compreensível.

A contribuição do TCC pode apoiar esse processo ao reduzir o espaço de busca por meio do subgrafo e gerar hipóteses diagnósticas. Porém, a interface deve permitir que o profissional inspecione e questione os resultados, evitando transformar a saída do LLM em uma decisão automática.

## 3. Contexto de uso — consolidação

| Dimensão | Descrição | Implicação de design |
|---|---|---|
| Usuários | SRE como usuário primário, com possível interação posterior de desenvolvedores, QA e gestores. | Priorizar necessidades do SRE e facilitar comunicação com outros papéis. |
| Tarefas | Delimitar incidente, analisar evidências, compreender dependências, avaliar hipóteses e comunicar diagnóstico. | Fluxo deve acompanhar a atividade real, não apenas organizar funcionalidades. |
| Equipamentos | [F] Computadores utilizados para acesso às ferramentas profissionais de observabilidade. | Interface deve ser adequada para leitura de informações técnicas e visualizações complexas. |
| Ambiente físico | [H] Ambiente profissional, potencialmente sujeito a interrupções durante incidentes. | Informações críticas devem ser facilmente identificáveis. |
| Ambiente social/organizacional | [H] Investigação pode envolver colaboração entre SRE, desenvolvedores e gestores. | Facilitar comunicação e compartilhamento de resultados. |
| Papéis/permissões/governança | [F] A Entrega 1 identificou necessidade de restringir acesso a informações de telemetria que podem conter dados sensíveis. | Considerar controle de acesso e exposição mínima de informações. |
| Volume de dados/histórico | [F] O problema do TCC envolve grandes volumes de dados de observabilidade. | Evitar apresentar toda a telemetria simultaneamente; utilizar filtragem e níveis de detalhe. |
| Pressão de tempo | [F] Incidentes podem exigir diagnóstico e ação em prazo reduzido. | Priorizar eficiência, feedback rápido e identificação clara do estado da análise. |
| Complexidade técnica | [F] Sistemas distribuídos possuem múltiplos serviços e relações entre componentes. | Utilizar representação das dependências e permitir aprofundamento progressivo. |
| Confiabilidade da informação | [H] O usuário pode precisar verificar se a hipótese produzida é sustentada pelas evidências. | Diferenciar claramente evidência observada de hipótese gerada. |


## 4. Jornada do usuário — equipe

**Persona:** {{P01}}  
**Objetivo da jornada:** {{...}}  
**Início e fim da jornada:** {{...}}

| Etapa                           | Situação/ação                                                                                | Objetivo                                           | Pensamento/emoção                                                                     | Dor                                                                       | Oportunidade de design                                         | Evidência                                                                         |
| ------------------------------- | -------------------------------------------------------------------------------------------- | -------------------------------------------------- | ------------------------------------------------------------------------------------- | ------------------------------------------------------------------------- | -------------------------------------------------------------- | --------------------------------------------------------------------------------- |
| **1. Recebimento do incidente** | O SRE recebe um alerta ou toma conhecimento de um comportamento anormal.                     | Entender qual ocorrência precisa ser investigada.  | [H] Precisa rapidamente determinar a gravidade.                                       | Alertas podem conter informações limitadas.                               | Apresentar resumo do incidente, serviço afetado e horário.     | [F] Alertas/ocorrências fazem parte das ferramentas de observabilidade.           |
| **2. Delimitação**              | O SRE define serviço, período e sintomas relacionados ao incidente.                          | Reduzir o espaço de busca.                         | [H] Quer evitar analisar dados irrelevantes.                                          | Grande quantidade de telemetria.                                          | Filtros simples e claramente identificados.                    | [F] Ferramentas como Datadog possuem filtros por sinais de observabilidade.       |
| **3. Processamento/análise**    | Os dados selecionados são processados pelo pipeline.                                         | Obter uma representação reduzida das evidências.   | [H] Precisa saber se pode avançar ou se deve aguardar.                                | Falta de visibilidade sobre o estado do processamento.                    | Feedback de processamento e estado atual da análise.           | [F] O TCC utiliza um pipeline em dois estágios.                                   |
| **4. Inspeção do subgrafo**     | O SRE analisa os componentes e relações selecionados.                                        | Compreender como a falha pode estar se propagando. | [H] Procura identificar um ponto provável de origem.                                  | Grafos muito grandes podem ser difíceis de interpretar.                   | Destacar componentes relevantes e permitir aprofundamento.     | [F] O TCC utiliza representação estrutural em grafos; Datadog possui Service Map. |
| **5. Avaliação da hipótese**    | O SRE consulta a hipótese gerada pelo LLM e as evidências associadas.                        | Formular um diagnóstico inicial.                   | [H] Precisa avaliar se a hipótese é plausível.                                        | Uma conclusão textual isolada pode não ser suficiente.                    | Apresentar hipótese + evidências + contexto.                   | [H] H03.                                                                          |
| **6. Investigação detalhada**   | O SRE consulta logs/traces ou evidências específicas relacionadas aos componentes apontados. | Confirmar ou refutar a hipótese inicial.           | [H] Pode aumentar a confiança ou perceber que precisa investigar outra possibilidade. | Excesso de informações pode dificultar a análise.                         | Aprofundamento progressivo e filtros contextuais.              | [F] Datadog oferece exploração detalhada de logs e traces.                        |
| **7. Comunicação**              | O SRE comunica o diagnóstico inicial para desenvolvedores ou outros responsáveis.            | Encaminhar a resolução do incidente.               | [H] Precisa transmitir informação suficiente sem excesso de detalhes.                 | Informações podem ser interpretadas de maneira diferente por cada equipe. | Gerar/organizar um resumo compartilhável do diagnóstico.       | [F] A Entrega 1 identificou comunicação entre papéis como parte do contexto.      |
| **8. Acompanhamento**           | A equipe responsável atua sobre o problema e acompanha seu comportamento.                    | Verificar evolução do incidente.                   | [H] Espera que o problema seja resolvido e que os sinais melhorem.                    | Pode ser necessário voltar às evidências anteriores.                      | Manter contexto da investigação e permitir consulta posterior. | [F] A Entrega 1 identificou necessidade de histórico/rastreabilidade.             |


> A jornada pode incluir etapas **antes, durante e depois** do uso do produto. Não transforme a jornada em lista de telas.

## Síntese

A análise das personas, do mapa de empatia e da jornada reforça que o principal problema de IHC não é simplesmente “mostrar o resultado do algoritmo”, mas apoiar o profissional na transformação de dados de observabilidade em uma investigação compreensível e verificável.

As necessidades que devem obrigatoriamente aparecer nos próximos cenários e tarefas são:

Delimitar o incidente por serviço, período e sintomas.
Reduzir o excesso de informação apresentado inicialmente.
Compreender as relações entre os serviços envolvidos.
Inspecionar o subgrafo de observabilidade produzido pelo pipeline.
Visualizar a hipótese gerada pelo LLM juntamente com suas evidências.
Aprofundar a investigação quando a evidência apresentada não for suficiente.
Diferenciar claramente fato/evidência de hipótese gerada.
Comunicar o diagnóstico inicial para desenvolvedores e demais envolvidos.
Manter rastreabilidade suficiente para que a investigação possa ser retomada posteriormente.

As hipóteses H01, H02 e H03 continuam abertas. As personas e a jornada fornecem direcionamento para investigá-las, mas não constituem validação dessas hipóteses.

## Checklist

- [ ] Existe pelo menos uma persona por integrante.
- [ ] As personas não são apenas diferenças demográficas superficiais.
- [ ] Está claro o que é dado real e o que é hipótese/proto-persona.
- [ ] A persona não “validou por ficção” uma hipótese da Entrega 1; afirmações continuam marcadas como hipótese quando não há evidência.
- [ ] Objetivos e dores têm consequência para o design.
- [ ] Contexto de uso está coerente com a Entrega 1.
- [ ] Em TCC sem interface original, a persona possui relação explícita com a contribuição técnica.
- [ ] Papéis administrativos, técnicos e decisórios só foram criados quando possuem objetivos/tarefas diferentes.
- [ ] Jornada possui etapas, dores e oportunidades e não é apenas wireflow.
- [ ] IDs das personas foram adicionados à rastreabilidade.
