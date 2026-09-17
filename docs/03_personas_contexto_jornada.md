# Entrega 3 — Personas, mapa de empatia, contexto de uso e jornada

**Data:** {{dd/mm/aaaa}}  
**Status:** ⬜ em desenvolvimento
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
| {{usuário/objetivo/característica/H01...}} | F / H / ? | {{...}} | incorporar / manter como hipótese / descartar / investigar |

## 1. Personas

### Persona P04 — Camila Nunes

**Autor(a):** João Vitor Sitta Giopatto 22.123.054-3  

**Tipo:** secundária  

**Base de evidências:** Entrega 1 e das análises de interfaces profissionais de observabilidade da Entrega 2

**Hipóteses da Entrega 1 relacionadas:** H01, H02, H03

![Persona P01](../assets/03_personas/persona_p01.svg)

| Campo | Descrição |
|---|---|
| Faixa etária / contexto relevante | [H] Adulta em contexto profissional de tecnologia. A idade específica não é relevante para o uso da solução. |
| Ocupação/papel | [H] Especialista em Observabilidade / Platform Engineer, responsável por acompanhar a qualidade da telemetria, organizar mecanismos de monitoramento e apoiar equipes na investigação de comportamentos anômalos. |
| Conhecimento do domínio | [H] Possui conhecimento elevado sobre observabilidade, arquitetura distribuída e relações entre serviços, mas seu foco principal está na infraestrutura de observabilidade e não na implementação do código de negócio. |
| Experiência tecnológica | [H] Alta familiaridade com logs, métricas, traces, mapas de dependência, dashboards e ferramentas de monitoramento. |
| Objetivos | [H] Identificar quais evidências de observabilidade são relevantes para um incidente, compreender como os sinais se relacionam entre os serviços e fornecer um contexto técnico organizado para as equipes responsáveis pelo diagnóstico e pela correção. |
| Necessidades | [H] Visualizar relações entre componentes, reduzir o volume inicial de telemetria analisada, acessar as evidências que sustentam uma hipótese e manter o contexto do incidente disponível para aprofundamento. |
| Dores/frustrações | 
[H] Grande volume de telemetria, dificuldade de correlacionar sinais heterogêneos, necessidade de navegar manualmente entre serviços e risco de perder evidências relevantes ao aplicar filtros excessivamente agressivos. |
| Motivadores | [H] Reduzir o tempo gasto na organização das evidências, melhorar a qualidade do contexto entregue às demais equipes e tornar a investigação mais rastreável. |
| Restrições/acessibilidade | [H] Pode ter acesso diferenciado a ambientes e dados de produção, além de lidar com dados sensíveis, limitações de instrumentação e diferentes níveis de granularidade da telemetria. |
| Ambiente típico de uso | [H] Computador de trabalho com plataforma de observabilidade, dashboards, terminal, documentação técnica e canais de comunicação com SREs e desenvolvedores. |
| Comportamentos relevantes | [H] Investiga anomalias a partir de sinais de observabilidade, compara serviços relacionados, verifica a qualidade dos dados disponíveis, procura evidências estruturais e questiona resultados que não estejam suficientemente sustentados pela telemetria. |

**Decisões de design influenciadas por P04:**

- Evidência antes da interpretação: a interface deve permitir acessar os elementos do trace utilizados para construir uma hipótese, evitando que o resultado do LLM apareça como uma conclusão independente dos dados.

Visão estrutural: o subgrafo deve destacar relações entre serviços e spans relevantes, pois a persona trabalha diretamente com a organização da telemetria.

Filtragem reversível: o usuário deve conseguir compreender o que foi removido da visualização e retornar ao contexto original quando necessário.

Aprofundamento progressivo: o fluxo deve começar por uma visão reduzida e permitir consultar logs, traces e componentes específicos sob demanda.

Estado da análise: o processamento do pipeline deve possuir feedback compreensível, permitindo diferenciar dados originais, resultado do filtro estrutural e interpretação posterior.

Limitações visíveis: ausência de telemetria, instrumentação parcial e outras limitações devem permanecer explícitas para evitar conclusões indevidas.

Compartilhamento de contexto: o resultado da investigação deve poder ser comunicado a SREs e desenvolvedores sem perder o serviço, período, evidências e hipótese analisados.

### Síntese das personas

P04 não substitui o SRE nem duplica o papel do desenvolvedor ou da QA. Seu diferencial é a responsabilidade hipotética sobre a telemetria e sua estruturação para investigação. A contribuição do TCC poderia produzir valor para esse perfil ao reduzir o espaço de análise por meio da filtragem estrutural do trace e ao organizar uma etapa posterior de interpretação semântica.

P04 é relevante como persona secundária porque ajuda a avaliar se a apresentação do subgrafo e das evidências é compreensível e tecnicamente rastreável.

## 2. Mapa de empatia — equipe

**Persona escolhida:** {{P01}}  
**Justificativa:** {{por que esse perfil é relevante}}

![Mapa de empatia](../assets/03_personas/mapa_empatia.svg)

Documente também em texto: o que vê; ouve; diz/faz; pensa/sente; dores; ganhos. Diferencie **evidência** de **hipótese**.

## 3. Contexto de uso — consolidação

| Dimensão | Descrição | Implicação de design |
|---|---|---|
| Usuários | {{...}} | {{...}} |
| Tarefas | {{...}} | {{...}} |
| Equipamentos | {{...}} | {{...}} |
| Ambiente físico | {{...}} | {{...}} |
| Ambiente social/organizacional | {{...}} | {{...}} |
| Papéis/permissões/governança | {{...}} | {{...}} |
| Volume de dados/histórico | {{...}} | {{...}} |

## 4. Jornada do usuário — equipe

**Persona:** {{P01}}  
**Objetivo da jornada:** {{...}}  
**Início e fim da jornada:** {{...}}

| Etapa | Situação/ação | Objetivo | Pensamento/emoção | Dor | Oportunidade de design | Evidência |
|---|---|---|---|---|---|---|
| 1 | {{...}} | {{...}} | {{...}} | {{...}} | {{...}} | {{...}} |

> A jornada pode incluir etapas **antes, durante e depois** do uso do produto. Não transforme a jornada em lista de telas.

## Síntese

Quais necessidades e objetivos devem obrigatoriamente aparecer nos cenários e nas tarefas seguintes?

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
