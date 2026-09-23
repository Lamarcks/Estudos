[[EXERCÍCIOS DE ARQUITETURA E ORGANIZAÇÃO DE COMPUTADORES]]
#ASSUNTO

## Conceitos principais

- **Sistemas Numéricos (Bases de Representação):** Métodos matemáticos para expressar e codificar informações quantitativas. Enquanto humanos utilizam o sistema decimal (base 10), os computadores operam no binário (base 2) em razão da lógica de tensão elétrica dos transistores. Bases intermediárias como octal (base 8) e hexadecimal (base 16) servem para compactar e facilitar a leitura humana dessas longas cadeias binárias.
- **Álgebra Booleana:** Estrutura matemática discreta que utiliza variáveis binárias (0 ou 1, Falso ou Verdadeiro) sob operadores lógicos (AND, OR, NOT). É o alicerce para projetar e simplificar expressões lógicas que comandam o fluxo de sinais elétricos em hardwares.
- **Arquitetura de Von Neumann:** Modelo conceitual clássico que define o computador através de cinco divisões funcionais: Unidade de Controle (UC), Unidade Aritmética e Lógica (UAL), Memória Principal, Dispositivos de E/S e Barramentos. Sua principal característica é armazenar dados e instruções de programas sob o mesmo espaço físico de memória.
- **Hierarquia de Memórias:** Pirâmide de classificação de dispositivos de armazenamento cujo objetivo é balancear velocidade (tempo de acesso), capacidade de dados e custos financeiros. Baseia-se no princípio de que memórias ultra-rápidas e caras (como os registradores) são limitadas e residem perto do processador, enquanto memórias baratas, massivas e mais lentas (secundárias) ficam na base.
- **Acesso Direto à Memória (DMA):** Técnica de Entrada e Saída que permite a periféricos transferirem blocos maciços de dados diretamente para a memória do sistema sem interromper ou onerar a CPU a cada byte transmitido.

---

## Conteúdo explicado

### 1. Sistemas Numéricos e Conversões de Base

#### A Lógica Posicional

Qualquer número em uma base \(b\) representa a somatória dos dígitos multiplicados por pesos de potências dessa base (\(b^{\text{posição}}\)), iniciando com o expoente \(0\) à extrema direita.

- **Exemplo (Decimal - Base 10):** \(892_{10} = (8 \times 10^2) + (9 \times 10^1) + (2 \times 10^0) = 800 + 90 + 2 = 892\).
- **Exemplo (Binário - Base 2):** \(1011_2 \rightarrow (1 \times 2^3) + (0 \times 2^2) + (1 \times 2^1) + (1 \times 2^0) = 8 + 0 + 2 + 1 = 11_{10}\).

#### Métodos de Conversão

1. **De Decimal para Outras Bases (Divisão Sucessiva):** Divide-se o valor decimal repetidamente pela base desejada até obter quociente zero. Os restos das divisões, anotados de baixo para cima, compõem o valor na nova base.
    - _Exemplo (13 para Binário):_ \(13 \div 2 = 6\) (resto 1) \(\rightarrow 6 \div 2 = 3\) (resto 0) \(\rightarrow 3 \div 2 = 1\) (resto 1) \(\rightarrow 1 \div 2 = 0\) (resto 1). Lendo de baixo para cima: \(1101_2\).
2. **Binário para Octal (Agrupamento por 3):** Como \(2^3 = 8\), separa-se o número binário em grupos de três bits de direita para a esquerda e converte-se cada trio diretamente para seu equivalente de 0 a 7.
    - _Exemplo:_ \(110101_2 \rightarrow 110\) e \(101 \rightarrow 65_8\).
3. **Binário para Hexadecimal (Agrupamento por 4):** Como \(2^4 = 16\), separa-se o binário em grupos de quatro bits da direita para a esquerda, usando letras de A a F para representar valores decimais de 10 a 15.
    - _Exemplo:_ \(11010101_2 \rightarrow 1101\) (\(D\)) e \(0101\) (\(5\)) \(\rightarrow D5_{16}\).
4. **Octal para Hexadecimal (e vice-versa):** Não há conversão direta imediata porque 8 e 16 não são potências múltiplas diretas. Usa-se obrigatoriamente a base **binária** como ponte.
    - _Octal para Hexadecimal:_ Expande-se cada dígito octal em 3 bits binários, depois reagrupa-se esses bits em blocos de 4 para achar o hexadecimal.
    - _Hexadecimal para Octal:_ Expande-se o hexadecimal em grupos de 4 bits, reagrupando-os de 3 em 3 para obter o octal.

---

### 2. Álgebra Booleana, Teoremas e Portas Lógicas

#### Operações Lógicas Fundamentais e Tabelas Verdade

- **AND (E / Conjunção / \(\cdot\)):** O resultado só é verdadeiro (1) se todos os operandos forem simultaneamente verdadeiros (1).
- **OR (OU / Disjunção / \(+\)):** O resultado é verdadeiro (1) se pelo menos um dos operandos for verdadeiro (1).
- **NOT (NÃO / Inversão / \(\bar{A}\) ou \(\neg A\)):** Operador unário que inverte o estado lógico da variável.

|Entrada A|Entrada B|A AND B|A OR B|NOT A|
|:--|:--|:--|:--|:--|
|0|0|0|0|1|
|0|1|0|1|1|
|1|0|0|1|0|
|1|1|1|1|0|

#### Portas Lógicas Especiais e Universais

- **NAND (Não E):** Realiza a operação AND e inverte o resultado (\(\overline{A \cdot B}\)). É considerada uma **porta universal** pois qualquer outro circuito lógico pode ser construído apenas usando portas NAND.
- **NOR (Não OU):** Negação completa da operação OR (\(\overline{A+B}\)). Também é uma porta de caráter universal.
- **XOR (OU Exclusivo / \(\oplus\)):** Produz saída 1 quando as entradas são diferentes (número ímpar de uns nas entradas).
- **XNOR (Não OU Exclusivo / \(\odot\)):** Inverso da XOR; produz saída verdadeira (1) apenas se as entradas forem iguais.

#### Leis de Simplificação Booleana

Essas regras permitem projetar circuitos físicos mais eficientes, compactando expressões lógicas de modo a gastar menos portas e energia:

- _Leis Comutativas:_ \(A + B = B + A\) e \(A \cdot B = B \cdot A\).
- _Leis Associativas:_ \((A + B) + C = A + (B + C)\) e \((A \cdot B) \cdot C = A \cdot (B \cdot C)\).
- _Lei Distributiva:_ \(A \cdot (B + C) = A \cdot B + A \cdot C\).
- _Lei da Absorção:_ \(A + (A \cdot B) = A\) e \(A \cdot (A + B) = A\).
- _Leis de De Morgan:_
    1. O complemento do produto lógico é a soma lógica dos complementos: \(\overline{A \cdot B} = \bar{A} + \bar{B}\).
    2. O complemento da soma lógica é o produto lógico dos complementos: \(\overline{A + B} = \bar{A} \cdot \bar{B}\).

---

### 3. Circuitos Lógicos Digitais

#### Lógica Combinacional vs. Lógica Sequencial

- **Lógica Combinacional:** Circuitos nos quais as saídas dependem única e exclusivamente das combinações das entradas presentes naquele instante. Não retêm memória de estados passados.
    - _Sinal Enable (\(En\)):_ Funciona como um pino interruptor de hardware. Quando \(En = 1\), o circuito opera normalmente; quando \(En = 0\), o componente fica desabilitado e suas saídas vão a zero.
    - _Exemplos de Circuitos:_ Codificadores, Decodificadores, Comparadores lógicos e **Multiplexadores** (dispositivos que direcionam dados de múltiplas entradas para uma única saída guiados por pinos seletores).
- **Lógica Sequencial:** Circuitos nos quais a saída depende tanto das entradas atuais quanto do estado armazenado anteriormente (memória). Dependem da evolução temporal e necessitam de um sinal de sincronismo chamado **Clock**.
    - **Latch:** Elemento mais básico de memória estável. É assíncrono e trabalha realimentando continuamente seu próprio sinal de saída em suas entradas cruzadas.
    - **Flip-Flop:** Dispositivo de armazenamento síncrono que altera seu estado binário interno (0 ou 1) apenas sob a ação estrita de uma **borda de transição** do sinal de clock (borda ascendente ou descendente).

#### Classificação de Circuitos Integrados (CIs / Chips)

Classificados conforme o volume de transistores integrados no chip de silício:

- **SSI:** Dezenas de transistores.
- **MSI:** Centenas de transistores.
- **LSI:** Milhares de transistores.
- **VLSI:** De dezenas de milhares a bilhões de transistores (como os microprocessadores atuais).

---

### 4. Estrutura do Processador (CPU)

A Unidade Central de Processamento é dividida em blocos funcionais mínimos:

1. **Unidade Aritmética e Lógica (UAL):** Bloco executor de todos os cálculos matemáticos (soma, subtração) e comparações lógicas booleanas do sistema.
2. **Unidade de Controle (UC):** Bloco coordenador. Ela busca as instruções brutas gravadas na memória, decodifica sua funcionalidade e gera os pulsos de controle comandando os outros componentes lógicos do computador.
3. **Registradores:** Células internas de memória de velocidade ultra-alta que armazenam variáveis temporárias imediatas usadas pela UAL e UC. Exemplo: o **Contador de Programa (PC)**, que guarda especificamente o endereço de memória física da próxima instrução a ser executada.
4. **Clock (Relógio):** Oscilador eletrônico que dita os passos (pulsos) lógicos da CPU. A sua frequência de operação, medida em Gigahertz (GHz), estabelece quantos ciclos de clock ocorrem por segundo.

#### Arquiteturas de Instrução: CISC vs. RISC

- **CISC (Complex Instruction Set Computers):**
    - _Características:_ Conjunto amplo, robusto e complexo de instruções integradas no próprio hardware. Uma instrução complexa faz muito trabalho, reduzindo o número de linhas de programa (economizando espaço de memória no passado).
    - _Trade-off:_ Devido à complexidade interna, cada ciclo de execução de instrução torna-se longo e variável.
    - _Segmento:_ Dominante em PCs tradicionais (chips Intel e AMD).
- **RISC (Reduced Instruction Set Computer):**
    - _Características:_ Conjunto enxuto, simplificado e altamente otimizado de instruções. Cada comando simples é processado de forma extremamente rápida (frequentemente 1 instrução por ciclo de relógio).
    - _Trade-off:_ Exige mais linhas de código (programas maiores) para realizar tarefas complexas, mas o software lida com essa otimização de forma eficiente.
    - _Segmento:_ Extremamente eficiente energeticamente; ideal para dispositivos móveis, smartphones e embarcados (processadores ARM).

---

### 5. Hierarquia de Sistemas de Memória

A memória é organizada de forma piramidal. À medida que subimos na pirâmide (em direção à CPU), a velocidade e o custo de fabricação sobem drasticamente, fazendo com que a capacidade de armazenamento diminua.

```
  ▲  [Nível 1] Registradores (Internos à CPU)
  │  [Nível 2] Memória Cache (L1, L2, L3 - SRAM integrada)
  │  [Nível 3] Memória Principal (RAM - DRAM dinâmica)
  │  [Nível 4] Memória Secundária (SSD / HDD - Persistentes)
  ▼  [Nível 5] Memória Terciária (Fitas Magnéticas - Backups Frios)
```

#### Tipos de Memória Semicondutora

- **RAM (Random Access Memory - Volátil):** Funciona como a mesa de trabalho do processador; retém os dados de sistemas operacionais e softwares em execução. Seus dados são completamente apagados sem energia elétrica.
    - _DRAM (Dinâmica):_ Tecnologia de baixo custo usada como a RAM principal de computadores; necessita de pulsos periódicos de atualização (_refresh_) para não perder os dados armazenados eletricamente em seus capacitores.
    - _SRAM (Estática):_ Rápida e cara, baseada em circuitos flip-flop; dispensa ciclos de _refresh_. É empregada na fabricação das memórias **Cache**.
- **ROM (Read-Only Memory - Não Volátil):** Memória gravada na fábrica que mantém suas informações mesmo sem energia elétrica. Usada para armazenar firmwares críticos de inicialização do sistema (como a BIOS).

#### O Princípio da Localidade na Memória Cache

A memória cache atua como um atalho ultra-rápido entre a lenta RAM e a rápida CPU. Seu funcionamento apoia-se em dois princípios lógicos:

1. **Localidade Temporal:** Se um dado da RAM foi acessado uma vez pela CPU, é altamente provável que o sistema precise lê-lo novamente em um futuro próximo (mantendo-o na cache).
2. **Localidade Espacial:** Se um dado específico foi acessado, as informações gravadas nos endereços de memória vizinhos a ele têm altíssima chance de serem requisitadas logo em seguida (trazendo blocos adjacentes para a cache).

#### Armazenamento Secundário

Dispositivos persistentes não voláteis de alta capacidade:

- **HDD (Discos Magnéticos):** Utilizam discos rotativos revestidos de material magnético lidos por cabeças físicas. Têm excelente relação custo por Gigabyte, mas são lentos devido ao movimento mecânico.
- **SSD (Unidades de Estado Sólido):** Dispositivos sem partes móveis baseados em células semicondutoras de **Memória Flash**. Oferecem tempos de acesso quase instantâneos e resistência mecânica física.
    - _Flash NOR:_ Permite acesso aleatório byte a byte; ideal para gravação rápida de firmware e códigos de boot.
    - _Flash NAND:_ Acesso rápido apenas em blocos densos; ideal para SSDs, cartões de memória e unidades USB.

---

### 6. Interface de Entrada/Saída (E/S)

Métodos estruturados para realizar a troca de dados entre a CPU/Memória e o mundo físico externo:

1. **E/S Programada (Espera Ativa):** A CPU fica presa em um ciclo de repetição contínuo verificando constantemente o estado do periférico para saber se há dados. Altamente ineficiente e obsoleta.
2. **E/S por Interrupção:** O processador segue executando outras tarefas até que um dispositivo envie um sinal físico de interrupção. A CPU interrompe temporariamente sua atividade corrente, realiza o tratamento do dado recebido e depois retorna ao estado anterior.
3. **Acesso Direto à Memória (DMA):** Um chip controlador de DMA dedicado assume os barramentos de controle de dados e endereços do computador. Ele coordena a cópia direta de blocos maciços de dados entre periféricos rápidos (como SSDs ou placas de rede) e a Memória RAM sem pedir intervenção direta da CPU, gerando apenas um único sinal de interrupção após terminar todo o lote de envio.
4. **Canais de Processamento de E/S:** Processadores independentes dedicados exclusivamente a gerenciar operações de entrada e saída em grandes servidores e data centers, liberando totalmente a CPU principal.

---

## Conceitos que não posso confundir

```
┌────────────────────────────────────────────────────────────────────────┐
│                              CISC vs RISC                              │
├──────────────────────────────────────┬─────────────────────────────────┤
│ CISC                            │ RISC                       │
├──────────────────────────────────────┼─────────────────────────────────┤
│ Instruções extensas e complexas      │ Instruções simples e enxutas    │
│ Poucos registradores gerais          │ Muitos registradores            │
│ Foco na eficiência de código (SW)    │ Foco na eficiência de relógio   │
│ Ciclo de relógio longo e variável    │ Ciclo curto e uniforme (1 ciclo)│
└──────────────────────────────────────┴─────────────────────────────────┘
```

- **Lógica Combinacional vs. Lógica Sequencial:** Circuitos combinacionais calculam saídas baseadas exclusivamente nas entradas do exato momento (não possuem memória). Circuitos sequenciais levam em consideração o estado interno anterior (histórico) e são sincronizados por pulsos de relógio (clock).
- **Latch vs. Flip-Flop:** Ambos guardam 1 bit de informação. Contudo, o latch é ativado e reage continuamente por níveis de tensão lógicos, enquanto o flip-flop atualiza de forma controlada apenas no instante das bordas de clock (transições físicas de subida/descida de sinal).
- **Flash NOR vs. Flash NAND:** Flash NOR oferece leitura rápida de bytes individuais, sendo usada para executar código de firmware direto na memória. Flash NAND lê apenas em blocos (não permite acesso byte a byte direto), mas tem alta velocidade de gravação e grande densidade física, sendo usada para armazenamento em massa de arquivos (SSDs).
- **E/S por Interrupção vs. DMA:** Na E/S por interrupção, embora a CPU seja livre para fazer outras tarefas antes do dispositivo estar pronto, a transferência de cada palavra de dado obrigatoriamente passa pelos registradores e ALU da CPU. No DMA, a CPU programa o controlador e depois se desliga completamente da transferência física; os dados trafegam de forma autônoma e direta para a RAM via hardware.

---

## Pontos importantes para prova

- **Gargalo de Von Neumann:** Fenômeno limitante que ocorre porque o processador precisa usar o mesmo caminho de barramento de sistema para buscar instruções na memória de código e ler/escrever dados na memória de dados de forma alternada. O processador veloz é obrigado a esperar a lenta transferência do barramento físico, reduzindo o rendimento teórico do computador.
- **A Porta Universal NAND:** Entenda como portas NAND são capazes de implementar as funções NOT, AND e OR unicamente pela combinação de suas conexões lógicas.
- **Princípios da Cache:** Saiba definir localidade espacial (endereços vizinhos) e temporal (repetição no tempo curto) de acessos e como isso evita que a CPU tenha que buscar dados na RAM a 60ns, puxando-os na cache a 1ns.
- **Etapas operacionais de um Canal de E/S / DMA:**
    1. _Inicialização:_ CPU envia comando para o módulo controlador indicando endereço inicial de RAM, tamanho do bloco e tipo de operação.
    2. _Transferência:_ O controlador de DMA ou Canal gerencia os barramentos e move autonomamente as informações utilizando buffers.
    3. _Controle:_ Monitoramento de erros de sinal e contagem de dados.
    4. _Interrupção:_ Ao final do envio de todo o bloco de dados, o controlador gera uma interrupção física única para avisar a CPU.

---

## Revisão rápida

- `Bases Numéricas:` Binário (2), Octal (8), Decimal (10), Hexadecimal (16).
- `Conversões:` Decimal para outra base = divisões sucessivas. De outra base para decimal = somatório de potências. Binário \(\leftrightarrow\) Octal agrupa de 3 em 3 bits. Binário \(\leftrightarrow\) Hexadecimal agrupa de 4 em 4 bits.
- `Álgebra Booleana:` AND (multiplicação lógica; tudo 1 dá 1). OR (soma lógica; qualquer entrada 1 dá 1). NOT (inverte o bit). Teoremas de De Morgan invertem sinais de produto e soma quebrando e unindo a barra de negação (\(\overline{A \cdot B} = \bar{A} + \bar{B}\) e \(\overline{A+B} = \bar{A} \cdot \bar{B}\)).
- `Arquitetura Von Neumann:` Divide o hardware em UC, UAL, Memória Principal, Dispositivos de E/S interconectados por barramentos de dados, endereço e controle. Dados e códigos residem no mesmo espaço físico de memória.
- `Hierarquia de Memória:` Registradores (ultra-rápidos, internos, baixa capacidade) \(\rightarrow\) Cache (SRAM, ponte veloz baseada em localidade de dados) \(\rightarrow\) Memória Principal (DRAM de acesso aleatório volátil) \(\rightarrow\) Memória Secundária (HDD e SSD persistentes não voláteis) \(\rightarrow\) Memória Terciária (Fitas magnéticas offline).
- `E/S:` Programada (CPU presa testando periférico) \(\rightarrow\) Interrupção (periférico sinaliza eletricamente a CPU) \(\rightarrow\) DMA (controlador assume barramento e gerencia cópia de blocos diretos para a RAM sem sobrecarregar a CPU).

---
