**Problema:** Quatro tarefas (A, B, C e D) aguardam em uma fila para execução com os respectivos tempos de processamento estimados em: **A (8 min), B (4 min), C (4 min) e D (4 min)**. Qual algoritmo apresenta o menor tempo de espera médio para o sistema?

**Conceito utilizado:** Algoritmos de Escalonamento de Lote (Batch): **FIFO (First-In, First-Out)** versus **SJF (Shortest Job First)**.

**Solução:**

#### Cenário A: Execução via FIFO (Ordem de chegada: A -> B -> C -> D)

1. **Tarefa A**: Inicia no minuto 0 e termina no minuto 8. (Tempo de retorno = 8).
2. **Tarefa B**: Inicia no minuto 8 e termina no minuto 12. (Tempo de retorno = 12).
3. **Tarefa C**: Inicia no minuto 12 e termina no minuto 16. (Tempo de retorno = 16).
4. **Tarefa D**: Inicia no minuto 16 e termina no minuto 20. (Tempo de retorno = 20).

- **Cálculo do tempo médio de retorno (turnaround)**: \[\text{Média} = \frac{8 + 12 + 16 + 20}{4} = 14 \text{ minutos}\]