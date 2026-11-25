# Roteiro de teste de usabilidade

## 1. Antes da sessão

- verificar protótipo/versão: abrir, em janela anônima e 30 min antes da sessão, a versão do protótipo identificada na Entrega 14 (passo 1), pelo link registrado na Entrega 11, e conferir se os pontos de partida abrem: F00B (UT01), F00C (UT02), F00A do fluxo M03 (UT03) e F00A do fluxo M04 (UT04);
- testar gravação e áudio: não há gravação; no início da chamada, testar com o participante o áudio e o compartilhamento de tela e conferir se a tela dele tem pelo menos 1440 px de largura; se a tela for menor, o link não abrir ou o compartilhamento atrasar a ponto de impedir a leitura, seguir a tabela de riscos técnicos da Entrega 12; o observador entra com câmera e microfone desligados;
- abrir formulários/planilhas: o moderador abre o [questionário pré e pós-teste](questionario_pre_pos_teste.md), e o observador, em outro computador, a [planilha de observação](planilha_observacao_modelo.md) e um cronômetro, ambos com o identificador da sessão (U01 a U04) e sem o nome do participante;
- limpar dados de sessão/conta de teste: não há conta nem login; cada tarefa é aberta pelo link do seu ponto de partida, em aba nova, para que o protótipo comece no estado de abertura e as rupturas aconteçam nos mesmos trechos para todos;
- separar instruções das tarefas: deixar prontos os textos da seção 4, para colar no chat da chamada;
- confirmar consentimento e duração: confirmar com o participante a duração (cerca de 20 min, com 30 min reservados), a exigência de tela e a leitura do termo no início da sessão;
- quando o protótipo usar resultados/processamentos simulados, preparar dados realistas e manter a simulação consistente entre participantes: o incidente INC-4721, as esperas, as rupturas, as instruções e a ordem das tarefas são os mesmos em todas as sessões, e a indicação de áreas clicáveis do modo de apresentação fica desligada.

## 2. Abertura padronizada

- agradecer participação: receber o participante com uma conversa breve, sem falar do protótipo, e agradecer: "Obrigado por participar.";
- explicar objetivo geral sem revelar hipóteses específicas: "Estamos avaliando o protótipo de uma interface de apoio à investigação de incidentes em sistemas distribuídos, para encontrar problemas antes de qualquer implementação. Você vai fazer quatro tarefas e responder a algumas perguntas. Eu conduzo a sessão, e um colega, com câmera e microfone desligados, anota o que acontece.";
- reforçar que o produto, não a pessoa, está sendo avaliado: "Não há resposta certa ou errada. Se algo for difícil, o problema é do protótipo, não seu.";
- explicar possibilidade de interrupção: "Você pode interromper a sessão a qualquer momento, sem justificar, e pedir a exclusão dos seus dados até 04/12/2026. Depois disso, ainda pode pedir que o termo e os dados que identificam você sejam apagados.";
- obter consentimento: ler o [termo](termo_consentimento_modelo.md), enviar no chat o link do formulário on-line do termo, esclarecer as dúvidas e confirmar que o participante enviou o aceite; em seguida, aplicar o perfil pré-teste (seção 3);
- explicar *think aloud* apenas se essa técnica for usada: "Enquanto faz as tarefas, diga em voz alta o que está pensando: o que procura, o que entende do que vê e o que espera que aconteça. Vou interferir o mínimo possível; se você me perguntar como fazer algo, posso devolver a pergunta, e conversamos sobre as dúvidas no final."

### Quando a interface é um protótipo de aplicação do tema do TCC

Explique de forma simples que a sessão avalia **como a pessoa interage com o protótipo**, e não a precisão/desempenho científico do algoritmo, modelo ou estudo do TCC.

Se algum resultado técnico estiver simulado, não engane o participante sobre o nível de implementação. Use uma explicação compatível com o objetivo do teste, sem antecipar o caminho da tarefa.

Depois do perfil pré-teste, o moderador lê a apresentação do sistema e das regras da simulação, que substitui a exploração livre. Ela não explica como o sistema produz os resultados mostrados, porque isso é perguntado no pós-teste:

> "O sistema apoia a investigação de incidentes em sistemas distribuídos. Você vai usar um protótipo com um único incidente fictício, visto em quatro momentos diferentes. Em cada tarefa, você assume o papel de uma pessoa da equipe, que pode não ser o seu papel no trabalho. Tudo o que aparece nele é simulado: o protótipo não está ligado a nenhum sistema real, e os dados e os tempos de espera foram preparados pela equipe. Estamos avaliando a interface, isto é, se ela ajuda você a fazer o que cada tarefa pede.
>
> Algumas regras da simulação: algumas áreas da tela não respondem ao clique, porque não foram prototipadas; os campos de texto não aceitam digitação, então, quando quiser escrever em um campo, clique nele e diga em voz alta o que escreveria; e, como o incidente é fictício, não cite dados da empresa em que você trabalha.
>
> Para cada tarefa, envio um link no chat. Abra-o em uma aba nova, em tela cheia. Depois eu leio a instrução e a deixo no chat, para você reler quando quiser."

## 3. Perfil pré-teste

Colete somente informações relevantes à interpretação dos resultados: experiência com domínio, frequência de uso de soluções similares, familiaridade com ferramentas profissionais, necessidades de acessibilidade pertinentes etc.

O moderador aplica oralmente a parte de pré-teste do [questionário](questionario_pre_pos_teste.md) e registra as respostas com o identificador da sessão. Os participantes têm perfil profissional especializado: no cabeçalho do questionário, registre o perfil de referência (P01 a P04) e os critérios da seção C da Entrega 12 que tornam o participante representativo. Se for participante proxy, registre essa condição, a justificativa e a limitação, que também vão para o perfil resumido da planilha e para a Entrega 14.

## 4. Tarefas

Ordem de aplicação, igual para todos: UT03, UT04, UT01 e UT02. Para cada tarefa, o moderador envia no chat o link do ponto de partida, espera o participante abri-lo, lê a instrução e a deixa no chat. A partir da segunda tarefa, antes de ler a instrução, ele diz: "Esta tarefa acontece em outro momento do mesmo incidente. O que você enviou antes não aparece nela." O tempo-limite não é informado ao participante.

| ID | Instrução ao participante | O moderador pode esclarecer | O moderador não deve dizer |
|---|---|---|---|
| UT03<br>partida: F00A do fluxo M03<br>tempo-limite: 11 min | "Você é Rafael Mendes, SRE de plantão. A ferramenta de alertas acaba de disparar o alerta que está na tela. Investigue o incidente no sistema e comunique a Lucas, desenvolvedor do checkout, o que você conclui até agora sobre a origem e o impacto. A equipe precisa dessa primeira conclusão para decidir os próximos passos. Avise quando considerar a tarefa concluída." | Termos do cenário: SRE de plantão é quem responde aos incidentes no turno; Lucas é o desenvolvedor que mantém o checkout. Regras da simulação (seção 2). | Nome ou posição de controles, como `Solicitar a análise`, `Ajustar o recorte`, `Comparar as hipóteses`, `Registrar o diagnóstico inicial` e `Escolher os destinatários`; qual hipótese ou componente é a origem; que a origem pode ficar "não determinada"; se convém ajustar o período ou esperar a análise; os horários de início do desvio. |
| UT04<br>partida: F00A do fluxo M04<br>tempo-limite: 12 min | "Você é Camila Nunes, especialista em observabilidade. Os alertas que estão na tela dispararam há pouco, e Rafael Mendes, SRE de plantão, pediu sua ajuda: ele precisa decidir em poucos minutos se aciona outras equipes. Use o sistema para descobrir quais serviços estão envolvidos, quais serviços o checkout chama direta ou indiretamente, em que ordem o problema se espalhou e qual seria a provável origem, indicando o grau de certeza de cada ligação entre os serviços. Faça chegar a Rafael o que tiver estabelecido assim que puder, mesmo sem ter terminado a investigação. Avise quando considerar a tarefa concluída." | Termos do cenário: quem é Rafael Mendes; acionar outras equipes é chamar as equipes responsáveis por outros serviços. Regras da simulação (seção 2). | Nome ou posição de controles, como `Dependências do serviço afetado`, `Mostrar componentes fora do subgrafo`, `Repetir a consulta`, `Registrar o retorno ao SRE` e `Ordenar os componentes envolvidos`; os valores "observada", "inferida" e "não verificada" ou o que significam; que a relação pagamento → antifraude não está no mapa de serviços; a ordem de propagação ou a origem provável; a opção de retorno parcial. |
| UT01<br>partida: F00B<br>tempo-limite: 8 min | "Você é Lucas, desenvolvedor do checkout. Rafael Mendes, SRE de plantão, acabou de lhe mandar a mensagem que está na tela. Atenda ao pedido dele usando o sistema e faça sua resposta, com o motivo da sua decisão, chegar a Rafael. Avise quando considerar a tarefa concluída." | Termos do cenário: quem é Rafael Mendes; o pedido é o que está na mensagem. Regras da simulação (seção 2). | O pedido da mensagem com outras palavras; nome ou posição de controles, como `Examinar a hipótese em foco`, `Subgrafo`, `Registrar a avaliação da hipótese`, `Escolher os destinatários` e `Enviar`; os valores da classificação da hipótese; quais evidências sustentam ou contradizem a hipótese; se a hipótese está certa. |
| UT02<br>partida: F00C<br>tempo-limite: 9 min | "Você é Mariana, analista de QA. O chamado da correção que está na tela pede sua verificação antes da liberação do checkout 2.14.1, marcada para hoje. Você já executou um teste em homologação: referência TC-0457, versão checkout 2.14.1, em 11/11/2026, das 10h05 às 10h15, com resultado 'passou'. Use o sistema para decidir o que as evidências permitem afirmar sobre a correção e faça sua conclusão, com o que a sustenta, chegar a Lucas, responsável pela correção, e a Rafael Mendes, SRE de plantão. Quem participou da investigação não poderá responder a perguntas antes da liberação. Avise quando considerar a tarefa concluída." | Termos do cenário: liberação é a implantação do checkout 2.14.1 em produção; homologação é o ambiente de teste anterior à produção; TC-0457 é a referência do teste já executado; quem são Lucas e Rafael Mendes. Regras da simulação (seção 2). | Nome ou posição de controles, como `Examinar as evidências citadas`, `Avaliar o teste da correção`, `Relacionar o teste ao incidente`, `Registrar o parecer sobre a verificação da correção` e `Repetir o envio`; os valores da conclusão do parecer; se o teste exercitou a condição da falha; que o acesso restrito é uma lacuna; se a correção funcionou; que o envio falhou ou precisa ser repetido. |

Tarefas podem envolver, conforme o escopo: localizar informação em dashboard; filtrar histórico; configurar análise; comparar resultados; gerar relatório; revisar alerta; editar permissão; recuperar-se de falha.

A tarefa deve expressar **objetivo do usuário**, e não “clique no filtro”, “abra o CRUD” ou “vá ao dashboard”.

## 5. Durante a tarefa

Registrar início/fim, sucesso, erros, hesitações, comentários, pedidos de ajuda e intervenções do moderador. Não transformar silêncio do participante em “problema” sem evidência adicional.

O observador marca o início no fim da leitura da instrução e o fim quando o participante declara a tarefa concluída, abandona ou atinge o tempo-limite. Na planilha, com o horário do cronômetro e o ID da tela, registra ações, hesitações, tentativas fora do roteiro, intervenções e incidentes técnicos em "Hesitações/comportamentos", e as falas e o texto dito nos campos livres em "Fala relevante".

O moderador não interrompe nem faz perguntas durante a tarefa e segue estas regras:

- depois de 30 s de silêncio, diz apenas "Lembre-se de dizer o que está pensando";
- diante de um pedido de ajuda, devolve a pergunta: "O que você faria agora?";
- se o participante disser que não consegue seguir, pergunta: "Você prefere continuar com uma indicação ou encerrar esta tarefa?"; a indicação dada é anotada com o momento e o conteúdo, e o encerramento conta como abandono;
- se o participante tentar digitar em um campo de texto, repete a regra de dizer em voz alta o que escreveria;
- se uma tela mostrar valores diferentes das escolhas do participante e ele perguntar, responde: "Considere o que você escolheu";
- se o protótipo falhar (link sem resposta ou ruptura fora de ordem), reabre o fluxo pelo link da tarefa; o tempo perdido é anotado como incidente técnico e descontado, e a tarefa que não puder ser concluída é repetida no fim da sessão;
- ao atingir o tempo-limite, encerra a tarefa dizendo "Vamos passar à próxima tarefa".

Observe também, quando pertinente:

- compreensão de termos técnicos, como hipótese diagnóstica, evidência, lacuna, as classificações das relações e as conclusões do parecer;
- percepção do estado do processamento: estágios da análise (F05, F02C), consulta às evidências (F06C), verificação da correção (F12C) e envio (F07C);
- interpretação de estados vazios e de erro: sem dados, acesso restrito, falha de consulta, nenhuma hipótese gerada e falha de disponibilização;
- revisão antes de ações de risco: confirmação dos destinatários (F07A), ajuste do recorte (F01A) e confirmação da conclusão do parecer (F13A);
- entendimento de permissões: acesso restrito aos logs do pagamento em produção;
- confiança ao interpretar resultados: se o participante separa hipótese, evidência e a própria conclusão e se consulta a ordem dos eventos antes de apontar a origem.

## 6. Pós-tarefa

Logo depois do fim de cada tarefa e antes de qualquer comentário, aplicar oralmente a SEQ: "De modo geral, quão difícil ou fácil foi realizar esta tarefa?", de 1 (muito difícil) a 7 (muito fácil). Em seguida, registrar comentário curto: “O que tornou essa tarefa fácil ou difícil?” Ao fim de UT03, UT01 e UT02, sem fechar o protótipo, perguntar: "Qual serviço e qual período você estava analisando nesta tarefa?" O moderador registra as respostas na parte pós-tarefa do questionário, e o observador anota a SEQ na coluna "Satisfação" da planilha.

## 7. Encerramento

- perguntas gerais: aplicar a parte pós-teste do questionário, na ordem, começando pela pergunta sobre as hipóteses diagnósticas; depois, conversar sobre as dúvidas anotadas durante as tarefas;
- explicar que as falhas encontradas (acesso restrito, consulta sem dados, falha de consulta e falha no envio) foram programadas e são iguais para todos os participantes;
- agradecer;
- confirmar como os dados serão usados: identificador anônimo, termo apagado até 31/01/2027 e possibilidade de pedir, pelo canal do convite, a exclusão dos dados até 04/12/2026 e, depois desse prazo, a exclusão do termo e dos dados que identificam o participante;
- salvar registros com ID anônimo: salvar a planilha e o questionário com o identificador da sessão no nome do arquivo (por exemplo, `U03_planilha`), na pasta de acesso restrito, fora do repositório;
- registrar limitações de perfil, ambiente ou simulação que afetem a interpretação: participante proxy, passagem para a sessão presencial, incidentes técnicos e tempo descontado, valores das telas diferentes das escolhas do participante e tarefa repetida ou não avaliada.
