**Problema:** A partir do código procedural de uma funcionalidade de Saque bancário, mapear toda a sua lógica de controle em uma representação gráfica e identificar os caminhos lógicos para planejar testes de cobertura completa.

**Conceito utilizado:** **Teste de Caixa Branca (Estrutural)**, **Grafo de Fluxo de Controle** e identificação de **Caminhos Independentes**.

**Solução:**

1. **Mapeamento e Marcação do Código**: O código é segmentado em blocos indivisíveis e sequenciais, recebendo marcadores numéricos lógicos correspondentes a cada decisão e processamento:
    
    ```
    public boolean saque(double valor){
        boolean status = false; // //1
        if(valor <= saldo){ // //1
            saldo = saldo - valor; // //2
            status=true; // //2
        }
        else{ // //3
            if(valor <= limiteCredito){ // //3
                limiteCredito = limiteCredito - valor; // //4
                status = true; // //4
            }
        }
        return status; // //5
    }
    ```
    
2. **Construção do Grafo de Fluxo**: Os nós (círculos) representam os blocos numerados e as arestas (setas) representam as transições lógicas de controle:
    - **Nó 1**: Declaração inicial, atribuição e a primeira decisão (`if (valor <= saldo)`).
    - **Nó 2**: Bloco interno do primeiro `if` (executado se a condição do Nó 1 for verdadeira).
    - **Nó 3**: Bloco `else` contendo a segunda decisão condicional (`if (valor <= limiteCredito)`).
    - **Nó 4**: Bloco interno do segundo `if` (executado se a condição do Nó 3 for verdadeira).
    - **Nó 5**: Retorno do status da transação (`return status`).
3. **Mapeamento de Caminhos Independentes**: Identifica-se a sequência de nós percorrida pelo fluxo com base em diferentes entradas lógicas:
    - _Caminho A_: 1 -> 2 -> 5 (valor de saque menor ou igual ao saldo disponível).
    - _Caminho B_: 1 -> 3 -> 5 (valor do saque maior que o saldo, e também maior que o limite de crédito disponível).
    - _Caminho C_: 1 -> 3 -> 4 -> 5 (valor do saque maior que o saldo, mas menor ou igual ao limite de crédito).

**Resultado:** Obtém-se um Grafo de Fluxo perfeitamente mapeado (com 5 nós e 6 arestas estruturais), permitindo ao projetista saber com precisão matemática que precisará desenhar exatamente 3 cenários de casos de teste estruturais distintos para garantir 100% de cobertura de todas as linhas de código e caminhos de decisão do método de Saque.

**Por que essa solução funciona:** A modelagem do código em um formato abstrato de grafo remove ruídos de sintaxe e expõe de forma crua os caminhos lógicos ocultos do algoritmo. Isso permite aplicar critérios rigorosos de cobertura lógica (como testes de comandos ou desvios de decisão) e calcular a Complexidade Ciclomática (que neste caso é V(G) = 6 arestas - 5 nós + 2 = 3), definindo de antemão o limite superior exato de casos de teste necessários.

**O que preciso aprender com esse exemplo:** Aprenda para a prova a associar cada trecho de decisão ou comando procedural a nós e arestas lógicas. Os testes de caixa branca focam em passar por todos os nós e arcos lógicos desenhados, garantindo que não restem trechos ocultos de código ou condições lógicas inexploradas no sistema.