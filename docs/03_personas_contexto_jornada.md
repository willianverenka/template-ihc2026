# Entrega 3 — Personas, mapa de empatia, contexto de uso e jornada

**Data:** 03/09/2026
**Status:** 🟨 em andamento
**Responsabilidade:** 1 persona por integrante; 1 mapa de empatia, 1 contexto de uso consolidado e 1 jornada por equipe (salvo orientação diferente do docente).

## Objetivo da atividade

Representar grupos de usuários de forma útil para decisões de design. Persona não é personagem decorativo: suas características devem alterar requisitos, prioridades, linguagem, fluxos ou critérios de avaliação.

## Entradas da Entrega 1

| Item da Entrega 1 | Status inicial | Evidência disponível agora | Como será tratado nesta entrega |
|---|---|---|---|
| H01 (Visualização estrutural relevante) | H | Análise da Dynatrace (C03) mostrou que "caminho visual" é essencial | incorporar na persona do dev e na jornada |
| H03 (Hipóteses com evidência estrutural) | H | Relatos de usuários na Dynatrace | incorporar na necessidade de rastreabilidade |
| Usuário: Desenvolvedor | F | Entregas 1 e 2 | incorporar como persona P02 |
| Usuário: SRE | F — escolha do perfil prioritário | Entrega 1, seção 7.2 | incorporar como proto-persona primária P01, produzida por Théo |
| Usuário: QA / atividade A03 | F — identificação do perfil e da atividade | Entrega 1, seções 2.1 e 3.2 | incorporar como proto-persona P03; validar características e comportamentos |
| H02 (Quantidade inicial de detalhes) | ? | Análises da Entrega 2 sugerem aprofundamento progressivo | manter como lacuna, também relevante para P03 |
| H04 (Colaboração e restrições de acesso) | H | Entrega 1, seção 5.4 | manter como hipótese relacionada ao encaminhamento de evidências para P03 |

## 1. Personas

### Persona P01 — Rafael Mendes

**Autor(a):** Théo Zago Zimmermann — 22.123.035-2

**Tipo:** primária

**Base de evidências:** proto-persona a validar, construída a partir da Entrega 1 e da análise de interfaces profissionais de observabilidade.

**Hipóteses da Entrega 1 relacionadas:** H01, H02, H03

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

- Priorizar informações relevantes para o incidente em vez de apresentar toda a telemetria disponível.
- Permitir delimitação por serviço, período e sintomas.
- Apresentar o subgrafo de forma compreensível.
- Permitir aprofundamento nas evidências.
- Apresentar hipóteses juntamente com as evidências relacionadas.
- Deixar claro o estado do processamento e da análise.
- Evitar excesso de informações simultâneas.

### Persona P02 — Lucas, o Desenvolvedor Sênior

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

**Decisões de design influenciadas por P02:**

- **Drill-down direto:** A interface deve permitir aprofundar do "Grafo de Problemas" diretamente para os detalhes do span anômalo com poucos cliques.
- **Evidências visíveis:** As hipóteses geradas pelo LLM não podem ser apenas textuais; devem apontar e destacar visualmente os componentes/serviços afetados (mitigando a dor de procurar "quem falhou").
- **Facilidade de compartilhamento:** Possibilidade de compartilhar links diretos com o contexto do erro (facilitando a comunicação entre SRE e Desenvolvedor).

### Persona P03 — Mariana, a Analista de QA

**Autor(a):** Willian Verenka Oliveira Silva - 22.124.081-5

**Tipo:** secundária

**Base de evidências:** Entrega 1 e das análises de interfaces profissionais de observabilidade da Entrega 2

**Hipóteses da Entrega 1 relacionadas:** H02, H03, H04

| Campo | Descrição |
|---|---|
| Faixa etária / contexto relevante | Adulta em contexto profissional de tecnologia, 30 anos. [H] Atua em uma equipe responsável por validar correções antes de sua liberação. |
| Ocupação/papel | Analista de Qualidade de Software (QA), responsável por verificar se falhas foram corrigidas e se a mudança não causou regressões. [F] O perfil e a atividade A03 foram identificados na Entrega 1. |
| Conhecimento do domínio | [H] Conhece os fluxos de negócio, os critérios de aceitação e os comportamentos esperados do sistema, mas não domina toda a topologia da infraestrutura distribuída. |
| Experiência tecnológica | [H] Tem alta familiaridade com ferramentas de teste, APIs, esteiras de integração contínua e registros de defeitos; possui experiência intermediária na consulta de logs, traces e mapas de dependências. |
| Objetivos | Confirmar, com evidências, se a correção eliminou o comportamento observado no incidente e identificar possíveis efeitos colaterais antes da liberação. |
| Necessidades | Receber o contexto preservado do incidente, compreender a hipótese diagnóstica e as evidências relacionadas, reproduzir o cenário em ambiente autorizado e registrar um resultado verificável. |
| Dores/frustrações | [H] Receber um chamado sem serviço, período, ambiente ou evidências suficientes; precisar reconstruir a investigação feita por SREs e desenvolvedores; não conseguir distinguir ausência de erro de ausência de telemetria. |
| Motivadores | [H] Evitar reincidências e regressões, dar retorno objetivo à equipe e liberar uma correção com confiança proporcional às evidências disponíveis. |
| Restrições/acessibilidade | [H] Possui acesso limitado à telemetria de produção e trabalha sob prazo de liberação. Resultados podem estar incompletos por diferenças entre produção e homologação, cobertura parcial de instrumentação ou dados sensíveis restritos. |
| Ambiente típico de uso | [H] Computador em ambiente de trabalho híbrido, alternando entre ferramenta de testes, sistema de chamados, comunicação da equipe e plataforma de observabilidade. |
| Comportamentos relevantes | [H] Parte do cenário e dos critérios de aceitação, tenta reproduzir a falha, compara o comportamento observado com o esperado, consulta evidências técnicas quando necessário e comunica se a correção foi confirmada, refutada ou permaneceu inconclusiva. |

**Decisões de design influenciadas por P03:**

- **Contexto preservado no encaminhamento:** o diagnóstico compartilhado deve manter incidente, serviço, ambiente, período, hipótese e evidências examinadas, evitando que a QA reinicie a investigação do zero.
- **Separação entre hipótese e verificação:** a interface deve diferenciar evidência observada, hipótese gerada pelo LLM e conclusão registrada por uma pessoa, sem apresentar a hipótese como correção confirmada.
- **Cobertura e limitações visíveis:** dados ausentes, acesso restrito, instrumentação parcial e janela temporal analisada devem permanecer explícitos para que a ausência de novos erros não seja interpretada automaticamente como sucesso.
- **Aprofundamento progressivo:** a QA deve partir de um resumo compreensível e acessar logs, traces e componentes do subgrafo sob demanda, sem exigir domínio avançado de infraestrutura para entender o incidente.
- **Resultado verificável:** o fluxo deve permitir registrar o resultado da verificação como confirmado, refutado ou inconclusivo e associá-lo às evidências consultadas; essa necessidade ainda deve ser validada com participantes representativos.

### Síntese das personas

A P01 — Rafael Mendes (SRE),  é a persona prioritária porque realiza diretamente a investigação de incidentes que constitui o recorte de IHC. Seu foco está na triagem e no diagnóstico inicial, enquanto o **Desenvolvedor (P02 — Lucas, secundária)** atua na resolução técnica. A atuação de Lucas depende do acionamento inicial do SRE, portanto, a interface precisa servir como ponte comunicativa, oferecendo tanto abstrações de alto nível para o SRE, quanto dados detalhados (spans, metadados) para Lucas confirmar a falha em seu código.

A P03 — Mariana complementa os perfis já produzidos pela equipe sem duplicar suas responsabilidades. O SRE permanece como persona primária e realiza a triagem e o diagnóstico inicial; o desenvolvedor sênior investiga o código e implementa a correção; a analista de QA verifica se o comportamento esperado foi restabelecido e procura regressões antes da liberação.

Por ser secundária, P03 não amplia automaticamente o recorte para um módulo completo de gestão de testes. Sua contribuição principal é orientar a continuidade do contexto entre diagnóstico, correção e verificação, além de impedir que uma hipótese do LLM ou a ausência de telemetria seja confundida com confirmação humana. As características e os comportamentos atribuídos a Mariana permanecem como hipóteses de uma proto-persona e precisam ser investigados com profissionais representativos.

## 2. Mapa de empatia — equipe

**Autor(a):** Gabriel Lovato — 22.123.004-8

**Persona escolhida:** P02 — Lucas (Desenvolvedor Sênior)
**Justificativa:** O sucesso do sistema de diagnóstico depende não só da detecção, mas da resolução do problema. A compreensão profunda das frustrações de um desenvolvedor ao investigar logs desestruturados orienta o design para exibir as evidências e o grafo estrutural de forma direcionada, aumentando a assertividade da solução.

- **O que vê:** Painéis com logs espalhados e desordenados, alertas de monitoramento constantes, repasse de chamados no Jira e mensagens de cobrança em canais de comunicação.
- **O que ouve:** "O serviço de checkout caiu, foi o seu deploy?", "O sistema está intermitente, precisamos disso funcionando rápido", "Verifica se é no seu código".
- **O que diz/faz:** Tenta reproduzir o erro localmente ("na minha máquina funciona"), gasta horas minerando traces no Datadog, consulta outros times para investigar se a falha começou em uma dependência antes do seu serviço.
- **O que pensa/sente:** Sente ansiedade pela urgência e frustração por perder tempo precioso navegando às cegas; deseja voltar a programar features novas ao invés de debugar problemas obscuros.
- **Dores [H]:** Ferramentas de observabilidade difíceis de usar, com excesso de informação irrelevante e falta de conexão clara entre logs e causa estrutural.
- **Ganhos [H]:** Reduzir o tempo investigativo (MTTR) indo diretamente para o serviço defeituoso guiado por hipóteses plausíveis fundamentadas em evidências do grafo.

## 3. Contexto de uso — consolidação

**Autor(a):** Gabriel Lovato — 22.123.004-8

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

**Autor(a):** Gabriel Lovato — 22.123.004-8

**Persona:** P02 — Lucas (Desenvolvedor Sênior)
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