**Descrição da situação-problema**

Observamos nos últimos anos uma revolução na Indústria. Com capacidade computacional embarcada nos mais diversos dispositivos, máquinas e veículos, viabilizaram-se processos avançados de manufatura e logística de produção. Os equipamentos das plantas industriais têm recursos para processamento e transmissão de dados, de forma que podem interagir entre si e com sistemas em nuvem para tornar os processos produtivos mais eficientes e confiáveis.

Considere uma fábrica que opera com equipamentos muito especializados, cuja compra só pode ser feita por encomenda. Assim, se um equipamento for danificado, sua substituição pode demorar muito, o que acarreta significativo prejuízo financeiro. Por isso, essa fábrica pretende implementar uma solução com sensores e transmissores nos equipamentos, a fim de coletar dados para um sistema responsável por monitorar a planta da fábrica, prever falhas e planejar a manutenção e a reposição dos equipamentos a fim de diminuir a probabilidade de um equipamento ficar inutilizado por defeito. Avalie quais serviços em nuvem poderiam ser usados na implementação de tal solução para manutenção preventiva dos equipamentos.

**Resolução da situação-problema:**

Os provedores de nuvem pública oferecem várias soluções gerenciadas para aplicações de IoT, como é o caso de soluções para gerenciamento de instalações industriais. Nesse caso, podemos identificar duas tarefas principais: o gerenciamento da coleta de dados dos sensores e a análise desses dados para diagnóstico e tomada de decisão sobre manutenção dos equipamentos.

Uma primeira estratégia seria escolher um serviço para auxiliar cada uma das tarefas. Podemos utilizar um serviço básico de coleta e armazenamento de dados para aplicações de IoT, como o Cloud IoT Core, e utilizar um serviço de Aprendizado de Máquina, como o Azure Machine Learning para a tarefa de análise de dados.

Uma segunda estratégia poderia ser um serviço para aplicações IoT que já contempla as duas funcionalidades, como é o caso do AWS IoT SiteWise ou do Azure Time Series Insights. Ambos os serviços já incluem mecanismos para gerar estimativas e fazer previsões em função dos dados coletados ao longo do tempo, assim como ferramentas para visualização dos dados que favorecem o gerenciamento eficiente dos recursos. A Figura 2 ilustra como seria o processo utilizando o serviço AWS IoT SiteWise.

![IoT gateways coletam os dados dos equipamentos AWS IoT SiteWise Análise integrada dos dados para monitoramento do desempenho e otimização das etapas da linha de produção. Coleta de dados dos equipamentos Estruturação dos dados, definição de métricas de desempenho e mapeamento dos processos. Criação de painéis de bordo com relatórios e gráficos.](https://content.cogna.com.br/content/dam/cogna/cms2/d3c82c1a-80e4-434c-bae7-0246f2f20ca2/3b9747aa-64ec-518c-a616-ee99622bb305.png)

Exemplo de serviços para aplicação de streaming de áudio.