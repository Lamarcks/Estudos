**Problema:** Demonstrar a aplicação matemática da Conjectura de Collatz. Dado um número de entrada `n > 1`: se `n` for par, ele é dividido por 2; se `n` for ímpar, ele é multiplicado por 3 e somado 1. O processo se repete até que o número atinja o valor 1.

**Conceito utilizado:** Operador de módulo (`%`), atribuição composta (`/=`) e repetição `while` de critério dinâmico.

**Solução:**

```
#include <stdio.h>
#include <stdlib.h>

int main() {
    int num, i;
    
    printf("\n\nDigite um numero: ");
    scanf("%d", &num);
    i = 0;
    
    while (num > 1) {
        if (num % 2 == 0) {
            num /= 2; // Atribuição composta (equivalente a num = num / 2)
        } else {
            num = 3 * num + 1;
        }
        printf("\n%d\n", num);
        i++;
    }
    
    return 0;
}
```

**Resultado:** Gera e imprime em linhas sequenciais todas as transformações matemáticas do número inserido até que ele seja reduzido a 1.

**Por que essa solução funciona:** O comando `num % 2 == 0` avalia se o resto da divisão por 2 é zero para determinar a paridade do número. A instrução `num /= 2` condensa o processamento reduzindo o número pela metade. A condição de parada `num > 1` encerra o laço assim que a sequência matemática atinge o valor de estabilização 1.

**O que preciso aprender com esse exemplo:** Operadores de atribuição composta (como `+=`, `-=`, `/=`, `*=`) reduzem a redundância na digitação do código, realizando operações matemáticas na variável diretamente no lado esquerdo da igualdade.

