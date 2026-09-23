**Problema:** Modelar o processo de negócio de **empréstimo de livros** em uma biblioteca. O fluxo de controle precisa prever a verificação de pendências no cadastro do usuário (multas ou atrasos). Se houver pendências, o usuário deve resolvê-las antes; se não houver, pode retirar o livro. Adicionalmente, para liberar o livro, o sistema deve realizar duas tarefas em paralelo: a desmagnetização física do livro e o registro da saída no sistema de banco de dados.

**Conceito utilizado:** **Diagrama de Atividades UML** com estruturas de decisão (losangos), paralelismo concorrente (barras transversais de **FORK** e **JOIN**) e partições lógicas (**Swimlanes**).

**Solução:** O processo é organizado de cima para baixo nas seguintes etapas:

1. **Swimlanes (Raias)**: O diagrama é dividido em três colunas de responsabilidade: `USUARIO`, `ATENDENTE` e `SERVIDOR BIBLIOTECA`.
2. **Fluxo de Decisão**:
    - O usuário apresenta a carteirinha no nó inicial.
    - O atendente consulta o sistema.
    - Um **losango de decisão** avalia: `EXISTEM PENDÊNCIAS?`.
    - Se **SIM**, o fluxo desvia para a atividade "Resolver as Pendências" (atribuição do atendente) e depois retorna ao fluxo principal. Se **NÃO**, segue diretamente.
3. **Paralelismo Concorrente (FORK e JOIN)**:
    - O usuário apresenta o livro.
    - Uma barra sólida horizontal de **FORK** divide o fluxo em duas atividades simultâneas: "Desmagnetização" (feita pelo atendente) e "Registro de Saída" (processada pelo servidor).
    - Uma barra sólida horizontal de **JOIN** une ambos os fluxos após sua conclusão, garantindo que o livro só seja liberado após as duas tarefas terminarem.
    - O usuário retira o livro e o processo atinge o estado final.

**Resultado:** Um modelo visual robusto e otimizado que demonstra o funcionamento lógico do empréstimo de livros, evidenciando de quem é a responsabilidade por cada passo e quais operações ocorrem em paralelo.

**Por que essa solução funciona:** A utilização de **FORK** e **JOIN** previne gargalos sequenciais ao explicitar que a desmagnetização e o registro de dados não dependem um do outro para acontecer, melhorando a eficiência projetada do software. As **Swimlanes** organizam visualmente a arquitetura lógica de responsabilidades entre atores e sistemas.

**O que preciso aprender com esse exemplo:** O **FORK sempre divide** um fluxo em múltiplos fluxos concorrentes. O **JOIN atua como uma barreira de sincronização**: o fluxo sequencial posterior só inicia quando todos os fluxos de entrada paralelos forem concluídos. As **Swimlanes** não alteram a execução lógica, servem apenas para organizar responsabilidades.