**Problema:** Ler uma matriz bidimensional quadrada de tamanho 3x3 e retornar a soma de todos os elementos contidos em sua diagonal principal e em sua diagonal secundária.

**Conceito utilizado:** Matriz bidimensional dinâmica, indexação matemática e manipulação de índices de linhas e colunas de forma simultânea.

**Solução:**

```
#include <stdio.h>

int main() {
    int matriz[35];
    int i, j, sDiagPrinc = 0, sDiagSec = 0;
    
    printf("Digite os elementos da matriz 3x3:\n");
    // Loops aninhados para ler os elementos de forma estruturada (linhas e colunas)
    for (i = 0; i < 3; i++) {
        for (j = 0; j < 3; j++) {
            scanf("%d", &matriz[i][j]);
        }
    }
    
    // Cálculo otimizado das diagonais com manipulação de índices em um único laço
    for (i = 0, j = 2; i < 3 && j >= 0; i++, j--) {
        sDiagPrinc += matriz[i][i]; // Diagonal principal: índices idênticos
        sDiagSec += matriz[i][j];   // Diagonal secundária: linhas sobem, colunas descem
    }
    
    printf("Soma dos elementos da diagonal principal: %d\n", sDiagPrinc);
    printf("Soma dos elementos da diagonal secundaria: %d\n", sDiagSec);
    return 0;
}
```

**Resultado:** Calcula e exibe com precisão a soma aritmética de ambas as diagonais da tabela numérica quadrada.

**Por que essa solução funciona:** Na diagonal principal, o índice da linha é sempre igual ao da coluna (posições ``, e ``). Na diagonal secundária, enquanto as linhas crescem sequencialmente, o índice das colunas deve decrescer sequencialmente (posições ``, `` e ``).

**O que preciso aprender com esse exemplo:** A leitura ou varredura de dados tabulares bidimensionais (matrizes) é feita utilizando **laços aninhados**, onde o laço externo controla a navegação pelas linhas e o laço interno percorre cada coluna daquela linha.