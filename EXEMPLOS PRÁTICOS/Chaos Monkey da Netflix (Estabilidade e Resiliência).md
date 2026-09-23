**Problema:** Garantir a continuidade de funcionamento e alta disponibilidade de sistemas distribuídos complexos de streaming e e-commerce sob falhas aleatórias e imprevisíveis de infraestrutura em nuvem (servidores caindo ou quedas inesperadas de rede de distribuição).

**Conceito utilizado:**

- Testes de Estabilidade e Resiliência em Produção.
- Engenharia do Caos (_Chaos Engineering_).
- Tolerância a Falhas e Recuperabilidade.

**Solução:** A empresa desenvolveu e integrou ao ambiente de produção ativo do usuário uma ferramenta automatizada chamada **Chaos Monkey**. Esse script tem como função única desligar, de forma deliberada e totalmente aleatória, servidores e serviços operacionais reais contínuos no ecossistema da nuvem.

**Resultado:** A engenharia de software foi forçada a desenhar e codificar estruturas totalmente tolerantes a falhas. Sempre que um servidor cai aleatoriamente pelo Chaos Monkey, outros nós redundantes sobem instantaneamente de forma autônoma para processar a carga, sem que o usuário final perceba qualquer travamento no filme ou carregamento de páginas.

**Por que essa solução funciona:** Ao induzir falhas reais e contínuas no mundo real de forma controlada, a equipe expõe os gargalos de colapso de infraestrutura, eliminando fragilidades de comunicação e aprimorando ativamente a maturidade de arquitetura.

**O que preciso aprender com esse exemplo:** A resiliência de sistemas críticos modernos é atingida assumindo que falhas vão acontecer e simulando-as de forma ativa no ambiente de produção para certificar o restabelecimento ágil.