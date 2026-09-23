
**Descrição da situação-problema**

Imagine uma empresa de comércio eletrônico que vende produtos online. Durante a Black Friday, a demanda por seus produtos aumenta significativamente, resultando em picos de tráfego no site. A infraestrutura atual não é dimensionada para lidar com esses picos, e a equipe de TI está preocupada com a possibilidade de a experiência do usuário ser prejudicada devido à lentidão ou falhas no site.

**Resolução da situação-problema**

A ideia é implementar uma estratégia de elasticidade para ajustar dinamicamente os recursos com base na demanda. A infraestrutura existente não é facilmente escalável devido à falta de automação. Utilizar serviços de nuvem que oferecem recursos de elasticidade automática, por exemplo, adotar instâncias autoescaláveis em uma plataforma de nuvem como AWS, Azure ou Google Cloud. Fazer um monitoramento em tempo real: a equipe precisa estar ciente dos picos de tráfego para acionar a elasticidade e implementar ferramentas de monitoramento que rastreiem métricas como utilização de CPU, tráfego de rede e desempenho do site. Configurar alertas para acionar automaticamente o provisionamento adicional de recursos.