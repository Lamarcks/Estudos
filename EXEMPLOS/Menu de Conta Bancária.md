**Problema:** Simular um menu iterativo de terminal para uma conta de banco que ofereça ao usuário as seguintes opções: Depósito (acumular saldo), Saque (deduzir saldo), Consultar Saldo ou Sair.

**Conceito utilizado:** Associação de laço `do...while` com a estrutura de seleção de casos `switch-case`.

**Solução:**

```
#include <stdio.h>
#include <stdlib.h>

int main() {
    float soma = 0, valor;
    int opcao;
    
    do {
        printf("\n Digite uma Operação");
        printf("\n 1. Deposito");
        printf("\n 2. Saque");
        printf("\n 3. Saldo");
        printf("\n 4. Sair");
        printf("\n Qual opcao? ");
        scanf("%d", &opcao);
        
        switch (opcao) {
            case 1:
                printf("\n Valor do depósito? ");
                scanf("%f", &valor);
                soma = soma + valor; // Acumulação do valor depositado
                break;
                
            case 2:
                printf("\n Valor do saque? ");
                scanf("%f", &valor);
                soma = soma - valor; // Dedução do valor sacado
                break;
                
            case 3:
                printf("\n Saldo atual = R$ %.2f \n", soma);
                break;
                
            default:
                if (opcao != 4) {
                    printf("\n Opção Inválida! \n");
                }
        }
    } while (opcao != 4); // Mantém o programa rodando até a opção de saída
    
    printf("Fim das operações. \n\n");
    return 0;
}
```

**Resultado:** O usuário gerencia as transações bancárias através do menu, e o saldo (`soma`) é preservado ao longo de todas as rodadas até que a opção `4` seja escolhida.

**Por que essa solução funciona:** A variável `soma` funciona como um acumulador que preserva o estado financeiro ao longo das iterações. O laço `do...while` garante que o menu de opções do terminal seja exibido na tela logo na inicialização do programa.

**O que preciso aprender com esse exemplo:** A combinação de `do...while` e `switch-case` é o padrão de arquitetura de software ideal para construir menus interativos de terminal estruturados.