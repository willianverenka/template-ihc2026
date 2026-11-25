# Entrega 10 — MoLIC

[← Início do projeto](../README.md) · [Entrega 9 — Modelo conceitual](09_modelo_conceitual.md) · [Entrega 11 — Protótipo no Figma](11_figma.md)

**Data:** 17/11/2026

**Status:** 🟩 concluída

**Responsabilidade:** 1 solução completa por integrante

## Objetivo e entradas

Modelar a interação como uma **conversa entre usuário e preposto do designer**, oferecendo visão global dos caminhos que permitem ao usuário atingir seus objetivos — incluindo alternativas e rupturas relevantes. MoLIC não deve ser reduzida a um fluxograma de telas.

A **MoLIC** (*Modeling Language for Interaction as Conversation*) é uma linguagem para a modelagem da interação humano-computador como uma conversa. O diagrama parte dos objetivos do usuário: cada tópico de conversa é uma **cena**, as decisões do sistema sobre o rumo da conversa são **processos**, e as **falas de transição** do usuário e do preposto ligam esses elementos. As **falas de recuperação de ruptura** mostram como a pessoa sai de um problema na comunicação com o preposto. Os elementos estão descritos na [legenda da notação](#legenda-da-notação).

Os diagramas modelam a conversa de que uma pessoa precisa para usar os resultados do pipeline do TCC (delimitar o incidente, acompanhar a análise, inspecionar o subgrafo, examinar hipóteses e evidências, registrar e enviar o resultado), e não o funcionamento interno do pipeline: os dois estágios aparecem apenas pelo signo estado do estágio, e o subgrafo e as hipóteses diagnósticas, como resultados que a pessoa confere.

As entradas são os cenários de interação CI01–CI04, o [mapa de objetivos](09_modelo_conceitual.md#3-mapa-de-objetivos) e o [esquema conceitual de signos](09_modelo_conceitual.md#4-esquema-conceitual-de-signos) da [Entrega 9](09_modelo_conceitual.md); as tarefas T01–T06 da [Entrega 5](05_analise_tarefas.md); e, da [Entrega 8](08_engenharia_usabilidade.md), as características da plataforma e as rupturas que o MoLIC precisa representar, falha de consulta e falha de disponibilização. Os vínculos estão nas linhas R01–R04 da [matriz de rastreabilidade](../RASTREABILIDADE.md#3-rastreabilidade-entre-contribuição-técnica-necessidades-e-artefatos).

## Soluções individuais

Cada integrante produziu o diagrama MoLIC do seu cenário de interação, com a leitura do caminho principal e das alternativas e rupturas, em arquivo próprio na pasta [`10_molic/`](10_molic/). Os diagramas estão em [`assets/10_molic/`](../assets/10_molic/), e cada SVG é também a fonte editável.

| MoLIC | Título | Autor(a) | Origem | Status | Entrega completa |
|---|---|---|---|---|---|
| M01 | Avaliação da hipótese sobre a falha no checkout após um deploy | Gabriel Lovato — 22.123.004-8 | CI01 · P02 · T01 | 🟩 concluída | [Abrir M01](10_molic/m01.md) |
| M02 | Parecer sobre a verificação de uma correção incerta | Willian Verenka Oliveira Silva — 22.124.081-5 | CI02 · P03 · T02 | 🟩 concluída | [Abrir M02](10_molic/m02.md) |
| M03 | Diagnóstico inicial com hipóteses concorrentes | Théo Zago Zimmermann — 22.123.035-2 | CI03 · P01 · T03 | 🟩 concluída | [Abrir M03](10_molic/m03.md) |
| M04 | Retorno ao SRE sobre a propagação de uma falha entre microsserviços | João Sitta Giopatto — 22.123.054-3 | CI04 · P04 · T04–T06 | 🟩 concluída | [Abrir M04](10_molic/m04.md) |

## Legenda da notação

Os diagramas usam a notação MoLIC apresentada na disciplina. Cada elemento:

- **Ponto de abertura** (círculo preto): início da conversa. A fala de abertura traz `gco:` (abertura de conversa relacionada à meta) com a meta O01, investigar um incidente e comunicar o resultado.
- **Cena** (retângulo de cantos arredondados): momento da conversa sobre um tópico. Nas cenas de objetivo, o tópico, no compartimento superior, é o objetivo da Entrega 9 com seu ID. Embaixo ficam os diálogos, com o nome do subtópico da Entrega 9 e, entre chaves, os signos do esquema da Entrega 9 e quem os emite: `d:` o preposto do designer, `u:` o usuário, `d+u:` o preposto apresenta e o usuário informa ou altera. Signos fora de chaves são ditos na cena, sem diálogo próprio. `*` marca signo obrigatório; `(default=…)`, o valor padrão; `lista(…)`, uma coleção; `(precond: …)` em itálico, diálogo que só ocorre sob a condição; texto entre aspas, mensagem do preposto.
- **Cena de alerta ou de recuperação apoiada** (borda tracejada, como a cena de alerta ou captura de erro dos slides): o preposto pede uma decisão antes de uma ação de risco (`confirmar os destinatários`, `confirmar o ajuste do recorte`, `confirmar a conclusão do parecer`) ou, depois de uma fala `[RA]`, descreve uma falha e oferece retomar a conversa (`repetir a consulta`, `repetir o envio`).
- **Processo do sistema** (quadrado preto): o sistema decide o rumo da conversa a partir do que o usuário disse; as saídas são falas do preposto.
- **Fala de transição** (seta contínua): `u:` fala do usuário que muda de tópico; `d:` fala do preposto depois de um processo. `precond:` indica a condição para a fala.
- **Fala de recuperação de ruptura** (seta tracejada): fala do preposto que comunica uma ruptura ou fala do usuário que sai dela (cancelar, alterar, repetir). A etiqueta antes de `d:` indica a estratégia, com as siglas da Entrega 9: `[AL]` prevenção apoiada (alerta), `[RA]` recuperação apoiada, `[CE]` captura de erro. A captura de erro aparece só em `[CE] d: acesso restrito`, que devolve a conversa à cena de origem, sem cena própria, pois a recuperação ocorre fora do sistema. Nos exemplos dos slides de MoLIC, as etiquetas `[SP]` e `[SR]` ocupam a posição de `[AL]` e `[RA]`. Prevenções passiva e ativa ficam nos signos; a ativa aparece no diagrama como precondição da fala.
- **Faixa de andamento** (barra de contorno espesso, com a fala do preposto dentro) entre um processo e uma cena: o preposto informa o andamento enquanto o processo continua (a análise, por estágio), e o usuário pode cancelar.
- **Acesso ubíquo** (retângulo cinza): mudança de tópico possível em qualquer momento da investigação. Aparece repetido junto de cada cena a que leva. Também recebe a fala de envio disponível, que devolve a pessoa à investigação.
- **Barra preta e ponto de encerramento** (círculo com anel): depois do envio disponível, um ramo leva `gcc:` (fechamento da conversa relacionada à meta O01) ao encerramento; o outro devolve a conversa ao acesso ubíquo. `u: sair` leva ao encerramento sem `gcc`: a conversa termina sem a meta, e o rascunho fica preservado.
- O pequeno ponto preto marca de onde a fala sai de uma cena ou de um acesso ubíquo.

Os diagramas usam só signos e valores definidos no esquema da Entrega 9; os valores do incidente de cada cenário aparecem na leitura de cada diagrama. Os acessos ubíquos são cinco: sair (M01–M04); registrar o resultado (M01–M04), porque o rascunho pode ser começado e retomado a qualquer momento; subgrafo (M01, M03, M04), que permanece na tela ao lado de hipóteses e evidências, conforme a Entrega 8; hipóteses e evidências (M02), que tem esse papel no diagrama sem a cena do subgrafo; e ajustar o recorte (M03, M04), sempre visível (MU04) e com confirmação depois de uma análise. Em M03 e M04, que começam pela delimitação, os acessos ao subgrafo, ao ajuste do recorte e ao registro do resultado exigem `precond: subgrafo disponível`, pois antes da primeira análise não há subgrafo nem evidências para preencher o registro.

## Checklist específico de modelagem

- [x] Existe **ponto de abertura** coerente com o início do objetivo.
- [x] As **cenas de conversa** representam tópicos/assuntos, não nomes de páginas apenas.
- [x] As transições/falas deixam claro o que o usuário ou o sistema comunica.
- [x] Há **ponto(s) de encerramento** para objetivos concluídos/abandonados quando aplicável.
- [x] Processamentos do sistema estão representados conforme a notação adotada em aula, sem “inventar” fala do usuário.
- [x] Rupturas (breakdowns) relevantes têm feedback e caminho de recuperação, não becos sem saída.
- [x] Acessos ubíquos/atalhos só aparecem quando semanticamente justificáveis.
- [x] O diagrama cobre caminhos alternativos importantes, e não apenas o “happy path”.
- [x] Nomes de objetivos, tópicos e signos são coerentes com a Entrega 9.
- [x] O diagrama é legível em tamanho normal no GitHub.
- [x] O MoLIC representa a conversa usuário–sistema, não o fluxo interno do algoritmo.
- [x] Processamento, filtros, administração, relatórios e históricos incluem retornos/rupturas quando relevantes.

## Consolidação da equipe

### Cobertura dos objetivos

Para que objetivos semelhantes tenham a mesma solução de interação, os quatro diagramas usam a mesma notação, o mesmo estilo e o mesmo texto nas cenas, diálogos e falas que se repetem: a abertura pelo link do resultado (M01, M02) ou pelo alerta de origem (M03, M04), a análise e o ajuste do recorte (M03, M04), a passagem do subgrafo às hipóteses (M01, M03, M04), a consulta às evidências, os acessos ubíquos e o envio (M01–M04).

| Objetivo | MoLIC que cobre | Lacunas/duplicidades | Decisão |
|---|---|---|---|
| O01 investigar um incidente e comunicar o resultado | M01, M02, M03, M04 | Objetivo geral do mapa, sem cena própria. | Meta da abertura (`gco`) e do fechamento (`gcc`) nos quatro diagramas; `u: sair` encerra a conversa sem `gcc`. |
| O02 delimitar o incidente | M03, M04 | Mesma cena nos dois diagramas: em M03 o recorte proposto é confirmado e ajustado depois da primeira análise; em M04, ajustado antes dela. | Cena com o mesmo texto; o ajuste depois de uma análise passa pela cena de alerta `confirmar o ajuste do recorte`, igual nos dois. |
| O03 acompanhar a análise | M03, M04 | Mesma cena nos dois diagramas; o diálogo `acompanhar os estágios` também aparece em `inspecionar o subgrafo (O05)`. | Faixa de andamento, `u: cancelar a análise` e `[RA] d: falha no estágio e causa` iguais. O diálogo se repete no subgrafo porque a geração de hipóteses continua depois que o subgrafo fica disponível. |
| O04 recuperar o contexto do incidente | M01, M02 | Mesma cena nos dois diagramas, com falas diferentes para chegar a O08: `u: examinar a hipótese em foco` (M01) e `u: examinar as evidências citadas` (M02). | Entrada pelo link do resultado com os mesmos diálogos; as duas falas são mantidas, e a cena oferece as duas no protótipo. |
| O05 inspecionar o subgrafo | M01, M03, M04 | Os diálogos variam conforme o cenário: `acompanhar os estágios` só onde há análise (M03, M04) e `mostrar componentes fora do subgrafo` só em M04. | Diálogos repetidos com o mesmo texto; acesso ubíquo `u: subgrafo` com `precond: subgrafo disponível`; consulta às evidências com as mesmas três saídas (`d: com dados ou sem dados`, `[CE] d: acesso restrito` e `[RA] d: falha de consulta e causa`). |
| O06 confirmar as dependências do serviço afetado | M04 | Nenhuma. | Cena alcançada a partir do subgrafo por `u: dependências do serviço afetado`. |
| O07 reconstruir a ordem de propagação | M04 | Ocorre durante o registro do retorno. | Cena alcançada a partir de `registrar o retorno ao SRE (O15)` por `u: ordenar os componentes envolvidos`; `u: manter a ordem de propagação` devolve a conversa a O15. |
| O08 examinar hipóteses e evidências | M01, M02, M03, M04 | Os diálogos variam conforme o cenário: `conferir as evidências associadas` em M01, M02 e M03; `identificar as lacunas` em M02, M03 e M04; e, só em M02, os signos evidências citadas, ambiente e conteúdo. Em M02, a consulta às evidências parte desta cena, e não do subgrafo, porque CI02 não usa componente em foco. | Mesma cena, com o mesmo texto nos diálogos repetidos; em M01, M03 e M04, `u: examinar as hipóteses` leva do subgrafo à cena com `precond: hipóteses diagnósticas geradas`, cumprida em M01 desde a abertura; em M02, a consulta tem as mesmas saídas e é chamada por `u: consultar as evidências associadas`, e o acesso ubíquo `u: hipóteses e evidências` devolve a conversa à cena a partir de qualquer outra. |
| O09 comparar hipóteses concorrentes | M03 | Nenhuma. | Cena com retorno a O08 por `u: identificar as lacunas`. |
| O10 avaliar o alcance da verificação | M02 | Nenhuma. | Cena com o processo da verificação, que devolve `[RA]` para referência do teste ou versão verificada vazia; alcançada de O08 por `u: avaliar o teste da correção`; depois de aberto o registro, o acesso ubíquo `u: hipóteses e evidências` leva de volta a O08 e, de lá, a O10. |
| O11 registrar e comunicar o resultado | M01, M02, M03, M04, por O12–O16 | Objetivo de agrupamento, sem cena própria. | Coberto pelas cenas de registro, alcançadas pelo acesso ubíquo `u: registrar …` em qualquer momento da investigação (em M03 e M04, com `precond: subgrafo disponível`), e pelo envio. |
| O12 registrar o diagnóstico inicial | M03 | Nenhuma. | Núcleo de `informar o conteúdo do resultado` igual nos quatro registros, com `*` conforme as restrições de cada tipo de resultado. |
| O13 registrar a avaliação da hipótese | M01 | Nenhuma. | Mesmo núcleo, com o diálogo `classificar a hipótese`. |
| O14 registrar o parecer sobre a verificação da correção | M02 | Nenhuma. | Mesmo núcleo, com o processo da conclusão do parecer e a cena de alerta `confirmar a conclusão do parecer`. |
| O15 registrar o retorno ao SRE | M04 | Nenhuma. | Mesmo núcleo, com retorno parcial seguido de atualização. |
| O16 enviar o resultado aos destinatários | M01, M02, M03, M04 | Mesmo fragmento nos quatro diagramas. | `confirmar os destinatários` (alerta) e `repetir o envio` (recuperação apoiada) iguais, com `precond: campos obrigatórios preenchidos` na fala que leva ao envio. |

Nenhum objetivo ficou sem diagrama. A falha de consulta e a falha de disponibilização, exigidas pela Entrega 8, estão nos quatro diagramas, assim como o acesso restrito, com captura de erro (narrado em M02), e a consulta sem dados (narrada em M04). A falha em um estágio, a geração sem nenhuma hipótese e o cancelamento da análise estão em M03 e M04, e o campo vazio na verificação da correção, em M02. Há alertas para o ajuste do recorte (M03, M04), para os destinatários (M01–M04) e para a conclusão do parecer (M02).

Quanto aos padrões de interface, o único equivalente a filtro é a delimitação do recorte (O02), que tem ajuste com alerta e retorno ao subgrafo quando cancelado. Administração, relatório e histórico não fazem parte do sistema interativo delimitado na Entrega 8 e não aparecem nos diagramas.

[H] Os diagramas são propostas de design da equipe, ainda não avaliadas com usuários; a verificação ocorre no teste com usuários da Entrega 14, pelas metas MU01–MU14 da Entrega 8.

### Preparação para o Figma

A passagem para a interface segue o que a disciplina apresenta: acessos ubíquos viram elementos persistentes de navegação; cada cena vira uma unidade de apresentação; diálogos viram elementos da unidade; falas do usuário viram controles; e falas do preposto viram mensagens de status ou de erro. A fala de sucesso aparece como mensagem de status na unidade da cena de destino. A fala de ruptura que leva a uma cena de alerta ou de recuperação apoiada vira unidade própria; a que devolve a conversa à mesma cena vira mensagem de erro nessa unidade. Como a Entrega 8 prevê subgrafo, hipóteses e evidências visíveis ao mesmo tempo, `inspecionar o subgrafo (O05)`, `examinar hipóteses e evidências (O08)` e `comparar hipóteses concorrentes (O09)` são painéis da mesma tela de investigação. Os estados e telas necessários são:

1. **Elementos persistentes** (acessos ubíquos, M01–M04): recorte sempre visível, com o ajuste disponível quando há subgrafo (M03, M04); acesso ao subgrafo (M01, M03, M04) ou, em M02, a hipóteses e evidências, que leva de volta à tela de investigação; acesso ao registro do resultado, que reabre o rascunho preservado e, em M03 e M04, fica disponível quando há subgrafo; e saída sem pedido de confirmação, pois o rascunho fica preservado.
2. **Incidente reaberto pelo link do resultado** (`recuperar o contexto do incidente (O04)`, M01, M02): recorte, hipótese em foco, evidências citadas e resultados do incidente, com autor, horário do envio e justificativa; controles para examinar a hipótese em foco e as evidências citadas.
3. **Delimitação** (`delimitar o incidente (O02)`, M03, M04): alerta de origem, recorte proposto e edição de serviço, sintoma e período como campos obrigatórios; controle para solicitar a análise; mensagem de erro com a causa da falha no estágio e o recorte preservado, que também é o estado depois do cancelamento da análise.
4. **Confirmação do ajuste do recorte** (cena de alerta, M03, M04): o recorte vigente, a mensagem do preposto e os controles para confirmar e para cancelar o ajuste.
5. **Andamento da análise** (`acompanhar a análise (O03)`, M03, M04): cada estágio com o estado aguardando, em andamento, concluído, cancelado ou falha, e o controle para cancelar; ao fim da filtragem estrutural, mensagem de status na tela de investigação, com a geração de hipóteses ainda em andamento.
6. **Subgrafo** (`inspecionar o subgrafo (O05)`, M01, M03, M04): o subgrafo indicado como seleção; estado do componente, desvio observado, instrumentação, relação, fonte da relação e caminho de propagação; início do desvio com a lacuna "período incompleto" ou desconhecido; a mensagem "nenhuma hipótese gerada"; componentes fora do subgrafo mostrados e ocultados (M04); exame das hipóteses indisponível até que sejam geradas.
7. **Evidências do componente em foco** (processo da consulta, M01–M04; em M02, das evidências associadas): carregando, com dados, sem dados apresentado como lacuna e identificador ausente; acesso restrito como mensagem de erro na mesma área, com a indicação de consulta fora do sistema; falha de consulta em unidade própria (`repetir a consulta`), com tipo de evidência, situação da consulta, causa e controle para repetir.
8. **Hipóteses e evidências** (`examinar hipóteses e evidências (O08)`, M01–M04): hipóteses A e B sem ordem de preferência, identificadas como produzidas pelo pipeline, com origem provável, explicação, caminho de propagação, evidências associadas e lacunas da hipótese; evidências citadas com ambiente e conteúdo mascarado (M02); troca da hipótese em foco, refletida no subgrafo (`comparar hipóteses concorrentes (O09)`, M03).
9. **Dependências e ordem de propagação** (O06 e O07, M04): relação ausente do mapa destacada, fonte da relação e classificação proposta, com "observada" indisponível para relação sem trace ou log; componentes envolvidos e ordem de propagação proposta pelo início do desvio, com posição desconhecida para o componente sem início do desvio.
10. **Verificação da correção** (`avaliar o alcance da verificação (O10)`, M02): dados do teste, com referência do teste e versão verificada obrigatórias; mensagem de erro que indica o campo vazio; evidências do teste ao lado das evidências citadas, com "com dados" diferenciado de "sem dados".
11. **Registro do resultado** (O12–O15, M01–M04): um formulário por tipo de resultado, com o núcleo comum, os campos obrigatórios marcados, o estado do envio "rascunho" e o controle para escolher os destinatários indisponível enquanto faltam campos obrigatórios; quem pode esclarecer só no parecer inconclusivo (M02); retorno parcial e atualização de um retorno anterior (M04).
12. **Confirmação da conclusão do parecer** (cena de alerta, M02): conclusão do parecer, lacunas e critério de aceitação, com os controles para confirmar e para rever a conclusão.
13. **Destinatários** (`enviar o resultado aos destinatários (O16)` e cena de alerta `confirmar os destinatários`, M01–M04): escolha entre as pessoas com acesso ao incidente e confirmação com o resultado, os destinatários e o link do resultado, com os controles para confirmar e para alterar os destinatários.
14. **Envio** (processo do envio, M01–M04): envio disponível como mensagem de status na tela de investigação, com horário do envio e link do resultado; falha de disponibilização em unidade própria (`repetir o envio`), com estado do envio, causa, rascunho preservado e controle para repetir o envio.

Esses estados incluem os que a Entrega 8 exige no protótipo: carregamento, consulta sem dados, falha de consulta, acesso restrito e falha de disponibilização. O protótipo da Entrega 11 não terá fluxo que não esteja nos quatro diagramas.

## Referências

- **CC8122 — MoLIC, partes A, B e C.** Material de aula disponibilizado na disciplina, baseado em Barbosa e Silva (2010), consultado em 17/11/2026. Notação MoLIC e passagem da interação para o design de interface.
- BARBOSA, Simone D. J.; SILVA, Bruno S. **Interação Humano-Computador**. Rio de Janeiro: Elsevier/Campus, 2010.
- Documentos do projeto: [M01](10_molic/m01.md), [M02](10_molic/m02.md), [M03](10_molic/m03.md), [M04](10_molic/m04.md), [Entrega 9](09_modelo_conceitual.md), [Entrega 8](08_engenharia_usabilidade.md), [Entrega 5](05_analise_tarefas.md) e [matriz de rastreabilidade](../RASTREABILIDADE.md).
