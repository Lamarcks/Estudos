- **Problema:** Um engenheiro de sistemas está projetando um sistema de controle de tráfego aéreo. O sistema antigo utiliza dados de radar históricos gravados em formato **octal (base 8)**, mas o novo banco de dados central opera em **decimal (base 10)**. Além disso, a nova antena do radar de empresas parceiras transmite sinais rápidos em **hexadecimal (base 16)**, mas o módulo de análise de risco do sistema do aeroporto só compreende instruções em **binário (base 2)**.
    
    É preciso:
    
    1. Converter o registro histórico octal $253_8$ para o formato decimal do novo sistema.
    2. Desenvolver um algoritmo de tradução instantânea para converter a leitura de radar $A3_{16}$ em binário.
- **Conceito utilizado:** Método posicional de conversão octal-decimal e conversão direta hexadecimal-binário baseada em substituição por tabelas de 4 bits.
    
- **Solução:** Executar as duas tarefas de forma segmentada:
    
    ##### Parte 1: Conversão de Octal para Decimal (\(253_8 \rightarrow \text{Decimal}\)):
    
    1. Escrever o número octal e identificar o peso posicional de base 8 de cada dígito da direita para a esquerda ($8^2$, $8^1$, $8^0$).
    2. Aplicar a multiplicação posicional: $$\text{Valor} = (2 \times 8^2) + (5 \times 8^1) + (3 \times 8^0)$$ _(Nota: No PDF original, há uma pequena errata de digitação na linha da fórmula que repete $3 \times 8^1$, mas os pesos e o cálculo de soma final são executados corretamente com base em $8^0$)_.
    3. Calcular as potências ($8^2 = 64$, $8^1 = 8$, $8^0 = 1$): $$\text{Valor} = (2 \times 64) + (5 \times 8) + (3 \times 1) = 128 + 40 + 3 = 171$$
    4. Resultado histórico: $171_{10}$.
    
    ##### Parte 2: Tradução Hexadecimal para Binário (\(A3_{16} \rightarrow \text{Binário}\)):
    
    1. Separar os caracteres hexadecimais: $A$ e $3$.
    2. Substituir diretamente cada dígito por seu bloco representativo de **4 bits** utilizando a tabela de equivalência direta:
        - O dígito \(A_{16}\) equivale ao valor decimal 10, representado como \(1010_2\) em binário.
        - O dígito \(3_{16}\) equivale ao valor decimal 3, representado como \(0011_2\) em binário.
    3. Unir os blocos em ordem: $$A3_{16} = 10100011_2$$
- **Resultado:**
    
    1. O registro antigo de radar $253_8$ foi gravado no novo banco como número **171** em decimal.
    2. O sinal de radar parceiro $A3_{16}$ foi interpretado instantaneamente pelo módulo de risco como a string binária $10100011_2$.
- **Por que essa solução funciona:** Funciona porque o método de expansão posicional por potências de 8 resolve o valor absoluto decimal do octal. Para a conversão do radar, a substituição direta funciona porque a base 16 é o quadrado perfeito da base binária agrupada em quatro níveis de bits (\(2^4 = 16\)), permitindo mapeamento de hardware direto sem divisões lógicas.
    
- **O que preciso aprender com esse exemplo:** Dígitos hexadecimais isolados sempre são expandidos em exatamente **4 bits** binários individuais para a conversão direta.