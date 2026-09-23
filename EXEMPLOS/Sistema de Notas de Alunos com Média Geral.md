**Problema:** Armazenar as notas de 3 alunos em 3 disciplinas diferentes, calculando a média aritmética obtida por cada aluno e gerando a média geral de desempenho de toda a classe.

**Conceito utilizado:** Matrizes bidimensionais homogêneas combinadas com vetores unidimensionais para armazenamento de estatísticas.

**Solução:**

```
#include <stdio.h>

#define NUM_ALUNOS 3
#define NUM_DISCIPLINAS 3

int main() {
    // Matriz inicializada com notas dos alunos
    float notas[NUM_ALUNOS][NUM_DISCIPLINAS] = {
        {7.5, 8.0, 9.0}, 
        {6.5, 7.0, 8.0}, 
        {8.0, 7.5, 8.5}
    };
    float mediasAluno[NUM_ALUNOS];
    float mediaGeral, soma = 0;
    
    // 1. Calcular a média das notas de cada aluno em todas as disciplinas
    for (int i = 0; i < NUM_ALUNOS; i++) {
        float somaNotas = 0;
        for (int j = 0; j < NUM_DISCIPLINAS; j++) {
            somaNotas += notas[i][j];
        }
        mediasAluno[i] = somaNotas / NUM_DISCIPLINAS;
    }
    
    // 2. Calcular a média geral da sala de aula
    for (int i = 0; i < NUM_ALUNOS; i++) {
        soma += mediasAluno[i];
    }
    mediaGeral = soma / NUM_ALUNOS;
    
    // 3. Exibição de resultados
    for (int i = 0; i < NUM_ALUNOS; i++) {
        printf("Média do aluno %d: %.2f\n", i + 1, mediasAluno[i]);
    }
    printf("Média geral de todos os alunos: %.2f\n", mediaGeral);
    
    return 0;
}
```

**Resultado:** Calcula e imprime sequencialmente a média individual de cada estudante e consolida a média global obtida pela sala.

**Por que essa solução funciona:** A matriz `notas[i][j]` organiza de forma limpa as notas por linhas (onde cada linha representa o índice de um aluno) e colunas (cada uma representando uma matéria). A diretiva `#define` atua em tempo de pré-compilação estabelecendo limites imutáveis para as dimensões das estruturas de dados.

**O que preciso aprender com esse exemplo:** A diretiva de pré-processador `#define` não consome nenhum byte físico de memória RAM; ela apenas estabelece rótulos simbólicos textuais que tornam o código mais fácil de ser alterado futuramente.