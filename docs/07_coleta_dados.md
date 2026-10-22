## Parte A — necessidades e requisitos de IHC

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
