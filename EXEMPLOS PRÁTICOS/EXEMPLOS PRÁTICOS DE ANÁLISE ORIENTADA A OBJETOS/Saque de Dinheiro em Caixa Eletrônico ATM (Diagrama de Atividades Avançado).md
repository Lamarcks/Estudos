**Problema:** Desenhar um diagrama de atividades que mapeie as operações completas executadas por um cliente que utiliza um **caixa eletrônico (ATM)** para realizar um saque usando cartão de crédito. O sistema deve separar o que é processado localmente no caixa físico e o que depende de validação nos servidores do banco. É necessário exigir a senha uma única vez e exibir o saldo em tela após a conclusão.

**Conceito utilizado:** **Diagrama de Atividades UML** com três partições/swimlanes, condicionais complexas e sincronização.

**Solução:** O fluxo é estruturado dividindo as tarefas em três raias verticais:

1. **Raia 1 (`Consumidor`)**:
    - Insere o cartão \(\rightarrow\) Digita a senha \(\rightarrow\) Solicita a quantidade de dinheiro \(\rightarrow\) Obtém o dinheiro \(\rightarrow\) Retira o cartão \(\rightarrow\) Fim.
2. **Raia 2 (`Caixa Automático`)**:
    - Valida o cartão \(\rightarrow\) Ejeta o cartão \(\rightarrow\) Mostra o saldo em tela após a confirmação do saque.
3. **Raia 3 (`Servidor do Banco`)**:
    - Verifica a senha digitada. Se a senha for inválida, o fluxo desvia diretamente para a ejeção do cartão.
    - Se a senha for válida, verifica se `Saldo > Quantidade`.
    - Se o saldo for suficiente, executa a operação paralela de "Débito em Conta". Caso contrário, desvia para mostrar o saldo sem liberar dinheiro.

**Resultado:** O diagrama final de atividades (conforme a _Figura 9 da Unidade 2, Aula 3_) mapeia com precisão a lógica distribuída de segurança e fluxo operacional do ATM.

**Por que essa solução funciona:** A divisão em raias deixa claro que ações críticas de segurança (como verificação de saldo e débito de valores) ocorrem no **Servidor do Banco** por motivos de integridade de dados, enquanto tarefas de interface (digitação e exibição) ocorrem no **Caixa Automático**.

**O que preciso aprender com esse exemplo:** Em sistemas distribuídos, as **ações de negócio críticas devem ser isoladas na raia do servidor central**, enquanto as raias periféricas lidam exclusivamente com interações de entrada/saída de dados com o usuário.