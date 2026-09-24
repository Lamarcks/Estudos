**Problema:** Três colaboradoras (Jennie, Mary e Helen) precisam preparar um bolo de forma síncrona. Algumas atividades podem ocorrer de forma simultânea e concorrente para ganhar tempo, mas outras exigem a finalização obrigatória de etapas anteriores (como aquecer o forno antes de assar). Como modelar essa concorrência com precisão lógica?

**Conceito utilizado:**

- **Diagrama de Atividades UML** orientado a processos colaborativos.
- **Forks** (abertura de paralelismo) e **Joins** (sincronização síncrona obrigatória).

**Solução:** A preparação foi mapeada em raias para Jennie, Mary e Helen:

1. **Mary**: Inicia o processo procurando a receita em papel.
2. **Sinal de Fork (Abertura de Paralelismo)**: Dispara três ações simultâneas e independentes:
    - _Ação 1 (Jennie)_: Mistura os ingredientes secos.
    - _Ação 2 (Mary)_: Mistura os ingredientes molhados.
    - _Ação 3 (Helen)_: Aquece o forno.
3. **Barra de Sincronização (Join de Preparo)**: Jennie e Mary devem obrigatoriamente terminar suas misturas para prosseguir. Assim que ambas concluem, Jennie mistura tudo.
4. **Barra de Sincronização Geral (Join do Forno)**: A mistura do bolo (Jennie) E o aquecimento do forno (Helen) devem estar concluídos. Apenas com ambos finalizados, a massa é levada para **Assar**.
5. **Nó de Decisão (Bolo Pronto?)**:
    - `[Não pronto]`: Retorna para assar por mais tempo.
    - `[Pronto]`: Mary retira o bolo do forno e o processo é finalizado.

**Resultado:** O processo operacional colaborativo foi padronizado de forma visual, garantindo que o bolo nunca seja assado em forno frio e economizando tempo por meio de tarefas executadas simultaneamente.

**Por que essa solução funciona:** O uso síncrono das barras de Fork e Join garante o gerenciamento de concorrência síncrona, definindo dependências lógicas claras que impedem que ações finais (assar) ocorram sem que pré-condições separadas estejam atendidas.

**O que preciso aprender com esse exemplo:** Em modelagem de sistemas de software, utilize **Forks e Joins** sempre que houver processamento de múltiplas _threads_ lógicas simultâneas que precisem se sincronizar ou consolidar em um ponto síncrono do banco de dados.
