# Entrega 5 — Análise de tarefas: HTA, GOMS e CTT

**Data:** 21/10/2026  
**Status:** 🟨 em andamento  
**Responsabilidade:** 1 HTA, 1 GOMS e 1 CTT individuais, derivados do cenário [C04](../04_cenarios_problema/c04.md)

[← Voltar à navegação da Entrega 5](../05_analise_tarefas.md)

## Objetivo da atividade

Modelar tarefas importantes sob perspectivas complementares: decomposição hierárquica (HTA), estrutura de metas/métodos/operações (GOMS) e relações temporais entre tarefas (CTT). O diagrama deve ser acompanhado de interpretação textual.

> **[H] Base e limite dos modelos:** os três modelos descrevem a **prática atual** da especialista em observabilidade, conforme o cenário hipotético C04. Não foram observados em campo; ordens, alternativas, critérios e regras de seleção são hipóteses a validar (Q1–Q6 de C04). A numeração T10–T12 é provisória, para não colidir com as tarefas dos demais integrantes.

## Seleção das tarefas

| ID | Tarefa | Persona/cenário de origem | Frequência/criticidade | Autor responsável |
|---|---|---|---|---|
| T10 | Investigar a propagação de uma falha entre serviços e entregar um retorno ao SRE (HTA) | P04 / C04 | Criticidade alta (decisões do SRE dependem do retorno) [H]; frequência **PENDENTE** | João Sitta Giopatto |
| T11 | Confirmar de quais serviços o serviço afetado depende durante um incidente (GOMS) | P04 / C04 | Criticidade alta (origem do desvio no cenário) [H]; frequência **PENDENTE** | João Sitta Giopatto |
| T12 | Comunicar o retorno ao SRE e acompanhar a decisão (CTT) | P04, SRE / C04 | Criticidade alta (decisão com prazo) [H]; frequência **PENDENTE** | João Sitta Giopatto |


---

## HTA — T10 Investigar a propagação de uma falha entre serviços e entregar um retorno ao SRE

**Autor(a):** João Sitta Giopatto — 22.123.054-3

### Descrição da tarefa

**Objetivo:** fornecer ao SRE um retorno sobre quais serviços estão envolvidos em um incidente e como a falha se propagou, indicando o grau de certeza de cada parte.  
**Início:** o SRE aciona a especialista após alertas em serviços diferentes.  
**Conclusão esperada:** o retorno é comunicado, completo ou parcial, a tempo da decisão do SRE.  
**Contexto:** incidente em produção, sem deploy recente, com telemetria em ferramentas separadas e prazo de poucos minutos (C04).

### Diagrama

![Up<img width="1000" height="500" alt="hta_t10" src="https://github.com/user-attachments/assets/77c4b2ba-cafa-4768-b453-ddd0f91a1761" />


### Decomposição e planos

| ID | Objetivo/operação | Plano/ordem | Problema ou decisão de design observada [H] |
|---|---|---|---|
| 0 | Fornecer ao SRE um retorno sobre os serviços envolvidos e a propagação | 1 > 2 > 3 > 4 > 5; repetir 3–4 enquanto houver relação não verificada e prazo; esgotado o prazo, ir a 5 com retorno parcial | O prazo vem de fora; a especialista decide sozinha quando parar. |
| 1 | Entender o pedido do SRE e o prazo | 1.1 > 1.2 > 1.3 | A decisão pendente do SRE pode não ser explícita no pedido. |
| 1.1 | Ler alertas e relato do SRE | — | — |
| 1.2 | Identificar a decisão pendente e o prazo | — | Define o que um retorno parcial precisa conter. |
| 1.3 | Confirmar funcionalidade e serviços alertados | — | — |
| 2 | Delimitar serviços e período anômalos | 2.1 > 2.2 > 2.3 | — |
| 2.1 | Consultar métricas de latência e erro | — | Ferramenta própria, separada de logs e traces. |
| 2.2 | Identificar o início do desvio em cada serviço | — | Horários em formatos e precisões diferentes. |
| 2.3 | Listar serviços candidatos | — | — |
| 3 | Estabelecer relações entre serviços candidatos | 3.1 > (3.2 e 3.3, em qualquer ordem) > 3.4 se restar lacuna; repetir por serviço | Mapa possivelmente desatualizado; escolha da fonte é implícita (ver T11). |
| 3.1 | Consultar o mapa de serviços | — | Pode omitir dependências recentes. |
| 3.2 | Examinar traces de requisições com falha | — | Amostragem e serviços sem instrumentação. |
| 3.3 | Buscar menções nos logs | — | Logs sem identificador da requisição. |
| 3.4 | Consultar responsáveis pelos serviços | — | Depende da disponibilidade de outras pessoas. |
| 4 | Reconstruir a ordem de propagação | 4.1 > 4.2 > 4.3; repetir 4.2 para cada par de serviços | Parte das ligações só pode ser inferida pelo horário. |
| 4.1 | Comparar horários de início do desvio | — | — |
| 4.2 | Relacionar registros de fontes distintas | — | Correlação manual entre ferramentas. |
| 4.3 | Classificar relações: observada, inferida, não verificada | — | Não há forma fixa de registrar essa classificação. |
| 5 | Comunicar o retorno ao SRE | 5.1 > 5.2 > 5.3 | O retorno pode ser lido como mais firme do que é. |
| 5.1 | Resumir serviços afetados, ordem e origem provável | — | — |
| 5.2 | Indicar lacunas e grau de certeza | — | Sem formato comum entre quem emite e quem lê. |
| 5.3 | Enviar e esclarecer dúvidas do SRE | — | — |

**Verificação do HTA:**

- **O objetivo 0 é uma meta do usuário?** Sim
- **As subtarefas são necessárias e suficientes?** 
- **Os planos indicam ordem, alternativa, repetição e condição?** Sim: sequência (1–5), repetição (3–4 e 4.2), alternativa (3.2 e 3.3) e condição (3.4).
- **A decomposição parou em nível útil?** Não, porque não se conhecem as ferramentas usadas.
---

## GOMS — T11 Confirmar de quais serviços o serviço afetado depende durante um incidente

**Autor(a):** João Sitta Giopatto — 22.123.054-3

### Goal

`G0: Obter uma lista confiável dos serviços dos quais o serviço afetado depende, a tempo de orientar a investigação.`

### Métodos, operadores e regras de seleção

- **Method M1 — partir do mapa de serviços:**
  - Operators: abrir o mapa; localizar o serviço afetado; perceber os serviços ligados a ele; comparar com os serviços que apresentam sintomas; decidir se o mapa parece coerente.
- **Method M2 — partir dos traces de requisições com falha:**
  - Operators: abrir a ferramenta de traces; filtrar por serviço afetado, erro e janela de tempo; abrir um trace; perceber os serviços chamados e a duração de cada etapa; decidir se examina outro trace ou se já há padrão.
- **Method M3 — partir dos logs do serviço afetado:**
  - Operators: abrir os logs; buscar termos de timeout e falha de conexão; perceber o endereço ou nome do destino; associar o destino a um serviço (por conhecimento prévio).
- **Method M4 — perguntar aos responsáveis:**
  - Operators: identificar a equipe provável; enviar a pergunta; aguardar a resposta; interpretar a resposta.
- **Selection Rule SR1:** usar M1 como primeira tentativa quando o mapa existe e é considerado atual para o serviço afetado.
- **Selection Rule SR2:** usar M2 quando o mapa não é considerado atual, quando M1 não explica os sintomas ou para verificar uma relação indicada pelo mapa.
- **Selection Rule SR3:** usar M3 quando o trace mostra espera sem etapa associada ou quando há poucos traces disponíveis.
- **Selection Rule SR4:** usar M4 quando M2 e M3 não identificam o destino, ou quando o destino não é reconhecido.
- **Regra de parada [H]:** considerar a dependência confirmada quando observada em ao menos uma fonte direta (trace ou log); se apenas o mapa ou uma inferência a sustenta, registrá-la como não verificada.


---

## CTT — T12 Comunicar o retorno ao SRE e acompanhar a decisão

**Autor(a):** João Sitta Giopatto — 22.123.054-3

### Descrição

Modela as relações temporais entre a preparação do retorno pela especialista, a decisão do SRE e a continuação da investigação. O foco é a coordenação entre os dois papéis e a pressão do prazo, não o conteúdo técnico do retorno.

### Diagrama

<img width="1940" height="626" alt="ctt_t12" src="https://github.com/user-attachments/assets/9db88e58-b6bc-46fc-9c42-ffd9fdb4658a" />


### Legenda e relações temporais usadas

| Operador/relação | Significado no diagrama | Exemplo no modelo |
|---|---|---|
| `>>` habilitação | A segunda tarefa só começa quando a primeira termina | Preparar e enviar o retorno (1) `>>` acompanhar o incidente (2); classificar relações (1.1.1) `>>` redigir retorno (1.1.2) |
| `[>` desabilitação | A segunda tarefa interrompe a primeira | Enviar retorno (1.2) interrompe a consolidação (1.1) quando o prazo se esgota, resultando em retorno parcial |
| `\|[]\|` concorrência com troca de informação | Tarefas em paralelo que trocam informação | O SRE decide (2.1) enquanto a especialista continua investigando (2.2); a atualização enviada pode alterar a decisão |
| `\|\|\|` concorrência independente | Tarefas em qualquer ordem ou em paralelo, sem troca | Descrever serviços e ordem (1.1.2.1) e declarar lacunas e certeza (1.1.2.2) |
| `[]` escolha | Apenas uma das alternativas é executada | Acionar equipes, reiniciar serviço ou aguardar mais evidências (2.1.2.x) |
| `*` iteração | A tarefa se repete | Classificar cada relação (1.1.1); atualizar achados (2.2) |

**Tipos de tarefa:** abstratas (borda tracejada), de usuário (cognitivas), de interação (ferramenta de comunicação) e, em vermelho, tarefas do papel SRE.


---

## Síntese da equipe

**PENDENTE** — a síntese é coletiva e será elaborada com as modelagens dos demais integrantes. Contribuições de T10–T12 para a síntese: (a) critério para decidir se o mapa de serviços é confiável; (b) forma de separar observação, inferência e lacuna ao comunicar; (c) relação entre o prazo do SRE e a completude do retorno.


## Checklist

Verificação individual de T10–T12. Os itens coletivos estão no [índice da Entrega 5](../05_analise_tarefas.md#checklist).

- [x] Ao menos 1 HTA, 1 GOMS e 1 CTT produzidos.
- [x] Cada artefato identifica autor e tarefa.
- [x] Diagramas legíveis, com fonte editável (SVG).
- [x] HTA contém planos, não apenas árvore de tópicos.
- [x] GOMS distingue Goals, Operators, Methods e Selection Rules.
- [x] CTT usa operadores temporais e tipos de tarefa coerentes.
- [x] Há texto explicando cada diagrama.
- [ ] Tarefas ligadas a cenários/personas na matriz de rastreabilidade. **PENDENTE** (confirmar R04).
- [x] As tarefas descrevem o que a pessoa faz, não passos internos de código.
- [ ] Notação do CTT e nível do GOMS conferidos com a orientação da aula. **PENDENTE.**
