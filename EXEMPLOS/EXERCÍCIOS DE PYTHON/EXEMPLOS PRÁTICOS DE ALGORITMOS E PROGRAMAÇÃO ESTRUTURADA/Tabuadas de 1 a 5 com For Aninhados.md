**Problema:** Imprimir sequencialmente as tabuadas completas de multiplicação dos números de 1 a 5, separando cada tabuada por uma quebra de linha física na tela do computador.

**Conceito utilizado:** Laços determinísticos aninhados (`for` internos dentro de `for` externos).

**Solução:**

```
#include <stdio.h>

int main() {
    int multi, num;
    
    // O laço externo controla qual tabuada está sendo calculada (1 a 5)
    for (num = 1; num <= 5; num++) {
        // O laço interno realiza as multiplicações de 1 a 10
        for (multi = 1; multi <= 10; multi++) {
            printf("%d ", num * multi);
        }
        printf("\n"); // Quebra de linha realizada no encerramento do laço interno
    }
    
    return 0;
}
```

**Resultado:** Gera na tela uma matriz organizada com 5 linhas horizontais, onde cada linha exibe os múltiplos das tabuadas correspondentes.

**Por que essa solução funciona:** Para cada ciclo único de execução do loop externo (`num`), o loop interno é acionado e executa de forma independente o seu ciclo completo de 10 repetições (`multi` de 1 a 10). O comando `printf("\n")` é posicionado estrategicamente após o término do loop interno para garantir que a próxima tabuada inicie em uma linha limpa de baixo.

**O que preciso aprender com esse exemplo:** Loops aninhados executam em velocidade multiplicativa: o número total de execuções das instruções internas é igual ao produto de repetições do laço externo pelo laço interno.