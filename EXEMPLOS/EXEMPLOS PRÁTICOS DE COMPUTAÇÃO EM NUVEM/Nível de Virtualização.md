**Descrição da situação-problema**

Uma empresa vai lançar um novo aplicativo para gestão de tarefas colaborativas. O objetivo é promover aumento de produtividade para pequenas empresas e profissionais liberais. O sistema inclui um serviço web e um banco de dados no qual são compartilhados os dados das tarefas. O aplicativo conecta-se no serviço web por meio de requisições HTTP para manipular os recursos do sistema. A empresa está com grande expectativa de sucesso. Para atender muitos clientes, já escolheu um grande provedor de nuvem pública para hospedar o sistema. Você foi contratado como consultor para definir a melhor estratégia de implantação do serviço web e do banco de dados nesse provedor específico que oferece apenas serviços nos modelos PaaS e IaaS. Você precisa determinar qual a melhor opção para implantação do serviço web e do banco de dados em termos do modelo de serviço e tecnologia de virtualização.

Resolução da situação-problema:

O Quadro 1 apresenta um resumo comparativo das tecnologias de virtualização. A máquina virtual é considerada um modelo de virtualização ao nível de hardware. Já o contêiner é considerado um modelo de virtualização ao nível de sistema operacional. Por isso, a imagem da máquina virtual é muito grande, comparada à do contêiner, pois a imagem da máquina virtual precisa conter seu próprio sistema operacional. Por outro lado, os contêineres compartilham o sistema operacional da máquina física no qual executam. A desvantagem é que a aplicação incluída no contêiner tem que ter sido implementada para o mesmo sistema operacional no qual o gerenciador de contêiner está executando.

|   |   |   |
|---|---|---|
||**Máquina Virtual**|**Contêineres**|
|Abordagem|Virtualização no nível de hardware|Virtualização no nível de sistema operacional|
|Denominação da ferramenta de virtualização|Hypervisor|Container Engine|
|Vantagens|- Maior nível de isolamento e segurança.<br>- Permite mais de um sistema operacional no mesmo hardware.|- Permite compartilhamento do sistema operacional.<br>- Mais “leve” (exige menos recursos e ocupa menos espaço).|

Quadro 1 | Comparação entre contêineres e máquinas virtuais.

Vamos avaliar cada componente do sistema para determinar qual dos dois modelos de virtualização é mais adequado. O banco de dados pode conter dados sobre os quais os clientes desejam privacidade, portanto a proteção e o isolamento dos dados é um critério relevante. Além disso, o banco de dados possui uma ou apenas algumas réplicas, não há necessidade de escalar para um número elevado de instâncias dos SGBD. Portanto, a melhor estratégia é implantar o banco de dados em uma máquina virtual alocada no modelo IaaS.

O outro componente do sistema é o serviço web, que podem necessitar de replicação em escala para balanceamento de carga. O serviço web se beneficia de tecnologias abertas e padronizadas disponíveis em plataformas pré-configuradas na maioria dos provedores, sem necessidade de gerenciamento de infraestrutura. Nesse caso, a opção mais adequada para implantar o serviço web seria um serviço PaaS baseado em contêiner para agilizar a replicação das instâncias.