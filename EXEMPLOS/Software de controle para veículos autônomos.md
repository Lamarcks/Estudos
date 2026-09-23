**Descrição da situação-problema**

Você é analista de TI em uma empresa do setor automotivo que decidiu iniciar a fabricação de veículos autônomos, que não precisam de motoristas, pois eles possuem um sistema de controle sofisticado, capaz de conduzir o veículo com segurança. Seu papel é liderar a equipe que vai implementar o software de controle para condução automática dos veículos. Você precisa, inicialmente, escolher um modelo de arquitetura para a solução desses veículos.

**Resolução da situação-problema**

Existem muitos aplicativos de navegação para veículos baseados em soluções em nuvem. No entanto, um software de controle para condução de veículo precisa tomar decisões em tempo real. Além do uso de serviços de inteligência artificial, esse tipo de aplicação requer baixa latência de comunicação e baixo tempo de resposta no processamento de dados. Se os veículos tivessem que se comunicar com servidores na nuvem, esses requisitos poderiam não ser atendidos. O modelo mais adequado, nesse caso, seria uma abordagem de Edge Computing, como ilustrado na Figura 7. Os carros poderiam se comunicar com altas taxas de transmissão por meio de uma rede sem fio 5G e aproveitar a capacidade de processamento e armazenamento de dados das estações de transmissão de dados para executar funcionalidades em tempo real. Mesmo assim, serviços em nuvem poderiam ser utilizados para agregar informações, armazenar dados históricos para análise de estatísticas e para cálculos de rotas longas que exigem dados do trânsito em várias regiões.

![](https://content.cogna.com.br/content/dam/cogna/cms2/d3c82c1a-80e4-434c-bae7-0246f2f20ca2/b73b9374-2fcb-565f-a89a-506b51da0b1a.png)

Cenário de aplicação com veículos autônomos.