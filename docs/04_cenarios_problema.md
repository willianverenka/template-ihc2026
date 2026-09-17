# Entrega 4 — Cenários de análise/problema

**Data:** 10/09/2026

**Status:** 🟨 em andamento

**Responsabilidade:** 1 solução completa por integrante

## Objetivo da atividade

Descrever situações atuais em que o usuário tenta alcançar um objetivo e encontra dificuldades. O cenário de análise/problema deve tornar visível **o contexto, os atores, as ações e as rupturas**, sem antecipar a interface que será projetada.

> **Regra central:** cenário de problema é a “história do problema”. Se o texto já diz “o sistema mostra”, “o aplicativo resolve” ou descreve botões/telas futuras, provavelmente está misturando problema com solução.

Sempre que possível, o cenário deve aprofundar uma **situação concreta já registrada na Entrega 1**.

### Quando o TCC não possuía interface

O cenário continua sendo uma história de **problema/atividade humana**, não uma história do futuro sistema. Descreva como o profissional realiza hoje uma atividade semelhante ou como lida atualmente com dados, resultados, configurações, logs, decisões e limitações que o tema do TCC pretende apoiar.

Exemplo: em vez de “o DBA abre o novo dashboard e executa o algoritmo”, descreva “o DBA precisa investigar uma consulta lenta, reúne informações em ferramentas distintas, compara planos manualmente e tem dificuldade para estimar o impacto de uma mudança”.

A interface da disciplina aparecerá somente depois, nos cenários de interação.

Se o integrante escolher um novo problema/situação, explique por que ele passou a ser relevante e indique a evidência que motivou sua inclusão.

## Cenário C01 — Investigação de falha no checkout após um deploy

**Autor(a):** Gabriel Lovato — 22.123.004-8

**Persona(s) relacionada(s):** P01 — Lucas, o Desenvolvedor Sênior

**Necessidade relacionada:** R01 — reduzir o esforço para localizar, correlacionar e interpretar evidências durante a investigação de um incidente

**Situação concreta da Entrega 1 relacionada:** seções 4.2, 4.4 e 4.5; atividade A01

**Hipóteses ainda presentes:** H01, H02, H03 e H04

### 1. Cenário inicial

Pouco depois de uma nova versão do sistema ser implantada, Lucas, desenvolvedor backend, é avisado pelo SRE de plantão de que o checkout apresenta erros e aumento de latência. Ele precisa descobrir se um dos microsserviços mantidos por sua equipe está relacionado ao incidente e reunir evidências suficientes para iniciar a correção.

Lucas consulta logs, métricas e traces nas ferramentas de observabilidade utilizadas pela empresa. Como os registros estão distribuídos entre diferentes serviços e há um grande volume de eventos no período, ele alterna entre fontes, ajusta filtros e tenta reconstruir manualmente o caminho percorrido pelas requisições que falharam. Algumas mensagens indicam erro no serviço de checkout, enquanto outras apontam timeouts em uma dependência de pagamento, mas não fica claro qual evento é a origem da falha e quais são apenas consequências de sua propagação.

Enquanto a investigação prossegue, Lucas recebe novas mensagens da equipe pedindo uma posição. A dificuldade de correlacionar as evidências aumenta o tempo de diagnóstico e pode levá-lo a atribuir a causa ao serviço errado, iniciar uma correção parcial ou acionar outra equipe sem contexto suficiente.

### 2. Questões de refinamento

Use os tipos de questões/taxonomia definidos na aula. As perguntas devem revelar informações **ainda ausentes** do cenário, não repetir o que já foi respondido.

| # | Questão | Por que precisa ser respondida | Fonte/forma de obter resposta |
|---|---|---|---|
| Q1 | **[Contexto]** O que normalmente desencadeia a investigação e quão urgente ela é? | O gatilho e a pressão de tempo alteram a ordem das ações e o nível de profundidade possível no diagnóstico inicial. | Entrega 1, seções 5.1 e 5.3; confirmar por entrevista com desenvolvedores e SREs. |
| Q2 | **[Recursos]** Quais sinais de observabilidade Lucas consulta e como tenta relacioná-los? | É necessário compreender o trabalho atual e em quais pontos ocorre a fragmentação das evidências. | Entrega 1, seções 4.1, 4.3 e 6.1; observar uma investigação ou realizar entrevista contextual. |
| Q3 | **[Atores]** Quem participa da investigação e como o contexto é transferido entre essas pessoas? | A passagem incompleta de informações pode obrigar outro profissional a reiniciar a busca e prolongar o incidente. | H04 e jornada da P01, etapa 1; validar com entrevistas com desenvolvedores e SREs. |
| Q4 | **[Ruptura]** O que impede Lucas de distinguir a causa inicial dos efeitos propagados? | Essa distinção é central para explicar a demora e o risco de um diagnóstico incorreto. | Entrega 1, seção 4.2, e dores da P01; confrontar com relatos e exemplos anonimizados de incidentes. |
| Q5 | **[Critério de conclusão]** Que evidências Lucas considera suficientes para comunicar um diagnóstico inicial? | Sem esse critério, não é possível delimitar quando a investigação cumpre seu objetivo nem avaliar a confiança do profissional. | Objetivo priorizado na Entrega 1, seções 7.3 e 9.2; investigar em entrevista semiestruturada. |
| Q6 | **[Consequência]** O que acontece quando a equipe age com base em evidências incompletas ou mal interpretadas? | A consequência determina a criticidade da tarefa e os riscos que precisam ser considerados nas etapas seguintes. | Entrega 1, seções 4.4 e 5.6; validar com profissionais do público-alvo. |

### 3. Cenário refinado

Reescreva o cenário incorporando as respostas. Marque o conteúdo novo de forma consistente (por exemplo, `**[NOVO: ...]**`).

**[NOVO — contexto e gatilho]** Em uma manhã de trabalho, poucos minutos depois da implantação de uma nova versão, Lucas, desenvolvedor backend responsável por três microsserviços críticos, é acionado pelo SRE de plantão porque o checkout apresenta erros e aumento de latência. Sob pressão para restabelecer o serviço dentro do prazo operacional, ele precisa identificar a provável origem do incidente, avaliar se algum serviço sob sua responsabilidade está envolvido e reunir evidências suficientes para orientar a primeira ação corretiva.

**[NOVO — recursos e ações]** Lucas parte das informações resumidas enviadas pelo SRE e consulta logs, métricas e traces nas ferramentas de observabilidade da empresa. Ele delimita o período próximo ao deploy, procura requisições com erro e compara identificadores e horários para reconstruir o caminho delas entre o checkout e suas dependências. Para aprofundar cada indício, alterna entre diferentes visões e fontes de telemetria, ao mesmo tempo que mantém a IDE e os canais de comunicação abertos.

**[NOVO — ruptura principal]** O volume de eventos inclui milhares de registros que não parecem ligados ao incidente. Além disso, as evidências relevantes estão fragmentadas: algumas mensagens mostram uma exceção no checkout, enquanto traces apontam timeouts no serviço de pagamento. Lucas precisa decidir manualmente se a exceção iniciou a falha, se foi provocada pela indisponibilidade da dependência ou se ambos os sinais são efeitos de outro problema. A incerteza aumenta porque nem sempre o contexto recebido informa os filtros já aplicados, as evidências descartadas ou o raciocínio seguido pelo SRE.

**[NOVO — colaboração e critério de conclusão, ainda a validar]** Enquanto investiga, Lucas recebe cobranças por uma estimativa e troca mensagens com o SRE e com a equipe responsável pelo pagamento. Para comunicar um diagnóstico inicial, ele procura relacionar o sintoma percebido, o serviço provavelmente originador, o caminho de propagação e os registros que sustentam essa interpretação. Ainda precisa ser validado com profissionais se esse conjunto de informações é suficiente e como eles avaliam a confiabilidade de cada evidência.

**[NOVO — consequências]** Se Lucas interpretar um efeito como causa, pode alterar o serviço errado, produzir uma correção parcial, recomendar um rollback desnecessário ou acionar outra equipe sem contexto suficiente. Além de prolongar a indisponibilidade, isso aumenta o retrabalho e mantém clientes expostos a um sistema instável.

### 4. Elementos extraídos

| Elemento | Evidência no cenário |
|---|---|
| Ator(es) | Lucas, desenvolvedor backend; SRE de plantão; equipe responsável pelo serviço de pagamento. |
| Objetivo(s) | Identificar a provável origem e a propagação do incidente, verificar a responsabilidade de seus serviços e comunicar um diagnóstico inicial fundamentado. |
| Contexto | Incidente em produção pouco depois de um deploy, com checkout instável, pressão de tempo e colaboração entre equipes. |
| Recursos/informações | Relato inicial do SRE, logs, métricas, traces, identificadores de requisição, horários, conhecimento da arquitetura e do código, IDE e canais de comunicação. |
| Ações | Delimitar o período, localizar requisições com erro, alternar entre fontes de telemetria, comparar registros, reconstruir o caminho da requisição, avaliar indícios e trocar informações com outras equipes. |
| Problemas/rupturas | Grande volume de eventos; evidências fragmentadas; dificuldade de correlacionar sinais e separar causa de consequência; transferência incompleta de contexto; interrupções e pressão por resposta. |
| Consequências | Diagnóstico demorado ou incorreto, correção parcial, alteração do serviço errado, rollback desnecessário, acionamento equivocado de outra equipe, retrabalho e prolongamento da instabilidade. |

### 5. Implicações para as próximas entregas

As seguintes tarefas merecem ser detalhadas na Entrega 5:

- delimitar o incidente por serviço, sintoma e período;
- localizar e correlacionar logs, métricas e traces de uma requisição com falha;
- reconstruir o caminho da falha entre serviços e distinguir causa provável de efeitos propagados;
- avaliar se as evidências sustentam um diagnóstico inicial;
- comunicar o diagnóstico e transferir o contexto da investigação para outra equipe.

Na coleta de dados, é necessário investigar o fluxo real usado por desenvolvedores e SREs, as ferramentas consultadas, o volume e os tipos de telemetria, os critérios usados para considerar uma evidência relevante, as informações exigidas em um repasse entre equipes, as restrições de acesso a dados de produção e as condições em que um profissional confia ou desconfia de uma hipótese diagnóstica. Essas informações também devem permitir revisar H01, H02, H03 e H04 sem tratá-las antecipadamente como fatos.

> Repita para C02, C03... com autoria individual.

## Checklist

- [ ] Há um cenário completo por integrante. *(Pendente: este arquivo contém somente a contribuição individual de Gabriel.)*
- [x] Cada cenário tem título, ator, objetivo, contexto e problema.
- [x] O cenário possui origem rastreável na Entrega 1 ou justifica claramente a inclusão de uma nova situação.
- [x] O texto descreve a situação atual, sem antecipar a solução.
- [x] Para TCC sem interface original, o cenário descreve uma prática humana plausível relacionada à contribuição técnica, e não “a falta de uma tela”.
- [x] Questões de refinamento acrescentam informação nova.
- [x] O refinamento mostra claramente o que foi adicionado/alterado.
- [ ] Cenários são diferentes o suficiente para cobrir objetivos/problemas relevantes. *(Será verificado quando os demais integrantes adicionarem suas contribuições.)*
- [ ] Cada cenário está ligado a persona/necessidade na matriz de rastreabilidade. *(R01 ainda precisa ser consolidada pela equipe na matriz.)*
