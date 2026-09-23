**Problema:** Realizar o mapeamento objeto-relacional para o relacionamento de **composição** entre a classe **`CreditoParcelado`** (classe Todo) e a classe **`ParcelaCreditoParcelado`** (classe Parte). Sendo uma composição (todo-parte forte), as parcelas não possuem existência conceitual própria fora do ciclo de vida do crédito parcelado ao qual pertencem.

**Conceito utilizado:** Mapeamento de **Composição física** no Mapeamento Objeto-Relacional.

**Solução:** A partir do recorte do diagrama de classes (conforme a _Figura 7 da Unidade 4, Aula 4_):

1. Mapeia-se a classe "Todo" (`CreditoParcelado`) em uma tabela individual:
    - `CreditoParcelado (`\(\underline{\text{creditoParceladoId}}\), dataLancamento, qtdadeParcelas, valorTotal, situacao, demaisFK`)`.
2. Mapeia-se a classe "Parte" (`ParcelaCreditoParcelado`) em outra tabela física.
3. **Regra Especial da Composição**: O identificador (PK) da classe Todo (`creditoParceladoId`) é inserido e incorporado como **parte integrante da Chave Primária Composta** da tabela que representa a classe Parte (`ParcelaCreditoParcelado`):
    - `ParcelaCreditoParcelado (`\(\underline{\text{creditoParceladoId}}\), \(\underline{\text{parcelaCreditoParceladoId}}\), dataVencimento, valorParcela, dataPagamento, juro, multa, outrosAcrescimos, desconto`)`.

**Resultado:** A integridade referencial do banco de dados é mantida de forma que, se um registro de `CreditoParcelado` for excluído, todas as suas linhas correspondentes de `ParcelaCreditoParcelado` são deletadas em cascata automaticamente, pois suas chaves dependem diretamente da existência do ID do pai.

**Por que essa solução funciona:** A composição implica que a chave de identificação da parte é fraca e depende da chave do todo. Definir a PK da tabela filha como uma chave composta contendo a PK da tabela pai garante fisicamente essa restrição de ciclo de vida forte no SGBDR.

**O que preciso aprender com esse exemplo:** A diferença crucial no mapeamento de banco de dados entre Agregação e Composição é:

- Na **Agregação (relação fraca)**: O ID do Todo vira apenas uma **chave estrangeira (FK) simples** na tabela da Parte.
- Na **Composição (relação forte)**: O ID do Todo vira **parte integrante da Chave Primária (PK) composta** da tabela da Parte.