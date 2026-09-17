# Projeto de Interação Humano-Computador (IHC)

Documentação acadêmica da **Equipe 11**, dedicada ao projeto de uma interface de apoio ao diagnóstico de falhas em sistemas distribuídos. O entendimento inicial do problema, dos usuários e do escopo está registrado na [Entrega 1](docs/01_conhecendo_o_problema.md).

## Princípio do projeto da disciplina

[F] O TCC da equipe prevê a construção e a avaliação técnica de um pipeline de diagnóstico, isto é, uma sequência de etapas de processamento. A interação está parcialmente prevista, mas uma interface completa orientada a um produto ainda não está definida. Na disciplina, o recorte escolhido é a investigação de um incidente por um profissional de confiabilidade de sistemas, o **Site Reliability Engineer (SRE)**. Essas definições constam das seções 0.4, 0.5 e 7 da [Entrega 1](docs/01_conhecendo_o_problema.md).

A interface de IHC aprofunda essa interação parcialmente prevista. Sua implementação no TCC permanece **não definida** e depende de decisão da equipe e do orientador, conforme o [Guia de escopo de IHC](GUIA_ESCOPO_IHC.md).

## Identificação

**Título do projeto de IHC:** EQUIPE 11

**TCC/projeto de origem:** Diagnóstico de falhas em sistemas distribuídos por pipeline em dois estágios: filtragem estrutural em grafos de observabilidade e geração de hipóteses com LLMs

**Orientador(a):** Leonardo Anjoletto Ferreira

**Disciplina:** Interação Humano-Computador

**Instituição:** FEI

**Semestre:** 2026/8

### Equipe

| Nome completo | Matrícula | GitHub | Responsabilidade principal |
|---|---:|---|---|
| Willian Verenka Oliveira Silva | 22.124.081-5 | [@willianverenka](https://github.com/willianverenka) | PENDENTE |
| Gabriel Lovato | 22.123.004-8 | [@gabriellovato7](https://github.com/gabriellovato7) | PENDENTE |
| Théo Zago Zimmermann | 22.123.035-2 | [@theozago](https://github.com/theozago) | PENDENTE |
| João Vitor Sitta | 22.123.054-3 | [@JVSittaG](https://github.com/JVSittaG) | PENDENTE |

Fonte: seção 0.1 da [Entrega 1](docs/01_conhecendo_o_problema.md). [?] A divisão de responsabilidades principais não está registrada nessa entrega; cada integrante deve cumprir as contribuições individuais e participar das consolidações indicadas na tabela de entregas abaixo.

## Relação entre TCC e projeto de IHC

| Item | Descrição |
|---|---|
| Tema central do TCC | Diagnóstico de falhas em sistemas distribuídos por filtragem estrutural de grafos de observabilidade e geração de hipóteses diagnósticas. |
| Resultado técnico esperado do TCC | Infraestrutura/backend: construção e avaliação experimental de um pipeline em dois estágios, que seleciona evidências por filtragem de grafos e utiliza um modelo de linguagem de grande porte (LLM) para gerar hipóteses sobre a origem da falha. |
| O TCC já previa interface? | Parcialmente. Estão previstos mecanismos para fornecer dados de observabilidade e consultar resultados, mas não uma interface completa de produto. |
| Capacidade técnica que pode gerar valor para pessoas | Reduzir o espaço de busca na telemetria e apresentar hipóteses apoiadas nas evidências selecionadas. [H] Isso pode reduzir o esforço de investigação; o benefício para o usuário ainda precisa ser verificado. |
| Usuário principal adotado em IHC | SRE de plantão, definido como perfil prioritário pela equipe. |
| Objetivo principal desse usuário | Formular e comunicar um diagnóstico inicial fundamentado sobre a provável origem e o impacto de um incidente. |
| Interface/recorte explorado na disciplina | Investigar um único incidente: delimitar serviço, período e sintomas; acompanhar o processamento; inspecionar o subgrafo e os componentes afetados; examinar hipóteses e evidências; comunicar o diagnóstico inicial. |
| Relação com o escopo formal do TCC | Aprofundamento de uma interação parcialmente prevista. O compromisso formal é construir e avaliar o pipeline; a incorporação da interface da disciplina ao TCC depende de decisão posterior da equipe e do orientador. |

Fonte: seções 0.4–0.5, 1.3–1.5, 7, 9.2 e 11 da [Entrega 1](docs/01_conhecendo_o_problema.md). As definições de escopo são decisões da equipe; os benefícios esperados permanecem hipóteses.

> **Importante:** a tabela acima explica a relação entre os dois trabalhos. Ela não altera o compromisso formal do TCC.

## Resumo do projeto pela perspectiva do usuário

[F] No recorte definido pela equipe, um SRE de plantão precisa formular e comunicar um diagnóstico inicial após um alerta ou implantação. A Entrega 1 registra a consulta a plataformas de observabilidade e a filtragem manual de registros de eventos (logs), métricas e rastros de execução entre serviços (traces) como referências do processo atual. [H] Localizar evidências relevantes e compreender a propagação da falha pode exigir esforço elevado, sob pressão de tempo e em colaboração com desenvolvedores e gestores. O TCC investiga a filtragem estrutural dessas evidências e a geração de hipóteses diagnósticas; a interface de IHC permitirá examinar o subgrafo selecionado, consultar os dados associados e avaliar a explicação antes de comunicar o diagnóstico. Fonte: seções 4, 5.4, 6.1 e 7 da [Entrega 1](docs/01_conhecendo_o_problema.md).

As hipóteses H01 e H03 tratam da utilidade da visualização das dependências e da apresentação de hipóteses acompanhadas de evidências; H02 registra a dúvida sobre a quantidade inicial de detalhes, e H04 trata da colaboração e das restrições de acesso. Esses pontos seguem sujeitos a investigação.

## Por que pensar em interface mesmo em TCCs técnicos?

Neste projeto, a contribuição técnica produz evidências selecionadas e hipóteses que precisam ser interpretadas por uma pessoa. As ações priorizadas na seção 9.2 da [Entrega 1](docs/01_conhecendo_o_problema.md) orientam o protótipo:

- **F01 — Delimitar o incidente:** restringir serviço, sintoma e período para definir o conjunto de evidências.
- **F02 — Inspecionar o subgrafo:** compreender os componentes afetados e a possível propagação da falha.
- **F03 — Examinar hipóteses e evidências:** formular um diagnóstico inicial fundamentado.

O treinamento de redes neurais em grafos (GNNs), a construção dos grafos e a definição dos algoritmos de filtragem ficam fora do recorte de IHC. A construção e a avaliação experimental desses mecanismos pertencem ao escopo técnico do TCC, conforme a delimitação da seção 11 da Entrega 1.

## Relação com apresentação e potencial de aplicação

[F] A motivação relatada por integrantes da equipe é o tempo gasto procurando manualmente registros relevantes para diagnosticar falhas. O TCC investiga um pipeline que seleciona evidências e gera hipóteses diagnósticas. [H] A interface pode demonstrar, inclusive na **INOVA**, como um SRE utilizaria esse resultado para investigar e comunicar um incidente com menor esforço. Essa redução de esforço é um benefício esperado, ainda sujeito a avaliação com usuários. Fonte: seções 1.2–1.5, 7 e 9.1 da [Entrega 1](docs/01_conhecendo_o_problema.md).

## Como usar este repositório

1. Leia o [Guia de uso e apresentação](GUIA_DE_USO.md).
2. Leia o [Guia de definição de escopo de IHC](GUIA_ESCOPO_IHC.md), especialmente se o TCC não previa interface.
3. Preencha as entregas na ordem em que forem trabalhadas na disciplina.
4. Em toda entrega individual, **identifique o autor**.
5. Salve imagens, diagramas e evidências em [`assets/`](assets/README.md).
6. Mantenha a [Matriz de rastreabilidade](RASTREABILIDADE.md) atualizada.
7. Na Entrega 1, diferencie **[F] fatos**, **[H] hipóteses** e **[?] lacunas de conhecimento**.
8. Antes de cada entrega, revise o checklist do arquivo e o [Checklist final](CHECKLIST_FINAL.md).
9. Sempre que uma evidência posterior contrariar uma hipótese inicial, **revise o projeto**. IHC é um processo iterativo.

## Entregas

| # | Entrega | Quantidade mínima / responsabilidade | Status |
|---:|---|---|---|
| 1 | [Conhecendo o projeto, o usuário e o problema](docs/01_conhecendo_o_problema.md) | 1 solução consolidada por equipe | 🟩 |
| 2 | [Público-alvo e análise de concorrência](docs/02_analise_concorrencia.md) | no mínimo 1 concorrente/interface representativa por integrante + síntese | 🟩 |
| 3 | [Personas, empatia, contexto e jornada](docs/03_personas_contexto_jornada.md) | 1 persona por integrante; demais artefatos consolidados | 🟩 |
| 4 | [Cenários de análise/problema](docs/04_cenarios_problema.md) | 1 solução completa por integrante | 🟨 |
| 5 | [Análise de tarefas: HTA, GOMS e CTT](docs/05_analise_tarefas.md) | cada integrante: pelo menos 1 HTA + 1 GOMS + 1 CTT | ⬜ |
| 6 | [Prototipação em papel](docs/06_prototipacao_papel.md) | 1 protótipo integrado por equipe | ⬜ |
| 7 | [Coleta de dados e aspectos éticos](docs/07_coleta_dados.md) | soluções individuais + técnicas distintas; questionário entre as técnicas | ⬜ |
| 8 | [Ciclo de vida e engenharia de usabilidade](docs/08_engenharia_usabilidade.md) | 1 solução consolidada por equipe | ⬜ |
| 9 | [Modelo conceitual e design centrado na comunicação](docs/09_modelo_conceitual.md) | soluções individuais + consolidação de objetivos/signos | ⬜ |
| 10 | [MoLIC](docs/10_molic.md) | 1 diagrama completo por integrante | ⬜ |
| 11 | [Protótipo no Figma](docs/11_figma.md) | 1 protótipo integrado por equipe, cobrindo fluxos modelados | ⬜ |
| 12 | [Planejamento da avaliação — DECIDE](docs/12_planejamento_avaliacao.md) | 1 plano consolidado por equipe | ⬜ |
| 13 | [Avaliação heurística](docs/13_avaliacao_heuristica.md) | 1 avaliação completa por integrante, todas as telas/estados e 10 heurísticas | ⬜ |
| 14 | [Avaliação por observação de usuários](docs/14_observacao_usuario.md) | avaliação consolidada; nº de participantes finais = nº de integrantes | ⬜ |

> Se o docente definir quantidade diferente para a turma/semestre, a orientação da disciplina prevalece.

## Visão de continuidade

O projeto deve formar uma cadeia de evidências:

**tema/contribuição do TCC → possível aplicação → usuários/stakeholders → objetivos → problema/contexto → alternativas → necessidades → personas → cenários → tarefas → modelo conceitual → MoLIC → protótipo → planejamento → inspeção → teste com usuários → melhorias**.

## Documentos de apoio

- [Guia de uso e apresentação](GUIA_DE_USO.md)
- [Guia para definir o escopo de IHC a partir do TCC](GUIA_ESCOPO_IHC.md)
- [Matriz de rastreabilidade](RASTREABILIDADE.md)
- [Checklist final](CHECKLIST_FINAL.md)
- [Bibliografia de IHC](BIBLIOGRAFIA.md)
- [Orientações de contribuição no GitHub](CONTRIBUTING.md)
- [Instrumentos reutilizáveis](instrumentos/README.md)
