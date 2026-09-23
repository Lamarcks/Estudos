[[EXEMPLOS-PRÁTICOS DE REDES DE COMPUTADORES]]
#ASSUNTO
## Visão geral

As **redes de computadores** consistem em sistemas de dispositivos de computação e comunicação interconectados que trocam dados e compartilham recursos de forma organizada por meio de normas chamadas **protocolos**. A infraestrutura de comunicação global da internet é sustentada por provedores de acesso (**ISPs**) e vias expressas de tráfego de alta capacidade denominadas **backbones**. O entendimento dessas estruturas exige o domínio de conceitos que vão do meio físico de transmissão (como cabos e sinais) até modelos de referência arquitetônicos (OSI e TCP/IP) e gerência avançada de tráfego, falhas e segurança.

---

## Conceitos principais

- **Protocolo de Comunicação**: Conjunto de regras formais que controlam e organizam a transmissão e a recepção segura de informações em uma rede.
- **Endereço IP**: Identificador lógico de 32 bits (IPv4) ou 128 bits (IPv6) que permite a localização e comunicação universal de dispositivos na rede.
- **Endereço MAC**: Endereço físico exclusivo gravado na placa de rede (NIC) de cada dispositivo, operando na camada de enlace para identificação local.
- **Encapsulamento**: Processo no qual os dados de uma camada superior são "embrulhados" com cabeçalhos de controle ao descerem pela pilha de protocolos (e desencapsulados ao subirem no destino).
- **Domínio de Colisão**: Área de rede onde pacotes transmitidos simultaneamente por múltiplos dispositivos podem colidir e corromper-se.
- **Domínio de Broadcast**: Segmento de rede no qual uma mensagem de difusão geral (enviada para todos) é recebida por todos os hosts conectados.

---

## Conteúdo explicado

### 1. Sinais e Meios de Transmissão (Camada Física)

Para que os dados viajem pela rede, eles precisam ser convertidos em sinais que se propagam por meios guiados ou não guiados:

#### Tipos de Sinais

- **Sinal Analógico**: Onda eletromagnética contínua definida por **amplitude** (voltagem/intensidade), **frequência** (ciclos por segundo em Hertz) e **fase** (graus ou radianos de deslocamento). É incomum em redes modernas devido à alta suscetibilidade a ruídos e limitações de velocidade.
- **Sinal Digital**: Representação discreta em formato binário de bits (estados `0` ou `1`). É altamente imune a ruídos, resiste a interferências e permite transmitir volumes massivos de informações.

#### Meios de Transmissão Guiados (Cabeados)

- **Cabo de Par Trançado**: Fios de cobre trançados helicoidalmente para cancelar campos eletromagnéticos e reduzir interferências. Dividido em categorias (**CAT 5, 5e, 6 e 7**) conforme a largura de banda e blindagem.
- **Cabo Coaxial**: Núcleo de cobre envolto por isolante, malha condutora e capa protetora. Utilizado historicamente em TV a cabo e redes de banda larga. Suas variantes incluem o **10Base2** (segmentos de até 185m a 10 Mbps) e o **10Base5** (até 500m de alcance).
- **Fibra Óptica**: Filamentos de vidro ou plástico que transmitem dados na forma de pulsos de luz. Oferece largura de banda colossal (taxas de até 10 Tbps), alcança longas distâncias e é totalmente imune a interferências eletromagnéticas.

#### Meios de Transmissão Não Guiados (Sem Fio)

Utilizam faixas de frequência do espectro eletromagnético:

- **Rádio e Wi-Fi (IEEE 802.11)**: Ondas de rádio omnidirecionais reguladas em frequências específicas (como 2,4 GHz e 5 GHz). Sofrem atenuação por obstáculos físicos.
- **Micro-ondas**: Ondas que viajam em linha reta, exigindo visada direta perfeita entre as antenas receptoras e transmissoras.
- **Satélites**: Comunicações de longa distância via satélites geoestacionários ou órbitas baixas/médias (**LEO, MEO e HEO**).
- **Outras tecnologias**: **Bluetooth** (curto alcance), **NFC** (troca de dados a centímetros), **Zigbee** (automação residencial) e **Redes Mesh** (dispositivos auto-organizados de forma descentralizada).

#### Modos de Operação do Canal

- **Simplex**: Comunicação em sentido único (unidirecional), como rádio ou TV.
- **Half-Duplex**: Comunicação bidirecional, mas alternada (apenas um transmite por vez), como walkie-talkies.
- **Full-Duplex**: Comunicação simultânea e bidirecional nas duas direções, padrão nas redes Ethernet modernas.

---

### 2. Dispositivos de Rede (Hardware) e Topologias

#### Equipamentos Básicos

- **Placa de Rede (NIC)**: Dispositivo de E/S instalado na máquina para enviar/receber dados, tratando o endereçamento físico.
- **Modem**: Modulador/demodulador que traduz sinais digitais do computador em sinais compatíveis com o meio físico da operadora (e vice-versa).
- **Hub**: Dispositivo de camada física (repetidor). Ele não lê endereços; apenas replica fisicamente qualquer sinal recebido para todas as suas portas, gerando um único domínio de colisão e alta lentidão pelo desperdício de banda.
- **Switch**: Opera na camada de enlace (camada 2). Ele analisa o cabeçalho e encaminha o quadro exclusivamente para a porta onde o dispositivo de destino (identificado pelo endereço MAC) está conectado. **Cada porta do switch forma seu próprio domínio de colisão**.
- **Bridge**: Dispositivo que interliga duas redes locais (LANs), segmentando domínios de colisão.
- **Roteador**: Equipamento inteligente de camada 3 que interconecta redes distintas e escolhe a melhor rota de tráfego usando tabelas de roteamento e endereçamento lógico IP. **Roteadores quebram domínios de broadcast**.
- **Gateway**: Dispositivo ou software que atua na borda da rede para traduzir protocolos e regras incompatíveis entre redes distintas.

#### Topologias Físicas e Geométricas

- **Malha (Mesh)**: Conexões ponto a ponto dedicadas e redundantes entre todos os dispositivos. Altíssima confiabilidade e tolerância a falhas, mas com alto custo de cabos e portas.
- **Estrela (Star)**: Dispositivos ligados individualmente a um concentrador central (switch ou roteador). Fácil de gerenciar e expandir, mas possui falha de ponto único (se o nó central falhar, toda a rede cai).
- **Barramento (Bus)**: Dispositivos conectados linearmente a um único cabo central compartilhado (backbone). Baixo custo, mas alta taxa de colisões e limitação física.
- **Anel (Ring)**: Cada dispositivo se conecta de forma circular aos seus dois vizinhos mais próximos. Os dados fluem em sentido único, com desempenho previsível (Token Ring), porém a falha de um único dispositivo interrompe todo o anel.
- **Híbrida**: Combinação de duas ou mais topologias para atender a necessidades específicas (ex.: estrelas conectadas a um barramento central).

---

### 3. Modelos de Referência (ISO/OSI vs. TCP/IP)

A padronização foi criada pela ISO e outras entidades (IEEE, ITU-T, ANSI) para garantir que dispositivos de diferentes fabricantes pudessem se comunicar.

```
       MODELO OSI (7 Camadas)              ARQUITETURA TCP/IP (4 Camadas)
    +---------------------------+          +---------------------------+
  7 | Aplicação (HTTP, SMTP...) | -------\ |                           |
    +---------------------------+         \|                           |
  6 | Apresentação (Cripto...)  | -------- | Aplicação                 |
    +---------------------------+         /| (HTTP, DNS, SSH, SMTP...) |
  5 | Sessão (Controle conexões)| -------/ |                           |
    +---------------------------+          +---------------------------+
  4 | Transporte (TCP, UDP)     | -------- | Transporte (Host-to-host) |
    +---------------------------+          +---------------------------+
  3 | Rede (Protocolo IP)       | -------- | Internet                  |
    +---------------------------+          +---------------------------+
  2 | Enlace (MAC, Switches)    | -------\ |                           |
    +---------------------------+         \| Acesso à Rede             |
  1 | Física (Cabos, Hubs, Bits)| -------- | (Ethernet, Wi-Fi...)      |
    +---------------------------+          +---------------------------+
```

**

#### Funções das Camadas e seus Protocolos

1. **Acesso à Rede / Enlace e Física**:
    - **Função**: Transmite bits brutos no meio físico (camada 1) e agrupa esses bits em **quadros** (frames) na camada 2 para entrega confiável entre nós vizinhos, usando detecção de erros via CRC.
    - **Protocolos**: Ethernet (802.3), Wi-Fi (802.11), PPP (conexões diretas ponto a ponto), HDLC e Frame Relay.
2. **Internet / Rede**:
    - **Função**: Cuida do endereçamento lógico e determina a rota que os **pacotes** (datagramas) devem seguir da origem ao destino.
    - **Protocolos**:
        - **IP (Internet Protocol)**: Protocolo de entrega de melhor esforço (não confiável e sem conexão).
        - **ICMP**: Mensagens de diagnóstico de erros e testes de conectividade (Buffer Full, TTL Exceeded, comandos _ping_ e _traceroute_).
        - **ARP / RARP**: Traduzem endereço IP em endereço MAC físico (e vice-versa).
        - **IGMP**: Gerenciamento de grupos multicast.
        - **Protocolos de Roteamento**: **OSPF** (estado de enlace, veloz e escalável), **BGP** (vetor de caminho, usado para interconectar sistemas autônomos na internet global) e **RIP** (vetor de distância, limitado a saltos, para redes pequenas).
3. **Transporte**:
    - **Função**: Fornece transporte seguro e integridade de dados de ponta a ponta através da segmentação.
    - **Protocolos**:
        - **TCP**: Serviço elástico, orientado à conexão, altamente confiável (retransmite pacotes perdidos).
        - **UDP**: Serviço sem conexão, sem confirmação (rápido, leve, ideal para streaming/tempo real).
4. **Aplicação / Sessão e Apresentação**:
    - **Função**: Sessão gerencia o diálogo e conexão entre hosts; Apresentação formata e criptografa os dados; Aplicação fornece a interface para os softwares de usuário.
    - **Protocolos**: HTTP, HTTPS (criptografado com TLS/SSL), SMTP (envio de e-mail), POP3/IMAP (recuperação de e-mails do servidor), SSH (acesso remoto criptografado), FTP/FTPS (transferência de arquivos), NTP (sincronização precisa de relógios) e DNS (tradução de nomes de domínio em IPs).

---

### 4. Endereçamento IPv4 e IPv6

#### Endereçamento IPv4

Possui **32 bits** representados por 4 octetos decimais de 0 a 255 (ex.: `192.168.1.1`).

- **Classes de Endereços Históricas (Classful)**:
    - **Classe A**: Começa com bit `0` (intervalo de `0.0.0.0` a `127.255.255.255`). Primeiro octeto identifica a rede (8 bits NET, 24 bits HOST). Suporta redes gigantescas.
    - **Classe B**: Começa com bits `10` (`128.0.0.0` a `191.255.255.255`). Dois octetos de rede, dois de host (16 bits NET, 16 bits HOST).
    - **Classe C**: Começa com bits `110` (`192.0.0.0` a `223.255.255.255`). Três octetos de rede, um de host (24 bits NET, 8 bits HOST).
    - **Classe D**: Reservada para grupos de transmissão multicast (`224.0.0.0` a `239.255.255.255`).
    - **Classe E**: Reservada para fins de pesquisa experimental.
- **CIDR (Classless Inter-Domain Routing)**: Substitui o rígido sistema de classes por alocações flexíveis usando a notação com barra (ex.: `/24`), especificando exatamente quantos bits pertencem à rede.
- **IPs Privados (Não Roteáveis na Internet)**: Reservados para uso interno local compartilhados globalmente via **NAT**:
    - `10.0.0.0/8`
    - `172.16.0.0/12`
    - `192.168.0.0/16`
- **IPs Especiais**: `127.0.0.1` (loopback para autoteste de rede local) e `169.254.0.0/16` (configuração automática APIFA quando o DHCP falha).

#### Matemática do Cálculo de Sub-redes

Para dividir um bloco de IP em sub-redes menores, pegamos bits emprestados da parte de host da máscara de rede.

##### Fórmulas Essenciais:

- \(\text{Quantidade de Sub-redes} = 2^x\), onde \(x\) é o número de bits tomados emprestados da máscara original.
- \(\text{Quantidade de Endereços por Sub-rede} = 2^y\), onde \(y\) é o número de bits que restaram para os hosts.
- \(\text{Endereços de Host Válidos} = 2^y - 2\) (subtrai-se o primeiro endereço, que identifica a **rede**, e o último, que é o endereço de **broadcast**).

##### Exemplo Prático: Dividir a Rede `192.168.0.0/24` em 4 sub-redes:

1. **Máscara Original**: `255.255.255.0` (em binário: `11111111.11111111.11111111.00000000`).
2. **Tomar Bits Emprestados**: Para criar 4 sub-redes, precisamos de \(2^2 = 4\), portanto, pegamos **2 bits emprestados** do último octeto.
3. **Nova Máscara**: Ativamos os dois primeiros bits do último octeto (`128 + 64 = 192`) \(\rightarrow\) `255.255.255.192` (em notação CIDR: `/26`).
4. **IPs Restantes de Host**: Restaram 6 bits (\(8 - 2 = 6\)). Cada sub-rede terá \(2^6 = 64\) endereços totais (\(2^6 - 2 = 62\) IPs válidos para os dispositivos).
5. **Tabela de Divisão de IPs**:
    - **Sub-rede 1**: ID da rede: `192.168.0.0` | IPs válidos: `192.168.0.1` a `.62` | Broadcast: `192.168.0.63`.
    - **Sub-rede 2**: ID da rede: `192.168.0.64` | IPs válidos: `192.168.0.65` a `.126` | Broadcast: `192.168.0.127`.
    - **Sub-rede 3**: ID da rede: `192.168.0.128` | IPs válidos: `192.168.0.129` a `.190` | Broadcast: `192.168.0.191`.
    - **Sub-rede 4**: ID da rede: `192.168.0.192` | IPs válidos: `192.168.0.193` a `.254` | Broadcast: `192.168.0.255`.

#### Protocolos de Suporte ao Endereçamento

- **DHCP**: Automatiza a entrega dinâmica de IPs locais por meio de 4 etapas sequenciais: **Discovery (Descoberta), Offer (Oferta), Request (Solicitação) e Confirmation (Confirmação)**.
- **NAT**: Permite que milhares de dispositivos de uma LAN local (com IPs privados) usem e compartilhem um único IP público roteável para acessar a internet, substituindo os cabeçalhos dos pacotes e gerenciando uma tabela de tradução de portas.

#### O Protocolo IPv6

Desenvolvido para sanar o esgotamento total de endereços IPv4, oferecendo um espaço de \(2^{128}\) endereços possíveis.

- **Formato**: 8 grupos de 4 dígitos hexadecimais separados por dois pontos (ex.: `2001:0db8:85a3:0000:0000:8a2e:0370:7334`).
- **Regra de Abreviatura**: Zeros à esquerda de um grupo podem ser omitidos; e uma única sequência contínua de blocos com valor zero pode ser reduzida a `::` (ex.: `2001:db8:85a3::8a2e:370:7334`).
- **Tipos de Endereço**:
    - **Unicast**: Comunicação direta de um para um (inclui o global público, o link-local para rede local física e o local exclusivo interno).
    - **Multicast**: Envio eficiente para um grupo específico de dispositivos.
    - **Anycast**: Pacote entregue ao nó mais próximo geograficamente de um grupo de serviços idênticos.
    - **Loopback**: Representado de forma simples por `::1`.
- **Melhorias Estruturais**: Cabeçalho fixo e simplificado de apenas 8 campos (contra 14 do IPv4), segurança IPsec obrigatória integrada de forma nativa e fim da necessidade obrigatória de NAT.

#### Coexistência de Protocolos (Transição de Redes)

Como é inviável desligar o IPv4 de uma só vez, os provedores utilizam técnicas de migração:

1. **Dual Stack (Pilha Dupla)**: Equipamentos e roteadores rodam nativamente de forma paralela as pilhas IPv4 e IPv6.
2. **Tunelamento**: Encapsula pacotes IPv6 dentro de pacotes IPv4 (ou vice-versa) para cruzar redes legadas (métodos: 6in4, Teredo, 6to4).
3. **NAT64**: Traduz requisições de nós IPv6 puros diretamente para servidores IPv4.
4. **DS-Lite (Dual-Stack Lite)**: Permite que provedores operem sua rede interna em IPv6 puro, transportando dados IPv4 de clientes por túneis.

---

### 5. Gerência de Redes, Desempenho e Segurança

#### As 5 Áreas de Gerenciamento da ISO (FCAPS)

- **Performance (Desempenho)**: Monitora largura de banda, latência e gargalos de hardware.
- **Fault (Falhas)**: Registra logs e alarmes, isolando problemas transitórios ou físicos de conectividade.
- **Configuration (Configuração)**: Planeja IPs, mapeia ativos de hardware instalados e armazena versões lógicas de rede.
- **Accounting (Contabilização)**: Define cotas de utilização, limites de consumo de recursos e balanço de carga.
- **Security (Segurança)**: Controla o acesso de usuários a ativos via chaves, criptografia e políticas corporativas.

#### Arquitetura de Redes SNMP

O Simple Network Management Protocol opera na camada de aplicação para coletar relatórios de performance e incidentes em servidores e equipamentos.

- **Componentes básicos**:
    1. **Gerente (Manager)**: Software central de controle e monitoramento operado pelo administrador.
    2. **Agentes (Agents)**: Processos em execução individual nos switches, roteadores e servidores monitorados.
    3. **MIB (Management Information Base)**: Banco de dados estruturado nos agentes que armazena variáveis lógicas sobre o estado físico do hardware.
    4. **SMI (Structure of Management Information)**: Define as regras de sintaxe e formatos de objetos gerenciados na MIB.

#### Métricas de Desempenho e Qualidade de Serviço (QoS)

- **Latência (Atraso)**: Tempo total gasto para enviar um pacote e receber a resposta. \[\text{Latência} = \text{Atraso de Transmissão} + \text{Atraso de Propagação}\]
    - _Atraso de Transmissão_: \(\text{Tamanho do pacote (bits)} / \text{Velocidade da interface (bps)}\).
    - _Atraso de Propagação_: \(\text{Comprimento físico do cabo (km)} / \text{Velocidade da luz no meio (km/s)}\).
- **Jitter**: Variação estatística de latência no recebimento de pacotes seguidos. Alto jitter destrói a qualidade de áudio e vídeo em tempo real (VoIP e streaming).
- **Throughput (Vazão Real)**: Taxa de dados útil efetivamente transmitida em um intervalo de tempo. É geralmente inferior à largura de banda nominal da interface devido a overheads e perdas.
- **QoS**: Conjunto de regras para priorizar tráfego crítico sensível ao tempo (ex.: marcar pacotes de voz acima de download de arquivos).

#### Protocolo VTP (VLAN Trunk Protocol)

- Protocolo proprietário da Cisco operando na camada 2 para propagar de forma automatizada alterações em VLANs (Virtual LANs) entre múltiplos switches interconectados, evitando desconfiguração humana.
- **Modos de Operação do VTP**:
    1. **Server**: Único modo que permite criar, modificar ou excluir VLANs lógicas. Ele propaga as alterações para a rede.
    2. **Client**: Apenas escuta e replica localmente em sua tabela as informações geradas pelo Server. Não permite alterações locais.
    3. **Transparent**: Repassa os quadros do VTP para outros switches vizinhos através de suas portas de tronco, mas ignora as alterações, não modificando sua própria tabela interna.

#### Falhas de Segurança e Métodos de Ataque

- **Sniffing (Interceptação)**: Prática de capturar tráfego de rede bruta. Pode ocorrer na camada 2 colocando a NIC em modo promíscuo, ou na camada 3 para coletar pacotes IP.
- **ARP Spoofing**: Invasão na qual o atacante envia falsas mensagens ARP associando seu endereço físico MAC ao IP do roteador gateway. Todo o tráfego da vítima é redirecionado de forma silenciosa para o invasor antes de ir ao destino.

---

## Conceitos que não posso confundir

|Termo A|Termo B|Diferença Crucial|
|:--|:--|:--|
|**Hub**|**Switch**|O Hub trabalha na camada 1, não possui inteligência e repete sinais de forma broadcast para todas as suas portas físicas. O Switch opera na camada 2, lê endereços MAC físicos do cabeçalho e encaminha de forma segmentada ponto a ponto.|
|**Switch**|**Roteador**|O Switch faz comutação interna local baseada em endereços físicos MAC na camada 2. O Roteador faz comunicação e interconexão de redes externas com base em IPs lógicos na camada 3.|
|**Erros**|**Falhas**|Erro refere-se a defeitos na transmissão física ou estados corrompidos de bits. Falha é o mau funcionamento ou resposta incorreta do sistema físico ou lógico frente ao que foi projetado.|
|**IPFIX**|**NetFlow**|NetFlow é uma tecnologia proprietária desenvolvida pela Cisco para análise e auditoria de estatísticas de fluxos IP. IPFIX é o padrão aberto internacional e flexível baseado no NetFlowv9 criado pela IETF para garantir interoperabilidade de fabricantes.|
|**TCP**|**UDP**|O TCP garante entrega confiável de dados, reordena pacotes, corrige erros e é lento (orientado à conexão). O UDP é sem conexão, não envia confirmações, descarta pacotes corrompidos e prioriza velocidade acima de tudo.|
|**OSI**|**TCP/IP**|O modelo OSI é um modelo conceitual e teórico rigoroso composto por 7 camadas. O TCP/IP é a arquitetura de implementação real de 4 camadas amplamente adotada de forma prática na Internet.|

---

## Pontos importantes para prova

- **CSMA/CD (Acesso Múltiplo com Detecção de Colisão)**: Protocolo que controla transmissões em cabos compartilhados. Passos: **Escutar o meio (Carrier Sense); se livre, iniciar transmissão; se colisão ocorrer, interromper a transmissão física imediatamente e enviar sinal de reforço de colisão (Jamming); aguardar tempo aleatório (Backoff) e retransmitir**.
- **Campos Fixos do Cabeçalho IPv6**: Versão (4 bits), Classe de Tráfego (8 bits), Identificação de Fluxo (20 bits), Tamanho dos Dados (16 bits), Próximo Cabeçalho (8 bits), Limite de Saltos (8 bits), Endereço de Origem (128 bits) e Endereço de Destino (128 bits). _Importante: Não há checksum no cabeçalho IPv6._.
- **Fórmulas Estatísticas de Falha de Equipamentos**: \[\text{MTBF} = \frac{\sum(\text{Tempo em funcionamento} - \text{Início})}{\text{Número de falhas}}\] \[\text{MTTR} = \frac{\text{Tempo total inativo parado por falhas}}{\text{Número de falhas}}\]
- **Mapeamento de Interfaces TMN**: Interface **Q** conecta blocos de gerência (OSF, WSF, MF, QAF); Interface **F** conecta as estações de trabalho; Interface **X** interconecta redes TMN de diferentes organizações; Interface **M** gerencia e monitora dispositivos não TMN.
- **Criptografia Simétrica vs. Assimétrica**: A simétrica utiliza a mesma chave matemática para cifrar e decifrar os dados. A assimétrica utiliza um par de chaves relacionadas matematicamente: uma chave pública (divulgada a todos) e uma chave privada (mantida em segredo absoluto pelo dono).
- **Etapas do Handshake DHCP**: Envolve a sequência de mensagens locais de broadcast: **Discover** (Cliente procura servidor) \(\rightarrow\) **Offer** (Servidor oferece configurações de IP) \(\rightarrow\) **Request** (Cliente solicita a alocação oficial do IP oferecido) \(\rightarrow\) **Acknowledge (ACK)** (Servidor confirma a reserva e entrega parâmetros DNS e Gateway).

---

## Revisão rápida

1. **Diferença Física**: Par trançado usa sinais elétricos discretos; Fibra óptica usa pulsos rápidos de luz.
2. **Switches**: Reduzem colisões segmentando cada porta em domínios de colisão independentes; mantêm broadcast unificado.
3. **Fórmula da Máscara**: Bits `1` representam a parte de rede, e bits `0` indicam hosts.
4. **IP Público vs. Privado**: IPs privados circulam apenas localmente em LANs; IPs públicos roteiam dados globalmente na internet.
5. **Cálculo IP Válido**: \(2^{\text{bits de host}} - 2\). Exclui rede (zeros) e broadcast (uns).
6. **IPv6**: 128 bits de endereçamento estruturados em hexadecimal.
7. **Handshake de Transporte**: TCP é focado em confiabilidade e controle de fluxo; UDP prioriza velocidade de transmissão em tempo real.
8. **QoS**: Gerencia a entrega de pacotes sensíveis à latência, minimizando o jitter.
9. **FCAPS**: Desempenho, Falhas, Configuração, Contabilização e Segurança.
10. **Ataque de Camada 2**: ARP Spoofing manipula a tabela física local direcionando o tráfego para um invasor.

---
