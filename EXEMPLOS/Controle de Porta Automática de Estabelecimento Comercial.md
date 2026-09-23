- **Problema:** Um projetista de sistemas digitais precisa desenvolver o diagrama elétrico do circuito de controle de uma porta automática de um shopping. O motor que abre a porta deve ser ativado (saída lógica $S = 1$) sob as seguintes condições de sensores físicos de entrada:
    
    - \(p = 1\) quando o sensor de presença infravermelho detecta uma pessoa se aproximando.
    - \(q = 1\) quando um funcionário ativa manualmente a chave física para abrir a porta.
    - \(z = 1\) quando o sistema central ativa a chave física para travar a porta fechada.
    
    A porta automática só deve abrir (\(S = 1\)) se, e somente se, ocorrer a seguinte condição lógica: a chave de abertura manual estiver ativada e a chave de travamento estiver desativada, **OU** se a chave de abertura estiver desativada e o sensor infravermelho detectar uma pessoa com a chave de travamento desativada.
    
- **Conceito utilizado:** Formulação de expressões lógicas a partir de sentenças em linguagem natural e sua representação gráfica através de diagramas combinacionais com portas **AND, OR e inversores (NOT)**.
    
- **Solução:** A resolução do circuito baseia-se em dois passos ordenados:
    
    ##### Passo 1: Traduzir as condições lógicas em linguagem matemática booleana:
    
    - Condição 1: Chave de abertura ligada (\(q\)) **E** chave de travamento desligada (\(\bar{z}\)) \(\rightarrow q \bar{z}\).
    - Condição 2: Chave de abertura desligada (\(\bar{q}\)) **E** sensor de presença detectando (\(p\)) **E** chave de travamento desligada (\(\bar{z}\)) \(\rightarrow \bar{q} p \bar{z}\).
    - O motor abre com a Condição 1 **OU** com a Condição 2.
    
    Expressão lógica resultante: $$S = q \bar{z} + \bar{q} p \bar{z}$$
    
    ##### Passo 2: Mapear as portas lógicas necessárias e construir o diagrama combinacional:
    
    - _Inversores (NOT):_ Dois inversores para obter os sinais negados de chave de abertura (\(\bar{q}\)) e trava (\(\bar{z}\)).
    - _Portas AND:_ Duas portas AND para calcular os termos-produto intermediários:
        1. Uma porta AND de duas entradas recebendo $q$ e $\bar{z}$.
        2. Uma porta AND de três entradas recebendo $\bar{q}$, $p$ and $\bar{z}$.
    - _Porta OR:_ Uma porta OR de duas entradas para unir as saídas das duas portas AND, produzindo o sinal do motor \(S\).
- **Resultado:** Diagrama de circuito impresso combinacional funcional que abre a porta com segurança absoluta de acordo com as especificações exigidas.
    
- **Por que essa solução funciona:** O circuito funciona porque as portas AND garantem que as condições restritivas de segurança (como a porta não abrir se o travamento $z$ estiver ativado, ou seja, $\bar{z} = 0$) sejam rigidamente respeitadas, enquanto a porta OR final garante a redundância de abertura manual ou automática.
    
- **O que preciso aprender com esse exemplo:** A negação física de uma variável em circuitos digitais é feita utilizando a porta **NOT** (inversora) colocada antes das portas de conjunção AND.