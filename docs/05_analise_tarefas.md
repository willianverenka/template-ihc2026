# Entrega 5 — Análise de tarefas: HTA, GOMS e CTT

**Data:** 17/09/2026

**Autor:** Théo Zago Zimmermann — 22.123.035-2

## Objetivo da atividade

Analisar como um SRE de plantão formula um diagnóstico inicial sobre um incidente em um sistema distribuído. O HTA organiza os objetivos e as etapas, o GOMS descreve os métodos usados pelo profissional e o CTT representa as relações entre as ações do usuário e as respostas do sistema.

Esta contribuição apresenta uma única tarefa, analisada pelas três técnicas, sem diagramas ou imagens.

## 1. Tarefa escolhida

| ID | Tarefa | Perfil do usuário | Cenário relacionado | Autor |
|---|---|---|---|---|
| T01 | Formular um diagnóstico inicial fundamentado sobre um incidente | SRE de plantão | C01 citado na entrega original: investigação de um incidente sob pressão de tempo | Théo Zago Zimmermann |

O projeto propõe um pipeline em dois estágios. Primeiro, ele seleciona informações relevantes em um grafo de observabilidade. Depois, um modelo de linguagem gera hipóteses sobre a falha. A tarefa escolhida trata de como o SRE utiliza esses resultados, junto de logs, métricas e traces, para entender a provável origem do incidente e seu impacto.

Escolhi essa tarefa porque, durante um incidente, não basta receber uma explicação pronta. O profissional precisa entender quais serviços foram afetados, conferir os indícios disponíveis e comunicar uma hipótese que ajude a equipe a decidir os próximos passos.

Na entrega original, a tarefa está relacionada à atividade A02, “Classificar a saúde do sistema”, e ao cenário C01 do SRE de plantão. Esses identificadores são mantidos como referência ao material do autor, sem associá-los automaticamente aos cenários de outros integrantes.

### Recorte da análise

A tarefa começa quando o SRE recebe ou identifica um alerta e termina quando registra e comunica um diagnóstico inicial com a origem provável, o impacto observado e as dúvidas restantes. Corrigir a falha ou comprovar definitivamente sua causa não faz parte desse recorte.

O usuário trabalha sob pressão de tempo e pode encontrar informações incompletas ou contraditórias. A frequência foi considerada alta na entrega original, mas essa estimativa ainda precisa ser confirmada com usuários. A criticidade é alta porque um diagnóstico equivocado pode direcionar a equipe para o componente errado.

Esta é uma proposta de interação baseada no contexto do projeto. O fluxo não foi validado por observação de SREs, e as hipóteses produzidas pelo pipeline não são tratadas como causas confirmadas.

## 2. HTA — Formular um diagnóstico inicial

### Objetivo principal

**0 — Formular um diagnóstico inicial fundamentado sobre o incidente.**

O SRE delimita o problema, examina os componentes afetados, relaciona as evidências às hipóteses e comunica sua interpretação inicial.

### Diagrama

![HTA T01](../assets/05_tarefas/hta_t01.svg)

### Decomposição da tarefa

| ID | Objetivo ou operação | Como é realizado | Resultado esperado |
|---|---|---|---|
| 0 | Formular um diagnóstico inicial | Executar 1, 2, 3 e 4, retornando à investigação quando necessário. | Diagnóstico inicial registrado, com evidências e limitações. |
| 1 | Delimitar o incidente | Identificar o serviço afetado, o período e o sintoma observado no alerta. | Um recorte inicial para a investigação. |
| 2 | Examinar os componentes e as evidências | Executar 2.1 e 2.2, repetindo a consulta para os componentes relevantes. | Serviços envolvidos e sinais da falha identificados. |
| 2.1 | Inspecionar o subgrafo | Observar as dependências entre os serviços e o caminho relacionado à falha. | Uma visão dos componentes afetados e da possível propagação do problema. |
| 2.2 | Consultar logs, métricas e traces | Conferir erros, alterações nas métricas e a sequência das chamadas no período selecionado. | Registros que ajudam a explicar o incidente. |
| 3 | Relacionar as hipóteses às evidências | Executar 3.1 e 3.2; voltar a 1 ou 2 se o recorte ou os dados forem insuficientes. | Uma interpretação sobre a provável origem e o impacto. |
| 3.1 | Comparar as hipóteses com os registros | Verificar se o serviço apontado e a ordem dos eventos fazem sentido diante dos dados. | Indícios favoráveis, contradições e lacunas identificados. |
| 3.2 | Definir a explicação inicial | Escolher a hipótese mais compatível com os dados e indicar o que ainda não foi esclarecido. | Uma hipótese de trabalho, sem afirmar uma certeza que não existe. |
| 4 | Registrar e comunicar o diagnóstico | Informar o sintoma, a origem provável, o impacto observado, as evidências e as dúvidas restantes. | Um resumo que a equipe possa consultar e utilizar na continuidade da investigação. |

### Planos

- **Plano 0:** realizar 1 → 2 → 3 → 4. Se a análise em 3 revelar uma lacuna importante, retornar a 2. Se o problema estiver fora do recorte escolhido, retornar a 1.
- **Plano 2:** realizar 2.1 → 2.2. Repetir a consulta para outros componentes quando as dependências ou os registros indicarem essa necessidade.
- **Plano 3:** realizar 3.1 → 3.2. Comparar mais de uma hipótese quando houver explicações concorrentes. Se nenhuma tiver suporte suficiente, registrar essa limitação.

O diagnóstico inicial não exige resolver todas as dúvidas. Se houver urgência e os dados continuarem insuficientes, o SRE comunica o que foi observado e o que ainda precisa ser investigado, sem apresentar uma hipótese fraca como causa confirmada.

### Dificuldades identificadas

O principal risco é confundir um serviço que apresentou erros com o serviço que iniciou a falha. Outro problema é aceitar uma hipótese apenas porque o texto parece convincente. Por isso, a interface deve facilitar a consulta aos registros e à sequência dos eventos, mantendo as evidências próximas da explicação.

## 3. GOMS — Formular um diagnóstico inicial

### Objetivo principal

**GOAL 0:** identificar uma provável origem e o impacto do incidente, registrando e comunicando um diagnóstico inicial baseado nas evidências disponíveis.

O objetivo é dividido em delimitar o incidente, reunir evidências, interpretar os resultados e comunicar a conclusão inicial.

### METHOD 1 — Investigar a partir dos resultados disponíveis

1. Ler o alerta e identificar o serviço, o período e o sintoma.
2. Selecionar o recorte do incidente.
3. Consultar o subgrafo e as hipóteses apresentados pelo pipeline.
4. Abrir os registros relacionados aos componentes apontados.
5. Comparar as hipóteses com os logs, as métricas e os traces.
6. Avaliar qual explicação tem mais suporte e qual impacto foi observado.
7. Registrar e comunicar o diagnóstico inicial, incluindo as evidências e as incertezas.

**Regra de seleção:** usar o Método 1 quando os resultados disponíveis cobrirem o recorte do incidente e permitirem localizar os registros relevantes. Se a comparação revelar lacunas importantes, passar ao Método 2.

### METHOD 2 — Ampliar a investigação antes de concluir

1. Identificar quais informações estão ausentes ou quais registros contradizem a explicação inicial.
2. Ajustar o período ou incluir componentes relacionados ao serviço afetado.
3. Solicitar uma nova análise para o recorte ajustado.
4. Consultar os novos resultados e os registros adicionais.
5. Comparar novamente as hipóteses com a sequência dos eventos e as dependências entre os serviços.
6. Avaliar se os novos dados permitem formular uma explicação inicial; repetir a busca se necessário e viável diante da urgência.
7. Registrar e comunicar a origem provável, o impacto e as limitações. Se não houver suporte para apontar uma origem, comunicar os fatos observados e deixar essa parte em aberto.

**Regra de seleção:** usar o Método 2 quando o alerta ou os resultados iniciais forem incompletos, quando houver conflito entre as evidências e a hipótese ou quando o recorte deixar de fora um componente relevante.

Os dois métodos atendem ao mesmo objetivo. O primeiro aproveita o material já disponível; o segundo amplia a investigação antes da comunicação. A troca de método depende do que o SRE encontra, não apenas da quantidade de dados exibidos.

### Operadores utilizados

| Tipo | Operadores | Exemplo na tarefa |
|---|---|---|
| Perceptivos e cognitivos | Ler, identificar, interpretar, comparar e decidir | Comparar o início dos erros com as chamadas entre os serviços e escolher uma hipótese de trabalho. |
| Interação | Selecionar, abrir, filtrar, solicitar, digitar e salvar | Ajustar o período, consultar um trace e registrar o diagnóstico. |

Não foi feita uma estimativa de tempo com KLM. A interface ainda não está definida, e o esforço de interpretação varia conforme o incidente e a experiência do profissional. O GOMS foi usado para organizar os métodos e as escolhas, não para afirmar quanto tempo o diagnóstico levará.

## 4. CTT — Formular um diagnóstico inicial

### Organização das tarefas

O CTT diferencia as ações feitas pelo SRE das respostas automáticas do sistema. Neste recorte, o processamento do pipeline faz parte do fluxo, pois ocorre depois da seleção do incidente e pode ser repetido quando o usuário altera o período ou os componentes analisados.

### Diagrama

![CTT T03](../assets/05_tarefas/ctt_t03.svg)

| ID | Tarefa | Tipo | Papel no fluxo |
|---|---|---|---|
| A0 | Formular um diagnóstico inicial | Abstrata | Agrupa a tarefa completa. |
| I1 | Selecionar o serviço e o período do incidente | Interação | Define o recorte da análise a partir do alerta. |
| S1 | Processar o recorte e apresentar os resultados | Sistema | Executa o pipeline e disponibiliza o subgrafo, as hipóteses e as referências às evidências. |
| A1 | Analisar os resultados | Abstrata | Agrupa I2, S2 e U1; pode ser repetida para diferentes evidências. |
| I2 | Selecionar componentes e solicitar seus registros | Interação | Permite consultar detalhes dos serviços e das chamadas relevantes. |
| S2 | Exibir os registros solicitados | Sistema | Apresenta logs, métricas e traces, ou informa que não há dados para a consulta. |
| U1 | Interpretar as evidências e avaliar as hipóteses | Usuário | Relaciona os dados à origem provável e ao impacto do incidente. |
| I3 | Ajustar o recorte da investigação | Interação | Altera o período ou os componentes quando faltam informações importantes. |
| I4 | Registrar e compartilhar o diagnóstico inicial | Interação | Comunica a interpretação do SRE, as evidências e as limitações. |

As tarefas abstratas agrupam etapas. As tarefas de usuário representam o raciocínio do profissional, sem uma ação direta na interface. As de interação envolvem o uso da interface, enquanto as de sistema são respostas automáticas da aplicação.

### Relações temporais

| Relação | Significado | Aplicação |
|---|---|---|
| `I1 []>> S1` | Ativação com passagem de informação | O serviço e o período selecionados são usados no processamento. |
| `S1 []>> A1` | Ativação com passagem de informação | Os resultados do pipeline ficam disponíveis para a análise do SRE. |
| `I2 []>> S2` | Ativação com passagem de informação | A seleção de componentes e registros define os detalhes apresentados. |
| `S2 []>> U1` | Ativação com passagem de informação | Os registros exibidos são utilizados na interpretação. |
| `A1*` | Repetição | O SRE repete a análise ao consultar outras evidências. |
| `I3 []>> S1` | Ativação com passagem de informação | Um recorte ajustado gera uma nova execução do pipeline. |
| `A1 []>> I4` | Ativação com passagem de informação | A interpretação resultante da análise é utilizada no diagnóstico registrado. |

Dentro de A1, a sequência básica é **I2 → S2 → U1**. O fluxo principal é **I1 → S1 → A1 → I4**, com repetição de A1 quando o SRE precisa consultar mais registros.

Após interpretar as evidências, o usuário decide se já pode comunicar uma conclusão inicial. Quando é necessário ampliar a investigação, realiza I3, aguarda S1 e volta a A1. Essa é uma condição de retorno do fluxo, não uma etapa obrigatória em toda análise.

Se o tempo disponível não permitir novas consultas, o usuário pode concluir com um diagnóstico limitado aos fatos observados. O registro deve deixar claro que a origem da falha ainda não foi determinada.

## 5. Síntese e implicações para a interface

As três técnicas mostram aspectos diferentes da mesma tarefa. O HTA ajuda a separar a investigação em objetivos menores. O GOMS mostra como o SRE escolhe entre usar os resultados disponíveis e ampliar a busca. O CTT evidencia a dependência entre as escolhas do usuário, o processamento e a interpretação dos dados.

A principal dificuldade não é apenas encontrar um erro, mas relacionar os sinais dos diferentes serviços e chegar a uma explicação inicial útil. A filtragem do grafo pode reduzir a quantidade de informação, mas o usuário ainda precisa conferir os detalhes e perceber quando a hipótese não corresponde aos registros.

Para a interface proposta, considero importantes estes pontos:

- Apresentar o serviço, o período e o sintoma investigados, para evitar uma análise fora do recorte.
- Permitir entender as dependências entre os componentes e consultar seus registros sem perder o contexto.
- Mostrar as hipóteses junto das evidências utilizadas, sem tratá-las como respostas definitivas.
- Permitir ajustar o recorte e informar quando a consulta não retorna dados.
- Registrar separadamente os fatos observados, a origem provável e as dúvidas restantes.
- Facilitar o compartilhamento do diagnóstico com a equipe, respeitando as permissões de acesso aos dados.

Um teste de usabilidade possível é apresentar um incidente com uma hipótese inicial incompleta e observar se o participante identifica a lacuna, consulta os registros necessários e comunica o diagnóstico com suas limitações. Isso ajudaria a avaliar a interação, mas não comprovaria a precisão técnica do pipeline.

## Referência da reescrita

Entrega individual de Théo Zago Zimmermann: “Entrega 5 — Análise de tarefas: HTA, GOMS e CTT”, datada de 10/09/2026. O tema e o recorte foram mantidos, com reorganização das explicações e dos modelos em formato textual.
