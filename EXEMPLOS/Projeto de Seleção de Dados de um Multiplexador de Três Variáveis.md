- **Problema:** Um engenheiro eletrônico precisa desenhar o circuito de um seletor de dados do tipo multiplexador. O circuito possui três variáveis lógicas de entrada física ($A$, $B$, $C$) que controlam a transmissão de sinais elétricos internos da placa. A função lógica matemática dada para orientar a saída $Z$ deste multiplexador é: $$Z = \bar{A}\bar{B}\bar{C} + \bar{A}B\bar{C} + ABC$$
    
    O engenheiro precisa construir e preencher a tabela verdade completa da saída $Z$ para todos os estados de entrada possíveis e compreender a lógica do circuito.
    
- **Conceito utilizado:** Mapeamento de expressões em **tabela verdade**, resolvendo termos de multiplicação lógica (AND) somados por operações de adição lógica (OR).
    
- **Solução:** Escrever todas as oito combinações binárias possíveis para as três entradas ($2^3 = 8$ estados) e testar a substituição de cada conjunto na expressão lógica $Z$:
    
    1. _Estado 1 (\(A=0, B=0, C=0\)):_ $$Z = (\bar{0} \cdot \bar{0} \cdot \bar{0}) + (\bar{0} \cdot 0 \cdot \bar{0}) + (0 \cdot 0 \cdot 0) = (1 \cdot 1 \cdot 1) + 0 + 0 = 1 + 0 + 0 = 1$$
    2. _Estado 2 (\(A=1, B=0, C=0\)):_ $$Z = (\bar{1} \cdot \bar{0} \cdot \bar{0}) + (\bar{1} \cdot 0 \cdot \bar{0}) + (1 \cdot 0 \cdot 0) = (0 \cdot 1 \cdot 1) + 0 + 0 = 0 + 0 + 0 = 0$$
    3. _Estado 3 (\(A=0, B=1, C=0\)):_ $$Z = (\bar{0} \cdot \bar{1} \cdot \bar{0}) + (\bar{0} \cdot 1 \cdot \bar{0}) + (0 \cdot 1 \cdot 0) = 0 + (1 \cdot 1 \cdot 1) + 0 = 0 + 1 + 0 = 1$$
    4. _Estado 4 (\(A=1, B=1, C=0\)):_ $$Z = (\bar{1} \cdot \bar{1} \cdot \bar{0}) + (\bar{1} \cdot 1 \cdot \bar{0}) + (1 \cdot 1 \cdot 0) = 0 + 0 + 0 = 0$$
    5. _Estado 5 (\(A=0, B=0, C=1\)):_ $$Z = (\bar{0} \cdot \bar{0} \cdot \bar{1}) + (\bar{0} \cdot 0 \cdot \bar{1}) + (0 \cdot 0 \cdot 1) = 0 + 0 + 0 = 0$$
    6. _Estado 6 (\(A=1, B=0, C=1\)):_ $$Z = (\bar{1} \cdot \bar{0} \cdot \bar{1}) + (\bar{1} \cdot 0 \cdot \bar{1}) + (1 \cdot 0 \cdot 1) = 0 + 0 + 0 = 0$$
    7. _Estado 7 (\(A=0, B=1, C=1\)):_ $$Z = (\bar{0} \cdot \bar{1} \cdot \bar{1}) + (\bar{0} \cdot 1 \cdot \bar{1}) + (0 \cdot 1 \cdot 1) = 0 + 0 + 0 = 0$$
    8. _Estado 8 (\(A=1, B=1, C=1\)):_ $$Z = (\bar{1} \cdot \bar{1} \cdot \bar{1}) + (\bar{1} \cdot 1 \cdot \bar{1}) + (1 \cdot 1 \cdot 1) = 0 + 0 + 1 = 1$$ _(Nota técnica: A tabela verdade impressa no PDF original contém pequenas erratas de digitação nos valores das saídas de algumas linhas intermediárias de teste, mas o mapeamento analítico da expressão resolvida em hardware segue o fluxo clássico booleano detalhado acima)_.
- **Resultado:** Tabela verdade preenchida, identificando com precisão em quais estados de seleção o multiplexador emitirá tensão lógica ativa (nível alto, 1) em sua saída física.
    
- **Por que essa solução funciona:** Esta solução funciona porque o multiplexador atua como um filtro lógico de hardware guiado por pinos seletores. Quando as entradas correspondem exatamente a um dos três termos lógicos da somatória ($A=0, B=0, C=0$ ou $A=0, B=1, C=0$ ou $A=1, B=1, C=1$), os transistores internos do chip fecham o circuito correspondente àquele ramo, liberando a passagem de tensão para a saída.
    
- **O que preciso aprender com esse exemplo:** A tabela verdade é construída testando sistematicamente todas as combinações binárias das entradas na expressão matemática lógica do circuito.