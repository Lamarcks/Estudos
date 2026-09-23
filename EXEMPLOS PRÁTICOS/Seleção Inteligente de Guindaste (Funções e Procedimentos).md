**Problema:** Calcular o peso de colunas de concreto armado a partir de dimensões inseridas via teclado (base, altura e comprimento) utilizando a equação $P = V \times R$ (onde $R = 25\text{ kN/m}^3$ é a constante de conversão de densidade)126. O programa deve direcionar de forma inteligente qual modelo de guindaste é adequado para realizar o trabalho com base na classificação de peso estabelecida: modelo G1 se o peso for menor ou igual a 500 kg; G2 se estiver na faixa entre 500 e 1500 kg; e G3 para pesos superiores a 1500 kg127.

**Conceito utilizado:** Modularização de códigos por meio de funções criadas pelo programador e conversão explícita de tipos de dados (_cast_)128129.

**Solução:**

```
#include <stdio.h>

// Função modularizada de cálculo matemático antes do main()
int calcularPeso() {
    float b, c, h = 0;
    
    printf("\n Digite o valor da base: ");
    scanf("%f", &b);
    
    printf("\n Digite o valor da altura: ");
    scanf("%f", &h);
    
    printf("\n Digite o valor do comprimento: ");
    scanf("%f", &c);
    
    // Cast explícito: converte o valor resultante para o formato inteiro
    return (int) (b * h * c * 25);
}

int main() {
    float peso;
    peso = calcularPeso(); // Chamada da função para obtenção de dados
    
    // Estrutura de validação condicional composta
    if (peso <= 500) {
        printf("\n O guindaste de modelo G1 deve ser usado\n");
    } else if (peso > 1500) {
        printf("\n O guindaste de modelo G3 deve ser usado\n");
    } else {
        printf("\n O guindaste de modelo G2 deve ser usado\n");
    }
    
    return 0;
}
```

**Resultado:** Calcula o peso físico e indica de forma explícita qual modelo de guindaste deve ser despachado para a obra129130.

**Por que essa solução funciona:** A função `calcularPeso()` encapsula a lógica de entrada e cálculo matemático de forma isolada128. A instrução `(int)` atua como um operador de conversão explícita (_cast_), forçando a truncagem do resultado do cálculo decimal para o tipo numérico inteiro, em conformidade com o tipo de retorno declarado na função129.

**O que preciso aprender com esse exemplo:** Criar sub-rotinas e funções antes do ponto de entrada principal (`main`) organiza o código, o que evita a necessidade de declarar assinaturas de funções (protótipos) e simplifica o fluxo de compilação em C.