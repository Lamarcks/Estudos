**Problema:** Uma empresa em expansão com diversas filiais precisa organizar seu sistema de armazenamento de arquivos corporativos. O volume de consultas diárias é altíssimo. O gerente de vendas questiona qual o melhor método lógico para recuperar as informações dos arquivos sem gerar lentidões nas filiais.

**Conceito utilizado:** Métodos de acesso a dados: **Sequencial**, **Direto** e **Indexado (Por Chave)**.

**Solução:** Adotar o método de **Acesso Indexado (Por Chave)**.

**Resultado:** O sistema operacional cria e mantém uma área específica de índice com ponteiros físicos mapeando o conteúdo em disco. Ao realizar a busca, a aplicação informa uma chave única de busca, e o S.O. pesquisa o ponteiro no arquivo índice e pula diretamente para a posição física onde o registro está localizado, eliminando leituras desnecessárias de blocos.

**Por que essa solução funciona:**

- O **Acesso Sequencial** é inviável, pois exige ler o arquivo inteiro desde o início até encontrar o registro desejado.
- O **Acesso Direto** exige que todos os registros físicos de dados tenham exatamente o mesmo tamanho fixo, o que limita a flexibilidade do sistema.
- O **Acesso Indexado** fornece o melhor desempenho, já que o custo de busca lógica de uma chave em índice pequeno é mínimo, permitindo saltar diretamente para os dados físicos.

**O que preciso aprender com esse exemplo:** Para grandes volumes de informações e alta concorrência em rede, o acesso indexado por chaves é o método recomendado, servindo como a lógica básica para a criação de bancos de dados eficientes.