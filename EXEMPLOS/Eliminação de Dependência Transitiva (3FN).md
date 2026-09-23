**Problema:** A seguinte tabela de funcionários (na 2FN) apresenta anomalias de redundância:

|#codFuncionario|Nome|idCargo|descCargo|
|:--|:--|:--|:--|
|148-9|Jane Anne|191|Analista Contábil I|
|721-4|Klaus Lins|323|Assistente de Produção II|

Dificuldade: O campo `descCargo` (descrição do cargo) não é determinado diretamente pela chave primária da tabela (`#codFuncionario`). Ele é determinado por `idCargo`, que é um atributo não chave. Isso configura uma dependência transitiva.

**Conceito utilizado:** Terceira Forma Normal (3FN) — eliminação de dependências transitivas.

**Solução:**

1. Identificar que o campo `descCargo` depende de outra coluna não chave (`idCargo`).
2. Remover a coluna dependente `descCargo` da tabela de funcionários.
3. Criar uma tabela própria para armazenar as descrições de cargos: `Cargo` (`#idCargo`, `descCargo`).
4. Manter o campo `&idCargo` como chave estrangeira na tabela de funcionários para preservar o relacionamento lógico de 1:N entre as duas.

**Resultado:** As tabelas separadas e limpas:

- `Funcionário` (#codFuncionario, Nome, &idCargo).
- `Cargo` (#idCargo, descCargo).

**Por que essa solução funciona:** Evita redundância extrema e anomalias de exclusão. Se o funcionário "Klaus Lins" for demitido e excluído do sistema, a informação de que o cargo `323` significa "Assistente de Produção II" não é perdida, pois está preservada na tabela independente de cargos.

**O que preciso aprender com esse exemplo:** Campos de tabelas na 3FN devem depender exclusivamente de três coisas: "da chave, de toda a chave, e de nada mais do que a chave". Se um campo não chave determina outro campo não chave, há violação da 3FN.
