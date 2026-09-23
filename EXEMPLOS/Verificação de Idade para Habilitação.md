**Problema:** Determinar se um jovem possui idade suficiente para tirar a Carteira Nacional de Habilitação. Caso não tenha, o programa simplesmente termina sem exibir nenhuma mensagem.

**Conceito utilizado:** Estrutura condicional simples (`if`).

**Solução:**

```
#include <stdio.h>

int main() {
    float idade;
    
    printf("Digite sua idade: \n");
    scanf("%f", &idade);
    
    if (idade >= 18) {
        printf("Você já pode tirar sua carteira de Habilitação você é maior de 18");
    }
    
    return 0;
}
```

**Resultado:** Se a idade inserida for maior ou igual a 18, exibe a mensagem de aptidão. Se for menor que 18, o programa encerra em silêncio.

**Por que essa solução funciona:** O operador relacional `>=` avalia a variável de entrada. Como não há a instrução `else`, o desvio condicional é ignorado se a proposição lógica retornar falso (`0`).

**O que preciso aprender com esse exemplo:** A estrutura condicional simples executa um bloco exclusivo de códigos somente se a sua proposição lógica associada for verdadeira