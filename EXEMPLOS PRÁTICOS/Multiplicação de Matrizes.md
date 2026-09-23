**Problema:** Ler duas matrizes de dimensões quaisquer informadas pelo usuário, validar se a operação de multiplicação é matematicamente viável e calcular a matriz produto resultante.

**Conceito utilizado:** Validação de regras de álgebra linear, matriz de dimensão dinâmica e laços `for` triplamente aninhados.

**Solução:**

```
#include <stdio.h>

int main() {
    int m, n, p, q, i, j, k;
    int soma = 0;
    
    printf("Digite as dimensões da primeira matriz (m x n): ");
    scanf("%d %d", &m, &n);
    printf("Digite as dimensões da segunda matriz (p x q): ");
    scanf("%d %d", &p, &q);
    
    // Validação matemática obrigatória
    if (n != p) {
        printf("A multiplicação entre as matrizes não é possível.\n");
        return 0;
    }
    
    // Declaração de matrizes baseando-se nas dimensões informadas
    int matriz1[m][n], matriz2[p][q], resultado[m][q];
    
    printf("Digite os elementos da primeira matriz:\n");
    for (i = 0; i < m; i++) {
        for (j = 0; j < n; j++) {
            scanf("%d", &matriz1[i][j]);
        }
    }
    
    printf("Digite os elementos da segunda matriz:\n");
    for (i = 0; i < p; i++) {
        for (j = 0; j < q; j++) {
            scanf("%d", &matriz2[i][j]);
        }
    }
    
    // Processamento da multiplicação de matrizes por laços triplos
    for (i = 0; i < m; i++) {
        for (j = 0; j < q; j++) {
            for (k = 0; k < p; k++) {
                soma += matriz1[i][k] * matriz2[k][j];
            }
            resultado[i][j] = soma;
            soma = 0; // Zera o acumulador para calcular a próxima célula
        }
    }
    
    printf("O produto das matrizes é:\n");
    for (i = 0; i < m; i++) {
        for (j = 0; j < q; j++) {
            printf("%d\t", resultado[i][j]);
        }
        printf("\n");
    }
    return 0;
}
```

**Resultado:** Calcula com exatidão a matriz produto resultante, estruturando e imprimindo a tabela de dados formatada no terminal.

**Por que essa solução funciona:** A multiplicação de matrizes exige que o número de colunas da primeira matriz (`n`) seja exatamente igual ao número de linhas da segunda matriz (`p`). A célula resultante da linha `i` e coluna `j` é calculada pela soma cumulativa da multiplicação ordenada de cada elemento da linha `i` da primeira matriz com a coluna `j` da segunda. Isso exige um terceiro loop interno (`k`).

**O que preciso aprender com esse exemplo:** O desenvolvimento do algoritmo de multiplicação de matrizes é um clássico de provas e exige o uso estruturado de três laços `for` aninhados.