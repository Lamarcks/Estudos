**Problema 1 (Classe C - 2 sub-redes):** Como dividir a rede local `192.168.1.0` com máscara padrão Classe C `255.255.255.0` (ou `/24`) em duas sub-redes distintas.

**Problema 2 (Classe C - 4 sub-redes):** Como dividir a rede local `192.168.0.0` (ou `192.168.1.0`) com máscara padrão `255.255.255.0` em quatro sub-redes distintas, identificando a nova máscara, o número de hosts disponíveis por sub-rede, as faixas de IPs válidos, bem como os IDs de rede e de broadcast.

**Problema 3 (Classe A/B - 4 sub-redes):** Como dividir a rede Classe A privada `10.0.0.0` com máscara padrão `/16` (`255.255.0.0`) em quatro sub-redes.

**Problema 4 (Cálculo de hosts para máscara /27):** Determinar a quantidade máxima de hosts (dispositivos) válidos que podem ser configurados em uma sub-rede que utiliza o prefixo CIDR `/27`.

**Conceito utilizado:** Sub-redes (**subnets**), notação **CIDR (Classless Inter-Domain Routing)** e equações matemáticas de divisão de rede:

- Fórmula para quantidade de sub-redes: \(2^x\) (onde \(x\) é o número de bits de host tomados emprestados da máscara de rede).
- Fórmula para número de endereços de hosts por sub-rede: \(2^y\) (onde \(y\) é o número de bits de host restantes).
- Fórmula para número de hosts válidos (atribuíveis a dispositivos): \(2^y - 2\) (subtraindo os endereços reservados para identificação da rede e de broadcast).

**Solução:**

- **Solução para o Problema 1 (Classe C - 2 sub-redes):**
    
    1. Para obter duas sub-redes, aplicamos \(2^x = 2^1 = 2\). Portanto, precisamos de **1 bit emprestado** do último octeto.
    2. A máscara original `/24` recebe mais 1 bit, tornando-se `/25`.
    3. A representação binária da nova máscara é `11111111.11111111.11111111.10000000`, o que equivale a `255.255.255.128` em decimal.
    4. As duas sub-redes resultantes são: `192.168.1.0/25` e `192.168.1.128/25`.
- **Solução para o Problema 2 (Classe C - 4 sub-redes):**
    
    1. **Conversão da máscara de rede original para binário**: `255.255.255.0` \(\rightarrow\) `11111111.11111111.11111111.00000000`.
    2. **Cálculo dos bits emprestados**: Para criar 4 sub-redes, precisamos de \(2^x = 4 \rightarrow x = 2\) bits emprestados.
    3. **Cálculo de hosts**: Com 2 bits emprestados do último octeto, sobram \(8 - 2 = 6\) bits de host. Cada sub-rede terá \(2^6 = 64\) endereços totais (IDs de rede e broadcast inclusos) e \(2^6 - 2 = 62\) IPs válidos para hosts.
    4. **Nova máscara de rede**: Somamos os valores posicionais dos dois bits ativados no último octeto: \(128 + 64 = 192\). A nova máscara decimal é `255.255.255.192` (ou `/26` em notação CIDR, pois há 26 bits ativados como '1').
    5. **Tabela de Divisão de IPs (Quadro 3)**:
        - **Sub-rede 1**: ID da rede: `192.168.0.0` (ou `.1.0`) | IPs válidos: `192.168.0.1` a `.62` | Broadcast: `192.168.0.63`.
        - **Sub-rede 2**: ID da rede: `192.168.0.64` (ou `.1.64`) | IPs válidos: `192.168.0.65` a `.126` | Broadcast: `192.168.0.127`.
        - **Sub-rede 3**: ID da rede: `192.168.0.128` (ou `.1.128`) | IPs válidos: `192.168.0.129` a `.190` | Broadcast: `192.168.0.191`.
        - **Sub-rede 4**: ID da rede: `192.168.0.192` (ou `.1.192`) | IPs válidos: `192.168.0.193` a `.254` | Broadcast: `192.168.0.255`.
- **Solução para o Problema 3 (Classe A/B - 4 sub-redes):**
    
    1. A máscara de sub-rede original é `255.255.0.0` (`/16`).
    2. Para obter 4 sub-redes, tomamos **2 bits emprestados** do terceiro octeto (\(2^2 = 4\)).
    3. Os dois primeiros bits do terceiro octeto são ativados: \(128 + 64 = 192\). A nova máscara resultante é `255.255.192.0` (ou `/18` em notação CIDR).
    4. As quatro sub-redes resultantes são: `10.0.0.0/18`, `10.0.64.0/18`, `10.0.128.0/18` e `10.0.192.0/18`.
- **Solução para o Problema 4 (Cálculo de hosts para máscara /27):**
    
    1. Uma máscara `/27` reserva 27 bits para a rede e deixa \(32 - 27 = 5\) bits para identificar hosts.
    2. Aplicamos a fórmula \(2^n - 2\), onde \(n = 5\): \[2^5 - 2 = 32 - 2 = 30\]
    3. A sub-rede pode conter até **30 hosts válidos** configurados em dispositivos.

**Resultado:** Redes locais divididas e estruturadas em segmentos menores, o que limita o tráfego local, melhora a segurança e otimiza a alocação de endereços IP sem desperdícios.

**Por que essa solução funciona:** A máscara de rede funciona comparando bits ativados (`1` para rede, `0` para hosts). Ao "pegar emprestado" bits da porção do host, o roteador consegue identificar logicamente subgrupos isolados dentro de um mesmo bloco de IP. O primeiro endereço (com todos os bits de host zerados) identifica a sub-rede em si, enquanto o último endereço (com todos os bits de host iguais a um) é reservado para enviar mensagens de broadcast simultaneamente a todas as máquinas desse segmento, não podendo ser usados por hosts comuns.

**O que preciso aprender com esse exemplo:** A divisão de sub-redes é essencial para segmentar domínios de broadcast locais. Lembre-se sempre de **subtrair 2** da quantidade de endereços totais para achar os IPs de hosts válidos e de calcular o intervalo com base nas potências de 2 correspondentes aos bits emprestados.