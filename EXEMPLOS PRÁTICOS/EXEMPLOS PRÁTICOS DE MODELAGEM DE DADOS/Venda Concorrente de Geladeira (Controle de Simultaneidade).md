**Problema:** Dois vendedores em terminais de caixa diferentes acessam o SGBD de uma loja de eletrodomésticos exatamente no mesmo instante para vender o último refrigerador em estoque. Sem controle de simultaneidade, ambos conseguiriam fechar a venda, deixando a loja com um cliente sem o produto.

**Conceito utilizado:** Controle de concorrência e propriedade de **Isolamento** de transações (requisito ACID).

**Solução:** O SGBD executa protocolos de bloqueio concorrente. Quando a transação do Vendedor A inicia a atualização do saldo do produto em estoque (ex: decrementando de 1 para 0), o SGBD bloqueia temporariamente o registro da geladeira. A transação do Vendedor B é colocada em espera. Assim que a transação de A é finalizada com sucesso, o estoque passa a ser 0, e a transação de B é notificada de que o produto não está mais disponível.

**Resultado:** Prevenção de inconsistências lógicas e manutenção da integridade do minimundo real no banco de dados.

**Por que essa solução funciona:** O isolamento garante que transações simultâneas sejam executadas como se fossem sequenciais, impedindo que uma transação leia dados "sujos" ou em estado intermediário de outra antes do encerramento desta.

**O que preciso aprender com esse exemplo:** Transações concorrentes mal gerenciadas quebram a consistência do banco. O isolamento é o mecanismo do SGBD que impede que operações simultâneas se interceptem de forma destrutiva.