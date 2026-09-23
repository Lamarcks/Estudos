- **Problema:** Um engenheiro aeroespacial precisa receber e traduzir em tempo real dados de sensores de radiação espacial emitidos por um satélite antigo da década de 1980. O satélite trabalha exclusivamente codificando dados em **hexadecimal (base 16)**, mas as novas estações modernas de recepção terrestre operam em **binário (base 2)**. É necessário converter os dados de hexadecimal para binário de forma rápida.
    
- **Conceito utilizado:** Conversão agrupada direta entre **Hexadecimal e Binário**, onde cada dígito de base 16 corresponde exatamente a um grupo fixo de 4 bits (sistema posicional binário $2^4 = 16$).
    
- **Solução:** Para codificar e decodificar as mensagens, aplicam-se regras de conversão direta baseadas em blocos lógicos de 4 bits:
    
    ##### Subproblema A: Converter os dados enviados do Satélite (Hex $\rightarrow$ Binário)
    
    1. Inicie a tradução pelo caractere hexadecimal localizado mais à esquerda.
    2. Substitua cada dígito hexadecimal isolado por seu equivalente binário direto de **4 bits**, utilizando a tabela de correspondência:
        - \(0 \rightarrow 0000_2\)
        - \(1 \rightarrow 0001_2\)
        - \(5 \rightarrow 0101_2\)
        - \(8 \rightarrow 1000_2\)
        - \(9 \rightarrow 1001_2\)
        - \(A \rightarrow 1010_2\)
        - \(B \rightarrow 1011_2\)
        - \(C \rightarrow 1100_2\)
        - \(D \rightarrow 1101_2\)
        - \(E \rightarrow 1110_2\)
        - \(F \rightarrow 1111_2\)
    3. Combine ordenadamente todos os quartetos de bits resultantes para obter o código final.
    
    ##### Exercício Prático: Converter a telemetria diária enviada pelo satélite:
    
    - _Dado 1: \(F1_{16}\)_
        - \(F \rightarrow 1111\)
        - \(1 \rightarrow 0001\)
        - Resultado: \(11110001_2\)
    - _Dado 2: \(CA_{16}\)_
        - \(C \rightarrow 1100\)
        - \(A \rightarrow 1010\)
        - Resultado: \(11001010_2\)
    - _Dado 3: \(DE_{16}\)_
        - \(D \rightarrow 1101\)
        - \(E \rightarrow 1110\)
        - Resultado: \(11011110_2\)
    
    ##### Subproblema B: Converter as instruções enviadas da Terra para o Satélite (Binário $\rightarrow$ Hex)
    
    1. Escreva o número binário e agrupe-o em conjuntos de **quatro bits**, iniciando da extrema direita (bit menos significativo) em direção à esquerda.
    2. Se o bloco mais à esquerda não possuir 4 dígitos, complete com zeros.
    3. Traduza cada quarteto binário para seu equivalente hexadecimal correspondente.
    
    ##### Exercício Prático: Converter a instrução terrestre $110100110101_2$:
    
    4. Agrupar da direita para a esquerda: $1101$, $0011$, $0101$.
    5. Trabalhar os pesos posicionais binários para cada quarteto (\(2^3, 2^2, 2^1, 2^0\)):
        - \(1101 \rightarrow (1 \times 8) + (1 \times 4) + (0 \times 2) + (1 \times 1) = 13 \rightarrow \text{D}\).
        - \(0011 \rightarrow (0 \times 8) + (0 \times 4) + (1 \times 2) + (1 \times 1) = 3\).
        - \(0101 \rightarrow (0 \times 8) + (1 \times 4) + (0 \times 2) + (1 \times 1) = 5\).
    6. Resultado em Hexadecimal: $D35_{16}$.
- **Resultado:** Tabela de aferições e comandos traduzida de forma ágil sem atrasos de processamento na estação terrestre.
    
- **Por que essa solução funciona:** Funciona porque 16 é uma potência exata de 2 (\(2^4=16\)). Isso possibilita que cada símbolo hexadecimal represente exatamente qualquer combinação possível de 4 bits, permitindo conversões puramente estruturais e agrupadas, eliminando a necessidade de realizar cálculos aritméticos complexos de divisão no processador.
    
- **O que preciso aprender com esse exemplo:** A conversão entre Binário e Hexadecimal é puramente baseada em agrupamento de **4 em 4 bits**, dispensando divisões aritméticas complicadas.