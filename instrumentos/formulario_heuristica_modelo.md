# Formulário de avaliação heurística — modelo

**Avaliador:** A0_ — ____________________

**Versão:** protótipo da Entrega 11, versão do catálogo de telas de 17/11/2026 (42 telas e estados, fluxos M01–M04)

**Data:** ____/____/________

**Estados especiais examinados (marque os que examinou):** ( ) carregamento e processamento (F05, F02C, F06C, F07C, F12C) ( ) sem dados ou nenhum resultado (F02V, F06V, F12V) ( ) erro (F01E, F12E) ( ) permissão (F06P) ( ) recuperação (F06R, F07R) ( ) cancelamento (F01X) ( ) confirmação antes de ação de risco (F01A, F07A, F13A) ( ) sucesso (F06S, F07S, F08S) ( ) detalhe mostrado a pedido (F02D, F03D, F12D, F16D)

## Cobertura

| H | Heurística | Fluxos/telas examinados | Violação? | IDs | Exemplo de boa prática se não violada |
|---:|---|---|---|---|---|
| 1 | Visibilidade do status do sistema — *os usuários são mantidos informados sobre o progresso do sistema, com feedback apropriado e em tempo razoável?* | | sim/não | | |
| 2 | Compatibilidade sistema–mundo real — *o sistema usa conceitos e linguagem familiares ao usuário, em vez de termos orientados ao sistema, e exibe as informações em ordem lógica e natural?* | | sim/não | | |
| 3 | Controle e liberdade do usuário — *os usuários podem fazer o que querem quando querem e sair de um estado indesejado sem percorrer um diálogo extenso?* | | sim/não | | |
| 4 | Consistência e padrões — *objetos e ações têm o mesmo significado ou efeito em diferentes situações?* | | sim/não | | |
| 5 | Prevenção de erros — *os usuários podem cometer erros que um bom projeto poderia prevenir?* | | sim/não | | |
| 6 | Reconhecimento em vez de memorização — *objetos, ações e opções estão visíveis, ou o usuário precisa lembrar informações de uma parte do sistema para outra?* | | sim/não | | |
| 7 | Flexibilidade e eficiência de uso — *as tarefas são eficientes e se adaptam às ações mais frequentes do usuário, por exemplo com atalhos?* | | sim/não | | |
| 8 | Estética e design minimalista — *os diálogos contêm informações irrelevantes ou raramente necessárias?* | | sim/não | | |
| 9 | Reconhecer, diagnosticar e recuperar erros — *as mensagens de erro usam linguagem simples, sem códigos, descrevem exatamente o problema e sugerem uma solução?* | | sim/não | | |
| 10 | Ajuda e documentação — *há informações de ajuda apropriadas, fáceis de encontrar e focadas nas tarefas do usuário?* | | sim/não | | |

## Problemas

Registre uma violação por linha. Em "Tela/estado", indique o ID do catálogo da Entrega 11 e o elemento de interface; se o problema se repete, todos os IDs; se falta algo, onde deveria estar. Em "Evidência", use a captura da tela com o problema destacado, salva como `assets/13_heuristica/a0N_v0M.png`. Severidade: 0, sem importância (não afeta a operação da interface); 1, cosmético (sem necessidade imediata de solução); 2, simples (baixa prioridade); 3, grave (alta prioridade, deve ser reparado); 4, catastrófico (deve ser reparado de qualquer forma). A justificativa considera frequência, impacto e persistência.

| ID | H | Tela/estado | Ação/condição | Problema | Consequência | Evidência | Severidade 0–4 | Justificativa | Recomendação |
|---|---|---|---|---|---|---|---:|---|---|
| V01 | | | | | | | | | |
