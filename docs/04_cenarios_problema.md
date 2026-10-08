# Entrega 4 — Cenários de análise/problema

**Data:** 10/09/2026  
**Status:** 🟨 em andamento  
**Responsabilidade:** 1 solução completa por integrante

## Objetivo da atividade

Descrever situações atuais em que o usuário tenta alcançar um objetivo e encontra dificuldades. Os cenários representam situações de investigação de incidentes em sistemas distribuídos, mantendo o foco no problema e no processo atual, sem antecipar a interface que será projetada.

---

# Cenário C03 — Dificuldade em distinguir a causa de um incidente de seus efeitos

**Autor(a):** Théo Zago Zimmermann — 22.123.035-2  
**Persona(s) relacionada(s):** P01 — SRE de plantão / P02 — Desenvolvedor  
**Necessidade relacionada:** Avaliar criticamente uma explicação provável antes de comunicar ou encaminhar uma ação de correção.  
**Situação concreta da Entrega 1 relacionada:** Seções 3.1, 4.3 e 4.4 — formular diagnóstico fundamentado a partir de telemetria e conhecimento do domínio.  
**Hipóteses ainda presentes:** H03, H04

## 1. Cenário inicial

Durante um incidente em um sistema distribuído, usuários começam a perceber lentidão e falhas em uma funcionalidade que depende de vários serviços. O SRE de plantão é acionado para identificar a origem do problema e orientar a equipe de desenvolvimento.

Os primeiros registros disponíveis mostram erros em um serviço responsável por atender às requisições da funcionalidade. À primeira vista, esse componente parece ser o principal suspeito. Entretanto, os registros de outros serviços indicam que um serviço de dependência já apresentava aumento de latência antes de os erros se intensificarem no componente inicialmente identificado.

O SRE tenta determinar se o primeiro serviço está provocando as falhas ou se está apenas apresentando os efeitos de um problema iniciado em sua dependência. Os sinais disponíveis permitem sustentar as duas interpretações: os erros se concentram no primeiro serviço, mas a alteração temporal observada no serviço dependente sugere uma possível origem diferente.

**[H] H03:** hipóteses diagnósticas acompanhadas das evidências que as sustentam podem ser mais úteis do que uma conclusão textual isolada, pois permitem ao profissional avaliar criticamente o resultado.

O SRE não consegue estabelecer, com os dados reunidos até aquele momento, qual interpretação explica melhor o incidente. Enquanto isso, a equipe de desenvolvimento aguarda uma indicação de onde concentrar a investigação. Encaminhar o problema ao responsável pelo primeiro serviço pode acelerar uma correção local, mas também pode levar a equipe a atuar em um componente que apenas manifesta as consequências da falha.


## 2. Questões de refinamento

| # | Questão | Por que precisa ser respondida | Fonte/forma de obter resposta |
|---|---|---|---|
| Q1 | Que evidências fazem o SRE considerar uma hipótese confiável o suficiente para compartilhá-la? | Define critérios de confiança e comunicação. | Entrevista com SREs. |
| Q2 | O profissional costuma considerar mais de uma causa possível para o mesmo incidente? | Verifica se a atividade envolve hipóteses concorrentes ou apenas confirmação de uma causa presumida. | Entrevista/observação. |
| Q3 | Como o diagnóstico inicial é comunicado ao desenvolvedor? | Identifica as informações necessárias para a colaboração entre os papéis. | Entrevista/observação. |
| Q4 | O desenvolvedor consegue verificar as evidências apresentadas pelo SRE? | Investiga a necessidade de rastreabilidade da explicação. | Entrevista/teste contextual. |
| Q5 | Quais informações poderiam levar o profissional a rejeitar uma hipótese? | Identifica como interpretações iniciais são questionadas diante de evidências contrárias. | Entrevista/estudo de incidentes. |

## 3. Cenário refinado

Durante o incidente, usuários continuam enfrentando lentidão e falhas na funcionalidade afetada. O SRE de plantão precisa indicar à equipe de desenvolvimento qual componente deve ser investigado primeiro, mas os sinais disponíveis apontam para explicações diferentes.

O serviço que recebe as requisições apresenta a maior concentração de erros, o que sugere que ele possa ser a origem do problema. Porém, os registros temporais mostram que uma dependência começou a apresentar latência elevada antes do aumento das falhas no serviço que recebe as requisições. O SRE considera a possibilidade de que o primeiro componente esteja apenas acumulando os efeitos do atraso na dependência, mas ainda não consegue confirmar essa relação.

Ao tentar justificar uma das interpretações para o desenvolvedor, o profissional percebe que os registros disponíveis mostram o que aconteceu em cada componente, mas não esclarecem suficientemente qual evento desencadeou a sequência de falhas. A concentração dos erros em um serviço favorece uma explicação; a ordem temporal dos eventos favorece outra. Nenhum dos sinais, isoladamente, resolve a divergência.

O desenvolvedor precisa dessa indicação para decidir onde concentrar os esforços de investigação e se deve priorizar uma correção local ou procurar um problema na dependência. Sem uma explicação suficientemente sustentada, o SRE hesita em recomendar uma ação específica. Se indicar o componente errado, a equipe poderá gastar tempo analisando uma consequência em vez da causa, prolongando o incidente e a indisponibilidade ou degradação percebida pelos usuários.

A dificuldade central não é simplesmente reunir ou consultar os registros, mas determinar o que eles permitem concluir diante de sinais que admitem interpretações concorrentes. O SRE precisa comunicar o que já é conhecido sem apresentar uma hipótese como se fosse uma causa confirmada, enquanto a equipe aguarda uma orientação para prosseguir.

## 4. Elementos extraídos

| Elemento | Evidência no cenário |
|---|---|
| **Ator(es)** | SRE de plantão e desenvolvedor responsável. |
| **Objetivo(s)** | Identificar uma explicação plausível para o incidente e orientar a investigação do componente mais relevante. |
| **Contexto** | Incidente que afeta uma funcionalidade utilizada por usuários e envolve serviços dependentes entre si. |
| **Recursos/informações** | Traces, logs, métricas, registros temporais e relações entre serviços. |
| **Ações** | Interpretar sinais, comparar explicações possíveis e comunicar o grau de sustentação do diagnóstico. |
| **Problemas/rupturas** | O componente com mais erros pode não ser a origem; a ordem dos eventos sugere outra causa, mas as evidências não confirmam a relação. |
| **Decisão bloqueada** | Determinar qual componente deve ser investigado primeiro e se a equipe deve priorizar uma correção local ou aprofundar a investigação de uma dependência. |
| **Consequências** | Possível investigação do componente errado, desperdício de esforço, atraso na correção e prolongamento do impacto para os usuários. |

## 5. Implicações para as próximas entregas

- Investigar como profissionais distinguem a origem de um incidente dos componentes que apresentam seus efeitos.
- Identificar quais evidências ajudam a avaliar explicações concorrentes quando os sinais parecem contraditórios.
- Modelar a tarefa de avaliar uma hipótese diagnóstica e comunicar suas limitações antes de recomendar uma ação.
- Considerar como expressar a diferença entre uma hipótese plausível e uma causa confirmada.
- Investigar como o profissional procede quando as evidências disponíveis não permitem desbloquear uma decisão.

## Checklist

- [ ] Há um cenário completo por integrante.
- [ ] Cada cenário tem título, ator, objetivo, contexto e problema.
- [ ] O cenário possui origem rastreável na Entrega 1 ou justifica claramente a inclusão de uma nova situação.
- [ ] O texto descreve a situação atual, sem antecipar a solução.
- [ ] Para TCC sem interface original, o cenário descreve uma prática humana plausível relacionada à contribuição técnica, e não a falta de uma tela.
- [ ] Questões de refinamento acrescentam informação nova.
- [ ] O refinamento mostra claramente o que foi adicionado ou alterado.
- [ ] Cenários são diferentes o suficiente para cobrir objetivos e problemas relevantes.
- [ ] Cada cenário está ligado a persona/necessidade na matriz de rastreabilidade.
