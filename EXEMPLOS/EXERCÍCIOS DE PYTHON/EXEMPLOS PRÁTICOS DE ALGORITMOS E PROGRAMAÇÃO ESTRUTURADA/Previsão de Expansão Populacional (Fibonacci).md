**Problema:** Criar um modelo matemático preditivo que calcule e exiba de forma sequencial os primeiros `N` termos da Sequência de Fibonacci para prever o crescimento populacional de coelhos ao longo de gerações sucessivas.

**Conceito utilizado:** Processamento determinístico iterativo baseado na soma lógica de elementos precedentes.

**Solução:**

```
#include <stdio.h>

int main() {
    int n;
    int primeiro = 0, segundo = 1, proximo;
    
    printf("Digite o número de termos da sequência de Fibonacci que você deseja calcular: ");
    scanf("%d", &n);
    
    printf("Sequência de Fibonacci até o termo %d:\n", n);
    
    for (int i = 0; i < n; i++) {
        if (i <= 1) {
            proximo = i; // Define de forma direta os dois valores iniciais da sequência (0 e 1)
        } else {
            proximo = primeiro + segundo; // Soma dos dois termos anteriores
            primeiro = segundo;           // Deslocamento da janela lógica de valores para a direita
            segundo = proximo;
        }
        printf("%d ", proximo);
    }
    printf("\n");
    return 0;
}
```

**Resultado:** Imprime sequencialmente os primeiros `N` termos da sequência (ex: para `N = 5 -> 0 1 1 2 3`).

**Por que essa solução funciona:** A cada iteração do laço `for`, as posições anteriores (`primeiro` e `segundo`) deslizam para a direita na sequência numérica, permitindo que a próxima iteração calcule o termo seguinte baseando-se sempre na soma atualizada dos dois termos anteriores.

**O que preciso aprender com esse exemplo:** Séries matemáticas que dependem de valores gerados em passagens anteriores podem ser implementadas em loops de forma otimizada simplesmente rotacionando os valores entre variáveis de controle auxiliares ao fim de cada ciclo.