**Problema:** Desenvolver um programa para professores lançarem quantas avaliações acharem necessárias para uma disciplina específica, calculando e exibindo a média aritmética final obtida pelo estudante.

**Conceito utilizado:** Acumuladores, contadores e leitura de sentinela com a função de captura de caractere `getchar()`.

**Solução:**

```
#include <stdio.h>
#include <stdlib.h>

int main() {
    int avalia, cont = 0, soma = 0;
    char letra;
    float media;
    
    do {
        printf("Digite uma nota para avaliação: \n");
        scanf("%d", &avalia);
        fflush(stdin); // Limpeza de resíduos no buffer de entrada do teclado
        
        cont++;               // Incremento do contador de avaliações
        soma = soma + avalia; // Acumulação do valor das notas
        
        printf("Digite qualquer letra para continuar ou 's' para encerrar: \n");
    } while ((letra = getchar()) != 's'); // Valida a permanência
    
    printf("\n\nQuantidade de avaliações = %d e soma das notas = %d. \n", cont, soma);
    media = (float)soma / cont; // Conversão de tipo (cast) para garantir resultado decimal
    printf("Media final do aluno: %.2f\n", media);
    
    return 0;
}
```

**Resultado:** Soma todas as notas inseridas pelo professor, faz a contagem de provas aplicadas e exibe a média correta arredondada.

**Por que essa solução funciona:** A função `fflush(stdin)` é executada antes da leitura para eliminar quaisquer quebras de linha (`\n`) ou espaços acumulados no buffer do teclado. A instrução `letra = getchar()` captura o caractere digitado diretamente e o valida em relação à condição de parada `'s'`.

**O que preciso aprender com esse exemplo:** A limpeza de buffer com `fflush(stdin)` ou procedimentos semelhantes é crucial antes de leituras de caracteres do teclado (`getchar` ou `scanf("%c")`) para evitar que a tecla Enter seja capturada indevidamente como dado válido.