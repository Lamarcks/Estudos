**Problema:** Validar se um número inteiro digitado pelo usuário é positivo (maior que zero) ou negativo (menor ou igual a zero), exibindo uma resposta explícita para ambas as situações.

**Conceito utilizado:** Estrutura condicional composta (`if-else`).

**Solução:**

```
#include <stdio.h>

int main() {
    int num;
    
    printf("Digite um número: ");
    scanf("%d", &num);
    
    if (num > 0) {
        printf("\n\nO número e positivo\n");
    } else {
        printf("O número e negativo");
    }
    
    return 0;
}
```

**Resultado:** Exibe na tela a mensagem correspondente ao sinal do número digitado.

**Por que essa solução funciona:** Se a condição `num > 0` for verdadeira, o compilador executa o primeiro bloco e salta o bloco `else`. Se a condição for falsa, o compilador ignora o primeiro bloco e executa obrigatoriamente as instruções dentro do bloco `else`.

**O que preciso aprender com esse exemplo:** O comando `else` atua como um plano B do fluxo, tratando de forma segura todas as situações lógicas que não foram capturadas pelo teste do `if`