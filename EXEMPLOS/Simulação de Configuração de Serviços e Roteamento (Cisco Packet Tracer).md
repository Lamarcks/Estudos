**Problema:** Configurar de forma simulada em um laboratório virtual (Cisco Packet Tracer) um roteador central interconectado a um switch local, ativando serviços automatizados de entrega de endereços de rede (DHCP), transferência de arquivos (FTP), controle de rotas de vizinhança (OSPF) e controle de prioridade contra loops físicos (Spanning Tree).

**Conceito utilizado:** Comandos de configuração via **CLI (Command Line Interface)** do sistema operacional Cisco IOS, gerenciando:

- Protocolo de Roteamento de Estado de Enlace **OSPF (Open Shortest Path First)**.
- Protocolo de Camada 2 **STP (Spanning Tree Protocol)**.
- **DHCP (Dynamic Host Configuration Protocol)** para entrega de IPs lógicos.
- **FTP (File Transfer Protocol)** de camada de aplicação.

**Solução:** Passo a passo sequencial executado diretamente nas consolas CLI dos dispositivos simulados:

1. **Configuração de Interfaces e OSPF no Roteador (CLI Roteador)**:
    
    ```
    enable                                     ! Entra no modo de privilégio de execução
    configure terminal                         ! Entra no modo de configuração global
    interface gig0/0                           ! Seleciona a interface GigabitEthernet 0/0
    ip address 192.168.1.1 255.255.255.0       ! Atribui o IP e a máscara local
    exit                                       ! Sai da interface e volta ao modo global
    router ospf 1                              ! Ativa o OSPF com identificador de processo 1
    network 192.168.1.0 0.0.0.255 area 0       ! Associa a sub-rede à Área 0 (backbone OSPF)
    ```
    
    _Explicação_: O comando `network 192.168.1.0 0.0.0.255 area 0` utiliza uma máscara coringa (`0.0.0.255`) para indicar que todas as interfaces do roteador que comecem com `192.168.1.` participarão do processo de roteamento dinâmico na área 0.
    
2. **Configuração do Spanning Tree no Switch (CLI Switch)**:
    
    ```
    enable                                     ! Entra no modo de privilégio
    configure terminal                         ! Entra no modo de configuração global
    spanning-tree vlan 1 priority 4096         ! Altera a prioridade da VLAN 1 para 4096
    ```
    
    _Explicação_: O valor padrão de prioridade de um switch no STP é `32768`. Ao configurar manualmente para `4096` (um valor menor), forçamos logicamente que esse switch se torne o **Root Bridge** (ponte raiz) da topologia, evitando loops em caminhos redundantes.
    
3. **Configuração do Serviço DHCP no Roteador (Interface gráfica/Config ou CLI)**:
    
    - Habilitar a interface FastEthernet0/0 com o IP `192.168.1.1/24`.
    - Criar o pool DHCP no roteador:
        - **Pool Name**: `POOL1`
        - **Network**: `192.168.1.0`
        - **Subnet Mask**: `255.255.255.0`
        - **Default Router**: `192.168.1.1`
4. **Configuração do Serviço FTP no Roteador (Serviço de Aplicação)**:
    
    - Navegar até a aba "Services" -> "FTP".
    - Habilitar o serviço FTP (marcar "Enable").
    - Adicionar um usuário com privilégios de acesso:
        - **Username**: `admin`
        - **Password**: `secretpassword`.
5. **Teste de Conectividade e Validação**:
    
    - Conectar um PC simulado ao Switch.
    - Configurar a placa de rede do PC para o modo **DHCP**; verificar se ele recebe automaticamente um IP válido da faixa `192.168.1.0/24`.
    - Abrir o cliente FTP no PC simulado e efetuar login com sucesso no IP do roteador (`192.168.1.1`) usando o login `admin`.

**Resultado:** Uma rede local totalmente configurada, roteável de forma dinâmica (via OSPF) e com distribuição dinâmica de IPs (via DHCP) de forma segura.

**Por que essa solução funciona:** Os comandos CLI de configuração do Packet Tracer replicam de forma idêntica o sistema operacional de rede proprietário da Cisco (IOS). Isso garante que a sintaxe, os estados das interfaces de rede e a negociação lógica de protocolos ocorram exatamente como fariam em equipamentos físicos reais de data centers e redes corporativas.

**O que preciso aprender com esse exemplo:** Aprender a sintaxe básica de configuração da CLI (comandos `enable`, `configure terminal`, endereçamento de interfaces) é essencial, pois os exames de certificações de rede frequentemente cobram comandos práticos de Spanning Tree e configuração de OSPF.