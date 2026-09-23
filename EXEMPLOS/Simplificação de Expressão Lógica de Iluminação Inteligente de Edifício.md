- **Problema:** Um engenheiro de hardware precisa projetar a placa eletrônica de controle para um sistema de iluminação de um prédio corporativo. A lâmpada do escritório deve acender (saída lógica 1) se qualquer uma das seguintes três condições ambientais medidas por sensores for atendida:
    
    1. O sensor de luz detecta escuro (\(A\)) **E** o sensor de presença detecta movimento (\(B\)).
    2. O sensor de luz detecta escuro (\(A\)) **E** o alarme de segurança predial está desativado (\(C\)).
    3. O sensor de presença detecta movimento (\(B\)) **E** o alarme predial está desativado (\(C\)).
    
    A expressão booleana bruta inicial desenvolvida pela equipe para governar a lâmpada é: $$S = AB + A(B+C) + B(B+C)$$
    
    O engenheiro precisa **simplificar ao máximo** essa expressão booleana para reduzir a quantidade de portas lógicas físicas na placa, barateando o circuito sem alterar a lógica de funcionamento.
    
- **Conceito utilizado:** Leis da álgebra de Boole: leis comutativa, associativa, distributiva, leis de absorção e teoremas básicos ($A+A=A$, $A \cdot A = A$, $A + AB = A$).
    
- **Solução:** Aplicar os teoremas booleanos passo a passo para compactar a expressão inicial:
    
    1. _Expressão inicial:_ $$S = AB + A(B+C) + B(B+C)$$
    2. _Aplicar a Lei Distributiva nos parênteses do segundo e terceiro termo:_ $$S = AB + AB + AC + BB + BC$$
    3. _Aplicar a Regra da Idempotência da Adição (\(AB + AB = AB\)) nos dois primeiros termos:_ $$S = AB + AC + BB + BC$$
    4. _Aplicar a Regra da Idempotência da Multiplicação (\(BB = B\)) no quarto termo:_ $$S = AB + AC + B + BC$$
    5. _Aplicar a Lei de Absorção (\(B + BC = B\)) agrupando o terceiro e quarto termo:_ $$S = AB + AC + B$$
    6. _Aplicar novamente a Lei de Absorção (\(AB + B = B\)) unindo o primeiro e o terceiro termo:_ $$S = B + AC$$
- **Resultado:** A expressão lógica totalmente simplificada é **$S = B + AC$**.
    
- **Por que essa solução funciona:** Esta simplificação é funcional porque as equivalências matemáticas discretas comprovam que os termos redundantes não afetam o resultado elétrico final. Em vez de usar cinco portas lógicas (três portas AND, duas portas OR) da expressão complexa original, o engenheiro precisa soldar apenas duas portas lógicas físicas no circuito final (uma porta AND para fazer $A \cdot C$, e uma porta OR para somar o resultado com $B$), mantendo exatamente a mesma equivalência lógica.
    
- **O que preciso aprender com esse exemplo:** A aplicação rigorosa de leis booleanas como a **Distribuição** ($A(B+C) = AB + AC$) e a **Absorção** (\(A + AB = A\)) reduz drasticamente a complexidade física, o consumo elétrico e o custo de fabricação de placas de circuitos.