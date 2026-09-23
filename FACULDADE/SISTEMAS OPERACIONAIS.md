[[ESTUDOS DE CASO DE SISTEMAS OPERACIONAIS]]
#ASSUNTO
## Conceitos principais

- **Sistema Operacional (S.O.)**: O software elo entre o hardware e os programas do usuário, responsável pelo gerenciamento de recursos e pela segurança/integridade dos dados do computador.
- **Processo**: Uma instância ativa de um programa de computador em execução, contendo seu próprio espaço de endereçamento, variáveis, registradores e contador de programa.
- **Thread (Processo Leve)**: Um fluxo de controle independente dentro de um processo. Múltiplas threads de um mesmo processo compartilham seu espaço de endereço e recursos, o que acelera a comunicação e economiza overhead de sistema.
- **Swapping**: Técnica de gerenciamento de memória onde processos inteiros são movidos da memória principal (RAM) para a memória secundária (disco) para liberar espaço, e retornados à RAM quando chegam seus momentos de execução.
- **Memória Virtual**: Extensão lógica da RAM física que utiliza espaço em disco para dar às aplicações a ilusão de possuírem mais memória disponível do que a fisicamente instalada.
- **DMA (Acesso Direto à Memória)**: Mecanismo de hardware que permite a dispositivos de E/S transferirem dados diretamente de/para a RAM sem ocupar a CPU.
- **Sistema de Arquivos**: Estrutura lógica implementada pelo S.O. para organizar, nomear, ler, gravar, proteger e recuperar dados em dispositivos de armazenamento secundário.

---

## Conteúdo explicado

### 1. Introdução, Funções e Evolução dos S.O.

#### Evolução Histórica das Gerações de Computadores

1. **Primeira Geração (1945–1955) — Válvulas e Painéis**: Máquinas imensas e lentas, operadas manualmente por fios e plugues. **Não existiam S.O. ou linguagens de programação**; caso uma válvula queimasse, todo o cálculo matemático militar (como logaritmos) se perdia.
2. **Segunda Geração (1955–1965) — Transistores e Sistemas Batch**: Surgimento dos _mainframes_ acessíveis apenas a bancos e grandes centros. Introdução do **processamento em lote (batch)**, que agrupava jobs em fitas magnéticas para otimizar o tempo de processamento. Surgimento das linguagens Fortran e Assembly.
3. **Terceira Geração (1965–1980) — Circuitos Integrados e Multiprogramação**: Divisão de produtos em linhas comerciais e científicas e o início do compartilhamento eficiente de CPU entre múltiplos processos na memória.
4. **Quarta Geração (1980–Presente) — Computadores Pessoais**: Era dos microchips e computadores pessoais rápidos e baratos. Desenvolvimento do MS-DOS, Unix e as primeiras interfaces gráficas (base do Windows). Surgiram sistemas de rede, sistemas distribuídos, embarcados, mobile e computação em nuvem.

#### As Duas Grandes Funções do S.O.

- **Estender a máquina (Abstração)**: O S.O. apresenta uma "máquina virtual" amigável aos desenvolvedores, ocultando a complexidade física do hardware. Por exemplo, trata dispositivos complexos simplesmente como arquivos legíveis.
- **Gerenciar Recursos**: Controla o compartilhamento ordenado de CPU, memória e periféricos entre os diversos processos concorrentes. Este gerenciamento ocorre no **tempo** (decidindo quem usa o recurso e por quanto tempo) e no **espaço** (dividindo o recurso físico, como a RAM, entre as aplicações).

#### Tipos de Sistemas Operacionais

- **Embarcados**: Utilizados em eletrodomésticos, TVs e celulares, combinando tempos reais com limitações rígidas de memória e energia.
- **Mobile**: Projetados para dispositivos móveis, focados em comunicação sem fio direta (Bluetooth, Wi-Fi) e periféricos como câmeras.
- **Na Nuvem**: Baseados na internet, onde os aplicativos e dados do usuário ficam salvos na web (ex: Chrome OS).
- **Cartões Inteligentes (Smart Cards)**: Os menores S.O.s existentes, operando com severas limitações físicas de energia e memória em chips de cartões de saque ou pagamento.

#### Estruturas do Núcleo (Kernel)

- **Arquitetura Monolítica**: O núcleo roda inteiramente em modo privilegiado (modo núcleo). É composto pelo kernel (dividido entre rotinas dependentes de hardware e rotinas independentes para system calls), o shell (interpretador de comandos) e sistemas de arquivos. **Exemplos**: Unix e Linux.
- **Arquitetura de Micronúcleo (Microkernel)**: O S.O. é dividido em pequenos módulos independentes que gerenciam funções específicas. Seus módulos podem ser modificados sem alterar todo o sistema. **Exemplo**: Windows 2000 (escrito em C).

---

### 2. Gerenciamento de Processos, Sincronização e Escalonamento

#### Estados de um Processo e Transições

Um processo ativo transita continuamente entre três estados principais:

1. **Em Execução**: Sendo processado ativamente pela CPU.
2. **Pronto**: Possui todos os recursos necessários para rodar, aguardando apenas que a CPU seja alocada pelo S.O..
3. **Bloqueado (Espera)**: Paralisado aguardando um evento externo ou operação de E/S (como leitura de disco ou teclado).

```
                     Aguarda evento / E/S
    (Em Execução) ───────────────────────────> (Bloqueado)
          │ ^                                       │
          │ │                                       │
      │ │ Escalonador                       │ Evento ocorre /
   Timeout│ │ seleciona                             │     E/S concluída
          v │                                       v
       (Pronto) <───────────────────────────────────┘
```

- **Transição 1 (Execução -> Bloqueado)**: Ocorre quando o processo faz uma requisição bloqueante.
- **Transição 2 (Execução -> Pronto)**: Ocorre por interrupção do relógio físico quando o tempo reservado (quantum) esgota.
- **Transição 3 (Pronto -> Execução)**: O escalonador escolhe o processo da fila de prontos.
- **Transição 4 (Bloqueado -> Pronto)**: O evento aguardado ocorre, e o processo volta a competir pela CPU.

> [!important] **Criação e Término de Processos**
> 
> - **Criação**: Ocorre na inicialização do sistema (_boot_), por requisição do usuário (duplo clique), chamada de sistema de outro processo ou jobs em lote.
> - **Término**: Pode ser voluntário (saída normal ou saída por erro previsto) ou involuntário (erro fatal de hardware/software como divisão por zero ou cancelamento por outro processo).

#### Condição de Disputa (Corrida) e Regiões Críticas

Quando dois ou mais processos compartilham uma área de memória ou arquivo, realizando leituras e escritas simultâneas, o resultado final pode se tornar inconsistente, dependendo estritamente do tempo de execução de cada um. Esse fenômeno é a **Condição de Disputa**.

Para evitá-lo, a seção do código que manipula essa memória compartilhada é chamada de **Região Crítica**. A aplicação deve implementar a **Exclusão Mútua**: garantir que apenas um processo entre na região crítica por vez.

#### Soluções para a Exclusão Mútua

##### A. Com Espera Ociosa (Gasto ineficiente de CPU em loops contínuos de teste)

- **Desabilitar Interrupções**: O processo desliga as interrupções ao entrar na região crítica. **Desvantagem**: Perigoso dar controle total ao usuário; não funciona em múltiplos processadores.
- **Variáveis de Impedimento (Lock)**: Variável binária de controle. **Desvantagem**: Mantém a condição de corrida se dois processos checarem o lock `0` ao mesmo tempo antes de alterá-lo para `1`.
- **Alternância Obrigatória (Turn)**: Variável compartilhada indica a vez. **Desvantagem**: Se um processo for rápido e outro lento, o lento impede o rápido de reentrar na região crítica, violando as regras de exclusão mútua.
- **Solução de Peterson**: Algoritmo puramente de software em C que utiliza primitivas `enter_region` e `leave_region`. **Desvantagem**: Ainda utiliza espera ociosa.
- **Instrução TSL (Test and Set Lock)**: Comando de hardware que lê e altera a variável lock em um único ciclo indivisível.

##### B. Sem Espera Ociosa (Processos são bloqueados e liberam a CPU)

- **Primitivas Dormir e Acordar (Sleep/Wakeup)**: Bloqueiam o processo quando ele não pode prosseguir e o despertam quando o recurso é liberado, eliminando o desperdício de CPU.
- **Semáforos**: Variáveis inteiras acessadas via operações atômicas indivisíveis: **DOWN** (decrementa; se for 0, o processo bloqueia na fila de espera) e **UP** (incrementa; se houver processos bloqueados, escolhe um para o estado pronto). Podem ser **Binários (Mutexes)** — assumindo valores 0 ou 1 — ou **Contadores** — assumindo inteiros positivos.
- **Monitores**: Estruturas de sincronização de alto nível encapsuladas em módulos (suportadas por linguagens como Java). O compilador garante que apenas um processo esteja ativo dentro do monitor por vez, utilizando variáveis de condição com primitivas `wait` e `signal`.
- **Troca de Mensagens**: Comunicação via chamadas ao sistema `send` (enviar) e `receive` (receber), útil para ambientes distribuídos de rede.

#### Algoritmos de Escalonamento de CPU

O escalonador decide qual processo usará a CPU a partir de metas como: maximizar o uso do processador e o rendimento (_throughput_), e minimizar o tempo de espera, o tempo de resposta e o _turnaround_ (tempo total do início ao fim do processo).

##### Escalonamento Não-Preemptivo (O processo retém a CPU até terminar ou bloquear voluntariamente)

- **FIFO (First-In, First-Out)**: Executa na ordem de chegada. Simples, mas ignora tamanho ou importância dos processos.
- **SJF (Shortest Job First)**: Roda primeiro o job mais curto. **Exemplo**: Quatro tarefas de \(8, 4, 4, 4\) minutos na fila. Se rodadas em ordem FIFO, a média de retorno é de \(14\) minutos. Se rodadas em SJF, a média cai para \(11\) minutos.

##### Escalonamento Preemptivo (O S.O. pode interromper o processo para alocar a CPU a outro)

- **SRT (Shortest Remaining Time First)**: Versão preemptiva do SJF; se um novo job chega com tempo restante total menor que o do atual em execução, a CPU é interrompida e dada a ele.
- **Round Robin (Circular)**: Cada processo recebe uma fatia idêntica de tempo máxima de uso (**quantum**), normalmente entre \(10\) e \(100\) milissegundos. Ao final do quantum, o processo vai para o fim da fila de prontos. Impede o monopólio da CPU.
- **Escalonamento por Prioridades**: Associa uma prioridade a cada processo; o de maior valor roda primeiro. Pode ser **estática** (imutável) ou **dinâmica** (alterada dinamicamente para evitar a inanição de processos de prioridades baixas).
- **Escalonamento Garantido**: Garante uma fração exata da CPU a cada usuário ativo (\(1/n\)).
- **Escalonamento por Loteria**: Distribui bilhetes aos processos; sorteios periódicos de fatias de CPU ocorrem de forma probabilística.
- **Fração Justa (Fair-share)**: Considera o dono do processo para evitar que um usuário com dezenas de tarefas monopolize a CPU contra outro usuário com uma única tarefa.

---

### 3. Gerenciamento de Memória Real e Virtual

#### Gerenciamento de Memória Real (Sem Paginação)

- **Monoprogramação sem Swapping**: Apenas um processo reside na memória compartilhada diretamente com o S.O.. Usado em sistemas embarcados clássicos ou no antigo MS-DOS.
- **Técnica de Overlay**: O programador dividia manualmente o programa em módulos independentes que usavam a mesma área física da RAM, sobrepondo dados desnecessários dinamicamente.
- **Alocação Particionada Fixa**: Memória dividida em partições de tamanho fixo definidas no boot. Processos são alocados nas partições de menor tamanho suficiente. Gera **fragmentação interna** (espaço desperdiçado dentro da partição).
- **Alocação Particionada Variável**: O S.O. cria partições dinamicamente conforme os processos chegam, alocando exatamente o espaço necessário. Evita a fragmentação interna, mas gera **fragmentação externa** (pequenos blocos vazios entre partições).
    - **Compactação de Memória**: Técnica que move todos os blocos ocupados para os endereços mais baixos da RAM, juntando os espaços livres. É extremamente custosa para o processador.

#### Swapping e Gerenciamento com Mapa de Bits

O gerenciador de memória real pode mapear áreas livres e ocupadas usando um **Mapa de Bits**:

- A memória RAM é dividida em pequenas unidades de alocação.
- Cada unidade é mapeada para 1 bit no mapa: **1 = ocupada por processo**, **0 = livre**.
- **Vantagem**: Tamanho fixo do mapa dependente apenas da RAM e da unidade adotada.
- **Desvantagem**: Processo extremamente lento para pesquisar sequências de bits `0` consecutivos para carregar novos programas.

#### Proteção e Relocação de Memória Física

Como os processos rodam em posições dinâmicas diferentes da RAM física, as instruções que usam endereços precisam ser ajustadas pelo _linker_ no carregamento. Para evitar que uma aplicação invada a área reservada a outra ou ao próprio S.O., o hardware do processador utiliza dois registradores especiais de proteção:

- **Registrador-Base**: Carrega o endereço inicial físico da partição do processo.
- **Registrador-Limite**: Define o tamanho máximo de endereçamento da partição.
- **Regra**: Todo endereço gerado pelo processo é checado fisicamente; se for maior que o limite ou fora da base, o hardware gera um erro e impede o acesso indevido.

#### Memória Virtual por Paginação

Divide o espaço de endereçamento em blocos lógicos de tamanho fixo chamados **Páginas** (as correspondentes na memória RAM física são chamadas de _frames_ ou molduras de páginas).

- **Tabela de Páginas**: Estrutura mantida pelo S.O. que mapeia endereços virtuais em endereços físicos na RAM ou bloco no disco.
- **Falta de Página (Page Fault)**: Ocorre quando um processo acessa um endereço cuja página virtual correspondente não está carregada na RAM física. O hardware interrompe a execução, e o S.O. localiza e carrega a página a partir do disco.
- **Paginação Sob Demanda**: Páginas de um processo só são trazidas do disco rígido para a RAM física no instante exato em que são acessadas, poupando espaço de memória.

#### Algoritmos de Substituição de Páginas (Substituição de Frame)

Quando a RAM física esgota e ocorre uma falta de página, o S.O. deve decidir qual página remover para liberar espaço para a nova:

> [!warning] **Modificação de Página** Se a página escolhida para remoção foi alterada na RAM (bit de modificação ativado), ela precisa ser regravada no disco para atualização. Caso não tenha sofrido modificações, basta descartá-la sem gravação.

- **FIFO**: Remove a página mais antiga na RAM. **Problema**: Pode remover páginas cruciais de uso frequente.
- **Segunda Chance**: Variação do FIFO. Checa o bit de referência da página mais antiga. Se for `1` (usada recentemente), o bit é zerado e ela é jogada ao fim da fila física, ganhando nova chance. Se for `0`, é removida.
- **Relógio (Clock)**: Versão simplificada da Segunda Chance que organiza as páginas em estrutura circular com ponteiro móvel, economizando movimentações de fila.
- **LRU (Least Recently Used)**: Remove a página que passou mais tempo sem ser referenciada. Tende a reter as mais ativas, mas sua implementação em hardware é de alto custo.
- **NUR (Not Used Recently)**: Classifica as páginas em categorias baseadas nos bits de referência e de modificação, removendo prioritariamente as não usadas e não modificadas recentemente.
- **LFU (Least Frequently Used)**: Remove a página com o menor contador de uso frequente.
- **WSClock (Working Set Clock)**: Combina o conjunto de trabalho (_working set_) do processo com a idade das páginas em relógio para decidir a remoção.

#### Memória Virtual por Segmentação

Diferente da paginação que divide a memória de forma fixa e unidimensional, a segmentação divide-a em **múltiplos espaços de endereçamento lógicos de tamanho variável** chamados **Segmentos**.

- Representa as divisões lógicas reais do programa conhecidas pelo programador (ex: segmento de código, tabela de símbolos, constante, pilha).
- **Vantagens**: Facilita o compartilhamento de procedimentos e bibliotecas e permite proteções isoladas diferentes para cada segmento (ex: código como apenas execução, constantes como apenas leitura).

---

### 4. Gerenciamento de Dispositivos (Entrada e Saída)

Os princípios de E/S orientam que a comunicação com mouses, teclados, impressoras e discos seja eficiente, confiável e transparente para o usuário.

#### Os 3 Princípios Fundamentais de E/S

1. **Transparência**: O software de aplicação interage com os dispositivos de forma abstrata, sem conhecer as peculiaridades físicas do hardware de cada fabricante.
2. **Eficiência**: Conclusão rápida de operações de E/S para evitar gargalos gerais do processamento.
3. **Consistência**: Comportamentos e APIs de chamadas consistentes e previsíveis.

#### Organização de Camadas de Software de E/S

- **Drivers de Dispositivos**: Programas desenvolvidos por fabricantes que fazem a comunicação direta de baixo nível com o controlador físico de hardware, traduzindo comandos abstratos do S.O. em comandos físicos de porta.
- **Camada de Gerenciamento de E/S (I/O Manager)**: Recebe solicitações dos aplicativos de alto nível, agenda-as em filas e controla a consistência e eficiência geral do subsistema.

#### Elementos Básicos de Comunicação de E/S

- **Controladores**: Chips físicos específicos do próprio dispositivo atuando como ponte entre o S.O. e a CPU.
- **Interrupções**: Sinais gerados pelo hardware de E/S avisando a CPU que a operação foi concluída e necessita de atenção.
- **Buffers e Filas**: Memória temporária de transferência usada para suavizar e equilibrar as discrepâncias de taxas de velocidade de transmissão de dados entre a CPU rápida e dispositivos lentos.
- **DMA (Direct Memory Access)**: Bloco físico que gerencia a movimentação de bytes entre o controlador e a memória principal de forma automática, aliviando a CPU de ler byte a byte durante a transmissão.

---

### 5. Sistemas de Arquivos e Diretórios

#### Conceito e Atributos de Arquivos

O arquivo é a abstração lógica visível que unifica o armazenamento a longo prazo, permitindo que dados sobrevivam ao término de processos concorrentes e caibam em grandes volumes.

- **Atributos de Controle**: Metadados gerenciados pelo S.O., como tamanho, identificador do dono/criador, data e hora de criação/modificação, permissões de controle de acesso (ACL) e flags de backup.

#### Métodos de Acesso a Arquivos

- **Acesso Sequencial**: Leitura realizada a partir do início do arquivo, byte a byte ou registro a registro na ordem em que foram gravados (ex: fitas magnéticas antigas).
- **Acesso Direto (Aleatório)**: Leitura ou gravação direta em qualquer bloco ou registro informando o número da posição física de disco. Exige que os registros internos tenham tamanho fixo.
- **Acesso Indexado (Por Chave)**: O S.O. pesquisa uma chave de busca em um arquivo índice contendo ponteiros diretos para a localização física correspondente, acelerando buscas complexas.

#### Estruturas de Arquivos Internas

1. **Sequência de bytes**: Arquivo é visto pelo S.O. apenas como fluxo livre de bytes. Alta flexibilidade para o desenvolvedor (Sistemas Unix/Windows modernos).
2. **Sequência de registro de comprimento fixo**: Estruturado em blocos repetitivos com tamanho imutável.
3. **Árvore de registros**: Estrutura em árvore ordenada por chave de busca indexada (usada em computadores comerciais de grande porte).

#### Tipos de Arquivos Suportados

- **Regulares**: ASCII (linhas de texto legível direto) ou Binários (estruturas internas compiladas exclusivas executáveis).
- **Diretórios**: Arquivos especiais que mantêm as conexões lógicas do sistema de caminhos.
- **Especiais de caracteres**: Modelam dispositivos de E/S seriais (terminais, impressoras).
- **Especiais de blocos**: Modelam o acesso direto físico a discos de armazenamento.

#### Estruturas de Diretórios e Nomes de Caminhos

- **Diretório Simples**: Um único diretório raiz centralizado contendo todos os arquivos.
- **Diretório Hierárquico**: Organização organizada em árvore lógica contendo subpastas estruturadas.
- **Caminho Absoluto**: O caminho completo unívoco que inicia diretamente na raiz (ex: `/usuário/meus_documentos/atividades.txt` em Unix ou `C:\` em Windows).
- **Caminho Relativo**: Vinculado ao diretório atual de trabalho de cada processo. Utiliza entradas especiais: **`.` (ponto)** referenciando a si próprio e **`..` (ponto-ponto)** referenciando seu diretório pai imediato na árvore.

> [!danger] **Palavras Reservadas em Sistemas de Arquivos** Sistemas de arquivos impedem a criação de diretórios ou arquivos com nomes associados a comandos internos. No Windows, por exemplo, não se pode criar arquivos com o nome **`con`** (derivado de _console_, que prepara a entrada de dados via teclado).

#### Técnicas de Implementação Física de Arquivos

- **Alocação Contígua**: Arquivos gravados em blocos sequenciais físicos contínuos no disco.
    - _Vantagens_: Muito simples de implementar, excelente desempenho de leitura e gravação.
    - _Desvantagem_: Provoca alta fragmentação externa do disco à medida que arquivos são deletados e exige que seu tamanho máximo seja definido na criação.
- **Alocação Encadeada (Lista Ligada)**: Cada bloco contém os dados e um ponteiro de endereço indicando onde começa o próximo bloco no disco.
    - _Vantagens_: Elimina a fragmentação externa física; qualquer bloco livre pode ser utilizado.
    - _Desvantagem_: Acesso aleatório extremamente lento, pois exige caminhar por toda a cadeia física para ler um bloco central.
- **FAT (Tabela de Alocação de Arquivos)**: Mapeia as conexões das listas ligadas dos arquivos físicos em uma tabela centralizada mantida na RAM. Acelera significativamente as buscas.
- **I-nodes (Nós de Índice)**: Estrutura lógica associada a cada arquivo contendo os atributos do arquivo e um conjunto de endereços físicos apontando diretamente para seus respectivos blocos em disco.

#### Segurança, Confiabilidade e Controle de Acesso

O S.O. deve manter a **Confidencialidade** (acesso apenas a autorizados), **Integridade** (dados não alterados indevidamente) e **Disponibilidade** (recursos acessíveis quando necessários).


##### Mecanismos de Proteção e Controle

- **Senha de acesso**: Associada ao arquivo; não permite granularidade fina de tarefas.
- **Grupo de usuários**: Compartilhamento e associação coletiva de arquivos.
- **Lista de Controle de Acesso (ACL)**: Lista associada ao arquivo detalhando permissões exatas de leitura/escrita para cada usuário ou grupo individual.
- **Active Directory / LDAP**: Controle de acesso corporativo unificado centralizado para autenticação e concessão de privilégios.
- **Princípio de Mínimos Privilégios (Least Privilege)**: Garantir que usuários tenham acesso estritamente necessário para exercer suas funções diárias, evitando ações administrativas por engano.
- **Backups Regulares**: Cópias de segurança diárias/semanais criptografadas e salvas fisicamente fora da rede principal para reverter perdas físicas ou contaminações por ransomware.

---

## Conceitos que não posso confundir

```
| Conceito A | Conceito B | Diferença Primordial |
| :--- | :--- | :--- |
| **Processo** | **Thread** | O processo possui espaço de endereçamento de memória próprio e isolado. As threads compartilham a mesma memória do processo pai. |
| **Swapping** | **Paginação** | O swapping transfere processos inteiros de uma vez entre RAM e disco. A paginação opera em nível fino, transferindo apenas páginas lógicas de tamanho fixo. |
| **Paginação** | **Segmentação** | A paginação divide a memória em tamanhos físicos idênticos e fixos (invisível ao programador). A segmentação divide em blocos lógicos variáveis (conhecidos pelo programador). |
| **Alocação Contígua** | **Alocação Encadeada** | A contígua aloca blocos contínuos adjacentes físicos (ótimo desempenho, mas gera fragmentação). A encadeada espalha blocos encadeados por ponteiros (sem fragmentação, mas acesso aleatório lento). |
| **Software Livre** | **Código Aberto** | O software livre pode ser modificado e redistribuído livremente, mantendo a obrigação de continuar livre. O código aberto permite modificação do código, mas o autor original pode impor restrições de uso e distribuição. |
```

---

## Pontos importantes para prova

1. **Diferenças de Hierarquia Unix vs Windows**:
    - No **Unix**, existe relação pai-filho estrita. Se o pai for encerrado ("morto"), todos os processos filhos da árvore são encerrados conjuntamente.
    - No **Windows**, os processos são isolados por IDs. Não há hierarquia estrita; se o pai morrer, o filho permanece ativo.
2. **Espera Ociosa (Busy Waiting)**: Entenda que algoritmos como Peterson, Variáveis de Lock, Alternância Obrigatória e TSL desperdiçam CPU de forma contínua em laços infinitos, ao contrário de Sleep/Wakeup ou Semáforos.
3. **Funcionamento do DMA**: Saber que ele desonera a CPU lendo dados dos dispositivos periféricos diretamente para a RAM.
4. **Registradores Base e Limite**: A barreira física de proteção de memória de processos em monoprogramação e partições fixas.
5. **A palavra reservada "con"**: Arquivos do Windows não podem possuir este nome por ser palavra de uso exclusivo do console de teclado do sistema.

---

## Revisão rápida

- **S.O.** é o elo entre hardware e software.
- **Kernel** opera em modo núcleo. **Shell** interpreta comandos.
- **Processos** transitam entre: _Execução_, _Pronto_ e _Bloqueado_.
- **Preempção** permite suspender processos para entrada de aplicações de alta prioridade.
- **Round Robin** utiliza fatias chamadas **quantum**.
- **Semáforos** utilizam chamadas **DOWN** (bloqueia se 0) e **UP** (desperta processos da fila).
- **Swapping** é lento por depender da velocidade de disco.
- **Páginas** têm tamanho fixo. **Segmentos** têm tamanhos variáveis.
- **Page Fault** interrompe a execução para buscar a página em disco.
- **Mínimos Privilégios (Least Privilege)** é a regra de ouro para controle de acessos em diretórios.

---

