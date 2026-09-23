**Problema:** Calcular o salário líquido de colaboradores de uma instituição de ensino com base em faixas salariais específicas de deduções diretas de INSS e de Imposto de Renda (IR).

**Conceito utilizado:** Expressões lógicas combinadas com operadores lógicos relacionais (`&&`) dentro de estruturas `if-else-if` encadeadas.

**Solução:**

```
#include <stdio.h>

int main() {
    float salario, inss, ir, sal_liquido;
    
    printf("Calculo de Salario Liquido Com desconto do IR e INSS\n\n");
    printf("\nDigite seu salario Bruto\n");
    scanf("%f", &salario);
    
    // 1. Calcular o desconto do INSS de forma direta pelas faixas
    if (salario <= 1320.0) {
        inss = salario * 0.075;
    } else if (salario > 1320.0 && salario <= 2571.29) {
        inss = salario * 0.09;
    } else if (salario >= 2571.30 && salario <= 3856.94) {
        inss = salario * 0.12;
    } else if (salario >= 3856.95 && salario <= 7507.49) {
        inss = salario * 0.14;
    } else {
        inss = 1051.04; // Teto de contribuição estabelecido
    }
    
    // 2. Calcular o desconto do IR de forma direta pelas faixas
    if (salario <= 1903.98) {
        ir = salario * 0;
    } else if (salario >= 1903.99 && salario <= 2826.65) {
        ir = salario * 0.075;
    } else if (salario >= 2826.66 && salario <= 3751.05) {
        ir = salario * 0.15;
    } else if (salario >= 3751.06 && salario <= 4664.68) {
        ir = salario * 0.225;
    } else if (salario > 4664.69) {
        ir = salario * 0.275;
    }
    
    // 3. Processamento do salário líquido final
    sal_liquido = (salario - inss) - ir;
    
    // 4. Apresentação das saídas
    printf("\nDesconto do INSS e: %.2f\n\n", inss);
    printf("Desconto do imposto de renda e: %.2f\n\n", ir);
    printf("Salário líquido: %.2f\n\n", sal_liquido);
    
    return 0;
}
```

**Resultado:** O programa deduz com precisão os valores de imposto e previdência, gerando o salário líquido final.

**Por que essa solução funciona:** O operador lógico `&&` (conjunção AND) valida se o salário se enquadra de forma simultânea nos limites mínimo e máximo de cada faixa de imposto. Se o salário ultrapassar os limites da tabela do INSS, o fluxo cai no último `else` que define o valor padrão de contribuição (teto).

**O que preciso aprender com esse exemplo:** Ao avaliar intervalos matemáticos (ex: entre R$ 1.320,01 e R$ 2.571,29), use o operador lógico `&&` para garantir que ambas as fronteiras numéricas sejam respeitadas simultaneamente