**Problema:** Modificar os valores de duas variáveis criadas e gerenciadas no escopo do programa principal utilizando instruções contidas dentro de uma função externa de processamento.

**Conceito utilizado:** Operador de endereço (`&`), desreferenciação por ponteiro (`*`) e passagem de parâmetros por referência.

**Solução:**

```
#include <stdio.h>

// Função que recebe parâmetros por referência utilizando ponteiros
int testar(int* n1, int* n2) {
    *n1 = -1; // Desreferenciação: acessa e altera o conteúdo da célula física original
    *n2 = -2;
    printf("\n\n Valores dentro da função testar(): ");
    printf("\n n1 = %d e n2 = %d", *n1, *n2);
    return 0;
}

int main() {
    int n1 = 10;
    int n2 = 20;
    
    printf("\n\n Valores antes de chamar a função: ");
    printf("\n n1 = %d e n2 = %d", n1, n2);
    
    testar(&n1, &n2); // Envia os endereços físicos de memória RAM das variáveis
    
    printf("\n\n Valores depois de chamar a função: ");
    printf("\n n1 = %d e n2 = %d\n", n1, n2);
    
    return 0;
}
```

**Resultado:** Os valores das variáveis na função principal são mutados de forma definitiva para `-1` e `-2` após a execução da sub-rotina.

**Por que essa solução funciona:** O operador de endereço `&` na chamada da função (`testar(&n1, &n2)`) envia os locais reais da memória das variáveis para a função. Na função, o caractere asterisco antes das variáveis (`*n1` e `*n2`) diz ao compilador que a operação matemática de atribuição deve ignorar a variável ponteiro local e ir direto no local físico apontado alterar o dado original lá na memória de forma direta.

**O que preciso aprender com esse exemplo:** Para realizar a alteração definitiva de variáveis de forma externa à função corrente, passe os dados por referência utilizando ponteiros.