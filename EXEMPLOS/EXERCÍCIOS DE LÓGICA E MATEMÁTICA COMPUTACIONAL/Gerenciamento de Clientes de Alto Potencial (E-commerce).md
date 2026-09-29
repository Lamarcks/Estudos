**Problema:** Uma empresa de varejo precisa identificar quais clientes de sua base têm alto potencial de compra na nova campanha de marketing para direcionar disparos de e-mail. A regra de negócio exige as seguintes condições simultâneas:

- O cliente deve ter idade entre 30 e 45 anos.
- Deve ter feito mais de 10 compras anteriormente.
- Deve possuir um ticket médio de gasto acima de R$ 50,00.
- O gênero do cliente não importa (pode ser feminino ou masculino).

Como estruturar a regra booleana para esta consulta de banco de dados e aplicá-la para classificar se a cliente **Ella Nelson** (Feminino, 34 anos, 16 compras anteriores, ticket médio de R$ 150,00) é elegível para o cupom promocional de 10%?

**Conceito utilizado:** Precedência operacional, uso de parênteses delimitadores e conjunções cumulativas (AND / \(\wedge\)).

**Solução:**

1. **Mapear os subcritérios individuais em fórmulas lógicas relacionais:**
    - Gênero: \((F \vee M)\) (Feminino ou Masculino).
    - Idade: \((I \geq 30 \wedge I \leq 45)\).
    - Total de Compras: \(TC > 10\).
    - Ticket Médio: \(TM > R$ 50,00\).
2. **Unificar os critérios respeitando a ordem de precedência por parênteses:** \[P = (F \vee M) \wedge (I \geq 30 \wedge I \leq 45) \wedge (TC > 10) \wedge (TM > 50)\]
3. **Avaliar as entradas booleanas para a cliente Ella Nelson:**
    - Gênero: \(F \implies (V \vee F) = V\).
    - Idade: \(34 \implies (34 \geq 30 \wedge 34 \leq 45) = V \wedge V = V\).
    - Total de Compras: \(16 \implies (16 > 10) = V\).
    - Ticket Médio: \(R$ 150,00 \implies (150 > 50) = V\).
4. **Calcular a conjunção final das proposições intermediárias:** \[P = V \wedge V \wedge V \wedge V = V\]

**Resultado:** Ella Nelson é avaliada com o valor lógico **Verdadeiro** (\(V\)) para a variável `cliente_potencial` e ganha o direito ao cupom promocional de 10% (\(P \rightarrow \text{Cupom}_{10%}\)).

**Por que essa solução funciona:** A organização correta das condições dentro dos parênteses garante que o interpretador de lógica de dados avalie as restrições de idade e gênero como subexpressões independentes. Como todas as quatro subexpressões resultaram em Verdadeiro, a conjunção geral (AND) resulta obrigatoriamente em verdadeiro.

**O que preciso aprender com esse exemplo:** A conjunção lógica (AND) serve para restringir decisões, exigindo que todas as condições de negócio cumulativas sejam atendidas de forma obrigatória. Parênteses são indispensáveis para garantir que o computador calcule primeiro os limites numéricos internos (como a faixa de idade) antes de cruzar com as outras restrições.
