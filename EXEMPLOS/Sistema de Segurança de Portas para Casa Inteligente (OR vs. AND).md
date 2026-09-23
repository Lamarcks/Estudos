- **Problema:** Um projetista de sistemas de automação predial precisa desenvolver dois circuitos lógicos alternativos de controle para um sistema de segurança residencial com duas portas monitoradas por sensores magnéticos (**Porta A** e **Porta B**) e conectados a uma **Lâmpada de Aviso** de alerta no painel central. As especificações são:
    
    - _Porta aberta_ emite sinal lógico **0**.
    - _Porta fechada_ emite sinal lógico **1**.
    - _Lâmpada de Aviso acesa_ exige nível lógico de saída **1**.
    
    Os requisitos dos circuitos são:
    
    1. **Configuração OR:** A lâmpada de aviso deve acender se **qualquer uma** das duas portas estiver aberta.
    2. **Configuração AND:** A lâmpada de aviso deve acender **apenas se ambas** as portas estiverem abertas simultaneamente.
- **Conceito utilizado:** Lógica de operações booleanas fundamentais **OR** (disjunção) e **AND** (conjunção), mapeamento de tabelas verdade e desenho de diagramas de circuitos de hardware.
    
- **Solução:** O projetista deve desenhar os circuitos e descrever suas tabelas verdade associadas:
    
    ##### Caso 1: Configuração OR (Alerta se QUALQUER porta abrir):
    
    Se os sensores das portas emitem 0 quando abertos, a lâmpada de aviso deve acender (saída 1) se o Sensor A for igual a 0 OU se o Sensor B for igual a 0. A tabela verdade correspondente é:
    
    | Sensor A (Porta) | Sensor B (Porta) | Lâmpada de Alerta (OR) | | :---: | :---: | :---: | | 0 (Aberta) | 0 (Aberta) | 1 (Alerta Ativo) | | 0 (Aberta) | 1 (Fechada) | 1 (Alerta Ativo) | | 1 (Fechada) | 0 (Aberta) | 1 (Alerta Ativo) | | 1 (Fechada) | 1 (Fechada) | 0 (Normal) |
    
    _Diagrama:_ Conectar os pinos de saída dos dois sensores de porta magnéticos diretamente em uma porta lógica de função **OR**.
    
    ##### Caso 2: Configuração AND (Alerta apenas se AMBAS as portas abrirem):
    
    A lâmpada só acende (saída 1) se o Sensor A for igual a 0 E o Sensor B for igual a 0 simultaneamente. A tabela verdade correspondente é:
    
    | Sensor A (Porta) | Sensor B (Porta) | Lâmpada de Alerta (AND) | | :---: | :---: | :---: | | 0 (Aberta) | 0 (Aberta) | 1 (Alerta Ativo) | | 0 (Aberta) | 1 (Fechada) | 0 (Normal) | | 1 (Fechada) | 0 (Aberta) | 0 (Normal) | | 1 (Fechada) | 1 (Fechada) | 0 (Normal) |
    
    _Diagrama:_ Conectar as saídas de sinal dos sensores físicos nas entradas de uma porta de lógica **AND**.
    
- **Resultado:** Dois protótipos de segurança residencial funcionais com lógicas de proteção residencial distintas e bem definidas via hardware.
    
- **Por que essa solução funciona:** A solução OR funciona porque a operação lógica OR produz saída verdadeira se pelo menos uma de suas entradas for verdadeira (no circuito, se pelo menos um sensor emitir status de aberto). A solução AND funciona porque a conjunção exige que todas as entradas sejam simultâneas para habilitar a saída ativa.
    
- **O que preciso aprender com esse exemplo:** Tabelas verdade representam matematicamente todos os comportamentos possíveis de sensores físicos no mundo real, definindo como o hardware do sistema de aviso responderá às mudanças de ambiente.