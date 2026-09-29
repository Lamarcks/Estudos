Exemplo: Soma de Antecessores de um Número (Recursiva)

**Problema:** Calcular a soma de todos os números inteiros positivos antecessores de um valor `N` informado (ex: se `N = 5`, deve calcular e exibir o resultado de $5 + 4 + 3 + 2 + 1 + 0$)168.

**Conceito utilizado:** Recursividade, empilhamento dinâmico na memória RAM e caso base de parada169170.

**Solução:**

```
#include <stdio.h>

// Função recursiva de soma acumulada
int somar(int valor) {
    if (valor != 0) { // Critério de parada / Validação
        return valor + somar(valor - 1); // Auto-chamada passando parâmetro decrementado
    } else {
        return valor; // Caso base: valor == 0 retorna 0 e interrompe a recursão
    }
}

int main() {
    int n, resultado;
    printf("\nDigite um numero inteiro positivo: ");
    scanf("%d", &n);
    
    resultado = somar(n); // Primeira chamada do motor recursivo
    
    printf("\nResultado da soma = %d\n", resultado);
    return 0;
}
```

**Resultado:** Retorna a soma aritmética exata de todos os termos antecessores até o zero171.

**Por que essa solução funciona:** O computador cria instâncias independentes da função na pilha de execução do sistema enquanto o critério de parada `valor != 0` for atendido172173. Quando `valor` atinge zero (caso base), as execuções começam a retornar os valores para as instâncias anteriores na pilha de memória de forma reversa, somando termo por termo até encerrar o ciclo170174.

**O que preciso aprender com esse exemplo:** Toda função recursiva necessita de uma verificação condicional que direcione a execução para o **caso base**, interrompendo as auto-chamadas consecutivas170.