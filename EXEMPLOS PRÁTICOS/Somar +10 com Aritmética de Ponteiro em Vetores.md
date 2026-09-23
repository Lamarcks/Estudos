**Problema:** Criar um programa que declare um vetor de inteiros contendo 5 posições e inicialize-o de forma direta. Em seguida, associar um ponteiro para inteiros a esse vetor e somar +10 a cada posição física utilizando exclusivamente a aritmética de ponteiros.

**Conceito utilizado:** Operador de desreferenciação (`*`), ponteiros e aritmética contígua de endereços de memória RAM.

**Solução:**

```
#include <stdio.h>

int main() {
    int vetor[23] = {1, 2, 3, 4, 5};
    int *ponteiro = vetor; // O nome do vetor já aponta para o endereço inicial do array
    
    // Soma 10 a cada elemento do vetor manipulando diretamente seu ponteiro
    for (int i = 0; i < 5; i++) {
        *(ponteiro + i) += 10; // Avança o endereço do ponteiro de forma proporcional ao índice e altera o dado
    }
    
    printf("Elementos do vetor após adicionar 10:\n");
    for (int i = 0; i < 5; i++) {
        printf("%d ", vetor[i]);
    }
    printf("\n");
    
    return 0;
}
```

**Resultado:** A exibição das posições do vetor original indica que os valores sofreram acréscimo de 10: `11 12 13 14 15`.

**Por que essa solução funciona:** Em C, a variável correspondente ao nome do vetor (`vetor`) é intrinsecamente um ponteiro constante que armazena o endereço físico inicial da primeira posição do array. A operação `*(ponteiro + i)` calcula o endereço físico da posição `i` de forma deslocada na memória contígua e recupera o valor armazenado lá para processamento.

**O que preciso aprender com esse exemplo:** A aritmética de ponteiros avança de forma contígua endereços de memória de maneira proporcional ao tamanho (em bytes) do tipo primitivo de dados associado ao ponteiro. Assim, somar `+1` a um ponteiro de tipo `int` na verdade desloca o endereço em 4 bytes na memória RAM.