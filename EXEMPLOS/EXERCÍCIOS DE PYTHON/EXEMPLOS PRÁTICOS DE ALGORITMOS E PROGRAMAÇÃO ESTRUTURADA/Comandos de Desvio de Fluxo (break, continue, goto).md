Exemplo: Jogo de Adivinhação de Número Secreto (break)

**Problema:** Solicitar que o usuário tente adivinhar um número secreto fixo. O programa deve prender o usuário em um loop contínuo de novas tentativas e só liberar a saída do fluxo quando o jogador acertar o número.

**Conceito utilizado:** Loop infinito controlado, desvio estruturado de interrupção imediata (`break`).

**Solução:**

```
#include <stdio.h>

int main() {
    int numero_secreto = 7;
    int tentativa;
    
    printf("Adivinhe o número secreto!\n");
    
    while (1) { // Criação de um laço infinito intencional
        printf("Insira um número: ");
        scanf("%d", &tentativa);
        
        if (tentativa == numero_secreto) {
            printf("Parabéns! Você adivinhou o número secreto.\n");
            break; // Força o encerramento do laço infinito
        } else {
            printf("Tente novamente!\n");
        }
    }
    
    return 0;
}
```

**Resultado:** O programa só encerra sua execução quando o usuário digita o número correto (`7`).

**Por que essa solução funciona:** A expressão `while (1)` cria um teste lógico que sempre retorna verdadeiro, mantendo o programa em execução indeterminada. O comando `break` age de forma física na pilha de instruções, forçando o compilador a ignorar a condição de permanência do laço e pulando imediatamente para a primeira linha de instrução externa após o bloco `while`.

**O que preciso aprender com esse exemplo:** A instrução `break` é a maneira mais segura e limpa de forçar a saída de loops infinitos ou repetições de validação quando o critério de parada é atingido de forma dinâmica.