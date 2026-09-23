**Problema:** Calcular o fatorial de um número inteiro positivo `N` ($N! = N \times (N-1) \times (N-2) \times \dots \times 1$) utilizando uma lógica de código elegante175.

**Conceito utilizado:** Auto-chamada recursiva aplicada ao cálculo do caso básico de fatorial ($0! = 1$)175176.

**Solução:**

```
#include <stdio.h>

// Função recursiva para cálculo de fatorial
int fatorial(int valor) {
    if (valor > 0) { // Critério de parada
        return valor * fatorial(valor - 1); // Auto-chamada multiplicativa
    } else {
        return 1; // Caso base: 0! equivale matematicamente a 1
    }
}

int main() {
    int n, resultado;
    printf("\nDigite um numero inteiro positivo: ");
    scanf("%d", &n);
    
    resultado = fatorial(n); // Dispara o motor recursivo
    
    printf("\nResultado do fatorial = %d\n", resultado);
    return 0;
}
```

**Resultado:** Gera o cálculo do fatorial de forma elegante, resolvendo internamente toda a pilha matemática de multiplicações175176.

**Por que essa solução funciona:** A execução cria instâncias independentes que mantêm operações de multiplicação pendentes na memória RAM176. Ao atingir a verificação de parada do caso base (`valor = 0`), a função retorna o valor neutro `1`, disparando a resolução matemática em cascata das multiplicações de volta para o topo da pilha176177.

**O que preciso aprender com esse exemplo:** A recursividade simplifica a implementação de lógicas matemáticas de natureza recursiva (problemas maiores que são formados por versões menores de si mesmos), embora consuma mais espaço físico de memória RAM para gerenciar o empilhamento das instâncias ativas do que laços de repetição tradicionais178179.