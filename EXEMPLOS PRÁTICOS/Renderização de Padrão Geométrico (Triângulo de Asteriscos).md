**Problema:** Criar uma ferramenta prática e visual que desenhe um triângulo perfeito na tela a partir de uma quantidade de linhas inserida pelo usuário. Exemplo para `N = 4` linhas:

```
   *
  ***
 *****
*******
```

**Conceito utilizado:** Cálculo geométrico espacial e loops aninhados para renderização de caracteres de espaçamento e conteúdo.

**Solução:**

```
#include <stdio.h>

int main() {
    int linhas, espacos, asteriscos;
    
    printf("Digite o número de linhas do triângulo: ");
    scanf("%d", &linhas);
    
    for (int i = 1; i <= linhas; i++) {
        // 1. Loop para renderizar os espaços em branco à esquerda
        for (espacos = 1; espacos <= linhas - i; espacos++) {
            printf(" ");
        }
        
        // 2. Loop para renderizar a quantidade ímpar de asteriscos por linha
        for (asteriscos = 1; asteriscos <= 2 * i - 1; asteriscos++) {
            printf("*");
        }
        
        printf("\n"); // Passagem para a linha de baixo
    }
    
    return 0;
}
```

**Resultado:** Renderiza uma pirâmide geométrica de asteriscos na tela com alinhamento visual preciso.

**Por que essa solução funciona:** A quantidade de espaços vazios decresce a cada linha à proporção de `linhas - i`. Em contrapartida, a quantidade de caracteres de asteriscos cresce seguindo a fórmula de progressão de números ímpares `2 * i - 1`. O alinhamento simétrico é garantido pela sincronia dessas duas dinâmicas gerenciadas por loops internos isolados.

**O que preciso aprender com esse exemplo:** Padrões visuais complexos podem ser facilmente construídos no terminal dividindo a linha horizontal em seções matemáticas e atribuindo um loop interno para desenhar cada segmento.