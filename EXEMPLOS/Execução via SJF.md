1. **Tarefa B**: Inicia no minuto 0 e termina no minuto 4. (Tempo de retorno = 4).
2. **Tarefa C**: Inicia no minuto 4 e termina no minuto 8. (Tempo de retorno = 8).
3. **Tarefa D**: Inicia no minuto 8 e termina no minuto 12. (Tempo de retorno = 12).
4. **Tarefa A**: Inicia no minuto 12 e termina no minuto 20. (Tempo de retorno = 20).

- **Cálculo do tempo médio de retorno (turnaround)**: \[\text{Média} = \frac{4 + 8 + 12 + 20}{4} = 11 \text{ minutos}\]

**Resultado:** O algoritmo **SJF** reduz o tempo médio de retorno do sistema de **14 para 11 minutos** para o mesmo conjunto de processos.

**Por que essa solução funciona:** Ao priorizar processos curtos, reduz-se o tempo de fila das tarefas menores, que são liberadas rapidamente. No FIFO, os processos pequenos sofrem o "efeito comboio", ficando retidos em fila aguardando a finalização do processo gigante (A).

**O que preciso aprender com esse exemplo:** O escalonador influencia diretamente a percepção de agilidade do sistema. Para sistemas em lote onde os tempos de processamento são previsíveis, o SJF é matematicamente superior ao FIFO na redução do tempo médio de retorno de tarefas.