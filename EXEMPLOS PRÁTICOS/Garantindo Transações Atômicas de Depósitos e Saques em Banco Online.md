**Problema:** Um banco online permite que clientes acessem e atualizem suas contas bancárias de forma concorrente e simultânea. Sem o devido controle, se um cliente realizar um depósito enquanto outro realiza um saque de forma síncrona no mesmo saldo, os valores finais salvos no banco de dados ficarão inconsistentes, podendo gerar saldos negativos e saldos finais incorretos.

**Conceito utilizado:** Transações atômicas de threads e sincronização usando **Mutexes**.

**Solução:** A equipe de engenharia deve estruturar a aplicação com as seguintes regras de sincronização:

1. **Threads Individuais**: Cada acesso ou conexão de transação do cliente roda em uma thread independente.
2. **Uso de Mutex**: Associar um semáforo binário (Mutex) a cada conta bancária ativa.
3. **Bloqueio Prévio**: Antes de alterar o saldo, a thread deve adquirir o Mutex correspondente àquela conta específica.
4. **Operação Atômica**: A leitura do saldo atual, a operação matemática de soma/subtração e a gravação final do novo saldo devem ser tratadas de forma atômica e ininterrupta.
5. **Tratamento de Exceções**: Caso o saque resulte em saldo negativo, implementar rotina para reverter a operação imediatamente.

**Resultado:** O sistema bancário torna-se confiável e consistente, impedindo corrupções de saldo em contas de acessos simultâneos de usuários.

**Por que essa solução funciona:** Ao bloquear o Mutex da conta, nenhuma outra transação paralela consegue ler ou escrever dados naquele saldo específico até que a transação em andamento conclua seu ciclo de gravação, garantindo a atomicidade lógica.

**O que preciso aprender com esse exemplo:** A sincronização robusta de dados impede a concorrência desordenada. Mutexes e a programação concorrente organizada são a fundação para garantir a integridade dos dados em sistemas transacionais de alto volume.