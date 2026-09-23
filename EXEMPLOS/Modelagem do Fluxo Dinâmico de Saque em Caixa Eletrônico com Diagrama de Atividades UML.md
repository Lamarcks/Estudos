**Problema:** Projetar detalhadamente a lógica de funcionamento e os fluxos internos concorrentes que ocorrem quando um cliente realiza a transação de saque de valores físicos em um Caixa Eletrônico (ATM), garantindo que validações de hardware e restrições financeiras sejam rigidamente executadas em sequência correta.

**Conceito utilizado:**

- **Diagrama de Atividades UML**.
- **Elementos**: _Swimlanes_ (Consumidor, Caixa Automático, Servidor do Banco), Nós de Decisão lúdica com Condições de Guarda, Forks e Joins.

**Solução:** A modelagem foi dividida em três partições verticais (Swimlanes):

1. **Consumidor**: Insere o cartão físico no leitor.
2. **Caixa Automático**: Lê o cartão físico e envia os dados lógicos para autenticação.
3. **Servidor do Banco**: Valida o cartão de forma eletrônica.
4. **Consumidor**: Digita a sua senha de acesso de segurança.
5. **Servidor do Banco**: Executa a rotina interna de verificação da senha.
    - _Nó de Decisão (Senha Válida?)_:
        - `[Não]`: Caixa Automático ejeta o cartão físico e encerra o fluxo com transação cancelada.
        - `[Sim]`: Consumidor é solicitado a informar a quantidade de dinheiro desejada.
6. **Servidor do Banco**: Avalia a consulta de saldo na conta do cliente.
    - _Nó de Decisão (Saldo > Quantidade solicitada?)_:
        - `[Não]`: Caixa Automático ejeta o cartão físico e encerra o fluxo.
        - `[Sim]`: O Servidor envia sinal de **Fork** paralelo:
            - _Ramo de Processamento_: Servidor debita o valor na conta corrente do cliente.
            - _Ramo de Hardware_: Caixa Automático ativa os motores físicos e disponibiliza as cédulas.
7. **Caixa Automático**: Sincroniza os ramos em uma barra de **Join**, exibe o saldo restante (opcional) e ejeta o cartão.
8. **Consumidor**: Retira o seu cartão físico.

**Resultado:** Um modelo algorítmico rigoroso em formato visual, impedindo a ocorrência de fraudes (como liberar dinheiro físico sem o débito em conta correspondente ocorrer com sucesso).

**Por que essa solução funciona:** O diagrama particionado por swimlanes delimita o que é processamento de hardware local (ATM), o que é processamento do banco de dados (Servidor) e o que é ação do usuário, permitindo projetar comunicações de rede sem gargalos.

**O que preciso aprender com esse exemplo:** O Diagrama de Atividades UML é excelente para projetar **lógica de sistemas cliente-servidor ou firmware de hardware**, pois ilustra decisões, concorrências (Forks/Joins) e responsabilidades de processamento de rede.
