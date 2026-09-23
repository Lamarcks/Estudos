**Problema:** Em uma topologia mista (Figura 2), existe um roteador gateway central. Conectados a ele estão:

- **Segmento Central inferior**: Uma cascata ligada apenas por hubs físicos.
- **Segmento Esquerdo**: Dois switches conectando dispositivos finais.
- **Segmento Direito**: Um switch conectando dispositivos. Como identificar corretamente a quantidade de domínios de colisão e de domínios de broadcast presentes nessa rede?

**Conceito utilizado:** Propriedades de segmentação física e lógica de dispositivos de hardware em redes Ethernet baseadas em CSMA/CD:

- **Hub**: Opera na camada 1; não possui inteligência de segmentação; replica todos os pacotes recebidos para todas as portas físicas, formando **um único domínio de colisão e um único domínio de broadcast**.
- **Switch**: Opera na camada 2; lê endereços MAC; segmenta colisões, criando **um domínio de colisão independente para cada porta física ativa**; repassa broadcast, mantendo as portas sob **um único domínio de broadcast**.
- **Bridge**: Opera na camada 2; separa dois domínios de colisão, mas mantém **um único domínio de broadcast**.
- **Roteador**: Opera na camada 3; lê endereços IP; **bloqueia e quebra domínios de broadcast** por padrão.

**Solução:** Análise da topologia com base na lógica física e de camada dos dispositivos:

1. **Cálculo dos Domínios de Broadcast**:
    - Como o roteador divide e isola as difusões lógicas por padrão, cada interface física ativa do roteador gera um domínio de broadcast isolado.
    - Existem três conexões saindo do roteador central (inferior, esquerda e direita).
    - **Resultado**: **3 domínios de broadcast**.
2. **Cálculo dos Domínios de Colisão**:
    - **Abaixo do roteador (Hubs)**: A conexão é feita apenas por hubs cascateados. Como os hubs não segmentam colisões, todo esse segmento inferior forma apenas **1 único domínio de colisão**.
    - **À esquerda do roteador (Switches)**: Os dispositivos conectam-se diretamente às portas físicas de um switch. Como cada porta de switch é isolada, há **2 domínios de colisão** distintos.
    - **À direita do roteador (Switch)**: Há uma conexão dedicada com outro switch de comutação. Isso gera **1 domínio de colisão**.
    - Somando as saídas: \(1 + 2 + 1 = 4\) domínios de colisão totais.

**Resultado:** A topologia possui **3 domínios de broadcast** e **4 domínios de colisão**.

**Por que essa solução funciona:** O roteador isola o tráfego da camada 3 e impede a propagação de pacotes destinados a `ff:ff:ff:ff:ff:ff` entre suas portas. Já o switch lê o endereço MAC do quadro e cria circuitos virtuais dedicados de comutação temporária entre a porta de origem e a de destino, garantindo que transmissões simultâneas em portas diferentes ocorram de forma paralela e sem conflito de sinais.

**O que preciso aprender com esse exemplo:** Saber contar domínios de colisão e broadcast em diagramas é uma questão clássica de provas de redes. Lembre-se: **Hub = tudo compartilhado**; **Switch = colisão segmentada por porta, broadcast unificado**; **Roteador = broadcast isolado**.