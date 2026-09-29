**Problema:** Gerenciar matrículas de estudantes em várias disciplinas escolares. O programa deve pedir o número total de disciplinas e a quantidade de alunos em cada uma delas. O sistema precisa:

1. Desconsiderar e pedir para reinserir se o número de alunos digitado for negativo.
2. Interromper e encerrar a contagem de forma definitiva se a soma de todos os alunos atingir o limite geral da escola (100 alunos).

**Conceito utilizado:** Sincronização de comandos `break`, `continue` e manipulação inversa de variável de controle (`i--`).

**Solução:**

```
#include <stdio.h>
#include <stdlib.h>

int main() {
    int total_disciplinas, limite_alunos = 100, total_alunos = 0;
    
    printf("Sistema de contagem de alunos matriculados!\n");
    printf("Insira o número de disciplinas disponíveis: ");
    scanf("%d", &total_disciplinas);
    
    for (int i = 1; i <= total_disciplinas; i++) {
        int alunos_matriculados;
        printf("Insira o número de alunos matriculados na disciplina %d: ", i);
        scanf("%d", &alunos_matriculados);
        
        // Regra de validação: valores inválidos de alunos
        if (alunos_matriculados < 0) {
            printf("Número de alunos inválido. Tente novamente.\n");
            i--; // Decrementa a variável de controle para repetir a mesma disciplina na próxima rodada
            continue; // Salta as somas e passa direto para a próxima rodada do laço
        }
        
        total_alunos += alunos_matriculados;
        
        // Regra de parada: estouro do limite máximo de alunos
        if (total_alunos >= limite_alunos) {
            printf("Limite de alunos atingido. Encerrando contagem de disciplinas.\n");
            break; // Interrompe o loop de disciplinas definitivamente
        }
    }
    
    printf("Total de disciplinas contadas: %d\n", total_disciplinas);
    printf("Total de alunos matriculados: %d\n", total_alunos);
    
    return 0;
}
```

**Resultado:** O sistema filtra dados incorretos com precisão e interrompe o cadastro imediatamente caso o limite de ocupação física da escola seja atingido.

**Por que essa solução funciona:** A linha `i--` reduz em 1 a contagem de controle do loop para que, ao passar pelo incremento automático `i++` do cabeçalho do `for`, a mesma disciplina seja processada novamente. O comando `continue` pula o cálculo de acumulação de alunos. O comando `break` protege o limite máximo de vagas da escola.

**O que preciso aprender com esse exemplo:** A redução manual da variável de controle (`i--`) em loops determinísticos é uma excelente técnica para forçar a repetição do processamento do índice atual no caso de entradas incorretas de dados