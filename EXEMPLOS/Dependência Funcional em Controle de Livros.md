**Problema:** Compreender como os atributos de um cadastro de acervo de biblioteca ou catálogo de livros se relacionam funcionalmente e como identificar o determinante de forma única.

**Conceito utilizado:** Dependência Funcional Simples (\(X \rightarrow Y\)).

**Solução:** Considere a relação de livros: \[\text{LIVROS}(\text{CodigoISBN}, \text{Titulo}, \text{Area}, \text{Formato}, \dots)\]

- O atributo `CodigoISBN` é o **determinante** (a origem da seta \(X\)).
- O atributo `Titulo` é o **dependente** (destino \(Y\)). Como o código ISBN é exclusivo de cada livro, conhecendo o ISBN, recupera-se apenas um único título correspondente. Graficamente representamos: \[\text{CodigoISBN} \rightarrow \text{Titulo}\]

**Resultado:** Mapeamento lógico das chaves de integridade, identificando que o ISBN determina univocamente todos os outros atributos descritivos do livro na tupla.

**Por que essa solução funciona:** O modelo relacional baseia-se na premissa de que a chave primária determina funcionalmente todas as outras colunas não chave de uma mesma linha.

**O que preciso aprender com esse exemplo:** Se \(A \rightarrow B\), isso significa que para cada valor de \(A\) existirá apenas um único valor correspondente de \(B\). O oposto não é necessariamente verdadeiro (ex: `Area` determina vários códigos ISBN, pois uma única área de conhecimento abriga muitos livros).