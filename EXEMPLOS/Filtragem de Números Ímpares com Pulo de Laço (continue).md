**Problema:** Percorrer uma contagem lógica de números inteiros de 1 a 20 e exibir na tela exclusivamente os números ímpares, sem alterar o contador de repetições.

**Conceito utilizado:** Operador de módulo e instrução de desvio de iteração (`continue`).

**Solução:**

```
#include <stdio.h>

int main() {
    for (int i = 1; i <= 20; i++) {
        if (i % 2 == 0) {
            continue; // Pula as instruções restantes apenas para números pares
        }
        printf("%d ", i);
    }
    printf("\n");
    return 0;
}
```

**Resultado:** Exibição exclusiva dos números ímpares: `1 3 5 7 9 11 13 15 17 19`.

**Por que essa solução funciona:** Ao encontrar a instrução `continue` quando `i` é par, o compilador suspende imediatamente a execução do bloco de instruções atual (saltando o comando de impressão `printf`) e avança de forma direta para o passo de incremento do laço (`i++`), reavaliando a permanência do loop para o próximo ciclo.

**O que preciso aprender com esse exemplo:** Diferente do `break` que encerra definitivamente o laço, o comando `continue` apenas interrompe a rodada de execução atual e obriga o programa a avançar para a próxima iteração do mesmo laço.