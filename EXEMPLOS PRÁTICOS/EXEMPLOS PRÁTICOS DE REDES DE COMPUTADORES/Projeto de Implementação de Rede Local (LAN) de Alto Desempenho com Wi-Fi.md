**Problema:** Conceber teoricamente e implementar uma rede local (LAN) de alto desempenho capaz de conectar de forma segura três computadores (dois notebooks e um computador desktop), permitindo alta taxa de transferência interna de arquivos locais e mobilidade física para os funcionários.

**Conceito utilizado:** Infraestrutura física de rede e comutação Ethernet Gigabit:

- Cabos de rede **CAT6 ou superior** para as conexões cabeadas.
- Dispositivos com placas de rede Gigabit Ethernet (taxas de transferência de 1000 Mbps).
- Roteador sem fio Wi-Fi padrão de alto desempenho.
- Switch dedicado Gigabit Ethernet para a comutação de alta velocidade da rede com fio.

**Solução:** Arquitetura teórica de conexão de hardware passo a passo:

1. **Levantamento de Ativos e Cabos**: Adquirir dois notebooks com Wi-Fi, um desktop com placa de rede integrada Gigabit Ethernet, um switch Gigabit Ethernet de 5 a 8 portas, cabos de rede CAT6 conectorizados e um roteador Wi-Fi homologado.
2. **Conexões Físicas com Fio**: Conectar o computador desktop e o roteador Wi-Fi diretamente às portas físicas do switch Gigabit Ethernet utilizando os cabos de rede CAT6 de alta performance.
3. **Configuração e Conexão Sem Fio**:
    - Ligar e alimentar o roteador Wi-Fi.
    - Configurar uma rede local segura (SSID exclusiva) utilizando protocolo forte de segurança sem fio (WPA2/WPA3 com senha complexa).
    - Configurar os notebooks locais para acessarem a rede local localizando o SSID configurado.
4. **Atribuição Lógica de IPs**: Configurar o roteador para operar como servidor DHCP local, entregando IPs automáticos na mesma faixa lógica para todos os dispositivos de rede conectados (com fio e Wi-Fi).
5. **Teste de Performance de Vazão (Throughput)**: Transferir um arquivo de tamanho massivo (ex.: 1 GB) do notebook sem fio para o computador desktop cabeado e cronometrar as velocidades reais alcançadas.

**Resultado:** Dispositivos conectados localmente de forma estável. As conexões cabeadas alcançam taxas nominais de 1000 Mbps (1 Gbps) com latências insignificantes, enquanto os notebooks usufruem de mobilidade contínua e segura nas dependências do escritório.

**Por que essa solução funciona:** Cabos de categoria CAT6 possuem um isolamento físico interno aprimorado, permitindo transferências de alta capacidade a 1 Gbps sem sofrer atenuação de ruído ou diafonia em frequências elevadas. O switch Gigabit gerencia o tráfego em sua camada de enlace, direcionando de forma isolada os quadros ponto a ponto entre as placas de rede ativas (NICs) dos computadores envolvidos na troca de arquivos.

**O que preciso aprender com esse exemplo:** A velocidade final de uma transferência é sempre ditada pelo "gargalo", ou seja, o link mais lento de toda a rota de dados. A transferência cabo-cabo (desktop-switch) será mais rápida e estável que a conexão sem fio (notebook-roteador), a qual pode sofrer atenuação física por paredes ou interferência eletromagnética de outras fontes de rádio.