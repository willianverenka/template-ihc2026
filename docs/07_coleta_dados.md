# Entrega 7 — Coleta de dados, necessidades e aspectos éticos

**Data:** 22/10/2026  
**Status:** 🟨 em andamento

## Objetivo da atividade

Planejar dados necessários para compreender usuários e requisitos de IHC, escolher técnicas adequadas e documentar instrumentos de modo que a aplicação possa ser reproduzida por pessoas diferentes.

## Para escopos de IHC derivados de TCC técnico

Quando o usuário e a interface foram propostos pela disciplina, uma prioridade da coleta é investigar se esse **cenário de uso realmente faz sentido**. Não trate o exercício de comercialização da Entrega 1 como validação de mercado.

Perguntas úteis incluem:

- esse perfil realmente realiza a atividade imaginada?
- quais ferramentas usa hoje?
- quais informações consulta?
- quais decisões toma?
- que vocabulário utiliza?
- quais parâmetros compreende e quais deveriam ser abstraídos?
- precisa de dashboard, histórico, filtros, relatórios ou comparação? Por quê?
- quais erros são frequentes e quais são críticos?
- existem papéis/permissões diferentes?
- que resultados do algoritmo/modelo seriam úteis ou difíceis de interpretar?

Quando o acesso ao perfil profissional for difícil, discuta com o docente alternativas metodológicas (especialistas próximos, dados secundários, literatura, participantes proxy) e registre as limitações. **Não esconda a limitação da amostra.**

## Hipóteses e lacunas prioritárias herdadas da Entrega 1

Antes de decidir “que dados coletar”, retome os itens `[H]` e `[?]` da Entrega 1 e o registro de hipóteses em [`../RASTREABILIDADE.md`](../RASTREABILIDADE.md). A coleta deve responder perguntas reais do projeto, e não apenas produzir um formulário porque a técnica foi solicitada.

| ID | Hipótese/lacuna | Evidência atual | Decisão que depende da resposta | Prioridade |
|---|---|---|---|---|
| H01 | [H] A visualização da estrutura de dependências entre serviços e spans será relevante para que o SRE compreenda a propagação da falha. Origem: [Entrega 1, seção 10](01_conhecendo_o_problema.md#10-hipóteses-e-dúvidas-prioritárias). | Indireta. Mapas de dependências e visões de topologia aparecem em Datadog, New Relic e Dynatrace ([Entrega 2](02_analise_concorrencia.md), C01–C03), o que mostra o uso do padrão no domínio, mas não a sua utilidade para o público da equipe. As personas P01, P02 e P04 da [Entrega 3](03_personas_contexto_jornada.md) são proto-personas. Nenhum dado coletado com profissionais. | Se o subgrafo será o elemento central da inspeção (F02) ou um recurso de apoio, e em que nível (serviço ou span) será apresentado. | alta |
| H02 | [?] Ainda não sabemos qual quantidade de detalhes deve ser apresentada inicialmente para equilibrar compreensão e sobrecarga cognitiva. Origem: [Entrega 1, seção 10](01_conhecendo_o_problema.md#10-hipóteses-e-dúvidas-prioritárias). | Indireta. A Entrega 2 identifica aprofundamento progressivo nos concorrentes e propõe RC02 (apresentar inicialmente o subgrafo e permitir expansão). Não há dado sobre o que os profissionais precisam ver primeiro. | O que compõe a primeira visão do incidente e o que fica disponível sob demanda (F02 e F03); como tornar a filtragem compreensível e reversível. | alta |
| H03 | [H] As hipóteses geradas pelo LLM serão mais úteis ao SRE quando apresentadas acompanhadas das evidências estruturais que as sustentam, em vez de apenas como conclusão textual. Origem: [Entrega 1, seção 10](01_conhecendo_o_problema.md#10-hipóteses-e-dúvidas-prioritárias). | Indireta. A Entrega 2 descreve recursos de concorrentes que ligam a causa indicada às entidades afetadas (C03) e propõe RC03. A presença do padrão nos produtos não mostra como o público decide confiar em uma explicação. | Como a hipótese é apresentada e vinculada às evidências (F03); quais informações permitem aceitar, questionar ou rejeitar a hipótese. | alta |
| H04 | [H] A investigação ocorre sob pressão de tempo e pode envolver colaboração entre SRE, desenvolvedores e gestores; políticas de acesso, responsabilidade sobre os serviços e dados sensíveis na telemetria podem limitar quem consulta, compartilha ou registra evidências. Origem: [Entrega 1, seção 5.4](01_conhecendo_o_problema.md#54-existem-fatores-sociais-ou-organizacionais). | Parcial. A Entrega 1, seção 5.5, registra que logs podem revelar dados sensíveis de usuários e que o acesso deve ser restrito. Colaboração, repasse de contexto e efeito das restrições ainda não foram investigados. | Conteúdo e forma de comunicação do diagnóstico inicial; necessidade de papéis/permissões e de ocultação de dados sensíveis, marcadas como “talvez” na seção 8 da Entrega 1. | média |

## Parte A — necessidades e requisitos de IHC

> **Responsabilidade:** solução individual por integrante.

### A01 — Willian Verenka Oliveira Silva

**Autor(a):** Willian Verenka Oliveira Silva — 22.124.081-5

Esta solução prioriza dados que precisam ser obtidos de um número maior de profissionais e de papéis diferentes: se a atividade e o usuário adotados são plausíveis, como a investigação ocorre hoje e com que frequência as dificuldades supostas nas Entregas 1 e 3 aparecem. O instrumento correspondente é o questionário [I01](#instrumento-i01--questionário).

#### Que dados coletar?

| Dado/informação | Hipótese/lacuna relacionada | Por que é necessário | Qual decisão de design pode afetar |
|---|---|---|---|
| Etapas da investigação em que cada papel atua e quem formula o primeiro parecer sobre a origem provável da falha | Plausibilidade do recorte: Entrega 1, seções 3.1, 3.3 e 7.2 | O SRE foi escolhido como usuário prioritário por decisão da equipe. Não há dado de outras organizações mostrando que esse perfil formula o diagnóstico inicial. | Manutenção de P01 como persona primária ou revisão do usuário principal e do peso das personas secundárias. |
| Frequência de participação em investigações e existência de escala de plantão | Plausibilidade do recorte; H04 (pressão de tempo) | Uma atividade rara ou concentrada em poucos papéis altera o equilíbrio entre facilidade de aprendizado e eficiência. | Metas de usabilidade da Entrega 8. |
| O que dá início à investigação (alerta, implantação, reclamação, chamado) | Contexto de uso: Entrega 1, seção 5.1 | Define de onde o usuário parte e que informação já possui ao iniciar. | Dados mínimos para delimitar o incidente (F01). |
| Ferramentas, informações consultadas e primeira informação examinada | H01, H02; Entrega 1, seções 4.1 e 6.3 | Revela padrões e vocabulário que o público já conhece e a ordem real de consulta. | Ordem de apresentação das informações e convenções a reaproveitar. |
| Tempo estimado até o diagnóstico inicial | [H] Entrega 1, seção 4.2: localizar evidências é demorado | Fornece uma referência aproximada para a redução de esforço esperada. | Metas e critérios de avaliação (Entregas 8 e 12). |
| Frequência de dificuldades específicas: volume de registros, correlação entre serviços, distinção entre origem e efeito, descoberta de dependências, dados ausentes, falta de acesso, repasse incompleto e retrabalho | H01, H02, H04; Entrega 1, seção 4.2 | Indica quais rupturas são comuns e para quais papéis, sem pressupor que todas existam. | Priorização entre F01, F02 e F03 e dos problemas tratados no protótipo. |
| Forma de examinar dependências entre serviços e ponto de partida preferido para a investigação | H01, H02 | Verifica se a estrutura é usada na prática e se a investigação começa por informação reduzida ou completa. | Destaque do subgrafo e composição da primeira visão. |
| Uso prévio de sugestões automáticas de causa, o que é conferido antes de aceitá-las e o que seria necessário para confiar em uma | H03 | Mostra como a confiança em resultados automáticos é construída hoje. | Vínculo entre hipótese e evidências; apresentação de incerteza. |
| Consequências já presenciadas de diagnósticos iniciais incorretos | Entrega 1, seções 4.4 e 5.6 | Identifica quais erros são críticos e devem ser prevenidos. | Prevenção de erros e comunicação dos limites da hipótese. |
| Destinatários, meios e conteúdo mínimo do repasse de uma investigação | H04; necessidade de contexto preservado de P03 | A Entrega 3 supõe que o contexto se perde entre diagnóstico, correção e verificação. | Conteúdo e formato da comunicação do diagnóstico inicial. |
| Restrições de acesso a dados de produção e sua interferência na investigação | H04; Entrega 1, seção 5.5 | Determina se papéis diferentes têm acesso a dados diferentes. | Necessidade de papéis/permissões e de mascaramento de dados. |
| Consulta a investigações anteriores e comparação com outros períodos | Entrega 1, seção 8: histórico e comparação marcados como “não” | A exclusão foi decidida sem evidência; os dados verificam se ela se mantém. | Inclusão ou exclusão de histórico e comparação no recorte. |
| Nome dado pela equipe ao primeiro parecer sobre a origem provável | Vocabulário do domínio | Evita impor à interface um termo criado pela equipe. | Signos e rótulos (Entregas 9 e 11). |

#### De quem coletar?

| Perfil/stakeholder | Critério de inclusão | Relação com persona/público |
|---|---|---|
| SRE | Atua como SRE e participou da investigação de pelo menos um incidente em sistema composto por vários serviços nos últimos 12 meses. | Usuário prioritário; P01. |
| DevOps, engenharia de plataforma ou observabilidade | Mesmo critério de participação; responsável por infraestrutura, monitoramento ou telemetria. | P04; também representa organizações que não possuem o cargo de SRE. |
| Desenvolvedor(a) | Mantém serviços em produção e participou da investigação ou da correção de um incidente nos últimos 12 meses. | P02. |
| Analista de QA | Verificou a correção de falha ocorrida em produção nos últimos 12 meses. | P03. |
| Gestor(a) de equipe técnica | Recebeu ou utilizou diagnósticos de incidentes para priorizar correções nos últimos 12 meses. | Stakeholder da Entrega 1, seção 2.2, sem persona; respostas analisadas separadamente. |

Ficam excluídos os integrantes da equipe e quem não participou de investigações no período, filtrados pela pergunta Q1. [H] O recrutamento será por conveniência, na rede profissional dos integrantes — dois atuam como desenvolvedores (Entrega 1, seção 1.2) — e em comunidades on-line de observabilidade. Por isso, é provável que desenvolvedores e poucas organizações predominem na amostra. Se responderem menos de cinco SREs, os resultados sobre esse perfil serão tratados como indícios, e o uso de DevOps e profissionais de plataforma com plantão como participantes proxy será discutido com o docente e registrado como limitação. Os resultados descrevem a amostra obtida, não a população de profissionais.

#### Aspectos éticos

- **Dados e riscos deste projeto:** o questionário trata de incidentes de trabalho. O principal risco não está nos dados pessoais pedidos, que são mínimos, mas no que o respondente pode relatar nas perguntas abertas: nomes de sistemas, arquitetura interna, clientes ou falhas não divulgadas do empregador; trechos de logs com dados pessoais de usuários finais ou credenciais, possibilidade já registrada na Entrega 1, seção 5.5; relatos de erros de diagnóstico que exponham o respondente ou colegas.
- **Voluntariedade:** parte dos contatos são colegas de trabalho dos integrantes. Para reduzir a pressão para participar, o convite é enviado por canais coletivos, sem cobrança individual nem lembretes personalizados, e não há incentivo. Apenas o consentimento, a triagem e o papel profissional são obrigatórios; as demais perguntas podem ficar em branco.
- **Consentimento:** a primeira página informa objetivo, duração, uso dos dados, ausência de identificação e prazo de descarte. O questionário só prossegue após o aceite. O texto também informa o limite do direito de desistir: antes do envio, basta fechar a página; depois dele, como as respostas não são identificadas, não é possível localizar e excluir uma resposta específica.
- **Minimização:** não são coletados nome, e-mail, empresa, cargo exato, idade, gênero ou localização. A coleta automática de e-mail fica desativada na ferramenta. Experiência e tamanho do sistema são perguntados em faixas. Cada pergunta corresponde a um dado da tabela acima.
- **Privacidade e anonimização:** as perguntas abertas pedem que não sejam incluídos nomes de pessoas, empresas, clientes ou sistemas, nem trechos de logs. Antes da análise, um integrante revisa as respostas abertas e substitui o que permitir identificação por marcadores como `[EMPRESA]` e `[SERVIÇO]`. Trechos de logs ou dados de terceiros que tenham sido incluídos são excluídos, sem cópia. Os respondentes são identificados como R01, R02 etc. Combinações de papel, experiência e tamanho do sistema com menos de três respondentes não são publicadas separadamente, para evitar reidentificação em comunidades pequenas.
- **Gravação:** não há gravação de áudio, vídeo ou tela.
- **Contato posterior:** quem aceitar participar das demais técnicas preenche um formulário separado, sem ligação com as respostas. Esses contatos são usados apenas para o recrutamento e excluídos após o fim das coletas.
- **Armazenamento:** as respostas brutas ficam na conta da ferramenta de formulários e em uma pasta compartilhada restrita aos integrantes. O repositório GitHub recebe somente dados agregados e trechos anonimizados.
- **Descarte:** a planilha bruta e o formulário são excluídos ao final da disciplina, após a Entrega 14.
- **LGPD aplicada ao caso:** mesmo sem nome, uma combinação de papel, experiência e relato pode identificar uma pessoa. Por isso, as respostas são tratadas como dados pessoais, com finalidade restrita a esta disciplina e coleta limitada ao necessário.

### A02 — Gabriel Lovato

**Autor(a):** Gabriel Lovato — 22.123.004-8

Esta solução prioriza dados que exigem aprofundamento e que um questionário capta mal: o raciocínio de desenvolvedores e SREs ao reconstruir um incidente recente, os critérios que usam para considerar uma explicação suficiente e o que é recebido e repassado entre esses papéis. O instrumento correspondente é a entrevista semiestruturada I02.

#### Que dados coletar?

| Dado/informação | Hipótese/lacuna relacionada | Por que é necessário | Qual decisão de design pode afetar |
|---|---|---|---|
| Sequência de ações em um incidente recente, do acionamento até a primeira explicação sobre a origem: fontes consultadas, ordem e mudanças de direção | H02; Entrega 1, seções 4.1 e 4.5 | O processo atual foi descrito pela equipe com base na própria experiência; falta o encadeamento real das ações relatado por outros profissionais. | Ordem de apresentação e caminho de aprofundamento entre F02 e F03; revisão das tarefas da Entrega 5. |
| Critérios usados para considerar uma explicação suficiente para agir ou comunicar | H03; Entrega 1, seção 7.3 | O objetivo priorizado é um diagnóstico “fundamentado”, mas não sabemos o que os profissionais consideram fundamentação suficiente. | Conteúdo mínimo de uma hipótese e das evidências associadas. |
| Informações que levam o profissional a rejeitar ou mudar uma explicação | H03 | Indica se contra-evidências e limites precisam aparecer junto da hipótese. | Apresentação de evidências contrárias e de incerteza. |
| Forma de avaliar sugestões prontas sobre a causa, vindas de ferramentas ou de colegas | H03 | A confiança em um resultado automático pode depender de fatores diferentes da confiança em um colega. | Identificação da origem da hipótese (gerada pelo modelo ou registrada por pessoa) e ações de verificação. |
| Situações em que foi preciso distinguir a origem da falha de seus efeitos e como isso foi resolvido | H01 | Mostra quando e como a estrutura de dependências é usada para decidir. | Destaque do caminho de propagação no subgrafo. |
| Informações recebidas no acionamento pelo SRE e o que precisou ser refeito | H04; jornada de P02, etapa 1 (Entrega 3) | A jornada supõe que uma comunicação com pouco contexto obriga o desenvolvedor a recomeçar a busca. | Conteúdo do diagnóstico compartilhado entre SRE e desenvolvedor. |
| Nível de detalhe necessário para chegar ao ponto do código (stack trace, parâmetros, mensagem de erro) | H02; decisões de design de P02 | Define até onde o aprofundamento precisa chegar para o desenvolvedor. | Profundidade do aprofundamento a partir de um componente do subgrafo. |
| Dados que o profissional não pôde acessar ou compartilhar durante o incidente | H04; Entrega 1, seção 5.5 | Revela se restrições de acesso alteram a investigação. | Permissões e ocultação de dados sensíveis. |
| Termos usados para a explicação provisória sobre a origem e para os serviços afetados | Vocabulário do domínio | Evita rótulos que o público não usa. | Signos e rótulos (Entregas 9 e 11). |

#### De quem coletar?

| Perfil/stakeholder | Critério de inclusão | Relação com persona/público |
|---|---|---|
| Desenvolvedor(a) backend | Mantém pelo menos um serviço em produção e participou da investigação ou da correção de um incidente nos últimos 6 meses. | P02. |
| SRE | Atuou na triagem ou no diagnóstico de um incidente nos últimos 6 meses. | P01; contraponto do repasse entre SRE e desenvolvedor. |
| DevOps ou engenharia de plataforma | Mesmo critério do SRE, em organizações que não possuem esse cargo. | Participante proxy de P01, registrado como tal. |

A meta é realizar de 4 a 6 entrevistas, com pelo menos dois desenvolvedores e dois SREs ou proxies. A janela de 6 meses é menor que a do questionário porque a entrevista depende da memória de um incidente específico. Ficam excluídos os integrantes da equipe e pessoas que trabalham na mesma equipe do entrevistador; se não houver alternativa, outro integrante conduz a entrevista. O recrutamento usa o formulário de interesse do questionário I01 e a rede profissional dos integrantes. [H] A amostra será pequena e por conveniência, e os relatos estão sujeitos a viés de memória e à tendência de descrever o processo ideal em vez do real; perguntar sobre um incidente concreto reduz, mas não elimina, esse viés. Essas limitações serão registradas com os resultados.

#### Aspectos éticos

- **Dados e riscos deste projeto:** a entrevista pede o relato detalhado de um incidente real. Isso pode revelar informações confidenciais do empregador — arquitetura, clientes, falhas não divulgadas — e expor erros do participante ou de colegas. A voz gravada também é um dado pessoal identificável.
- **Voluntariedade:** o entrevistador não entrevista colegas da própria equipe de trabalho. O participante pode deixar de responder qualquer pergunta ou interromper a entrevista sem justificativa e sem consequência. Não há incentivo.
- **Consentimento:** o termo, adaptado de `instrumentos/termo_consentimento_modelo.md`, é enviado com antecedência e confirmado verbalmente no início. A gravação de áudio tem consentimento separado; se recusada, a entrevista ocorre apenas com anotações.
- **Minimização:** registram-se apenas papel, faixa de experiência e tipo de sistema. Não se registram nome, empresa ou cargo exato. O participante é orientado a descrever os serviços de forma genérica (por exemplo, “o serviço de pagamento”) e a não compartilhar tela nem trechos de logs.
- **Gravação:** somente áudio, sem vídeo. O arquivo é baixado para a pasta restrita da equipe no mesmo dia e removido da nuvem da ferramenta de videochamada.
- **Anonimização:** a transcrição é feita em até 7 dias, com ID E01, E02 etc. Nomes de pessoas, empresas, clientes e sistemas são substituídos por marcadores, e detalhes que permitam identificar o incidente (datas, valores específicos) são removidos quando não forem necessários à análise.
- **Desconforto:** falar de incidentes com consequências pode gerar desconforto ou sensação de julgamento. A abertura deixa claro que o estudo trata da atividade, não do desempenho de pessoas, e o participante pode escolher um incidente menos sensível.
- **Armazenamento:** áudios, transcrições e fichas ficam na pasta restrita aos integrantes. O repositório GitHub recebe apenas resumos codificados e trechos anonimizados.
- **Descarte:** o áudio é excluído após a conferência da transcrição. Transcrições e fichas são excluídas ao final da disciplina, e os contatos usados no agendamento, após o fim das coletas.

### A03 — Théo Zago Zimmermann

**Autor(a):** Théo Zago Zimmermann — 22.123.035-2

Esta solução prioriza o comportamento efetivo do SRE durante uma investigação, que não depende do que o profissional lembra ou acredita fazer: a ordem em que consulta as fontes, quando recorre às relações entre serviços, quanto examina antes de restringir a análise e como distingue a origem da falha de seus efeitos. O instrumento correspondente é a observação I03.

#### Que dados coletar?

| Dado/informação | Hipótese/lacuna relacionada | Por que é necessário | Qual decisão de design pode afetar |
|---|---|---|---|
| Ordem em que fontes e ferramentas são consultadas | H02; Entrega 1, seção 4.1 | Relatos tendem a descrever o processo ideal; a ordem observada mostra o caminho efetivo. | Organização da primeira visão e do caminho de aprofundamento (F01–F03). |
| Momento e forma de uso das relações entre serviços (mapa de serviços, visualização do trace) | H01 | Mostra se a estrutura é usada para decidir ou apenas consultada. | Centralidade do subgrafo na inspeção (F02). |
| Volume examinado antes de restringir a análise: serviços, consultas e filtros até a primeira hipótese | H02 | Indica quanto da telemetria o profissional examina antes de delimitar o incidente. | Grau de redução inicial e reversibilidade da filtragem. |
| Hesitações, retornos a fontes já consultadas e mudanças de hipótese | [H] Entrega 1, seção 4.2 | Localiza as rupturas da atividade. | Problemas prioritários para o protótipo e prevenção de erros. |
| Sinais usados para distinguir a origem da falha de seus efeitos (ordem temporal, concentração de erros, dependências) | H01, H03 | Indica quais evidências sustentam a decisão sobre a origem. | Evidências a associar a cada hipótese (F03). |
| Tempo até a primeira hipótese verbalizada e até o diagnóstico comunicado | [H] Entrega 1, seção 4.2 | Referência para metas de eficiência, com a ressalva do ambiente controlado. | Metas da Entrega 8 e critérios da Entrega 12. |
| Conteúdo do diagnóstico comunicado ao final da tarefa | H04; Entrega 1, seção 7.3 | Mostra o que o SRE considera necessário comunicar. | Estrutura da comunicação do diagnóstico inicial. |
| Semelhança percebida entre a situação simulada e o trabalho real | Validade da técnica | Necessária para interpretar os resultados obtidos em ambiente controlado. | Peso dado aos achados na síntese da entrega. |

#### De quem coletar?

| Perfil/stakeholder | Critério de inclusão | Relação com persona/público |
|---|---|---|
| SRE | Tem pelo menos 1 ano de experiência com sistemas compostos por vários serviços, investigou incidentes nos últimos 12 meses e já usou ferramentas de traces e de métricas. | P01 — usuário prioritário. |
| DevOps ou engenharia de plataforma com plantão | Mesmos critérios, em organizações que não possuem o cargo de SRE. | Participante proxy de P01, registrado como tal; relacionado a P04. |

A meta é realizar de 3 a 5 sessões. Ficam excluídos os integrantes da equipe, o participante do piloto e pessoas que trabalham na mesma equipe do moderador. [H] A observação ocorre em um ambiente controlado, com dados sintéticos e ferramentas que podem ser diferentes das usadas pelo participante no trabalho. Por isso, a familiaridade prévia com as ferramentas é registrada e a semelhança com o trabalho real é perguntada ao final. A presença do observador também pode alterar o comportamento. Essas limitações e o eventual uso de proxies serão registrados com os resultados.

#### Aspectos éticos

- **Dados e riscos deste projeto:** observar uma investigação real exporia dados de produção, que podem conter dados pessoais de usuários finais (Entrega 1, seção 5.5) e informações confidenciais do empregador. Por isso, a observação usa apenas um ambiente de demonstração com dados sintéticos, operado em máquina da equipe, sem acesso a contas ou sistemas do participante. O risco restante é o participante se sentir avaliado, por exemplo, por não identificar a origem da falha simulada.
- **Voluntariedade:** o participante pode interromper a sessão a qualquer momento, sem justificativa e sem consequência. O moderador não observa colegas da própria equipe de trabalho. Não há incentivo.
- **Consentimento:** o termo, adaptado de `instrumentos/termo_consentimento_modelo.md`, informa a tarefa, a duração e as opções de registro. Gravação de tela e gravação de áudio têm consentimentos separados; se forem recusadas, a sessão é registrada apenas pela ficha do observador.
- **Minimização:** registram-se apenas papel, faixa de experiência e familiaridade com as ferramentas do ambiente. A gravação de tela se limita à janela do ambiente de demonstração; antes de iniciar, o participante é orientado a desativar notificações. A câmera não é usada.
- **Gravação:** tela e áudio do pensar em voz alta, quando autorizados. Não há dados de produção na tela, mas a voz é dado pessoal identificável.
- **Anonimização:** participantes identificados como O01, O02 etc. Comentários sobre práticas do empregador feitos durante a sessão são anonimizados na transcrição. Se o participante identificou ou não a origem simulada é informado apenas de forma agregada, para descrever a dificuldade da tarefa, nunca como avaliação individual.
- **Desconforto:** pensar em voz alta sob observação e com limite de tempo pode gerar tensão. A abertura reforça que se estuda a atividade, a tarefa tem limite de 25 minutos e pode ser encerrada pelo participante.
- **Armazenamento:** gravações e fichas ficam na pasta restrita aos integrantes. O repositório GitHub recebe apenas fichas consolidadas, linhas do tempo anonimizadas e resultados agregados.
- **Descarte:** gravações são excluídas após a codificação das sessões. Fichas e transcrições são excluídas ao final da disciplina, e os contatos usados no agendamento, após o fim das coletas.

## Parte B — ferramentas de coleta

> Cada integrante deve preparar uma técnica/instrumento completo. As técnicas devem ser diferentes entre si e **questionário deve estar entre as técnicas escolhidas**, conforme o enunciado da disciplina.

### Instrumento I01 — Questionário

**Autor(a):** Willian Verenka Oliveira Silva — 22.124.081-5  
**Técnica:** questionário  
**Objetivo:** verificar, entre profissionais de diferentes papéis, se a investigação de incidentes e a formulação de um diagnóstico inicial pelo SRE correspondem à prática atual; caracterizar ferramentas, informações consultadas, dificuldades, critérios de confiança em sugestões automáticas e repasse de contexto; e recrutar participantes para as demais técnicas. Os dados investigam a plausibilidade do recorte e H01–H04.  
**Público:** SREs, DevOps, profissionais de plataforma ou observabilidade, desenvolvedores, analistas de QA e gestores de equipes técnicas que participaram da investigação de incidentes em sistemas compostos por vários serviços nos últimos 12 meses, conforme os critérios da [Parte A — A01](#de-quem-coletar).

#### Procedimento padronizado de aplicação

1. **Preparação:** criar o formulário on-line a partir da cópia textual abaixo, sem alterar a redação. Configurar: coleta de e-mail desativada; sem exigência de login; uma página para cada bloco indicado abaixo; ordem aleatória das linhas em Q16 e das opções de Q20, quando a ferramenta permitir. Aplicar um piloto com dois profissionais que não farão parte da amostra para verificar compreensão e tempo de resposta. Aplicar a esta cópia textual qualquer ajuste feito após o piloto, descrevendo-o na mensagem de commit, e descartar as respostas do piloto.
2. **Apresentação/consentimento:** divulgar sempre o mesmo convite: “Estamos estudando como profissionais investigam incidentes em sistemas com vários serviços, para uma disciplina de Interação Humano-Computador da FEI. Se você participou de alguma investigação nos últimos 12 meses, pode responder a um questionário anônimo de 10 a 15 minutos: [link]”. O convite é publicado em comunidades on-line de observabilidade e grupos profissionais dos integrantes, sem envio individual. A página inicial do formulário apresenta o termo e exige o aceite (C1).
3. **Aplicação:** manter o formulário aberto por 14 dias, com um único lembrete coletivo no oitavo dia. Os integrantes não respondem dúvidas individuais sobre o conteúdo das perguntas, para não interferir nas respostas; dúvidas sobre a pesquisa são respondidas pelo contato informado no termo e registradas.
4. **Encerramento:** a página final agradece e oferece o link do formulário separado de interesse em participar das técnicas I02–I04. Ao fim do prazo, o formulário é fechado e a quantidade de respostas por papel é registrada.
5. **Armazenamento/anonimização:** exportar as respostas para uma planilha na pasta restrita da equipe; excluir respostas sem consentimento ou com “Não” em Q1; revisar e anonimizar as respostas abertas antes da análise; atribuir IDs R01, R02...; publicar no repositório apenas tabelas agregadas e trechos anonimizados; excluir a planilha bruta e o formulário ao final da disciplina.

#### Instrumento

**Link do formulário:** PENDENTE — será criado a partir desta cópia textual, que é a versão de referência do instrumento.

**Legenda:** ○ escolha única; ☐ múltipla escolha. Perguntas sem a indicação “obrigatória” podem ficar em branco.

---

**Página 1 — Apresentação e consentimento**

> **Investigação de incidentes em sistemas com vários serviços**
>
> Este questionário faz parte de um trabalho da disciplina de Interação Humano-Computador da FEI. Queremos entender como profissionais investigam incidentes — falhas, indisponibilidades ou degradação de desempenho — em sistemas compostos por vários serviços que se comunicam entre si. **Estamos estudando a atividade e as ferramentas, não avaliando o seu desempenho.**
>
> - Duração estimada: 10 a 15 minutos.
> - Não pedimos nome, e-mail nem empresa. Nas respostas abertas, **não inclua** nomes de pessoas, empresas, clientes ou sistemas, nem trechos de logs ou outros dados de produção.
> - Somente as perguntas marcadas como obrigatórias precisam ser respondidas.
> - A participação é voluntária. Você pode desistir a qualquer momento antes do envio, fechando esta página, e nada será registrado. Como as respostas não são identificadas, depois do envio não conseguiremos localizar e excluir uma resposta específica.
> - As respostas serão usadas apenas nesta disciplina, analisadas pela equipe e divulgadas somente de forma agregada ou em trechos anonimizados. Os dados brutos serão excluídos ao final do semestre letivo.
> - Responsáveis: Willian Verenka Oliveira Silva, Gabriel Lovato, Théo Zago Zimmermann e João Vitor Sitta Giopatto (Equipe 11). Contato: PENDENTE — e-mail institucional de um integrante, a definir antes do piloto.

**C1.** Você leu as informações acima e concorda em participar? *(obrigatória)*

- ○ Sim, concordo em participar
- ○ Não concordo → *encerra o questionário*

---

**Página 2 — Participação em investigações**

**Q1.** Nos últimos 12 meses, você participou da investigação de pelo menos um incidente (falha, indisponibilidade ou degradação de desempenho) em um sistema composto por vários serviços que se comunicam entre si? *(obrigatória)*

- ○ Sim
- ○ Não → *encerra com a mensagem: “Obrigado pelo interesse! Este questionário é destinado a quem participou de investigações de incidentes nos últimos 12 meses.”*

---

**Página 3 — Perfil profissional**

**Q2.** Qual é o seu papel principal no trabalho atualmente? *(obrigatória)*

- ○ SRE (Site Reliability Engineer)
- ○ DevOps ou engenharia de plataforma
- ○ Especialista em observabilidade ou monitoramento
- ○ Desenvolvimento de software — backend
- ○ Desenvolvimento de software — outro (frontend, mobile, full stack)
- ○ Qualidade de software (QA)
- ○ Gestão de equipe técnica
- ○ Outro: ________

**Q3.** Há quanto tempo você trabalha com sistemas compostos por vários serviços?

- ○ Menos de 1 ano
- ○ 1 a 2 anos
- ○ 3 a 5 anos
- ○ 6 anos ou mais

**Q4.** Você participa de escala de plantão (*on-call*) para responder a incidentes?

- ○ Sim, regularmente
- ○ Sim, ocasionalmente
- ○ Não, mas minha equipe tem escala de plantão
- ○ Não; minha equipe não tem escala de plantão

**Q5.** Aproximadamente quantos serviços compõem o sistema em que você mais investiga incidentes?

- ○ Até 10
- ○ 11 a 50
- ○ 51 a 200
- ○ Mais de 200
- ○ Não sei estimar

---

**Página 4 — Como a investigação acontece hoje**

**Q6.** Nos últimos 3 meses, com que frequência você participou de investigações de incidentes?

- ○ Nenhuma vez
- ○ Menos de uma vez por mês
- ○ Uma a três vezes por mês
- ○ Cerca de uma vez por semana
- ○ Várias vezes por semana

**Q7.** O que costuma dar início às investigações de que você participa?

- ☐ Alerta automático de monitoramento
- ☐ Problema percebido após uma implantação (*deploy*) ou mudança
- ☐ Reclamação de usuários ou clientes
- ☐ Chamado ou pedido de outra equipe
- ☐ Algo que eu mesmo(a) percebi ao acompanhar o sistema
- ☐ Outro: ________

**Q8.** Em quais etapas de uma investigação você costuma atuar?

- ☐ Receber o alerta e fazer a triagem inicial
- ☐ Investigar onde a falha começou
- ☐ Comunicar a situação a outras pessoas ou equipes
- ☐ Aplicar medidas de contenção (por exemplo, reverter versão, reiniciar ou redirecionar tráfego)
- ☐ Corrigir o problema no código ou na configuração
- ☐ Verificar se a correção resolveu o problema
- ☐ Acompanhar ou priorizar o trabalho da equipe
- ☐ Outra: ________

**Q9.** Nas investigações de que você participa, quem costuma formular o primeiro parecer sobre onde a falha provavelmente começou?

- ☐ SRE
- ☐ DevOps ou engenharia de plataforma
- ☐ Especialista em observabilidade ou monitoramento
- ☐ Desenvolvedor(a) responsável pelo serviço afetado
- ☐ Gestor(a) da equipe
- ☐ Não há papel definido; depende do incidente
- ☐ Outro: ________

**Q10.** Como você ou sua equipe chamam esse primeiro parecer, dado antes de a causa ser confirmada? *(resposta curta)*

________

**Q11.** Quais ferramentas você utiliza para investigar incidentes? *(produtos listados em ordem alfabética)*

- ☐ AWS CloudWatch ou X-Ray
- ☐ Azure Monitor ou Application Insights
- ☐ Datadog
- ☐ Dynatrace
- ☐ Elastic/Kibana ou OpenSearch
- ☐ Google Cloud Observability
- ☐ Grafana (incluindo Loki, Tempo ou Mimir)
- ☐ Jaeger ou Zipkin
- ☐ New Relic
- ☐ Prometheus
- ☐ Splunk
- ☐ Consultas por linha de comando ou scripts próprios
- ☐ Outra: ________

**Q12.** Quais informações você costuma consultar durante uma investigação?

- ☐ Logs (registros de eventos)
- ☐ Métricas (por exemplo, latência, taxa de erros, uso de recursos)
- ☐ Traces (rastros de requisições entre serviços)
- ☐ Mapa ou diagrama de dependências entre serviços
- ☐ Histórico de implantações e mudanças
- ☐ Alertas e seu histórico
- ☐ Chamados ou registros de incidentes
- ☐ Código-fonte
- ☐ Documentação, *runbooks* ou procedimentos
- ☐ Conversas com outras pessoas
- ☐ Outra: ________

**Q13.** Qual dessas informações você costuma consultar primeiro?

- ○ Logs
- ○ Métricas
- ○ Traces
- ○ Mapa ou diagrama de dependências
- ○ Histórico de implantações e mudanças
- ○ Alertas e seu histórico
- ○ Chamados ou registros de incidentes
- ○ Código-fonte
- ○ Documentação, *runbooks* ou procedimentos
- ○ Conversas com outras pessoas
- ○ Depende do incidente
- ○ Outra: ________

**Q14.** Neste questionário, “diagnóstico inicial” é uma explicação provisória sobre onde a falha provavelmente começou e o que ela afeta, suficiente para decidir a próxima ação. Em uma investigação típica de que você participa, quanto tempo passa entre o início da investigação e esse diagnóstico inicial?

- ○ Menos de 15 minutos
- ○ De 15 a 30 minutos
- ○ Mais de 30 minutos até 1 hora
- ○ Mais de 1 hora até 4 horas
- ○ Mais de 4 horas
- ○ Varia demais para estimar
- ○ Não sei

---

**Página 5 — Dificuldades**

**Q15.** Pense na última investigação de incidente de que você participou. O que mais dificultou ou mais facilitou chegar a um diagnóstico inicial? Não inclua nomes de pessoas, empresas, clientes ou sistemas, nem trechos de logs. *(resposta longa)*

________

**Q16.** Com que frequência as situações abaixo ocorrem nas investigações de que você participa? *(uma resposta por linha)*

| Situação | Nunca | Raramente | Às vezes | Frequentemente | Sempre | Não se aplica |
|---|:---:|:---:|:---:|:---:|:---:|:---:|
| a. Precisar examinar um grande volume de registros até encontrar os relacionados ao incidente | ○ | ○ | ○ | ○ | ○ | ○ |
| b. Precisar relacionar manualmente registros de serviços diferentes que pertencem à mesma requisição ou ocorrência | ○ | ○ | ○ | ○ | ○ | ○ |
| c. Ter dúvida se um serviço com erros é a origem da falha ou se apenas foi afetado por outro serviço | ○ | ○ | ○ | ○ | ○ | ○ |
| d. Precisar descobrir, durante o incidente, de quais serviços um componente depende | ○ | ○ | ○ | ○ | ○ | ○ |
| e. Perceber que faltavam dados para concluir a análise (por exemplo, serviço sem instrumentação ou amostragem de traces) | ○ | ○ | ○ | ○ | ○ | ○ |
| f. Não ter acesso a dados necessários para a investigação | ○ | ○ | ○ | ○ | ○ | ○ |
| g. Receber uma investigação de outra pessoa sem informações suficientes para continuar | ○ | ○ | ○ | ○ | ○ | ○ |
| h. Refazer etapas de uma investigação que outra pessoa já havia feito | ○ | ○ | ○ | ○ | ○ | ○ |

**Q17.** Quando um diagnóstico inicial se mostrou incorreto, quais consequências você já presenciou?

- ☐ Acionamento de uma pessoa ou equipe que não era responsável
- ☐ Alteração no serviço ou componente errado
- ☐ Reversão de versão (*rollback*) ou reinício desnecessário
- ☐ Atraso na recuperação do sistema
- ☐ Perda de evidências necessárias para a investigação
- ☐ Comunicação incorreta a clientes ou a outras áreas
- ☐ Não presenciei consequências relevantes
- ☐ Nunca presenciei um diagnóstico inicial incorreto
- ☐ Outra: ________

---

**Página 6 — Relações entre serviços e ponto de partida**

**Q18.** Durante uma investigação, com que frequência você examina como os serviços envolvidos dependem uns dos outros (quais serviços chamam quais)?

- ○ Nunca → *segue para Q20*
- ○ Raramente
- ○ Às vezes
- ○ Frequentemente
- ○ Sempre

**Q19.** De que forma você examina essas relações?

- ☐ Mapa de serviços da ferramenta de observabilidade
- ☐ Visualização de um trace (por exemplo, em cascata)
- ☐ Diagramas ou documentação de arquitetura
- ☐ Leitura do código ou de configurações
- ☐ Meu conhecimento prévio do sistema
- ☐ Perguntando a outras pessoas
- ☐ Outra: ________

**Q20.** Qual ponto de partida você considera mais adequado no começo de uma investigação? *(opções em ordem aleatória)*

- ○ Um conjunto reduzido de informações já selecionadas, aprofundando depois
- ○ Todos os dados do período, para que eu mesmo(a) faça a filtragem
- ○ Depende da situação
- ○ Não tenho preferência

**Q21.** Por que você escolheu essa resposta? Se depende da situação, de quê? *(resposta longa)*

________

---

**Página 7 — Sugestões automáticas de causa**

**Q22.** Você já utilizou alguma ferramenta que sugere automaticamente a causa provável de um incidente (por exemplo, análise automática de causa raiz, correlação de anomalias ou assistente baseado em inteligência artificial)?

- ○ Sim, frequentemente
- ○ Sim, algumas vezes
- ○ Não → *segue para Q24*
- ○ Não sei → *segue para Q24*

**Q23.** Antes de aceitar ou descartar uma sugestão desse tipo, o que você costumava fazer?

- ☐ Conferia os registros ou dados em que a sugestão se baseava
- ☐ Comparava com mudanças ou implantações recentes
- ☐ Reproduzia ou testava a suposta causa
- ☐ Consultava outra pessoa
- ☐ Aceitava sem conferir
- ☐ Descartava sem conferir
- ☐ Outro: ________

**Q24.** Imagine que uma ferramenta indique uma causa provável para um incidente que você está investigando. O que você precisaria saber para decidir se confia nessa indicação? *(resposta longa)*

________

---

**Página 8 — Comunicação e acesso aos dados**

**Q25.** Nas investigações de que você participa, para quem o diagnóstico inicial costuma ser comunicado?

- ☐ Desenvolvedores responsáveis pelos serviços
- ☐ SRE ou pessoa de plantão
- ☐ DevOps ou engenharia de plataforma
- ☐ QA
- ☐ Gestores
- ☐ Atendimento ou relacionamento com clientes
- ☐ Não costuma ser comunicado
- ☐ Outro: ________

**Q26.** Por quais meios esse diagnóstico costuma ser comunicado?

- ☐ Mensagens em ferramenta de chat (por exemplo, Slack ou Teams)
- ☐ Chamado ou *ticket*
- ☐ Registro em ferramenta de gestão de incidentes
- ☐ Reunião ou chamada
- ☐ Link para uma consulta ou painel na ferramenta de observabilidade
- ☐ Documento de análise pós-incidente (*postmortem*)
- ☐ Outro: ________

**Q27.** Ao repassar ou receber uma investigação em andamento, que informações não podem faltar para que a outra pessoa consiga continuar? *(resposta longa)*

________

**Q28.** Na sua organização, existem restrições sobre quem pode consultar ou compartilhar dados de produção, como logs e traces?

- ○ Sim
- ○ Não → *segue para Q30*
- ○ Não sei → *segue para Q30*

**Q29.** Essas restrições interferem nas investigações de que você participa? Se sim, de que forma? *(resposta longa)*

________

---

**Página 9 — Investigações anteriores e comparação**

**Q30.** Durante uma investigação, com que frequência você consulta investigações de incidentes anteriores (registros, análises pós-incidente ou conversas)?

- ○ Nunca → *segue para Q32*
- ○ Raramente
- ○ Às vezes
- ○ Frequentemente
- ○ Sempre

**Q31.** Em que situação e com qual objetivo você faz essa consulta? *(resposta longa)*

________

**Q32.** Durante uma investigação, com que frequência você compara o comportamento do sistema com outro período (por exemplo, antes de uma implantação)?

- ○ Nunca
- ○ Raramente
- ○ Às vezes
- ○ Frequentemente
- ○ Sempre

---

**Página 10 — Encerramento**

**Q33.** Há algo sobre a investigação de incidentes que não perguntamos e que você considera importante? *(resposta longa)*

________

> **Mensagem final:** Obrigado pela participação! Se quiser participar de uma conversa ou atividade posterior sobre este tema (entrevista, observação ou grupo de discussão), use este formulário separado: [link PENDENTE]. Ele não tem ligação com as respostas deste questionário.

#### Como os dados serão analisados

1. **Preparação da base:** excluir respostas sem consentimento, com “Não” em Q1 ou do piloto; sinalizar respostas idênticas enviadas em sequência como possíveis duplicatas; anonimizar as respostas abertas, conforme os aspectos éticos de A01.
2. **Perguntas fechadas:** contagem de respostas por grupo de papel (SRE; DevOps, plataforma ou observabilidade; desenvolvimento; QA; gestão e outros). Serão apresentados números absolutos; percentuais apenas para grupos com pelo menos dez respondentes. Nas escalas de frequência (Q16, Q18, Q30 e Q32), serão apresentadas a distribuição de cada item, a mediana e a proporção de “Frequentemente” e “Sempre”, excluindo “Não se aplica”. Como a amostra é por conveniência, não serão feitos testes estatísticos inferenciais.
3. **Cruzamentos:** Q2 × Q8 e Q9, para verificar quem formula o diagnóstico inicial em cada papel; Q2 × Q16, para comparar dificuldades por papel; Q5 × Q18 e Q20, para verificar se o tamanho do sistema altera o exame de dependências e o ponto de partida; Q22 × Q23 e Q24, para relacionar uso de sugestões automáticas e critérios de confiança.
4. **Perguntas abertas** (Q10, Q15, Q21, Q24, Q27, Q29, Q31 e Q33): codificação temática com códigos iniciais derivados de H01–H04 e códigos novos que surgirem das respostas. Dois integrantes codificam separadamente as mesmas respostas, comparam a codificação e resolvem divergências antes de codificar o restante. Cada tema é apresentado com o número de respondentes que o mencionaram e trechos anonimizados (por exemplo, “R07”). Os termos de Q10 serão listados com suas frequências.
5. **Critérios definidos antes da coleta:** a tabela abaixo indica o que será considerado indício de sustentação, refutação ou refinamento. “Maioria” significa mais da metade dos respondentes do grupo considerado. O questionário fornece tendências da amostra; o estado final de cada hipótese depende da triangulação com I02–I04, descrita na Síntese.

| Hipótese/lacuna | Perguntas | Indício de sustentação | Indício de refutação ou refinamento |
|---|---|---|---|
| Plausibilidade do recorte | Q2, Q6, Q8, Q9 | A maioria dos SREs e DevOps marca “Investigar onde a falha começou” em Q8, e esses papéis aparecem em Q9 como responsáveis pelo primeiro parecer. | O primeiro parecer é atribuído principalmente a desenvolvedores ou “depende do incidente”; revisar o papel de P01 como persona primária. |
| H01 | Q5, Q16c, Q16d, Q18, Q19 | A maioria examina dependências “frequentemente” ou “sempre” e usa mapa ou trace para isso; Q16c é frequente. | Exame raro ou baseado apenas em conhecimento prévio; diferenças por tamanho do sistema refinam quando a estrutura deve ser apresentada. |
| H02 | Q16a, Q16e, Q20, Q21 | Não se aplica diretamente, por ser lacuna `[?]`. | A distribuição de Q20 e as condições citadas em Q21 transformam H02 em uma hipótese verificável sobre o conteúdo da primeira visão. |
| H03 | Q22, Q23, Q24 | As respostas a Q24 citam a possibilidade de conferir os dados que sustentam a indicação, e Q23 mostra conferência antes de aceitar. | A confiança depende sobretudo de outros fatores, como histórico de acertos da ferramenta, autoria ou reprodução do problema. |
| H04 | Q4, Q16f, Q16g, Q16h, Q25–Q29 | Q16f–h ocorrem “às vezes” ou mais para a maioria, e Q29 relata interferência das restrições. | Repasses suficientes e restrições sem interferência; problemas concentrados em certos papéis ou transições refinam a hipótese. |
| Histórico e comparação (Entrega 1, seção 8) | Q30, Q31, Q32 | Consulta e comparação raras mantêm a exclusão. | Uso frequente e ligado ao diagnóstico inicial em Q31 leva a reavaliar a exclusão. |

Os resultados alimentam a revisão das personas (Entrega 3), as metas de usabilidade (Entrega 8), os signos e rótulos (Entregas 9 e 11) e o registro de hipóteses em [`../RASTREABILIDADE.md`](../RASTREABILIDADE.md).

### Instrumento I02 — Entrevista semiestruturada

**Autor(a):** Gabriel Lovato — 22.123.004-8  
**Técnica:** entrevista semiestruturada  
**Objetivo:** compreender em profundidade como desenvolvedores e SREs reconstroem um incidente recente até uma primeira explicação sobre sua origem, que critérios usam para considerá-la suficiente, como avaliam sugestões prontas de causa e o que é repassado entre os papéis. Investiga H01–H04, com ênfase em H03 e H04.  
**Público:** desenvolvedores backend, SREs e, como proxy, profissionais de DevOps ou plataforma que participaram de investigações de incidentes nos últimos 6 meses, conforme os critérios de A02.

#### Procedimento padronizado de aplicação

1. **Preparação:** recrutar os participantes e agendar sessões de 45 a 50 minutos por videochamada. Enviar o termo de consentimento com dois dias de antecedência. Realizar uma entrevista piloto com um profissional fora da amostra para ajustar a redação e o tempo dos blocos; aplicar os ajustes ao roteiro antes da primeira entrevista válida. Definir o integrante responsável pelas anotações e preparar a ficha de registro.
2. **Apresentação/consentimento:** ler a abertura padronizada do roteiro. Confirmar o consentimento e a escolha sobre a gravação de áudio. Iniciar a gravação somente após o aceite e registrar o aceite verbal no início do áudio ou na ficha.
3. **Aplicação:** seguir os blocos na ordem. Ler as perguntas principais como estão escritas e usar as sondagens apenas quando a resposta não cobrir o ponto. Não sugerir respostas, não avaliar as decisões relatadas e não mencionar o pipeline do TCC, grafos, LLM ou ideias de interface. Respeitar o tempo aproximado de cada bloco.
4. **Encerramento:** fazer as perguntas finais, agradecer, informar como os dados serão anonimizados e oferecer o envio de um resumo dos resultados agregados. Encerrar a gravação.
5. **Armazenamento/anonimização:** transferir o áudio para a pasta restrita no mesmo dia e removê-lo da nuvem da ferramenta. Transcrever em até 7 dias, com IDs E01, E02..., substituindo nomes e detalhes identificáveis por marcadores. Excluir o áudio após a conferência da transcrição. Publicar no repositório apenas resumos codificados e trechos anonimizados. Excluir transcrições e fichas ao final da disciplina.

#### Instrumento

**Abertura padronizada (ler ao participante):**

> Obrigado por participar. Esta entrevista faz parte de um trabalho da disciplina de Interação Humano-Computador da FEI. Queremos entender como profissionais investigam incidentes em sistemas compostos por vários serviços. Estamos estudando a atividade, não avaliando você nem a sua equipe; não há respostas certas ou erradas. A conversa dura cerca de 45 minutos. Você pode deixar de responder qualquer pergunta ou interromper a entrevista a qualquer momento. Pedimos que não cite nomes de pessoas, empresas, clientes ou sistemas e que não compartilhe a tela nem trechos de logs; descreva os serviços de forma genérica, por exemplo, “o serviço de pagamento”.
>
> *[Somente se houver consentimento para gravação:]* Vou iniciar a gravação de áudio agora. Você confirma que concorda em participar e em ter o áudio gravado?

**Bloco 1 — Contexto (5 min)**

- **P1.** Qual é o seu papel atual e como ele se relaciona com incidentes em produção?
- **P2.** Com que frequência você participa de investigações de incidentes e em que momento costuma entrar nelas?
  - *Sondagens:* Você participa de escala de plantão? Quem mais costuma participar dessas investigações?

**Bloco 2 — Um incidente recente (15 min)**

- **P3.** Pense no incidente mais recente cuja investigação você acompanhou e que consiga descrever sem detalhes confidenciais. Como você ficou sabendo dele?
- **P4.** Conte, passo a passo, o que você fez desde esse momento até ter uma primeira explicação sobre onde a falha começou.
  - *Sondagens:* Qual informação você consultou primeiro? Por quê? Em que momento mudou de direção? O que levou a isso? Procurou algo que não encontrou? Quanto tempo levou cada parte?
- **P5.** Durante essa investigação, que dúvidas você teve sobre qual serviço estava na origem do problema?
  - *Sondagens:* Como resolveu essa dúvida? Que informação ajudou a decidir? *[Somente se o participante citar mais de um serviço:]* Como você verificou a relação entre esses serviços?
- **P6.** Como você lidou com a quantidade de dados disponível no começo da investigação?
  - *Sondagens:* O que deixou de olhar? Por quê? Em algum momento precisou voltar a dados que tinha deixado de lado?

**Bloco 3 — Suficiência da explicação (8 min)**

- **P7.** Como você soube que a explicação era suficiente para comunicar ou agir?
  - *Sondagens:* O que ainda faltava confirmar quando você comunicou? Alguém questionou a explicação? Por quê?
- **P8.** Que informação faria você mudar de ideia sobre essa explicação?
- **P9.** Depois, a explicação se confirmou? O que aconteceu em seguida?

**Bloco 4 — Sugestões prontas de causa (8 min)**

- **P10.** Você já recebeu, de uma ferramenta ou de um colega, uma sugestão pronta sobre a causa de um incidente? Conte como foi.
  - *Sondagens:* Como decidiu se a sugestão era confiável? O que conferiu antes de agir? Isso muda quando a sugestão vem de uma ferramenta e quando vem de uma pessoa? Já seguiu uma sugestão que estava errada? O que aconteceu?
- **P11.** O que faria você descartar uma sugestão de causa sem segui-la?

**Bloco 5 — Repasse e acesso aos dados (8 min)**

- **P12.** Nesse incidente, de quem você recebeu ou para quem repassou a investigação? Como isso foi feito?
  - *Sondagens:* Por qual meio? O que estava presente no repasse? O que faltou? O que precisou ser refeito?
- **P13.** Que informações não podem faltar quando você recebe uma investigação em andamento? E quando você a repassa?
- **P14.** Houve dados que você não podia acessar ou compartilhar? Como isso afetou a investigação?

**Bloco 6 — Encerramento (3 min)**

- **P15.** Que termos você e sua equipe usam, durante um incidente, para se referir à explicação provisória sobre a origem e aos serviços afetados?
- **P16.** Há algo sobre a investigação de incidentes que eu não perguntei e que você considera importante?

**Fechamento (ler):**

> Obrigado pela participação. As informações serão anonimizadas antes de qualquer análise, e o áudio será excluído depois da transcrição. Se quiser, enviamos um resumo dos resultados agregados ao final do estudo. *[Encerrar a gravação.]*

**O entrevistador não deve:** sugerir causas, ferramentas ou soluções; mencionar o pipeline do TCC, grafos, subgrafos, LLM ou telas; concordar ou discordar das decisões relatadas; reformular uma pergunta oferecendo exemplos de resposta.

**Ficha de registro (preenchida pelo anotador):**

| Campo | Registro |
|---|---|
| ID do participante | E__ |
| Papel / faixa de experiência | |
| Data / duração | |
| Gravação de áudio | sim / não |
| Gatilho do incidente relatado | |
| Sequência de ações (fonte → ação → decisão) | |
| Dúvidas sobre origem e efeitos | |
| Critério de suficiência citado | |
| Avaliação de sugestões de causa | |
| Repasse: o que havia, o que faltou, o que foi refeito | |
| Restrições de acesso | |
| Termos do domínio | |
| Falas relevantes (com minutagem) | |
| Desvios do roteiro | |

#### Como os dados serão analisados

1. **Preparação:** transcrição anonimizada de cada entrevista ou, quando não houver gravação, consolidação das notas do anotador no mesmo dia.
2. **Linha do tempo por entrevista:** reconstrução do incidente relatado — gatilho, sequência de fontes consultadas, mudanças de direção, momento da primeira explicação e repasse —, o que permite comparar participantes e confrontar o relato com as tarefas modeladas na Entrega 5.
3. **Codificação temática:** códigos iniciais derivados das hipóteses — ORIGEM-EFEITO e DEPENDÊNCIAS (H01); VOLUME e APROFUNDAMENTO (H02); SUFICIÊNCIA, CONFIANÇA e REJEIÇÃO (H03); REPASSE, RETRABALHO e ACESSO (H04) — e códigos novos que surgirem. Dois integrantes codificam separadamente as duas primeiras entrevistas, comparam os resultados, ajustam as definições dos códigos e só então codificam as demais.
4. **Comparação entre papéis:** matriz participante × tema, comparando desenvolvedores e SREs. Temas citados por um único participante são mantidos como indícios, não como padrões.
5. **Uso no design:** os resultados produzem uma lista de critérios de suficiência e de informações mínimas do repasse, com o número de participantes que citou cada item, e uma lista de termos do domínio. Esses produtos alimentam a revisão de P01 e P02, o conteúdo das hipóteses e evidências (F03) e a comunicação do diagnóstico. As evidências sobre H01–H04 são trianguladas com I01, I03 e I04 antes de alterar o estado das hipóteses.

### Instrumento I03 — Observação

**Autor(a):** Théo Zago Zimmermann — 22.123.035-2  
**Técnica:** observação  
**Objetivo:** observar como SREs investigam um incidente até formular e comunicar um diagnóstico inicial, em ambiente controlado e com dados sintéticos, registrando a ordem de consulta das fontes, o uso das relações entre serviços, o volume examinado antes de restringir a análise, as hesitações e a distinção entre origem e efeitos. Investiga H01, H02 e a plausibilidade da tarefa, complementando os relatos obtidos por I01 e I02.  
**Público:** SREs e, como proxy, profissionais de DevOps ou plataforma com plantão, conforme os critérios de A03.

#### Procedimento padronizado de aplicação

1. **Preparação:** instalar, em máquina da equipe, uma aplicação de demonstração de microsserviços com telemetria sintética — por exemplo, a aplicação de demonstração do projeto OpenTelemetry, que simula uma loja virtual e oferece traces, métricas, logs e injeção de falhas por *feature flags*. Registrar a versão e a configuração utilizadas. Manter o gerador de carga ativo e, 10 minutos antes de cada sessão, ativar a mesma falha no serviço de pagamento, de modo que os erros também apareçam no serviço de finalização da compra e na loja. Restaurar o ambiente entre as sessões. Testar a gravação, preparar a ficha e realizar uma sessão piloto com um profissional fora da amostra para calibrar a instrução, o tempo e as definições da ficha. Definir moderador e observador. Se o ambiente não puder ser preparado, a técnica será rediscutida com o docente antes da aplicação; dados de produção não serão usados como substituto.
2. **Apresentação/consentimento:** ler a abertura padronizada e confirmar o consentimento e as opções de gravação. Fazer o aquecimento do pensar em voz alta. Conduzir uma familiarização de até 5 minutos, em que o moderador mostra onde ficam traces, métricas e logs usando um serviço sem relação com a falha.
3. **Aplicação:** ler e entregar por escrito a instrução da tarefa. Iniciar a cronometragem. O moderador usa apenas as intervenções permitidas; o observador preenche a ficha com a minutagem dos eventos. A tarefa termina quando o participante comunica o diagnóstico ou após 25 minutos.
4. **Encerramento:** fazer as perguntas pós-sessão, agradecer e, se o participante quiser, informar qual falha foi simulada. Encerrar a gravação e restaurar o ambiente.
5. **Armazenamento/anonimização:** transferir as gravações para a pasta restrita no mesmo dia, com IDs O01, O02... Completar a ficha a partir da gravação em até 7 dias, anonimizando comentários sobre o empregador. Excluir as gravações após a codificação. Publicar no repositório apenas fichas consolidadas e resultados agregados.

#### Instrumento

**Abertura padronizada (ler ao participante):**

> Obrigado por participar. Esta atividade faz parte de um trabalho da disciplina de Interação Humano-Computador da FEI. Queremos entender como profissionais investigam incidentes em sistemas compostos por vários serviços. Você vai investigar um incidente simulado em uma loja virtual de demonstração, com dados fictícios. Estamos estudando a atividade e as dificuldades que ela envolve, não avaliando você; não há resposta certa esperada. A sessão dura cerca de 45 minutos, e a investigação tem limite de 25 minutos. Você pode interromper a qualquer momento. Pedimos que, durante a investigação, diga em voz alta o que está pensando, procurando e decidindo.
>
> *[Somente se houver consentimento:]* Vou iniciar a gravação da tela do ambiente e do áudio agora. Você confirma que concorda?

**Aquecimento do pensar em voz alta (2 min):** o moderador pede: “Para praticar, procure no navegador a previsão do tempo para amanhã, dizendo em voz alta o que está fazendo e pensando.”

**Instrução da tarefa (ler e entregar por escrito):**

> Você está de plantão em uma loja virtual composta por vários serviços. Há alguns minutos, um alerta informou aumento de erros na finalização de compras. Investigue com as ferramentas disponíveis, como faria no seu trabalho, até ter uma explicação provisória sobre onde a falha provavelmente começou e quais serviços ela afeta. Quando chegar a essa explicação, comunique-a em voz alta como se estivesse falando com a equipe de desenvolvimento. Durante a investigação, continue dizendo o que está pensando.

**Intervenções permitidas ao moderador:**

- Após cerca de 15 segundos de silêncio: “Continue dizendo o que está pensando.”
- “O que você está procurando agora?”
- Quando o participante perguntar o que fazer: “Pode seguir como faria no seu trabalho.”
- Dúvidas sobre o funcionamento do ambiente (por exemplo, como abrir uma ferramenta) podem ser respondidas; dúvidas sobre o incidente, não.
- Aos 20 minutos: “Faltam cerca de cinco minutos.”

**O moderador não deve:** indicar o serviço com falha ou fontes a consultar; confirmar ou negar hipóteses; comentar o desempenho do participante; mencionar o pipeline do TCC, grafos, subgrafos, LLM ou telas.

**Ficha de observação (preenchida pelo observador):**

*Cabeçalho*

| Campo | Registro |
|---|---|
| ID do participante | O__ |
| Papel / faixa de experiência | |
| Familiaridade prévia com as ferramentas do ambiente | nenhuma / alguma / alta |
| Data / moderador / observador | |
| Registro | tela / áudio / somente ficha |

*Eventos*

| Tempo (mm:ss) | Ferramenta/fonte | Ação | Código | Fala relevante | Observação |
|---|---|---|---|---|---|
| | | | | | |

*Códigos de eventos*

| Código | Definição |
|---|---|
| CON-L / CON-M / CON-T / CON-MAP | Consulta a logs / métricas / traces / mapa de serviços. |
| FIL | Aplica, altera ou remove filtro de serviço, período ou atributo. |
| DEP | Examina a relação entre dois ou mais serviços. |
| HIP+ | Verbaliza uma hipótese sobre a origem da falha. |
| HIP− | Descarta uma hipótese verbalizada anteriormente. |
| RET | Volta a uma fonte ou visão já consultada. |
| HES | Hesitação: pausa de mais de 15 segundos sem ação nem fala, ou verbalização explícita de dúvida. |
| AJU | Pede ajuda ao moderador. |
| COM | Comunica o diagnóstico: fala dirigida à equipe de desenvolvimento com a origem provável e os serviços afetados. |

*Resumo da sessão*

| Campo | Registro |
|---|---|
| Tempo até a primeira hipótese (HIP+) | |
| Tempo até a comunicação (COM) ou encerramento por tempo | |
| Número de trocas de ferramenta/fonte | |
| Número de filtros aplicados ou alterados | |
| Serviços examinados antes da primeira hipótese | |
| Uso de DEP antes ou depois da primeira hipótese | |
| Serviço apontado como origem / serviços apontados como afetados | |
| Evidências citadas na comunicação | |
| Grau de certeza expresso na comunicação | |

**Perguntas pós-sessão (5 min):**

1. Como essa investigação se compara às que você faz no trabalho? O que foi diferente?
2. Em que momento você teve mais dúvida? O que fez a respeito?
3. O que precisaria verificar para ter mais segurança na explicação que deu?
4. Houve alguma informação que você usaria no seu trabalho e não encontrou aqui?

#### Como os dados serão analisados

1. **Codificação das sessões:** o observador completa a ficha a partir da gravação. Na primeira sessão, dois integrantes codificam os eventos separadamente, comparam o resultado e ajustam as definições dos códigos antes de codificar as demais.
2. **Linha do tempo por sessão:** sequência codificada de eventos e medidas descritivas — tempos até HIP+ e COM, número de trocas de fonte, filtros e serviços examinados antes da primeira hipótese.
3. **Comparação entre sessões:** fontes usadas no início da investigação; uso das relações entre serviços (DEP) antes ou depois da primeira hipótese e na decisão sobre a origem (H01); volume examinado antes de restringir a análise (H02); concentração de HES e RET, que indica rupturas; sinais citados para separar origem e efeitos.
4. **Comunicação final:** comparação do conteúdo dos diagnósticos comunicados (origem, serviços afetados, evidências e grau de certeza) para identificar uma estrutura mínima de comunicação.
5. **Uso no design:** os resultados são apresentados de forma agregada e alimentam a revisão das tarefas da Entrega 5, as metas de eficiência da Entrega 8 — com a ressalva do ambiente controlado — e a composição da primeira visão e da inspeção do subgrafo (F02). Com 3 a 5 sessões, os achados indicam padrões a confirmar; são triangulados com I01 e I02 antes de alterar o estado de H01 e H02.

## Síntese

O conjunto de técnicas pretende reduzir quatro lacunas sobre os usuários: **(1)** se o recorte é plausível, isto é, se o SRE formula o diagnóstico inicial de incidentes, com que frequência e a partir de quais gatilhos; **(2)** como a investigação é feita hoje, incluindo fontes, ordem de consulta, rupturas e tempo; **(3)** como uma explicação sobre a origem de uma falha ganha ou perde credibilidade; e **(4)** como o contexto circula entre papéis e quais restrições de acesso existem.

As técnicas se complementam. O questionário (I01) alcança mais pessoas e papéis e indica frequências, mas depende de autorrelato. A entrevista semiestruturada (I02) aprofunda o raciocínio em incidentes recentes. A observação (I03) registra o comportamento efetivo em uma investigação controlada e reduz a dependência da memória, mas usa dados sintéticos. O grupo focal (I04) confronta as necessidades de papéis diferentes no repasse. Uma hipótese só será considerada **sustentada** ou **refutada** quando pelo menos duas técnicas apontarem na mesma direção; resultados de uma única técnica levam, no máximo, ao **refinamento**.

| Hipótese da Entrega 1 | Técnicas | Ficará sustentada se | Ficará refutada se | Ficará refinada se |
|---|---|---|---|---|
| Recorte: o SRE formula o diagnóstico inicial (seções 3.1, 3.3 e 7.2) | I01, I02, I03 | SREs relatam e demonstram realizar a investigação até o primeiro parecer. | O primeiro parecer cabe predominantemente a outro papel. | A responsabilidade varia por organização ou tipo de incidente. |
| H01 — estrutura de dependências | I01, I02, I03 | As relações entre serviços são examinadas com frequência e usadas para separar origem e efeitos, no relato e na observação. | As relações são pouco examinadas ou não influenciam a decisão sobre a origem. | A utilidade depende do tamanho do sistema, do papel ou de a origem ser ambígua. |
| H02 — quantidade inicial de detalhes | I01, I03, I04 | Não se aplica: H02 é lacuna `[?]`. | Não se aplica. | Os dados indicam o que os profissionais examinam antes de restringir a análise, e H02 passa a ser uma hipótese verificável sobre a primeira visão. |
| H03 — hipótese acompanhada de evidências | I01, I02, I04 | A decisão de confiar depende de conferir os dados que sustentam a explicação. | A confiança depende de outros fatores, e as evidências associadas não alteram a decisão. | As evidências importam apenas para certos papéis ou situações, ou precisam incluir contra-evidências e incerteza. |
| H04 — colaboração e restrições de acesso | I01, I02, I04 | Repasses incompletos, retrabalho e restrições de acesso aparecem com frequência e afetam a investigação. | Os repasses ocorrem com contexto suficiente e as restrições não interferem. | Os problemas se concentram em certas transições entre papéis ou em certos tipos de dado. |

Os resultados terão limitações já conhecidas: amostra por conveniência, provável predominância de desenvolvedores, poucas organizações e possível uso de participantes proxy no lugar de SREs. Essas limitações serão registradas junto aos resultados. Até a análise, H01–H04 permanecem **abertas**; quando os dados forem coletados e analisados, os novos estados serão registrados em [`../RASTREABILIDADE.md`](../RASTREABILIDADE.md), preservando o histórico.

## Checklist

- [ ] Hipóteses/lacunas prioritárias da Entrega 1 foram revisitadas.
- [ ] Se o escopo de IHC foi derivado de TCC técnico, a coleta investiga a plausibilidade do usuário, tarefa e contexto adotados.
- [ ] Perguntas não pressupõem que dashboard, CRUD, filtros ou relatórios sejam necessários; investigam a necessidade.
- [ ] Cada dado a coletar responde uma dúvida concreta do projeto ou justifica outra necessidade de informação.
- [ ] Parte A identifica dados e perfis de coleta de forma específica.
- [ ] Aspectos éticos são contextualizados para o projeto.
- [ ] Há uma técnica completa por integrante e técnicas distintas.
- [ ] Questionário está incluído entre as técnicas.
- [ ] Cada instrumento possui objetivo, público, procedimento e conteúdo integral.
- [ ] Perguntas evitam indução e coletam apenas dados necessários.
- [ ] Está claro como os dados serão analisados e usados no design.
