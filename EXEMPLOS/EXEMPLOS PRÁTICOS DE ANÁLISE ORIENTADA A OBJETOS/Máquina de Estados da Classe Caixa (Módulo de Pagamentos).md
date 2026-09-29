**Problema:** No módulo de pagamentos do sistema de locação de veículos, gerenciar de forma precisa os estados lógicos do objeto da classe **`Caixa`**. O caixa financeiro da empresa deve possuir um ciclo de vida restrito por horários rígidos e aprovações gerenciais específicas para segurança da tesouraria.

**Conceito utilizado:** **Diagrama de Máquina de Estados UML** com transições de estado orientadas a tempo e condições de guarda.

**Solução:** O ciclo de vida do objeto `Caixa` é modelado com os seguintes estados e transições (_Figura 12 da Unidade 4, Aula 2_):

1. **Estado 1: `Abrindo` (ou Aberto)**:
    - O caixa é instanciado. Adquire automaticamente o estado de `Abrindo` ao ser cadastrado no sistema.
    - Contém a ação interna: `do / abrirCaixa`.
2. **Transição 1 (`Abrindo` $\rightarrow$ `Liberando`)**:
    - Disparada pelo evento: `liberar` sob a condição de guarda `[= 08h ou usuário gerente determinar]`.
3. **Estado 2: `Liberando` (ou Liberado)**:
    - O caixa está ativo para receber transações físicas e em cartão.
    - Ações internas: `entry / lancarSaldoEntrada` (executada assim que o estado é ativado) e `do / liberarCaixa`.
4. **Transição 2 (`Liberando` $\rightarrow$ `Fechando`)**:
    - Disparada pelo evento: `fechar` sob a condição de guarda `[= 18h ou usuário gerente determinar]`.
5. **Estado 3: `Fechando` (ou Fechado)**:
    - O caixa é encerrado temporariamente para o balanço do dia.
    - Ações internas: `entry / lancarSaldoFechamento` e `do / fecharCaixa`.
6. **Transição 3 (`Fechando` $\rightarrow$ `Abrindo`)**:
    - O ciclo é reiniciado no dia seguinte às 6h da manhã pela transição baseada no evento: `abrir` sob a condição de guarda `[= 06h]`.

**Resultado:** A classe `Caixa` possui suas transições de estado blindadas contra aberturas ou fechamentos fora do padrão operacional da empresa.

**Por que essa solução funciona:** As ações de entrada (`entry`) garantem que o sistema lance o saldo de forma obrigatória no banco de dados tanto na abertura (entrada de troco) quanto no fechamento de contas do caixa, automatizando rotinas críticas de auditoria financeira.

**O que preciso aprender com esse exemplo:** A sintaxe interna de um estado na máquina de estados segue a nomenclatura padrão **`cláusula / operação`**. A ação **`entry` ocorre na entrada imediata do estado**, a ação **`exit` na saída** e a ação **`do` ocorre de forma contínua** enquanto o objeto estiver estacionado naquele estado.