**Problema:** Gerar a tabuada de um número de forma estruturada utilizando uma sintaxe de loop concisa e compactada em uma única instrução.

**Conceito utilizado:** Estrutura de repetição determinística (`for`).

**Solução:**

```
#include <stdio.h>

int main() {
    int multiplicador, resultado, num;
    
    printf("Tabuada de qual numero: ");
    scanf("%d", &num);
    
    // Sintaxe compacta de iteração
    for (multiplicador = 0; multiplicador <= 10; multiplicador++) {
        resultado = num * multiplicador;
        printf("%d x %d = %d\n", num, multiplicador, resultado);
    }
    
    return 0;
}
```

**Resultado:** Calcula e exibe de forma iterativa as 11 multiplicações associadas ao valor inserido.

**Por que essa solução funciona:** O laço `for` agrupa três expressões obrigatórias: **Inicialização** (`multiplicador = 0`), **Condição de permanência** (`multiplicador <= 10`) e **Instrução de Incremento** (`multiplicador++`) de maneira isolada em seu cabeçalho.

**O que preciso aprender com esse exemplo:** _Nota de Depuração:_ No exemplo fornecido na página original do PDF, o cabeçalho continha a linha `for(multiplicador=10; multiplicador<10; multiplicador++)`. Esse código possui uma falha de lógica: como o multiplicador começa em 10, o teste lógico `10 < 10` retorna falso imediatamente, impedindo o loop de rodar qualquer repetição. Isso exemplifica por que devemos revisar e planejar com cuidado a lógica dos limites de nossos loops determinísticos para provas!