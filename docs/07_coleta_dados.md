# Entrega 7 — Coleta de dados, necessidades e aspectos éticos

**Data:** {{dd/mm/aaaa}}  
**Status:** ⬜ não iniciada

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
| H01 | {{...}} | {{...}} | {{...}} | alta / média / baixa |

## Parte A — necessidades e requisitos de IHC

> **Responsabilidade:** solução individual por integrante.

### A01 — {{autor}}

**Autor(a):** {{nome — matrícula}}

#### Que dados coletar?

| Dado/informação | Hipótese/lacuna relacionada | Por que é necessário | Qual decisão de design pode afetar |
|---|---|---|---|
| {{...}} | {{H01/H02/...}} | {{...}} | {{...}} |

#### De quem coletar?

| Perfil/stakeholder | Critério de inclusão | Relação com persona/público |
|---|---|---|
| {{...}} | {{...}} | {{...}} |

#### Aspectos éticos

Analise voluntariedade, consentimento, minimização de dados, privacidade, riscos, gravação, anonimização, armazenamento e descarte. Não responda apenas “sim, por causa da LGPD”: explique **quais dados e riscos existem neste projeto**.

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

## Parte B — ferramentas de coleta

> Cada integrante deve preparar uma técnica/instrumento completo. As técnicas devem ser diferentes entre si e **questionário deve estar entre as técnicas escolhidas**, conforme o enunciado da disciplina.

### Instrumento I01 — {{nome da técnica}}

**Autor(a):** {{nome — matrícula}}  
**Técnica:** questionário / entrevista semiestruturada / observação / grupo focal / outra autorizada  
**Objetivo:** {{...}}  
**Público:** {{...}}

#### Procedimento padronizado de aplicação

1. {{preparação}}
2. {{apresentação/consentimento}}
3. {{aplicação}}
4. {{encerramento}}
5. {{armazenamento/anonimização}}

#### Instrumento

Cole aqui o questionário/roteiro completo ou forneça link **mais uma cópia textual no repositório**.

#### Como os dados serão analisados

{{ex.: distribuição de respostas, codificação temática, agrupamento de problemas}}


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
## Síntese

Explique quais lacunas de conhecimento sobre usuários o conjunto de técnicas pretende reduzir. Indique explicitamente quais hipóteses da Entrega 1 deverão ficar **sustentadas, refutadas ou refinadas** após a análise dos dados. Quando os dados forem coletados/analisados, atualize o histórico em `RASTREABILIDADE.md`.

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
