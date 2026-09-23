**Problema:** Como explicar de forma simples a diferença abstrata entre um programa e um processo, além do funcionamento de interrupções de prioridades no processador?

**Conceito utilizado:** Definição de **Programa**, **Processo**, alternância de contexto e tratamento de **Interrupções**.

**Solução:** Associe os elementos do sistema com o ato cotidiano de fazer um bolo:

- **A Receita**: O **programa** em si (um conjunto estático de instruções escritas).
- **Os Ingredientes**: Os **dados de entrada**.
- **O Cozinheiro**: O **processador (CPU)**.
- **O Preparo**: O **processo** (a receita sendo ativamente executada pelo cozinheiro através de ações sequenciais: misturar, bater, assar).

**Situação de Interrupção**: Se o filho do cozinheiro se machuca durante o preparo:

1. O cozinheiro interrompe o processo atual (fazer o bolo).
2. Ele salva mentalmente onde parou na receita (salvamento do estado e contexto de registradores).
3. O cozinheiro chaveia para um novo processo de maior prioridade: socorrer o filho utilizando o programa de primeiros socorros.
4. Uma vez que o filho está seguro (evento concluído), o cozinheiro retorna à cozinha e retoma a preparação do bolo exatamente do ponto em que havia parado.

**Resultado:** O processador executa tarefas concorrentemente simulando paralelismo (pseudoparalelismo), tratando prioridades dinamicamente sem perder o progresso das tarefas de menor prioridade.

**Por que essa solução funciona:** Ao manter uma tabela estruturada contendo o estado exato (contador de programa, valores de variáveis e registradores) no momento da interrupção, o S.O. consegue restaurar o processo interrompido sem que haja inconsistências no processamento.

**O que preciso aprender com esse exemplo:** Um programa é estático (passivo); um processo é dinâmico (ativo) e possui estado associado. A alternância rápida de processos orientada por interrupções é o que possibilita aos computadores modernos dar a ilusão de que tudo roda ao mesmo tempo (pseudoparalelismo).
