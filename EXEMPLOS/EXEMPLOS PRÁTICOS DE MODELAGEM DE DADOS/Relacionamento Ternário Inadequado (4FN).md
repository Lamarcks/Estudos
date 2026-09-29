**Problema:** A tabela `Compra` a seguir (na 3FN) tenta gerenciar transações de compras agregando o Fornecedor, o Produto e o Comprador em um relacionamento ternário único:

|CodFornecedor|CodProduto|CodComprador|
|:--|:--|:--|
|101|BA3|01|
|102|CJ10|05|
|110|88A|25|
|530|BA3|01|
|101|BA3|25|

Dificuldade: A tabela mistura dois fatos multivalorados independentes de negócio (o comprador está vinculado ao processo de compra genérico, em vez de estar associado de forma direta aos produtos que ele consome). Isso gera dependências multivaloradas e anomalias de inserção complexas.

**Conceito utilizado:** Quarta Forma Normal (4FN) — eliminação de dependências multivaloradas.

**Solução:** Decompor a tabela original de relacionamento ternário em duas tabelas de relacionamentos binários independentes compartilhando a chave `CodFornecedor`:

1. Tabela 1: `Fornecedor_Produto` (`#CodFornecedor`, `#CodProduto`).
2. Tabela 2: `Produto_Comprador` (`#CodProduto`, `#CodComprador`).

**Resultado:** Duas tabelas independentes e normalizadas em 4FN que impedem violações das regras de negócio durante atualizações.

**Por que essa solução funciona:** Ao separar os relacionamentos multivalorados independentes, o banco de dados elimina a necessidade de repetir registros adicionais vazios ou parciais para mapear novos fornecedores de produtos que ainda não possuem um comprador associado.

**O que preciso aprender com esse exemplo:** Evite criar relacionamentos ternários desnecessários no MER conceitual. Mapeie relacionamentos de forma binária e direta entre as partes envolvidas no processo real para atingir naturalmente a 4FN.