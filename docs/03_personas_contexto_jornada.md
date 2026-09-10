# Entrega 3 — Personas, mapa de empatia, contexto de uso e jornada

**Data:** {{dd/mm/aaaa}}  
**Status:** ⬜ não iniciada  
**Responsabilidade:** 1 persona por integrante; 1 mapa de empatia, 1 contexto de uso consolidado e 1 jornada por equipe (salvo orientação diferente do docente).

## Objetivo da atividade

Representar grupos de usuários de forma útil para decisões de design. Persona não é personagem decorativo: suas características devem alterar requisitos, prioridades, linguagem, fluxos ou critérios de avaliação.

## Atenção a projetos técnicos

Em TCCs sem interface original, a persona pode representar um **profissional que se apropria da contribuição técnica**: DBA, analista, cientista de dados, administrador, pesquisador, técnico, operador, gestor ou especialista de domínio.

Não escolha um perfil apenas porque “parece combinar” com a tecnologia. Explique **qual objetivo esse perfil teria e qual parte da contribuição do TCC produziria valor para ele**. Se ainda for hipótese, mantenha como hipótese/proto-persona a validar.

Também considere papéis diferentes quando houver tarefas distintas, por exemplo:

- operador que executa análises;
- administrador que configura e gerencia permissões;
- especialista que interpreta resultados;
- gestor que consulta relatórios e decide;
- auditor que revisa histórico.

## Entradas da Entrega 1

Antes de criar personas, retome os tipos de usuários, características relevantes, objetivos e hipóteses registradas na Entrega 1. A persona **não deve transformar uma hipótese inicial em fato por meio de uma história fictícia**.

| Item da Entrega 1 | Status inicial | Evidência disponível agora | Como será tratado nesta entrega |
|---|---|---|---|
| {{usuário/objetivo/característica/H01...}} | F / H / ? | {{...}} | incorporar / manter como hipótese / descartar / investigar |

## 1. Personas

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

A P03 — Mariana complementa os perfis já produzidos pela equipe sem duplicar suas responsabilidades. O SRE permanece como persona primária e realiza a triagem e o diagnóstico inicial; o desenvolvedor sênior investiga o código e implementa a correção; a analista de QA verifica se o comportamento esperado foi restabelecido e procura regressões antes da liberação.

Por ser secundária, P03 não amplia automaticamente o recorte para um módulo completo de gestão de testes. Sua contribuição principal é orientar a continuidade do contexto entre diagnóstico, correção e verificação, além de impedir que uma hipótese do LLM ou a ausência de telemetria seja confundida com confirmação humana. As características e os comportamentos atribuídos a Mariana permanecem como hipóteses de uma proto-persona e precisam ser investigados com profissionais representativos.

## 2. Mapa de empatia — equipe

**Persona escolhida:** {{P01}}  
**Justificativa:** {{por que esse perfil é relevante}}

![Mapa de empatia](../assets/03_personas/mapa_empatia.svg)

Documente também em texto: o que vê; ouve; diz/faz; pensa/sente; dores; ganhos. Diferencie **evidência** de **hipótese**.

## 3. Contexto de uso — consolidação

| Dimensão | Descrição | Implicação de design |
|---|---|---|
| Usuários | {{...}} | {{...}} |
| Tarefas | {{...}} | {{...}} |
| Equipamentos | {{...}} | {{...}} |
| Ambiente físico | {{...}} | {{...}} |
| Ambiente social/organizacional | {{...}} | {{...}} |
| Papéis/permissões/governança | {{...}} | {{...}} |
| Volume de dados/histórico | {{...}} | {{...}} |

## 4. Jornada do usuário — equipe

**Persona:** {{P01}}  
**Objetivo da jornada:** {{...}}  
**Início e fim da jornada:** {{...}}

| Etapa | Situação/ação | Objetivo | Pensamento/emoção | Dor | Oportunidade de design | Evidência |
|---|---|---|---|---|---|---|
| 1 | {{...}} | {{...}} | {{...}} | {{...}} | {{...}} | {{...}} |

> A jornada pode incluir etapas **antes, durante e depois** do uso do produto. Não transforme a jornada em lista de telas.

## Síntese

Quais necessidades e objetivos devem obrigatoriamente aparecer nos cenários e nas tarefas seguintes?

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
