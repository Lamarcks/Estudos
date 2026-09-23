**Problema:** Calcular a área total (metragem quadrada) de vários terrenos sem a necessidade de fechar e reabrir o programa a cada novo cálculo.

**Conceito utilizado:** Laço de repetição com teste lógico no fim (`do...while`).

**Solução:**

```
#include <stdio.h>

int main() {
    float metragem1 = 0, metragem2 = 0, resultado = 0;
    int resp;
    
    do {
        printf("Calculo de metros quadrados\n\n");
        
        printf("Digite a 1a metragem do terreno: ");
        scanf("%f", &metragem1);
        
        printf("\nDigite a 2a metragem do terreno: ");
        scanf("%f", &metragem2);
        
        resultado = (metragem1 * metragem2);
        printf("\n\nTerreno tem = %.2f m2 \n", resultado);
        
        printf("Digite 1 para continuar ou 2 para sair\n");
        scanf("%d", &resp);
        
    } while (resp == 1); // Condição de parada testada no fim do bloco
    
    return 0;
}
```

**Resultado:** O programa executa os cálculos de metragem e continua solicitando novas dimensões enquanto o usuário digitar o número `1` na pergunta de continuidade.

**Por que essa solução funciona:** A estrutura `do...while` executa o seu bloco de comandos pelo menos uma vez antes de avaliar a condição lógica posicionada na linha `while (resp == 1);`. Se o valor de `resp` for `1`, o programa realiza um salto de volta para o topo (`do`), iniciando uma nova rodada de processamento.

**O que preciso aprender com esse exemplo:** Utilize o laço `do...while` quando as instruções internas precisarem ser executadas obrigatoriamente no mínimo uma vez antes que qualquer verificação lógica de repetição seja feita.