- **Problema:** Um programador está desenvolvendo o firmware de controle de um sistema de microcontroladores embarcados. Ele recebe a leitura física de um sensor em formato **binário** de 12 bits: $001111101011_2$. Para facilitar a depuração visual rápida do sinal no terminal, o programador precisa:
    
    1. Converter o número binário do sensor para a **base octal (base 8)**.
    2. Converter o mesmo valor gerado para a **base hexadecimal (base 16)** para inserção em diagramas esquemáticos de circuito impresso da placa.
- **Conceito utilizado:** Conversão rápida por agrupamento de bits, agrupando os bits de **3 em 3** para base octal (\(2^3 = 8\)) e de **4 em 4** para base hexadecimal (\(2^4 = 16\)).
    
- **Solução:** A execução da conversão direta por agrupamentos de bits ocorre nos seguintes passos lógicos:
    
    ##### Etapa 1: Converter Binário para Octal (\(001111101011_2 \rightarrow \text{Octal}\)):
    
    1. Escrever a cadeia binária de 12 bits e agrupá-la em blocos de **três bits**, começando de trás para frente (da direita para a esquerda): $$\text{Blocos:} \quad \quad \quad \quad$$
    2. Traduzir cada trio de bits binários em um único algarismo octal (0 a 7) com o auxílio da tabela de referência:
        - \(001_2 \rightarrow 1_8\)
        - \(111_2 \rightarrow 7_8\)
        - \(101_2 \rightarrow 5_8\)
        - \(011_2 \rightarrow 3_8\)
    3. Unir os símbolos lógicos: $1753_8$.
    
    ##### Etapa 2: Converter Octal para Hexadecimal (\(1753_8 \rightarrow \text{Hexadecimal}\)):
    
    4. Como 8 e 16 não são múltiplos diretos de potências simples, usa-se a base binária como ponte.
    5. Expandir os dígitos octais em blocos de 3 bits para restabelecer o binário original (\(001111101011_2\)).
    6. Reagrupar a mesma cadeia binária em novos blocos de **quatro bits**, começando da direita para a esquerda: $$\text{Novos blocos:} \quad \quad \quad $$ _(Nota explicativa: O PDF original possui uma pequena errata visual na linha de conversão do primeiro quarteto ao escrever $011 \rightarrow 3$, mas logo em seguida corrige o agrupamento inteiro para o quarteto correto de quatro bits $0011 \rightarrow 3$)_.
    7. Converter cada bloco de 4 bits para o símbolo hexadecimal correspondente:
        - \(0011_2 \rightarrow 3_{16}\)
        - \(1110_2 \rightarrow E_{16}\) (decimal 14)
        - \(1011_2 \rightarrow B_{16}\) (decimal 11)
    8. Unir os caracteres hexadecimais: $3EB_{16}$.
- **Resultado:** O sinal binário foi convertido para **$1753_8$** para depuração em tempo de execução e para **$3EB_{16}$** para os diagramas físicos e firmware.
    
- **Por que essa solução funciona:** Esta técnica funciona porque as bases 8 e 16 pertencem à mesma família de potência de base 2 ($2^3$ e $2^4$). Agrupar ou expandir bits binários em trios ou quartetos substitui completamente as divisões e multiplicações matemáticas, garantindo 100% de precisão de forma muito rápida.
    
- **O que preciso aprender com esse exemplo:** Para ir de octal para hexadecimal, **sempre utilize o binário como intermediário**, transformando o octal em grupos de 3 bits e reagrupando-os em blocos de 4 bits.