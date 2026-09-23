- **Problema:** Um engenheiro precisa desenvolver um sistema de controle de vagas para um estacionamento inteligente. Os painéis eletrônicos de exibição e os sistemas de processamento central operam unicamente na **base decimal (base 10)**, mas os sensores físicos de vagas enviam informações codificadas em formatos diferentes conforme o fabricante:
    
    - O **Sensor 1** envia dados em formato hexadecimal: \(B5_{16}\).
    - O **Sensor 2** envia dados em formato binário: \(11001100_2\).
    
    Como traduzir ambas as leituras para o formato decimal exigido pelo sistema central?
    
- **Conceito utilizado:** Conversão posicional de polinômios com potências da base original ($2^{\text{posição}}$ para binários e $16^{\text{posição}}$ para hexadecimais).
    
- **Solução:** Resolver a conversão de cada sensor de forma individualizada:
    
    ##### Conversão do Sensor 1 (\(B5_{16} \rightarrow \text{Decimal}\)):
    
    1. Separar os símbolos do número hexadecimal e anotar suas posições da direita para a esquerda, iniciando do zero:
        - Dígito \(5 \rightarrow \text{posição } 0\)
        - Dígito \(B \rightarrow \text{posição } 1\)
    2. Converter as letras para seus valores decimais equivalentes:
        - \(B = 11_{10}\).
    3. Multiplicar cada dígito pela base 16 elevada ao expoente da posição: $$\text{Valor} = (11 \times 16^1) + (5 \times 16^0)$$
    4. Calcular os termos exponenciais ($16^1 = 16$ e $16^0 = 1$): $$\text{Valor} = (11 \times 16) + (5 \times 1) = 176 + 5 = 181$$
    5. Resultado do Sensor 1: $181_{10}$.
    
    ##### Conversão do Sensor 2 (\(11001100_2 \rightarrow \text{Decimal}\)):
    
    6. Escrever o número binário e associar a potência de base 2 correspondente a cada posição onde o bit for igual a 1 (da direita para a esquerda, iniciando da posição 0):
        - Bit 1 na posição 7 \(\rightarrow 1 \times 2^7 = 128\)
        - Bit 1 na posição 6 \(\rightarrow 1 \times 2^6 = 64\)
        - Bit 1 na posição 3 \(\rightarrow 1 \times 2^3 = 8\)
        - Bit 1 na posição 2 \(\rightarrow 1 \times 2^2 = 4\)
        - Os bits das posições 5, 4, 1 e 0 são iguais a 0 \(\rightarrow\) somam 0.
    7. Somar todos os valores obtidos: $$\text{Soma} = 128 + 64 + 0 + 0 + 8 + 4 + 0 + 0 = 204$$
    8. Resultado do Sensor 2: $204_{10}$.
- **Resultado:** Os dados dos sensores são integrados ao servidor central decimal como vaga número **181** e vaga número **204**, respectivamente.
    
- **Por que essa solução funciona:** Toda base posicional numérica funciona sob o teorema polinomial, onde o peso geométrico de cada caractere é regido pelo termo $\text{Dígito} \times \text{Base}^{\text{posição}}$. Ao somarmos os termos ponderados, trazemos o valor físico absoluto para a base decimal.
    
- **O que preciso aprender com esse exemplo:** Para converter qualquer base para decimal, basta multiplicar os dígitos pelas potências crescentes da base original e somar os resultados.