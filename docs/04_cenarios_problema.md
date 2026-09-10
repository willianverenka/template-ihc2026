# Entrega 4 — Cenários de análise/problema

**Data:** 10/09/2026  
**Status:** 🟨 em andamento  
**Responsabilidade:** 1 solução completa por integrante

## Objetivo da atividade

Descrever situações atuais em que o usuário tenta alcançar um objetivo e encontra dificuldades. Os cenários abaixo representam situações de investigação de incidentes em sistemas distribuídos, mantendo o foco no problema e no processo atual, sem antecipar a interface que será projetada.

> **Observação:** os cenários são baseados principalmente nas informações levantadas na Entrega 1. Quando detalhes específicos não foram observados diretamente pela equipe, eles são tratados como hipóteses a validar, e não como fatos.

---

# Cenário C03 — Avaliação de uma hipótese antes de encaminhar a correção

**Autor(a):** Théo Zago Zimmermann — 22.123.035-2  
**Persona(s) relacionada(s):** P01 — SRE de plantão / P02 — Desenvolvedor  
**Necessidade relacionada:** Avaliar criticamente uma explicação provável antes de comunicar ou encaminhar uma ação de correção.  
**Situação concreta da Entrega 1 relacionada:** Seções 3.1, 4.3 e 4.4 — formular diagnóstico fundamentado a partir de telemetria e conhecimento do domínio.  
**Hipóteses ainda presentes:** H03, H04

## 1. Cenário inicial

Durante uma investigação, o SRE identifica um conjunto de serviços que apresenta comportamento anormal. Os dados indicam uma possível relação entre eventos ocorridos em diferentes componentes.

O profissional precisa interpretar essas informações e construir uma explicação plausível para o incidente. Entretanto, os dados disponíveis não necessariamente determinam uma única causa.

O SRE pode considerar diferentes possibilidades e consultar os registros associados a cada uma delas. Para decidir qual hipótese deve ser comunicada à equipe de desenvolvimento, ele precisa avaliar se existem evidências suficientes para sustentá-la.

**[H] H03:** hipóteses diagnósticas acompanhadas das evidências que as sustentam podem ser mais úteis do que uma conclusão textual isolada, pois permitem ao profissional avaliar criticamente o resultado.

Uma interpretação incorreta pode fazer com que o desenvolvedor investigue ou corrija o componente errado.

## 2. Questões de refinamento

| # | Questão | Por que precisa ser respondida | Fonte/forma de obter resposta |
|---|---|---|---|
| Q1 | Que evidências fazem o SRE considerar uma hipótese confiável o suficiente para compartilhá-la? | Define critérios de confiança e comunicação. | Entrevista com SREs. |
| Q2 | O profissional costuma considerar mais de uma causa possível para o mesmo incidente? | Verifica se a atividade é de escolha entre hipóteses ou apenas confirmação. | Entrevista/observação. |
| Q3 | Como o diagnóstico inicial é comunicado ao desenvolvedor? | Identifica informações necessárias para colaboração entre papéis. | Entrevista/observação. |
| Q4 | O desenvolvedor consegue verificar as evidências apresentadas pelo SRE? | Investiga a necessidade de rastreabilidade da explicação. | Entrevista/teste contextual. |
| Q5 | Quais informações poderiam levar o profissional a rejeitar uma hipótese? | Identifica mecanismos de validação e recuperação de uma interpretação incorreta. | Entrevista/estudo de incidentes. |

## 3. Cenário refinado

O SRE identifica um conjunto de eventos relacionados ao incidente e observa que determinados componentes apresentaram comportamento anormal.

**[NOVO: Em vez de considerar automaticamente o primeiro componente que apresenta erro como a origem do incidente, o profissional compara a ordem temporal e as relações entre os componentes envolvidos.]**

Ele formula uma ou mais explicações possíveis e verifica se os traces, logs e métricas disponíveis sustentam essas explicações.

**[NOVO: Uma hipótese é considerada mais útil quando o profissional consegue relacioná-la a evidências observáveis e explicar por que determinado componente é considerado provável origem ou parte relevante da propagação.]**

Quando a evidência é insuficiente ou contraditória, **[NOVO: o SRE pode precisar ampliar a investigação, consultar outro profissional ou revisar a hipótese inicial.]**

Depois de chegar a uma interpretação que considera suficientemente fundamentada, ele comunica o diagnóstico inicial ao desenvolvedor responsável, incluindo as evidências utilizadas na análise.

## 4. Elementos extraídos

| Elemento | Evidência no cenário |
|---|---|
| **Ator(es)** | SRE de plantão e desenvolvedor responsável. |
| **Objetivo(s)** | Avaliar hipóteses e comunicar um diagnóstico inicial fundamentado. |
| **Contexto** | Incidente com múltiplos componentes e possibilidade de diferentes causas. |
| **Recursos/informações** | Traces, logs, métricas, relações temporais e estruturais entre serviços. |
| **Ações** | Comparar eventos, formular hipóteses, verificar evidências, rejeitar/aceitar interpretações e comunicar diagnóstico. |
| **Problemas/rupturas** | Dados podem ser insuficientes ou ambíguos; uma hipótese pode ser confundida com certeza. |
| **Consequências** | Encaminhamento incorreto, investigação desnecessária e correção do componente errado. |

## 5. Implicações para as próximas entregas

- Investigar como profissionais avaliam a confiabilidade de um diagnóstico.
- Investigar como evidências devem ser associadas a uma hipótese.
- Modelar a tarefa de **formular, verificar e comunicar um diagnóstico inicial**.
- Considerar a necessidade de diferenciar hipótese de certeza.
- Investigar mecanismos de revisão quando novas evidências contradizem a interpretação inicial.



## Checklist

- [ ] Há um cenário completo por integrante.
- [ ] Cada cenário tem título, ator, objetivo, contexto e problema.
- [ ] O cenário possui origem rastreável na Entrega 1 ou justifica claramente a inclusão de uma nova situação.
- [ ] O texto descreve a situação atual, sem antecipar a solução.
- [ ] Para TCC sem interface original, o cenário descreve uma prática humana plausível relacionada à contribuição técnica, e não “a falta de uma tela”.
- [ ] Questões de refinamento acrescentam informação nova.
- [ ] O refinamento mostra claramente o que foi adicionado/alterado.
- [ ] Cenários são diferentes o suficiente para cobrir objetivos/problemas relevantes.
- [ ] Cada cenário está ligado a persona/necessidade na matriz de rastreabilidade.
