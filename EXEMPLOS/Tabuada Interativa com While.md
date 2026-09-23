**Problema:** Gerar a tabuada de multiplicação de 0 a 10 para qualquer número inteiro solicitado ao usuário.

**Conceito utilizado:** Laço de repetição com teste condicional no início (`while`).

**Solução:**

```
#include <stdio.h>

int main() {
    int multiplicador = 0, resultado, num;
    
    printf("Tabuada de qual numero: ");
    scanf("%d", &num);
    
    while (multiplicador <= 10) {
        resultado = num * multiplicador;
        printf("%d x %d = %d\n", num, multiplicador, resultado);
        multiplicador = multiplicador + 1; // Incremento da variável de controle
    }
    
    return 0;
}
```

**Resultado:** Exibe as multiplicações de 0 a 10 do número de forma sequencial na tela.

**Por que essa solução funciona:** A variável `multiplicador` serve como o contador de controle do laço. O teste lógico `multiplicador <= 10` é verificado no início de cada iteração. Como a variável de controle é incrementada de 1 em 1 dentro do laço, ela eventualmente chega a 11, tornando a expressão de teste falsa e encerrando o laço de forma segura.

**O que preciso aprender com esse exemplo:** Qualquer laço de repetição indefinido (`while`) necessita de uma variável de controle que seja modificada dentro do laço para atingir o critério de parada, sob o risco de prender o sistema em um loop infinito.