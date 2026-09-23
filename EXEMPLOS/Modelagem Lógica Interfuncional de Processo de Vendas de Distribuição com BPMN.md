**Problema:** Uma distribuidora possui gargalos severos de comunicação entre os departamentos Comercial, Contas a Receber, Expedição, Faturamento e Logística. Vendas são canceladas na expedição por falta de estoque real, clientes inadimplentes têm pedidos liberados e o faturamento perde tempo ajustando notas fiscais de itens em falta. Mapear visualmente esse processo complexo com rigor técnico em notação BPMN para posterior automação em sistema.

**Conceito utilizado:**

- **BPMN (Business Process Model and Notation)**.
- **Elementos Gráficos da Notação**: _Pools_ (Piscina), _Lanes_ (Raias), _Gateways_ Exclusivos e de Desvios de Mensagens.

**Solução:** A empresa mapeou o fluxo detalhado dividindo-o em responsabilidades (raias):

1. **Raia Comercial**: Recebe o pedido do cliente por canais externos -> Verifica preenchimento -> Encaminha de forma eletrônica para a raia de Contas a Receber.
2. **Raia Contas a Receber**: Recebe dados do pedido -> Verifica adimplência de crédito do cliente.
    - _Gateway Exclusivo (Aprovado?)_: Se Não, envia fluxo de mensagem/e-mail para a Raia Comercial avisando do impedimento; Se Sim, dispara fluxo de sequência para a Raia de Expedição.
3. **Raia Expedição**: Recebe pedido -> Inicia separação física das quantidades no estoque.
    - _Gateway Exclusivo (Tem estoque de tudo?)_: Se Não, dispara fluxo de notificação ao Comercial (para atualizar o cliente) e avisa o Faturamento; Se Sim, envia para Faturamento.
4. **Raia Faturamento**: Recebe dados -> Executa ajustes lógicos retirando do faturamento os itens faltantes do estoque -> Emite Nota Fiscal eletrônica e gera boleto de cobrança bancária -> Despacha para a Logística.
5. **Raia Logística**: Recebe nota/boleto -> Efetua o carregamento do caminhão de transporte -> Realiza a rota de entrega final ao cliente -> Fim do processo.

**Resultado:** O mapeamento em BPMN gerou o **Diagrama de Processo de Negócio (DPN)**. Ele integrou e amarrou as regras lógicas de negócio, impedindo a liberação de faturas errôneas ou despacho de pedidos sem análise de crédito.

**Por que essa solução funciona:** Ao estabelecer as **raias de responsabilidade**, cada ator sabe exatamente o que precisa processar. Os **gateways exclusivos** baseados em dados lógicos (adimplência e saldo de estoque) travam ações equivocadas antes que elas atinjam a área de despacho.

**O que preciso aprender com esse exemplo:** O BPMN unifica a linguagem de negócios e tecnologia, forçando a integração sequencial horizontal das tarefas entre setores e eliminando as perdas de dados e atrasos gerados por silos funcionais isolados.
