# Entrega 3 — Personas, mapa de empatia, contexto de uso e jornada

**Data:** 03/09/2026
**Status:** ✅ concluída
**Responsabilidade:** 1 persona por integrante; 1 mapa de empatia, 1 contexto de uso consolidado e 1 jornada por equipe (salvo orientação diferente do docente).

## Objetivo da atividade

Representar grupos de usuários de forma útil para decisões de design. Persona não é personagem decorativo: suas características devem alterar requisitos, prioridades, linguagem, fluxos ou critérios de avaliação.

## Entradas da Entrega 1

| Item da Entrega 1 | Status inicial | Evidência disponível agora | Como será tratado nesta entrega |
|---|---|---|---|
| H01 (Visualização estrutural relevante) | H | Análise da Dynatrace (C03) mostrou que "caminho visual" é essencial | incorporar na persona do desenvolvedor |
| H03 (Hipóteses com evidência estrutural) | H | Relatos de usuários na Dynatrace | incorporar na necessidade de rastreabilidade |
| Usuário: Desenvolvedor | F | Entregas 1 e 2 | incorporar como persona P01 |
| Usuário: SRE | F | Entregas 1 e 2 | (Sendo feito por outro integrante da equipe) |

## 1. Personas

### Persona P01 — Lucas, o Desenvolvedor Sênior

**Autor(a):** Gabriel Lovato — 22.123.004-8
**Tipo:** secundária (SRE é o foco primário geral, mas o Dev atua na resolução técnica e usa a ferramenta no aprofundamento)
**Base de evidências:** proto-persona a validar / literatura e conhecimentos da equipe (desenvolvedores)
**Hipóteses da Entrega 1 relacionadas:** H01, H03

| Campo | Descrição |
|---|---|
| Faixa etária / contexto relevante | 28 anos. Trabalha em modelo híbrido numa equipe ágil (squad) responsável por 3 microsserviços críticos. |
| Ocupação/papel | Desenvolvedor Backend. |
| Conhecimento do domínio | Alto conhecimento da regra de negócio de seu escopo e dos serviços que mantém, mas visão limitada da infraestrutura global da empresa. |
| Experiência tecnológica | Alta. Trabalha diariamente com IDEs, Git, Docker e lê logs no Kibana/Datadog, porém não possui fluência avançada em topologias complexas de redes e clusters Kubernetes. |
| Objetivos | Resolver bugs reportados com a maior rapidez e precisão possíveis, focando na identificação da causa raiz direto no código. |
| Necessidades | Precisa de rastreabilidade do erro, desde a manifestação no sistema até a linha de código defeituosa, com evidências claras de que o seu serviço originou a falha. |
| Dores/frustrações | Perder tempo cruzando logs fragmentados de diversas origens; ser acionado incorretamente para incidentes que são culpa de integrações de terceiros. |
| Motivadores | Entregar código de alta qualidade, resolver problemas difíceis sem "achismos" e não sofrer com retrabalho. |
| Restrições/acessibilidade | Frequente pressão de tempo, imposta por gestores e SREs quando há falhas críticas em produção (SLAs rígidos). |
| Ambiente típico de uso | Home office ou escritório físico; usa múltiplos monitores, IDE sempre aberta, recebe muitas notificações no Slack/Teams. |
| Comportamentos relevantes | Vai direto para a stack trace (rastreamento do erro). Tende a ignorar métricas genéricas de infraestrutura (CPU, RAM) que não domina. |

**Decisões de design influenciadas por P01:**

- **Drill-down direto:** A interface deve permitir aprofundar do "Grafo de Problemas" diretamente para os detalhes do span anômalo com poucos cliques.
- **Evidências visíveis:** As hipóteses geradas pelo LLM não podem ser apenas textuais; devem apontar e destacar visualmente os componentes/serviços afetados (mitigando a dor de procurar "quem falhou").
- **Facilidade de compartilhamento:** Possibilidade de compartilhar links diretos com o contexto do erro (facilitando a comunicação entre SRE e Desenvolvedor).

### Síntese das personas

A equipe possui a persona do SRE (primária - desenvolvida por outro integrante), focada na triagem, monitoramento geral e contenção imediata, enquanto o **Desenvolvedor (Lucas - secundária)** entra como o perfil técnico resolvedor. A atuação de Lucas depende do acionamento inicial do SRE, portanto, a interface precisa servir como ponte comunicativa, oferecendo tanto abstrações de alto nível para o SRE, quanto dados detalhados (spans, metadados) para Lucas confirmar a falha em seu código.

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
