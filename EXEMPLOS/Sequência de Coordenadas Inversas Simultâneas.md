**Problema:** Imprimir na tela uma sequência lógica onde duas variáveis de controle sofrem modificações simultâneas: a variável `x` deve decrescer de 10 até 0, enquanto a variável `y` deve crescer de 0 até 10 ao mesmo tempo.

**Conceito utilizado:** Manipulação multivariável e atribuições múltiplas no cabeçalho do laço `for`.

**Solução:**

```
#include <stdio.h>
#include <stdlib.h>

int main() {
    // Declaração, inicialização, condições e passos lógicos feitos de forma dupla no cabeçalho
    for (int x = 10, y = 0; x >= 0 && y <= 10; x--, y++) {
        printf("x = %d, y = %d\n", x, y);
    }
    return 0;
}
```

**Resultado:** Exibição passo a passo de linhas de coordenadas contendo os valores inversos das duas variáveis de controle.

**Por que essa solução funciona:** A linguagem C permite que você utilize a vírgula (`,`) como separador para inicializar variáveis e aplicar incrementos ou decrementos de forma múltipla no cabeçalho do laço `for`. As condições lógicas são mantidas ativas pela conjunção lógica `&&`.

**O que preciso aprender com esse exemplo:** Variáveis declaradas diretamente dentro do cabeçalho de inicialização de um laço `for` têm escopo local em relação àquela iteração e serão permanentemente apagadas da memória do computador pelo compilador assim que o laço se encerrar.