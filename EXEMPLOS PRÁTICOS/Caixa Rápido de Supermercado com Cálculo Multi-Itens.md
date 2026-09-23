**Problema:** Calcular o valor total de uma compra de supermercado que contém uma quantidade variada de itens, baseando-se em vetores dinâmicos de preços unitários e quantidades físicas adquiridas para cada produto, atualizando a conta de forma imediata.

**Conceito utilizado:** Passagem de múltiplos vetores de referência cruzados e ponteiro acumulador de retorno de cálculo.

**Solução:**

```
#include <stdio.h>

// Função acumula de forma cruzada dados de preço e quantidade por referência
void calcularPrecoTotal(float precoUnitario[], int quantidade[], int numItens, float *precoTotal) {
    *precoTotal = 0; // Inicializa o acumulador de destino por ponteiro
    for (int i = 0; i < numItens; i++) {
        *precoTotal += precoUnitario[i] * quantidade[i];
    }
}

int main() {
    int numItens;
    printf(" Digite o número de itens comprados: ");
    scanf("%d", &numItens);
    
    float precoUnitario[numItens];
    int quantidade[numItens];
    float precoTotal;
    
    // Coleta dos dados dos itens comprados
    for (int i = 0; i < numItens; i++) {
        printf("\n Digite o preço unitário do item %d: ", i + 1);
        scanf("%f", &precoUnitario[i]);
        printf(" Digite a quantidade do item %d: ", i + 1);
        scanf("%d", &quantidade[i]);
    }
    
    // Executa a função passando o ponteiro da variável acumuladora local
    calcularPrecoTotal(precoUnitario, quantidade, numItens, &precoTotal);
    
    printf("\n Preço total da compra: R$ %.2f\n\n", precoTotal);
    return 0;
}
```

**Resultado:** Multiplica as quantidades de cada produto por seu respectivo preço, somando tudo em lote, e exibe o preço total da compra consolidado.

**Por que essa solução funciona:** A passagem por referência da variável `precoTotal` (`&precoTotal`) permite que a função modifique diretamente a célula de memória do programa principal. Isso elimina a necessidade de forçar a função a retornar dados pelo comando `return`, permitindo que ela atualize de forma segura diversas variáveis de contabilidade diretamente na raiz de execução.

**O que preciso aprender com esse exemplo:** A passagem de parâmetros por referência é o padrão de engenharia ideal quando precisamos que uma sub-rotina atualize ou retorne múltiplos resultados consolidados ao final de sua execução.