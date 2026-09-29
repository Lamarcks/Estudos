**Problema:**  
Classificar indivíduos em três diferentes faixas etárias ("Menor de idade", "Adulto" ou "Idoso") com base em um valor numérico de idade.

**Conceito utilizado:**  
Operadores relacionais (`<`, `>=`), operador booleano (`and`) e estruturas condicionais encadeadas (`if`, `elif`, `else`).

**Solução:**

```
idade = 25  

if idade < 18:
    print("Menor de idade")
elif idade >= 18 and idade < 65:
    print("Adulto")
else:
    print("Idoso")
```

**Resultado:**  
Impressão textual exata correspondente à faixa lógica onde a idade se enquadra (neste caso, "Adulto").

**Por que essa solução funciona:**  
O Python avalia a sequência estruturada de cima para baixo. Ao atingir a condição `elif` verdadeira (25 é maior que 18 E menor que 65), ele executa o bloco interno e ignora as avaliações subsequentes.

**O que preciso aprender com esse exemplo:**  
O `elif` evita aninhamentos confusos de `if` estruturados e interrompe a avaliação lógicas assim que um critério é satisfeito.