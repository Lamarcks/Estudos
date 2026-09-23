**Problema:** Preencher um vetor de números inteiros de tamanho 3 com dados capturados do teclado e, em seguida, gerar uma saída que exiba o dobro de cada um dos valores informados.

**Conceito utilizado:** Passagem implícita por referência de vetores unidimensionais para sub-rotinas sem retorno (`void`).

**Solução:**

```
#include <stdio.h>

// Procedimento de preenchimento (passagem implícita por referência)
void inserir(int a[]) {
    int i = 0;
    for (i = 0; i < 3; i++) {
        printf("Digite o valor %d: ", i);
        scanf("%d", &a[i]); // Altera os dados de forma definitiva na memória principal
    }
}

// Procedimento de exibição de dados
void imprimir(int b[]) {
    int i = 0;
    for (i = 0; i < 3; i++) {
        printf("\n numeros[%d] = %d", i, 2 * b[i]);
    }
    printf("\n");
}

int main() {
    int numeros[35];
    printf("\n Preenchendo o vetor... \n");
    inserir(numeros); // Passagem do vetor sem colchetes ou operadores adicionais
    printf("\n Dobro dos valores informados:");
    imprimir(numeros);
    return 0;
}
```

**Resultado:** O programa atualiza os dados do vetor com as entradas digitadas pelo usuário e exibe as multiplicações dobradas corretas.

**Por que essa solução funciona:** Em C, a passagem de arrays (vetores e matrizes) para funções ocorre **sempre de forma implícita por referência**. O compilador não faz cópias do vetor físico na memória RAM; ele simplesmente envia à sub-rotina o endereço físico da primeira célula (`índice 0`) do vetor original, permitindo que a função o manipule livremente.

**O que preciso aprender com esse exemplo:** Ao passar vetores para funções, não utilize os símbolos de colchetes ou operadores de ponteiro no argumento da chamada; passe apenas o nome identificador do vetor de forma limpa.