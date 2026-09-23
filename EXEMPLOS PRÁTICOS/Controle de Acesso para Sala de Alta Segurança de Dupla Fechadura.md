 **Problema:** Um projetista de sistemas de segurança eletrônica precisa projetar o circuito lógico combinacional para controlar a liberação de entrada (sinal físico de saída de acesso $P$) de uma sala que possui duas fechaduras eletrônicas por cartão magnético (**Fechadura A** e **Fechadura B**) e um sensor físico infravermelho de presença (**Sensor S**). As regras restritivas para permitir o acesso à sala (\(P = 1\)) são:
    
    1. Ambas as fechaduras magnéticas, $A$ e $B$, devem estar desbloqueadas (nível lógico 1) simultaneamente;
    2. **OU** o sensor de presença de movimento deve detectar atividade (nível lógico 1) quando pelo menos uma das fechaduras magnéticas estiver desbloqueada (nível lógico 1).
    
    É preciso elaborar a expressão lógica simplificada correspondente, apontar as portas lógicas necessárias e desenhar o diagrama de interligações do circuito físico de hardware.
    
- **Conceito utilizado:** Álgebra booleana, portas combinacionais lógicas AND e OR, mapeamento e síntese de circuitos com portas interconectadas.
    
- **Solução:** A especificação técnica e física do projeto elétrico ocorre nas seguintes etapas lógicas:
    
    ##### Etapa 1: Tradução das condições em expressão booleana:
    
    - _Condição 1:_ Fechaduras A e B desbloqueadas simultaneamente \(\rightarrow\) Operação lógica AND \(\rightarrow (A \text{ AND } B)\).
    - _Condição 2:_ Pelo menos uma fechadura desbloqueada (\(A \text{ OR } B\)) **E** movimento detectado pelo sensor (\(S\)) \(\rightarrow (S \text{ AND } (A \text{ OR } B))\).
    - _Sinal de Acesso final (P):_ Condição 1 **OU** Condição 2.
    
    Expressão lógica final consolidada: $$P = (A \cdot B) + (S \cdot (A + B))$$
    
    ##### Etapa 2: Mapeamento de portas lógicas físicas de hardware:
    
    - Uma porta **AND** de duas entradas para a expressão \((A \cdot B)\).
    - Uma porta **OR** de duas entradas para a expressão \((A + B)\).
    - Uma porta **AND** de duas entradas para combinar a saída da porta OR anterior com o sensor \(S\).
    - Uma porta **OR** de duas entradas final para somar os resultados lógicos e gerar a saída física \(P\).
    
    ##### Etapa 3: Desenho das conexões do circuito físico:
    
    1. Conectar as linhas elétricas $A$ e $B$ nas entradas da primeira porta AND.
    2. Derivar as mesmas linhas $A$ e $B$ para alimentar as entradas da porta OR.
    3. Ligar o pino de saída dessa porta OR em uma entrada da segunda porta AND, e ligar o pino do sensor físico $S$ na outra entrada desta mesma porta AND.
    4. Conectar os pinos de saída das duas portas AND nas duas entradas da porta OR final do sistema para extrair o sinal físico de controle do trinco da porta $P$.
- **Resultado:** Circuito combinacional e diagrama elétrico finalizado que gerencia o acesso físico ao cofre corporativo com alta tolerância a falhas.
    
- **Por que essa solução funciona:** Esta solução funciona porque o circuito foi construído em estrita equivalência algébrica com os requisitos físicos. A porta OR final atua como um comutador elétrico paralelo seguro, permitindo a liberação do trinco se o acesso administrativo for validado pelas duas chaves de cartão OU se a movimentação física for confirmada enquanto um operador autorizado mantém pelo menos uma chave acionada.
    
- **O que preciso aprender com esse exemplo:** Requisitos lógicos complexos de segurança predial são traduzidos em circuitos físicos interconectando de forma ordenada portas lógicas **AND** (conjunção de restrições) e portas **OR** (alternativas lógicas de liberação).
    