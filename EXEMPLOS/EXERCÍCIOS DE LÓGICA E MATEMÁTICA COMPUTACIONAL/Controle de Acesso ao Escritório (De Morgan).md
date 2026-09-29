**Problema:** A política de segurança física de um escritório exige que um funcionário só seja liberado para entrar se atender a pelo menos uma de três condições: possuir cartão de acesso válido (\(C\)), ser membro da equipe de segurança (\(S\)), ou ser um gerente (\(M\)). Como o sistema de automação deve reescrever matematicamente essa regra para saber as condições exatas em que a entrada do funcionário deve ser **negada e bloqueada** (\(\neg E\))?

**Conceito utilizado:** Primeira Lei de De Morgan para negação de disjunções cumulativas (NAND/NOR).

**Solução:**

1. **Definir a expressão lógica de entrada autorizada (\(E\)):** \[E = C \vee S \vee M\]
2. **Aplicar a negação lógica sobre a expressão de acesso (\(\neg E\)):** \[\neg E = \neg(C \vee S \vee M)\]
3. **Aplicar a Lei de De Morgan para distribuir a negação:** A lei estabelece que a negação de uma disjunção ("OU") equivale à conjunção ("E") das proposições individualmente negadas. \[\neg E = \neg C \wedge \neg S \wedge \neg M\]

**Resultado:** O sistema físico negará o acesso apenas se o funcionário **não** possuir um cartão de acesso válido **E** **não** for membro da equipe de segurança **E** **não** for um gerente. Na tabela-verdade do circuito de segurança, o bloqueio (\(\neg E = 1\)) ocorrerá exclusivamente no estado de entrada binário \(000\).

**Por que essa solução funciona:** A equivalência lógica provada pelas tabelas-verdade das Leis de De Morgan garante que os dois caminhos de escrita produzem exatamente as mesmas saídas booleanas sob qualquer combinação de estados físicos das portas de entrada.

**O que preciso aprender com esse exemplo:** Negar uma escolha com "OU" (\(P \vee Q\)) exige que **ambas** as condições individuais deixem de acontecer ao mesmo tempo. Essa conversão simplifica a escrita de códigos de testes unitários e otimiza a velocidade de processamento lógico de circuitos de hardware digital.