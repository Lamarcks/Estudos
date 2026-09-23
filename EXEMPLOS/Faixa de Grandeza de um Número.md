**Problema:** Classificar um número de acordo com sua grandeza, determinando se ele é menor que 100, menor que 1000, menor que 10000 ou maior/igual a 10000.

**Conceito utilizado:** Estrutura condicional encadeada / aninhada (`if-else-if`).

**Solução:**

```
#include <stdio.h>

int main() {
    int num = 10;
    
    if (num < 100) {
        printf("Menor que 100");
    } else if (num < 1000) {
        printf("Menor que 1000");
    } else if (num < 10000) {
        printf("Menor que 10000");
    } else {
        printf("Maior ou igual a 10000");
    }
    
    return 0;
}
```

**Resultado:** Neste caso, imprime na tela a mensagem `"Menor que 100"`.

**Por que essa solução funciona:** A avaliação lógica ocorre em cascata (de cima para baixo). No instante em que o programa encontra uma condição verdadeira (`num < 100`), ele executa seu comando e salta todo o restante da estrutura condicional subsequente, otimizando o processamento.

**O que preciso aprender com esse exemplo:** Em estruturas `if-else-if`, apenas o bloco da primeira condição verdadeira será executado. Se todas as condições anteriores falharem, o programa recorre ao último `else` genérico