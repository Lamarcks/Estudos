**Problema:** Calcular a massa final resultante da combinação molecular entre reagentes químicos do tipo A e B ($A + B \rightarrow C$). Um mol do composto A possui peso de $321.43\text{ g}$, enquanto um mol do tipo B pesa $150.72\text{ g}$138139. O programa deve receber a quantidade de mols utilizada no experimento e gerar a massa resultante sem alterar os parâmetros de controle iniciais139.

**Conceito utilizado:** Passagem de parâmetros por cópia de dados (passagem por valor) e uso de constantes no escopo local140141.

**Solução:**

```
#include <stdio.h>

// Função com passagem de parâmetros por valor
float calcularMassa(float a, float b) {
    const float mA = 321.43; // Constante local de peso molecular
    const float mB = 150.72;
    
    // Imprime tabela de referência fixa exigida pelo departamento
    printf("\n mol A : mol B ");
    printf("\n 1,2 : 1,0 \t= %f", 1.2 * mA + 1 * mB);
    printf("\n 1,4 : 1,0 \t= %f", 1.4 * mA + 1 * mB);
    printf("\n 1,6 : 1,0 \t= %f", 1 * mA + 1.6 * mB);
    
    return (a * mA) + (b * mB);
}

int main() {
    float a = 0, b = 0, resultado = 0;
    
    printf("\n Digite as massas (mols) dos elementos A e B: ");
    scanf("%f %f", &a, &b);
    
    resultado = calcularMassa(a, b); // Os valores de a e b originais são preservados
    
    printf("\n\n Massa final do composto = %.2f g/mol\n", resultado);
    return 0;
}
```

**Resultado:** Calcula de forma precisa a massa final de compostos e exibe os dados comparativos de referência das reações químicas sem alterar os parâmetros informados pelo usuário141.

**Por que essa solução funciona:** A passagem por valor faz com que o programa principal tire uma cópia exata do conteúdo das variáveis originais e as envie de forma isolada para as variáveis locais da função receptora (`a` e `b`)140142. Qualquer alteração de dados nessas cópias pela função ocorre de forma estritamente isolada e não modifica os dados originais no programa principal142.

**O que preciso aprender com esse exemplo:** A passagem por valor é o mecanismo padrão da linguagem C e é a escolha ideal quando a função precisa ler ou processar dados sem o risco de alterar as variáveis originais que foram fornecidas a ela140142.