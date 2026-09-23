**Problema:** Calcular a aproximação de raiz quadrada de um número com alta precisão matemática utilizando a equação recursiva de Newton180181: $$x_n = \frac{x_{n-1} + \frac{n}{x_{n-1}}}{2}$$

**Conceito utilizado:** Recursão complexa matemática, inclusão da biblioteca `<math.h>`, uso de funções de valor absoluto (`fabs()`), potenciação (`pow()`) e critério de parada de alta precisão182183.

**Solução:**

```
#include <stdio.h>
#include <math.h>

// Função recursiva com precisão de parada decimal
float calcularRaiz(float n, float raizAnt) {
    // Implementação matemática da fórmula de aproximação de Newton
    float raiz = (pow(raizAnt, 2) + n) / (2 * raizAnt);
    
    // Critério de precisão: diferença entre a raiz atual e anterior menor que 0.001
    if (fabs(raiz - raizAnt) < 0.001) {
        return raiz; // Retorna o valor se atingir a precisão
    }
    
    // Auto-chamada passando a raiz aproximada como novo chute
    return calcularRaiz(n, raiz);
}

int main() {
    float numero, raiz;
    printf("\nDigite um número para calcular a raiz: ");
    scanf("%f", &numero);
    
    // Inicialização passando o número e a sua metade como o chute inicial (chute = numero / 2)
    raiz = calcularRaiz(numero, numero / 2);
    
    printf("\nRaiz quadrada: %f\n", raiz);
    return 0;
}
```

**Resultado:** O programa aproxima e exibe a raiz quadrada exata do número com precisão de três casas decimais184.

**Por que essa solução funciona:** A função `calcularRaiz` realiza de forma dinâmica o refino matemático do palpite inicial utilizando a fórmula de Newton183. A cada auto-chamada recursiva, o palpite se aproxima mais do valor real de raiz183. O loop recursivo é interrompido pelo comando `fabs(raiz - raizAnt) < 0.001` quando a variação numérica entre aproximações consecutivas for insignificante, garantindo a precisão182183.

**O que preciso aprender com esse exemplo:** A recursividade é uma excelente escolha para implementar métodos matemáticos numéricos iterativos e de aproximações sucessivas, permitindo parametrizar o limite de precisão do cálculo de forma dinâmica183185.