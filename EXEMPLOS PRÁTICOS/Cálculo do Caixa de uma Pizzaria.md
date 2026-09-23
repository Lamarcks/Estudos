**Problema:** Automatizar o caixa de uma pizzaria do bairro. O programa deve receber o valor total bruto de uma conta de mesa, a quantidade de clientes que dividirá a conta e o percentual de desconto concedido. O sistema deve exibir o valor total líquido com desconto e quanto cada pessoa pagará.

**Conceito utilizado:** Processamento aritmético com regras de proporção (porcentagem) e otimização de variáveis na saída.

**Solução:**

```
#include <stdio.h>

int main() {
    float valor_bruto = 0;
    float valor_liquido = 0;
    float desconto = 0;
    int qtd_pessoas = 0;
    
    printf("\n Digite o valor total da conta: ");
    scanf("%f", &valor_bruto);
    
    printf("\n Digite a quantidade de pessoas: ");
    scanf("%d", &qtd_pessoas);
    
    printf("\n Digite o desconto (em porcentagem): ");
    scanf("%f", &desconto);
    
    // Cálculo do desconto pela regra de três simples
    valor_liquido = valor_bruto - (valor_bruto * desconto / 100);
    
    printf("\n Valor da conta com desconto = %f", valor_liquido);
    printf("\n Valor a ser pago por pessoa = ");
    // Cálculo feito direto no comando de impressão (poupa variáveis)
    printf("%f\n", valor_liquido / qtd_pessoas);
    
    return 0;
}
```

**Resultado:** Exibição exata do valor da conta abatida pelo desconto e divisão igualitária do valor por pessoa.

**Por que essa solução funciona:** A operação `valor_bruto * desconto / 100` calcula o montante do desconto. Ao colocar a divisão `valor_liquido / qtd_pessoas` diretamente no argumento do `printf`, o resultado é impresso sem que seja necessário gastar memória alocando uma nova variável apenas para armazenar essa conta intermediária.

**O que preciso aprender com esse exemplo:** Se você precisa de um resultado para exibição imediata e não precisará utilizá-lo para cálculos posteriores, pode realizar a operação aritmética diretamente dentro do comando de impressão (`printf`) para otimizar o uso da memória