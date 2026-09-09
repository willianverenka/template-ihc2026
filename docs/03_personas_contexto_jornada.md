# Entrega 3 — Personas, mapa de empatia, contexto de uso e jornada

**Data:** 03/09/2026
**Status:** ✅ concluída
**Responsabilidade:** 1 persona por integrante; 1 mapa de empatia, 1 contexto de uso consolidado e 1 jornada por equipe (salvo orientação diferente do docente).

## Objetivo da atividade

Representar grupos de usuários de forma útil para decisões de design. Persona não é personagem decorativo: suas características devem alterar requisitos, prioridades, linguagem, fluxos ou critérios de avaliação.

## Entradas da Entrega 1

| Item da Entrega 1 | Status inicial | Evidência disponível agora | Como será tratado nesta entrega |
|---|---|---|---|
| H01 (Visualização estrutural relevante) | H | Análise da Dynatrace (C03) mostrou que "caminho visual" é essencial | incorporar na persona do dev e na jornada |
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

**Persona escolhida:** Lucas (Desenvolvedor Sênior)
**Justificativa:** O sucesso do sistema de diagnóstico depende não só da detecção, mas da resolução do problema. A compreensão profunda das frustrações de um desenvolvedor ao investigar logs desestruturados orienta o design para exibir as evidências e o grafo estrutural de forma direcionada, aumentando a assertividade da solução.

- **O que vê:** Painéis com logs espalhados e desordenados, alertas de monitoramento constantes, repasse de chamados no Jira e mensagens de cobrança em canais de comunicação.
- **O que ouve:** "O serviço de checkout caiu, foi o seu deploy?", "O sistema está intermitente, precisamos disso funcionando rápido", "Verifica se é no seu código".
- **O que diz/faz:** Tenta reproduzir o erro localmente ("na minha máquina funciona"), gasta horas minerando traces no Datadog, consulta outros times para investigar se a falha começou em uma dependência antes do seu serviço.
- **O que pensa/sente:** Sente ansiedade pela urgência e frustração por perder tempo precioso navegando às cegas; deseja voltar a programar features novas ao invés de debugar problemas obscuros.
- **Dores [H]:** Ferramentas de observabilidade difíceis de usar, com excesso de informação irrelevante e falta de conexão clara entre logs e causa estrutural.
- **Ganhos [H]:** Reduzir o tempo investigativo (MTTR) indo diretamente para o serviço defeituoso guiado por hipóteses plausíveis fundamentadas em evidências do grafo.

## 3. Contexto de uso — consolidação

| Dimensão | Descrição | Implicação de design |
|---|---|---|
| Usuários | Desenvolvedores backend encarregados da manutenção de serviços (e SREs focados em triagem inicial). | Necessidade de visões que contemplem desde a abstração do serviço anômalo (SRE) até os spans de erro precisos (Dev). |
| Tarefas | Investigar a causa raiz (A01), correlacionar sintomas com o erro e confirmar a responsabilidade. | A tela central deve destacar os nós faltosos no subgrafo filtrado (H02) e oferecer a hipótese diagnóstica do LLM. |
| Equipamentos | Computadores de alta performance, 1 a 2 monitores adicionais. | A interface deve aproveitar o espaço de tela para mapas/grafos estruturais, sem poluição de abas inúteis. |
| Ambiente físico | Modelo híbrido (escritório/casa), sujeito a interrupções recorrentes via chat/e-mail. | O sistema deve reter o estado atual de navegação e filtros, pois o dev alterna o foco entre IDE, código e a ferramenta de diagnóstico. |
| Ambiente social/organizacional | Cobrança por SLAs (Acordos de Nível de Serviço) curtos. Cultura de DevOps onde o próprio dev é cobrado pela disponibilidade. | As hipóteses da IA precisam ser claras e acionáveis, auxiliando a equipe a justificar problemas (ex: "o banco de dados falhou, não o código"). |
| Papéis/permissões/governança | Restrições ao acessar dados sensíveis em produção. | Omissão ou anonimização clara de dados PII (Personal Identifiable Information) em payloads no nível do span. |
| Volume de dados/histórico | Alta frequência de logs, com milhares de eventos irrelevantes gerados por minuto. | O mecanismo de filtragem estrutural de grafos da aplicação é o coração do valor, entregando apenas o ruído pertinente (subgrafo) ao Dev. |

## 4. Jornada do usuário — equipe

**Persona:** Lucas (Desenvolvedor Sênior)
**Objetivo da jornada:** Diagnosticar e iniciar a correção de um erro crítico que impactou seu serviço de backend, partindo do momento em que foi acionado pelo time de SRE.
**Início e fim da jornada:** Do recebimento do link/alerta reportando falha até a descoberta da linha/local de código afetada.

| Etapa | Situação/ação | Objetivo | Pensamento/emoção | Dor | Oportunidade de design | Evidência |
|---|---|---|---|---|---|---|
| 1. Acionamento e Contexto | É marcado no Slack por um SRE com um link apontando para um incidente. | Entender rapidamente o impacto e qual serviço/sintoma está associado a ele. | Preocupação e dúvida: "Será que o erro está no meu serviço ou no banco de dados?" | Comunicação com pouco contexto, forçando o Dev a recomeçar a busca do zero. | Sistema pode gerar um link com a visão filtrada pelo SRE, preservando os mesmos filtros e o grafo analisado. | [H] |
| 2. Análise da Hipótese | Abre o link e se depara com a interface da ferramenta exibindo o diagnóstico (LLM) da anomalia. | Obter um resumo inteligível do que deu errado antes de mergulhar nos dados crus. | Curiosidade e alívio de não precisar varrer logs iniciais manualmente. | Explicações genéricas ou "alucinações" de IA que não dizem de onde vieram os dados. | Exibir a hipótese diagnóstica amarrada visualmente aos nós do subgrafo (H03). | [H] |
| 3. Exploração do Subgrafo | Interage com a visualização estrutural (grafo), clicando no componente defeituoso (em vermelho). | Identificar o exato ponto de quebra da requisição dentro das dependências. | Foco intenso. | Excesso de conexões irrelevantes gerando complexidade cognitiva inútil. | Destacar o caminho anômalo e aplicar "blur" (desfoque) ou ocultar os nós do grafo não pertinentes ao erro (H02). | [H] |
| 4. Detalhamento (Drill-down) | Acessa os spans (telemetria detalhada) vinculados ao nó defeituoso no painel lateral. | Encontrar a stack trace, parâmetros anômalos ou a mensagem exata de erro (`Exception`). | Urgência: "Aqui está o problema, qual foi a exception disparada?". | Encontrar propriedades inúteis ou campos vazios misturados com dados cruciais. | Agrupar metadados anômalos no topo e formatar JSONs/stack traces de maneira amigável para cópia rápida. | [H] |
| 5. Ação Corretiva | Copia a causa técnica da ferramenta para a sua IDE e começa a programar o reparo. | Codificar a solução sabendo exatamente qual trecho consertar. | Confiança em saber onde atacar o problema e sensação de progresso. | Ter que reproduzir todo o ambiente localmente sem ter os parâmetros exatos. | Possibilitar que ele exporte os dados da exceção encontrada. | [F] |

## Síntese

Quais necessidades e objetivos devem obrigatoriamente aparecer nos cenários e nas tarefas seguintes?
- A capacidade de acessar um diagnóstico gerado por IA (LLM) ancorado em evidências visuais no subgrafo.
- A navegação em aprofundamento progressivo ("drill-down"), saindo da visão macro do grafo para o detalhamento de um span/log.
- Um fluxo de compartilhamento de contexto (link ou exportação de evidências) para viabilizar a transição de responsabilidade entre SREs e Desenvolvedores.

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
