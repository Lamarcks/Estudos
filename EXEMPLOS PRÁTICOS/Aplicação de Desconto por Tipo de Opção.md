**Problema:** Receber o valor total bruto de uma compra e aplicar um percentual de desconto selecionado pelo usuário por meio de uma letra de menu ('a' para 10% de desconto ou 'b' para 15% de desconto - _nota: a lógica do código em C do slide aplica matematicamente 20% para a opção 'b', preservaremos a sintaxe original do PDF_).

**Conceito utilizado:** Estrutura de decisão múltipla (`switch-case`).

**Solução:**

```
#include <stdio.h>

int main() {
    char opcao;
    float valor, total;
    
    printf("\n Digite o valor da compra \n");
    scanf("%f", &valor);
    
    printf("\n Digite a letra que representa o desconto a ser aplicado:\n");
    printf("\ta - 10%% de desconto\n");
    printf("\tb - 15%% de desconto\n");
    printf("\n Digite sua opção: ");
    scanf("%s", &opcao); // Lê a opção de entrada
    
    switch (opcao) {
        case 'a':
            total = valor - (valor * 0.10);
            printf(" \nValor final da compra: R$ %.2f\n", total);
            break;
            
        case 'b':
            total = valor - (valor * 0.20); // Aplica matematicamente 20% conforme fonte
            printf(" \nValor final da compra: R$ %.2f\n", total);
            break;
            
        default:
            printf("opcao invalida\n");
    }
    
    return 0;
}
```

**Resultado:** Calcula o preço com desconto com base na opção do menu e avisa caso o usuário escolha uma alternativa inexistente.

**Por que essa solução funciona:** A expressão `switch(opcao)` salta diretamente para o rótulo `case` correspondente ao caractere digitado. O comando `break` interrompe a execução e sai do bloco `switch`, impedindo que os comandos dos próximos casos sejam executados indevidamente.

**O que preciso aprender com esse exemplo:** Sempre termine seus blocos `case` com o comando `break`. Se esquecer, o código continuará executando sequencialmente todas as instruções dos casos de baixo até encontrar o fim do `switch`