**Problema:** Calcular a média aritmética entre duas notas bimestrais inseridas pelo usuário. Se a média for igual ou superior a seis, o aluno é aprovado; caso contrário, reprovado.

**Conceito utilizado:** Representação gráfica por diagramas de bloco (fluxogramas) e transposição para a sintaxe C.

**Solução:** O fluxo gráfico (losangos para decisão, retângulos para processamento) é convertido no seguinte programa em C:

```
#include <stdio.h>

int main() {
    float num1, num2, media;
    
    printf("Digite o primeiro numero: ");
    scanf("%f", &num1);
    
    printf("Digite o segundo numero: ");
    scanf("%f", &num2);
    
    media = (num1 + num2) / 2;
    
    printf("Media = %.2f", media);
    return 0;
}
```

**Resultado:** O programa recebe os valores reais das notas, realiza o cálculo aritmético correto e exibe a média final arredondada para duas casas decimais.

**Por que essa solução funciona:** Os parênteses na expressão `(num1 + num2) / 2` forçam a precedência da soma antes da divisão. O uso do operador `&` no `scanf` repassa os endereços físicos de memória para que o computador salve os valores digitados.

**O que preciso aprender com esse exemplo:** Sempre isole operações de menor precedência (como a soma) com parênteses quando precisar que elas ocorram antes de operações de maior precedência (como a divisão)