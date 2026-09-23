[[EXEMPLOS-PRÁTICOS DE COMPUTAÇÃO EM NUVEM]]
#ASSUNTO

## Visão geral

A **Computação em Nuvem (Cloud Computing)** é um modelo de fornecimento de recursos de Tecnologia da Informação (TI) — como processamento, armazenamento, redes e software — como serviços entregues sob demanda pela Internet, baseando-se no modelo de pagamento baseado no uso real. O paradigma baseia-se fortemente na **virtualização** para abstrair a complexidade da infraestrutura física, compartilhar recursos de hardware entre múltiplos clientes e viabilizar a **elasticidade rápida**. Com isso, as empresas podem migrar seus sistemas locais para ambientes de nuvem pública, privada ou híbrida, convertendo custos iniciais de capital (CapEx) em despesas operacionais periódicas (OpEx), otimizando a relação entre desempenho, escalabilidade e custo.

---

## Conceitos principais

- **Computação em Nuvem (Definição NIST):** Modelo que permite o acesso remoto, ubíquo, conveniente e sob demanda a um pool compartilhado de recursos computacionais configuráveis (redes, servidores, armazenamento, aplicações e serviços) que podem ser rapidamente alocados e liberados com mínimo esforço gerencial ou interação direta com o provedor.
- **Virtualização:** Tecnologia de abstração de hardware que permite criar múltiplas instâncias lógicas e isoladas (Máquinas Virtuais) compartilhando o mesmo recurso de hardware físico subjacente, coordenada por uma ferramenta de controle denominada _Hypervisor_.
- **Containerização:** Modelo de virtualização ao nível do sistema operacional. Diferente das VMs, os contêineres não emulam um sistema operacional completo; eles encapsulam apenas a aplicação e suas dependências diretas, compartilhando o kernel do sistema operacional do servidor hospedeiro através de um _Container Engine_.
- **Elasticidade Rápida:** Capacidade de um sistema de expandir ou contrair de forma dinâmica, em tempo real e de forma automatizada, a alocação de recursos computacionais para responder de maneira precisa às variações de carga de trabalho.
- **Acordo de Nível de Serviço (SLA):** Instrumento contratual e técnico no qual o provedor de nuvem especifica as garantias de qualidade de serviço (QoS), confiabilidade, disponibilidade e desempenho oferecidas ao cliente, sendo monitoradas continuamente por mecanismos automáticos.

---

## Conteúdo explicado

### Módulo 1: Fundamentos da Computação em Nuvem e o Modelo NIST

A computação em nuvem consolidou-se como uma evolução direta da **Utility Computing (Computação de Utilidade)**, aproximando a TI do modelo de serviços básicos de consumo (como eletricidade ou água), em que o usuário consome o serviço de forma transparente e paga apenas pelo que utiliza, sem investimentos iniciais pesados em infraestrutura física.

O órgão regulador norte-americano NIST (National Institute of Standards and Technology) classifica a computação em nuvem através de um padrão estrutural composto por **cinco características essenciais**, **três modelos de serviço** e **quatro modelos de implantação**.

#### As 5 Características Essenciais da Nuvem (Modelo NIST):

1. **Self-service sob demanda (Autoatendimento):** O usuário adquire, configura e gerencia unilateralmente os recursos computacionais de forma automatizada e sem necessitar de interação humana da equipe do provedor.
2. **Amplo acesso à rede (Broad Network Access):** Os recursos e serviços estão permanentemente disponíveis por meio da rede (Internet) e podem ser acessados a partir de mecanismos e protocolos padronizados, suportando múltiplos dispositivos e sistemas operacionais (dispositivos móveis, thin clients, computadores locais).
3. **Pooling de recursos (Agrupamento de recursos):** Os recursos físicos e virtuais do provedor de nuvem são reunidos em uma infraestrutura compartilhada para atender a múltiplos clientes de maneira transparente (modelo _multi-tenant_ ou multi-inquilino). Os recursos são alocados e ajustados dinamicamente com base na demanda, sem que o cliente precise saber a localização física precisa do hardware.
4. **Elasticidade rápida:** Os recursos computacionais podem ser alocados ou liberados rapidamente, inclusive de forma automática (via scripts ou monitoramento de métricas), ajustando-se à variação de tráfego. Para o usuário, cria-se a "ilusão" de que a capacidade do provedor é ilimitada.
5. **Serviço medido (Mensurabilidade):** O consumo dos recursos computacionais (processamento, memória, volume de dados transferidos, contas ativas) é monitorado, auditado e contabilizado detalhadamente, garantindo transparência na tarifação.

---

### Módulo 2: Tecnologias de Suporte — Virtualização e Containerização

Para viabilizar a agilidade e a eficiência necessárias, os datacenters de nuvem utilizam duas abordagens tecnológicas fundamentais para o isolamento de aplicações:

```
+-----------------------------------+     +-----------------------------------+
|            MÁQUINA VIRTUAL        |     |             CONTÊINER             |
+-----------------------------------+     +-----------------------------------+
|  +--------------+ +------------+  |     |  +--------------+ +------------+  |
|  | Aplicação A  | | Aplicação B|  |     |  | Aplicação A  | | Aplicação B|  |
|  +--------------+ +------------+  |     |  +--------------+ +------------+  |
|  |   Sist. Op.  | |  Sist. Op.  |  |     |  |  Libs/Deps   | |  Libs/Deps  |  |
|  |   Convidado  | |   Convidado |  |     |  +--------------+ +------------+  |
|  +--------------+ +------------+  |     |       Container Engine (Docker)   |
|         Hypervisor (Hardware)     |     |       Sist. Operacional Hospedeiro|
+-----------------------------------+     +-----------------------------------+
|          Máquina Física (HW)      |     |          Máquina Física (HW)      |
+-----------------------------------+     +-----------------------------------+
```

#### A. Virtualização de Servidores (Nível de Hardware)

Utiliza uma camada de software chamada **Hypervisor** para emular por completo componentes físicos de hardware (placa-mãe, CPU, memória RAM, discos, placas de rede). Cada ambiente lógico isolado criado é uma **Máquina Virtual (VM)**, que opera de forma totalmente independente e possui seu próprio Sistema Operacional (SO) completo instalado.

- **Tipos de Hypervisor:** VMware ESXi, XenServer e Microsoft Hyper-V.
- **Fatores Críticos Viabilizados:**
    - _Independência de hardware:_ O hypervisor esconde as peculiaridades físicas do hardware de destino. Isso permite que VMs sejam facilmente migradas de um servidor físico para outro, sem problemas de compatibilidade.
    - _Consolidação de servidores:_ Processo de agrupar o maior número possível de VMs ativas em poucos servidores físicos ativos, desligando servidores físicos temporariamente ociosos para economizar energia e reduzir custos no datacenter.
    - _Facilidade de replicação:_ Como a VM é tratada como software, ela pode ser copiada, restaurada e replicada por meio de operações simples de manipulação de arquivos.

#### B. Containerização (Nível de Sistema Operacional)

Substitui o hypervisor de hardware por um **Container Engine (como o Docker)**, permitindo que as aplicações rodem em ambientes lógicos e isolados chamados **Contêineres**. Diferente das VMs, os contêineres compartilham o mesmo núcleo (kernel) do sistema operacional da máquina hospedeira.

- **Docker:** Plataforma de código aberto amplamente utilizada para empacotar e distribuir aplicações com suas dependências exatas (bibliotecas, arquivos de configuração), assegurando consistência do ambiente de execução.
- **Kubernetes (K8s):** Sistema de orquestração de contêineres responsável por automatizar a implantação, o escalonamento horizontal e o gerenciamento resiliente de contêineres espalhados em clusters de servidores.
- **Vantagens dos Contêineres:** Por serem mais "leves" e não precisarem inicializar um SO convidado completo, os contêineres consomem menos recursos e inicializam em segundos, facilitando processos de replicação em escala de serviços Web.
- **Desvantagem:** Por compartilharem o mesmo sistema operacional, oferecem um nível de isolamento e segurança lógica menor do que as máquinas virtuais.

---

### Módulo 3: Modelos de Serviço (IaaS, PaaS, SaaS) e Especializados

O modelo de serviço determina a fronteira de responsabilidades administrativas entre o cliente e o provedor de nuvem, além do nível de controle sobre a infraestrutura.

```
 Nível de Controle Administrativo (Cliente)
 <=============================================================
 On-Premise          IaaS                PaaS             SaaS
 [Cliente]          [Provedor (HW)]     [Provedor (HW+SO)] [Provedor (Tudo)]
 - Apps             - Apps              - Apps           - Configurações
 - SO / BD          - SO / BD           - Configuração   - Uso Final
 - Hardware         - [VM isolada]      - [Ambiente]     - [App Web]
 =============================================================>
 Nível de Abstração da Complexidade (Transparência)
```

1. **IaaS (Infraestrutura como Serviço):** O provedor oferece recursos fundamentais de hardware virtualizado (servidores virtuais, armazenamento persistente em disco e conectividade de rede).
    - _Controle do Cliente:_ O cliente possui acesso administrativo (_root_) sobre os sistemas operacionais das VMs, sendo inteiramente responsável pela instalação, configuração, atualização do SO, escolha de bancos de dados, segurança lógica de rede local (firewalls) e otimização.
    - _Exemplos:_ Amazon EC2, Azure Virtual Machines, Google Compute Engine.
2. **PaaS (Plataforma como Serviço):** O provedor fornece de forma dinâmica um ambiente de desenvolvimento e execução de aplicações completo e pré-configurado, composto por sistema operacional, servidores web, compiladores de linguagens de programação e gerenciadores de banco de dados (SGBDs).
    - _Controle do Cliente:_ O cliente não gerencia máquinas virtuais, nem atualizações de SO ou infraestrutura física. Ele se concentra exclusivamente na lógica do código e na publicação (_deploy_) de suas aplicações na nuvem.
    - _Exemplos:_ Google App Engine, AWS Elastic Beanstalk, Heroku.
3. **SaaS (Software como Serviço):** O provedor de nuvem disponibiliza soluções de software prontas e finalizadas para os usuários finais, acessadas remotamente pela internet por meio de navegadores web (_thin clients_).
    - _Controle do Cliente:_ O usuário não tem controle algum sobre o desenvolvimento, o sistema operacional, o banco de dados ou a infraestrutura física de suporte. Ele apenas consome as funcionalidades e personaliza preferências de uso na aplicação.
    - _Exemplos:_ Microsoft Office 365, Google Workspace, Salesforce.

#### Modelos de Serviços Especializados (Evolução XaaS):

- **DBaaS (Banco de Dados como Serviço):** Especialização de PaaS na qual o provedor disponibiliza o SGBD pronto para uso e cuida de toda a sua infraestrutura subjacente, atualizações, backups e dimensionamento. Exemplos: Amazon RDS, Google Cloud SQL, Microsoft Azure Cosmos DB, MongoDB Atlas.
- **BaaS (Backend como Serviço):** Plataforma pré-configurada voltada para simplificar e agilizar o desenvolvimento do _frontend_ de aplicações web e móveis, fornecendo no backend serviços automáticos de autenticação de usuários, bancos de dados em tempo real e armazenamento de objetos. Exemplo: Google Firebase.
- **BPaaS (Processos de Negócio como Serviço):** Entrega de ferramentas integradas na nuvem para modelagem de fluxos de trabalho, gestão corporativa e integração de dados de processos empresariais.
- **FaaS (Function as a Service) / Serverless Computing:** Modelo em que os desenvolvedores executam pequenos fragmentos de código (funções) em resposta a eventos específicos sem gerenciar qualquer servidor. O provedor gerencia o provisionamento instantâneo do ambiente e cobra apenas pelo tempo de processamento exato da função. Exemplos: AWS Lambda, Azure Functions.

---

### Módulo 4: Modelos de Implantação e Infraestrutura de Rede em Nuvem

O modelo de implantação define as fronteiras de acesso à infraestrutura de nuvem, bem como o nível de isolamento regulatório dos recursos:

1. **Nuvem Privada (Private Cloud):** A infraestrutura de nuvem é operada e utilizada exclusivamente por uma única organização. Pode ser gerenciada internamente pela organização ou terceirizada e hospedada localmente ou em instalações de terceiros. É indicada para empresas com rígidos requisitos de conformidade de segurança e controle de dados.
2. **Nuvem Pública (Public Cloud):** A infraestrutura computacional pertence a um provedor comercial terceirizado e é compartilhada de forma concorrente e escalável entre múltiplos clientes (público geral). Os clientes pagam sob demanda e se beneficiam de uma infraestrutura global escalável.
3. **Nuvem Comunitária (Community Cloud):** Infraestrutura dedicada para uso exclusivo de um grupo específico de organizações que compartilham objetivos, requisitos de segurança ou interesses regulatórios comuns. A administração pode ser realizada por um consórcio dessas empresas ou terceirizada.
4. **Nuvem Híbrida (Hybrid Cloud):** Composição integrada e transparente de duas ou mais infraestruturas de nuvens distintas (públicas, privadas ou comunitárias) que mantêm sua autonomia física, mas são interconectadas por tecnologias padronizadas ou proprietárias, viabilizando a portabilidade de dados e aplicações.
    - _Cloud Bursting (Transbordo na Nuvem):_ Cenário clássico de nuvem híbrida em que a aplicação é executada rotineiramente na nuvem privada (para proteger dados críticos) e, em momentos sazonais de pico de tráfego, "transborda" temporariamente para uma nuvem pública alocando servidores adicionais, evitando sobrecarga e lentidão lógica.
5. **Virtual Private Cloud (VPC - Nuvem Privada Virtual):** Modelo de rede lógica no qual o provedor de nuvem pública reserva uma seção isolada e segura de sua infraestrutura dedicada exclusivamente para uma organização, utilizando conexões criptografadas de rede (VPN), firewalls e segmentação de sub-redes virtuais.

#### Plataformas Open Source para Nuvem:

Plataformas que funcionam como "sistemas operacionais para datacenters", permitindo que empresas gerenciem seus servidores físicos e configurem suas próprias nuvens privadas ou híbridas.

- _OpenStack:_ Composto por projetos modulares integrados:
    - **Nova:** Gerencia o ciclo de vida de instâncias computacionais (VMs).
    - **Neutron:** Virtualiza componentes e gateways de rede e conexões lógicas.
    - **Swift:** Armazenamento de dados não estruturados de objetos de alta disponibilidade.
    - **Cinder:** Fornece e gerencia discos virtuais persistentes de armazenamento em bloco para as VMs.
    - **Keystone:** Gerenciamento centralizado de identidades, autenticação e controle de acessos lógicos.
    - **Glance:** Repositório e gerenciador de imagens pré-configuradas de máquinas virtuais.
- _Outras Plataformas líderes:_ Apache CloudStack, Eucalyptus, OpenNebula.

---

### Módulo 5: Qualidade de Serviço (QoS) e Gestão de Desempenho

O desempenho satisfatório do acesso remoto depende de uma conexão de rede estável e de mecanismos de garantia de infraestrutura de TI.

#### Métricas de Desempenho de Rede (QoS):

- **Atraso (Latência):** O tempo total necessário para a transmissão de um pacote de dados do remetente ao destinatário na rede.
- **Jitter:** A variação estatística no atraso da transmissão dos pacotes de dados. Altos valores prejudicam o desempenho de transmissões em tempo real (como chamadas de voz e streaming de mídia).
- **Taxa de Transmissão (Bandwidth / Throughput):** Volume físico de dados que é transmitido com sucesso de forma efetiva através de conexões lógicas por segundo (Mbps).
- **Taxa de Perda:** Percentual de pacotes transmitidos pelo nó de origem que não foram entregues ao destinatário.

#### Indicadores e Métricas de Confiabilidade de Serviço (SLA):

- **Disponibilidade:** Porcentagem real de tempo em que um serviço em nuvem permaneceu totalmente ativo e apto para responder requisições de forma bem-sucedida.
- **Performance (Desempenho):** Medida de capacidade de execução, frequentemente quantificada pelo tempo de resposta total de ponta a ponta que uma transação requer.
- **Confiabilidade:** Capacidade do serviço em operar sem interrupções indesejadas, medida pelo **Tempo Médio Entre Falhas (MTBF)**.
- **Resiliência:** Capacidade do sistema em tolerar desastres lógicos e físicos, medida pelo grau de tolerância a falhas e pelo **Tempo Médio para Recuperação (MTTR)** de incidentes.

#### Mecanismos Tecnológicos de Garantia de Desempenho e Confiabilidade:

##### 1. Dimensionamento Automático (Automated Scaling)

Ajusta dinamicamente os recursos disponíveis de acordo com métricas de utilização de hardware (como uso de CPU) monitoradas pelo Monitor de SLA.

- **Vertical (Scale-up/down):** Aumenta ou diminui a capacidade física de uma mesma instância lógica de máquina virtual (ex: alterar RAM de 8GB para 16GB). _Gargalo:_ Limitado por barreiras físicas de hardware da máquina física e pode gerar tempo de inatividade (_downtime_).
- **Horizontal (Scale-out/in):** Adiciona ou remove réplicas lógicas de servidores (instâncias de VMs ou contêineres idênticos) no pool ativo de balanceamento de carga. É ideal para arquiteturas elásticas e aplicações web.

##### 2. Balanceamento de Carga (Load Balancing)

Mecanismo de distribuição e direcionamento inteligente das requisições recebidas entre múltiplos servidores redundantes em execução no ambiente do provedor, otimizando o tempo de resposta geral e prevenindo sobrecargas. Pode ser feito com base na localização geográfica do cliente para direcionar ao datacenter mais próximo.

##### 3. Mecanismos de Recuperação de Falhas (Disaster Recovery)

Depende da criação redundante de réplicas do sistema para tolerar indisponibilidades do servidor físico:

- **Modelo Ativo-Ativo:** Todas as réplicas lógicas idênticas do sistema participam de forma simultânea do processamento e recebem requisições ativamente por meio do balanceamento de carga. Se uma instância cair, o tráfego é direcionado para as réplicas restantes. _Risco:_ Se a réplica sobrevivente já estiver sobrecarregada, o desempenho pode sofrer degradação acentuada.
- **Modelo Ativo-Passivo:** Existe uma instância principal ("Ativa") que responde a 100% das consultas regulares, enquanto uma réplica secundária ("Passiva" ou _hot standby_) permanece inativa ou ociosa. A secundária é ativada apenas se a principal falhar. _Desvantagem:_ Gera maior custo financeiro de ociosidade de recursos.

---

### Módulo 6: Gerenciamento e Armazenamento de Dados na Nuvem

Sistemas de gerenciamento de dados em nuvem enfrentam desafios complexos para assegurar integridade, persistência física e escalabilidade lícita a custos viáveis.

#### Classificação dos Dados no SGBD:

- **Estruturados:** Organizados de forma rígida em esquemas de tamanhos fixos estruturados sob formatos e chaves lógicas de relacionamentos (SGBDs relacionais SQL).
- **Não estruturados:** Não possuem formato fixo predefinido e variam em tamanho e propriedades (imagens, binários, vídeos, metadados).
- **Semiestruturados:** Meio-termo, organizados por tags lógicas ou marcações fáceis que auxiliam a sua identificação automática (ex: arquivos XML, JSON).

#### Os 4 Modelos de Armazenamento de Dados em Nuvem:

1. **Armazenamento em Blocos (Block Storage):** Oferece unidades virtuais de disco rígido (discos virtuais secundários de baixo nível de abstração) formadas por blocos lógicos sobre HDs ou SSDs físicos do datacenter, alocadas de forma dedicada para servirem como discos de inicialização e gravação de VMs ou contêineres. Exemplos: Amazon EBS, Google Persistent Disk, Azure Disk Storage.
2. **Armazenamento de Arquivos (File Storage):** Armazenamento baseado em compartilhamento remoto de diretórios e sistemas de arquivos distribuídos em rede via protocolos padronizados de comunicação como NFS (Network File System) ou SMB (Server Message Block). Exemplos: Amazon EFS, Google Cloud Filestore, Azure Files.
3. **Armazenamento de Objetos (Object Storage):** Repositório global voltado para arquivos binários não estruturados (áudios, imagens, vídeos, backups), em que cada arquivo é gerenciado de forma isolada como um "objeto" individual, que possui um identificador exclusivo e metadados descritivos detalhados. O acesso e a manipulação dos objetos ocorrem por meio de requisições web baseadas no protocolo HTTP (Web APIs lógicas de métodos lógicos como get e put). Exemplos: Amazon S3, Google Cloud Storage, Azure Blob Storage.
4. **Armazenamento de Bases de Dados (Database Storage):** Sistemas gerenciadores de bancos de dados relacionais e NoSQL hospedados e gerenciados pelo provedor, que aceitam conexões de consultas de linguagens padronizadas de dados.

#### Teorema CAP e as Propriedades BASE:

Formulado pelo pesquisador Eric Brewer, o **Teorema CAP** estabelece que um sistema de dados distribuído geograficamente não é capaz de garantir de forma simultânea as seguintes três propriedades:

- **Consistência (C - Consistency):** Todos os nós lógicos do sistema de banco de dados têm exatamente a mesma visão dos dados ao mesmo tempo.
- **Disponibilidade (A - Availability):** Todas as requisições enviadas ao sistema sempre recebem uma resposta de sucesso ou erro, sem bloqueios.
- **Tolerância a partições de rede (P - Partition Tolerance):** O sistema continua em funcionamento normal mesmo diante de falhas de comunicação ou interrupções físicas de enlaces de rede entre nós distribuídos do cluster.

> **A Regra CAP:** Na presença inevitável de partições de rede físicas (P), o banco de dados é forçado a escolher entre consistência forte (C) ou disponibilidade total (A).

Como alternativa ao rigor ACID de bancos relacionais tradicionais, muitos sistemas distribuídos escaláveis NoSQL adotam as **Propriedades BASE**:

- **Basically Available (Basicamente Disponível):** O sistema se mantém em funcionamento respondendo consultas mesmo em cenários parciais de falha.
- **Soft State (Estado Leve/Fluido):** Os dados lógicos podem sofrer alterações e flutuações de atualização sem garantia de consistência síncrona permanente em todas as réplicas.
- **Eventually Consistent (Eventualmente Consistente):** O sistema de banco de dados assegura que, caso nenhuma atualização nova ocorra por determinado tempo, todas as réplicas se harmonizarão e alcançarão a consistência completa.

##### Níveis de Consistência Clássicos:

- _Consistência Forte:_ Garante que qualquer acesso subsequente à atualização concluída sempre retornará o valor mais recente.
- _Consistência Fraca:_ O sistema não assegura que as leituras seguintes à gravação retornarão o valor atualizado. O intervalo de incerteza é chamado de "janela de inconsistência".

---

### Módulo 7: Classificação dos Sistemas de Banco de Dados em Nuvem

O ecossistema de bancos de dados na nuvem é classificado de acordo com duas variáveis principais: **Modelo de Dados (Relacional vs. Não Relacional)** e se foi desenvolvido de forma **Nativa para Nuvem (Cloud Native) ou Não Nativa (Adaptado)**.

```
                     |
         NATIVO      |      NÃO-NATIVO (Tradicional)
                     |
   RELACIONAL        |
   - SQL Azure |  - Amazon RDS
                     |  - Relational Cloud
---------------------+------------------------------
   NÃO-RELACIONAL    |
   - Dynamo    |  - Neo4j (Grafo)
   - BigTable  |  - CouchDB (Documento)
   - Cassandra |  - MongoDB (Documento)
                     |
```

- **Sistemas Relacionais:** Utilizam álgebra relacional, estruturação de tabelas bem definidas e linguagem de consulta SQL. Implementam transações ACID robustas e consistência forte. _Limitação:_ Baixo desempenho nativo e complexidade de escalabilidade distribuída de múltiplos servidores.
- **Sistemas NoSQL (Not Only SQL):** Não utilizam o modelo relacional clássico e sacrificam a consistência forte síncrona em favor de alta disponibilidade e escalabilidade distribuída horizontal para volumes massivos de dados. São subdivididos em quatro categorias principais:
    1. _Chave-Valor:_ Estrutura ultra-simplificada de hash para acessos rápidos de get e put por chaves (ex: Amazon DynamoDB).
    2. _Coluna (Família de Colunas):_ Estrutura de chaves lógicas para arrays multidimensionais esparsos indexados de colunas (ex: BigTable, Cassandra, HBase).
    3. _Documento:_ Armazena documentos semiestruturados (como JSON) acessados por identificadores exclusivos (ex: CouchDB, MongoDB).
    4. _Grafo:_ Especializado no armazenamento e consultas eficientes de conexões lógicas complexas de vértices e arestas de relacionamentos complexos (ex: Neo4j).

---

### Módulo 8: Segurança, Privacidade e Gestão de Riscos

Como o acesso remoto às aplicações em nuvem ocorre através da Internet, que é considerada um meio físico de comunicação inseguro, é crucial implementar controles lógicos rigorosos de proteção.

#### Propriedades de Segurança da Informação:

1. **Confidencialidade:** Garantia de sigilo do conteúdo das informações transmitidas ou armazenadas, impedindo que partes não autorizadas as leiam.
2. **Integridade:** Garantia de que as informações transmitidas ou guardadas não foram modificadas por incidentes de rede ou ataques intencionais.
3. **Autenticidade:** Confirmação lícita da identidade real de todas as partes envolvidas no processo de comunicação.
4. **Disponibilidade:** Garantia de que o sistema computacional e as redes estarão ativos e funcionais para receber as requisições de serviços.

#### Mecanismos Tecnológicos de Proteção em Nuvem:

- **Criptografia:** Codificação matemática das informações para protegê-las contra interceptações de tráfego (espionagem) na Internet.
    - _Simétrica:_ Utiliza a mesma chave única para codificar e decodificar dados.
    - _Assimétrica (Chave Pública):_ Usa um par de chaves relacionadas matematicamente. A chave pública codifica a mensagem, e apenas a chave privada correspondente e mantida em segredo pode decodificar.
- **Função Hash (Código Hash):** Algoritmo que gera uma assinatura matemática única baseada no conteúdo lógico do arquivo enviado. O destinatário calcula o hash novamente para verificar a integridade da transmissão.
- **Gerenciamento de Identidade e Acesso (IAM):** Ferramenta essencial do provedor para gerenciar e autenticar usuários lógicos, agrupar privilégios administrativos e definir permissões e credenciais lógicas de forma minuciosa aos recursos do sistema.
- **Single Sign On (SSO - Autenticação Unificada):** Permite que usuários acessem com segurança múltiplos serviços em diferentes provedores por meio de um único portal integrado de autenticação.
- **Imagens Fortalecidas (Hardened VM Images):** Modelos pré-configurados de VMs cujo sistema operacional foi previamente higienizado e modificado por especialistas lógicos de segurança, eliminando softwares desnecessários e vulnerabilidades padrão de portas lógicas ativas.

#### Processo de Gerenciamento de Riscos (Ciclo de 3 Etapas):

Para garantir confiabilidade e segurança contínuas na migração, as empresas implementam um ciclo recorrente estruturado em três estágios:

1. **Avaliação:** Identificação e classificação minuciosa das ameaças potenciais e vulnerabilidades lógicas presentes na infraestrutura de rede e operação do provedor.
2. **Tratamento:** Definição das estratégias e implementação ativa das políticas e mecanismos tecnológicos de controle para eliminar, contornar ou mitigar as ameaças avaliadas.
3. **Controle:** Avaliação diagnóstica periódica da eficácia de todas as ações de segurança implementadas anteriormente, promovendo melhorias.

---

## Conceitos que não posso confundir

|Conceito A|Conceito B|Diferença Crítica e Inequívoca|
|:--|:--|:--|
|**Elasticidade**|**Escalabilidade**|A **elasticidade** refere-se ao ajuste dinâmico e em tempo real dos recursos de forma automática para responder a flutuações na demanda sazonal. A **escalabilidade** é a capacidade arquitetural estável de um sistema de suportar um aumento contínuo na carga de trabalho de forma sustentável, mantendo a performance.|
|**Escalabilidade Horizontal**|**Escalabilidade Vertical**|A **horizontal** adiciona novas instâncias de servidores (VMs adicionais) ao pool ativo, distribuindo a carga de tráfego de rede entre elas. A **vertical** aumenta a capacidade física de uma única VM existente (mais RAM, mais núcleos de CPU).|
|**Máquina Virtual (VM)**|**Contêiner**|A **VM** utiliza virtualização de hardware através do hypervisor e possui seu próprio SO isolado e independente de grande tamanho de imagem. O **contêiner** opera no nível do sistema operacional, compartilha o kernel do SO hospedeiro através de um container engine, sendo muito mais leve e portátil.|
|**Nuvem de Armazenamento**|**Armazenamento para Nuvem**|A **nuvem de armazenamento** é um ambiente direcionado exclusivamente aos dados do usuário e arquivos que buscam interatividade direta e flexibilidade física. O **armazenamento para nuvem** foca na configuração interna técnica dos serviços de infraestrutura e nos discos virtuais das VMs.|
|**Modelo Ativo-Ativo**|**Modelo Ativo-Passivo**|No **ativo-ativo**, todas as réplicas lógicas idênticas do sistema participam e distribuem o processamento em tempo real. No **ativo-passivo**, apenas uma máquina atende o tráfego ativamente, e a réplica secundária permanece em ociosidade até que ocorra uma falha na primária.|
|**SLA**|**QoS**|O **SLA** é o documento formal do acordo que estabelece as regras e métricas contratadas. O **QoS** é a abordagem técnica geral e o conjunto de métricas quantitativas de desempenho em rede utilizadas para garantir os níveis de desempenho contratados.|
|**Re-platform**|**Re-factor / Re-architect**|No **re-platform**, a aplicação sofre adaptações mínimas para aproveitar as plataformas e SGBDs gerenciados da nuvem (PaaS, DBaaS). No **re-factor**, a aplicação é completamente reescrita do zero para utilizar microsserviços e recursos nativos da nuvem.|
|**Criptografia Simétrica**|**Criptografia Assimétrica**|A **simétrica** utiliza uma única chave compartilhada secreta para codificar e decodificar dados. A **assimétrica** utiliza um par de chaves distintas (uma chave pública para codificar e uma chave privada secreta para decodificar).|

---

## Pontos importantes para prova

1. **Etapas de Ciclo de Migração para a Nuvem (Processo de Morais):** Deve ser respondido na ordem lógica correta das etapas:
    - _Etapa 1 — Planejamento:_ Levantamento minucioso dos requisitos técnicos da aplicação, análise de riscos regulatórios, escolha dos provedores de nuvem, escolha do modelo de serviço (IaaS, PaaS, SaaS) e de implantação, estimativa de custos econômicos e definição da estratégia exata de migração.
    - _Etapa 2 — Execução:_ Migração prática que envolve a extração de dados locais, conversão de formatos de dados, transferência lógica de volumes de informações, adaptações na arquitetura dos sistemas de software locais e substituição por bibliotecas e APIs nativas do provedor.
    - _Etapa 3 — Avaliação:_ Testes de validação de consistência dos dados, testes de estresse de desempenho de processamento, auditoria lógica de integridade de segurança, e mensuração direta da qualidade de experiência do usuário final.
2. **As 3 Estratégias de Migração Clássicas:**
    - _Re-host (Lift and Shift):_ Migração da aplicação exata e suas VMs para a nuvem sem alterações de código ou arquitetura. Menor custo inicial, mas não se beneficia da elasticidade e mecanismos dinâmicos da nuvem.
    - _Re-platform ( abordagem intermediária):_ Migração dos componentes lógicos adaptando a base para serviços nativos gerenciados (ex: banco relacional local para DBaaS) sem reescrever o código geral.
    - _Re-factor ou Re-architect:_ Remodelação estrutural completa da aplicação para utilizar tecnologias nativas de microsserviços, FaaS e contêineres. Envolve maior custo, tempo de implementação e complexidade de testes, mas maximiza a economia de recursos.
3. **Arquitetura Monolítica vs. Microsserviços:**
    - _Monolito:_ Todas as funcionalidades lógicas e módulos estão embutidos em um único componente de software e executam em um mesmo processo. _Problema:_ Dificuldade de atualizar módulos pontuais (exige reiniciar o software completo), alto consumo de memória e alto custo operacional de replicação (é preciso duplicar a aplicação inteira).
    - _Microsserviços:_ Divisão funcional lógica da aplicação em múltiplos componentes menores e especializados (_microsserviços_) altamente coesos e fracamente acoplados, que se comunicam via APIs web lógicas através de um gateway unificado (_API Gateway_). _Vantagem:_ Permite a replicação seletiva e independente apenas dos módulos críticos que estão sofrendo picos de tráfego, evitando desperdício de recursos financeiros do provedor.
4. **Edge Computing (Computação de Borda):** Paradigma descentralizado cujo objetivo não é substituir o datacenter de nuvem central, mas complementá-lo. Consiste em mover o processamento e a análise de dados para a borda física da rede, nos próprios dispositivos ou em infraestruturas locais. É altamente indicada para redes de sensores IoT, análise de tráfego de veículos autônomos e aplicações multimídia que exigem tempo de resposta ultra-rápido (baixa latência).
5. **Regra do Armazenamento Temporário:**
    - _Armazenamento Transitório:_ Volume lógico que só persiste enquanto a máquina virtual correspondente estiver em execução lógica ativa, sendo limpo e retornado ao pool livre quando a VM for interrompida ou desligada (ex: arquivos temporários, cache).
    - _Armazenamento Persistente:_ Caráter permanente; dados sobrevivem a reinicializações e encerramentos físicos da VM correspondente.

---

## Revisão rápida

```
              COMPUTAÇÃO EM NUVEM: O ESSENCIAL

         [NIST: 5 Características - 3 Modelos - 4 Implantações]
              /                      |                      \
  [Características]              [Serviços]              [Implantação]
  - Autoatendimento              - IaaS (Hardware)       - Pública (Pública)
  - Amplo Acesso                 - PaaS (Ambiente)       - Privada (Dedicada)
  - Pool de Recursos             - SaaS (Software)       - Comunitária (Grupo)
  - Elasticidade Rápida          - FaaS (Sem Servidor)   - Híbrida (Bursting)
  - Serviço Medido

  [Tecnologias de Suporte]:
  - Virtualização (Hypervisor/VMs): Isolamento de hardware, SO dedicado completo.
  - Containerização (Docker/K8s): Leveza lógica, compartilha o kernel do SO hospedeiro.

  [Desempenho e Confiabilidade]:
  - QoS: Atraso, Jitter, Taxa de transmissão, Perda.
  - SLA: Acordo quantitativo com Monitor de SLA e dimensionamento automático.
  - Redundância: Ativo-Ativo (distribuído) vs. Ativo-Passivo (ociosidade em reserva).

  [Gerenciamento de Dados]:
  - CAP: Escolha entre Consistência (C) e Disponibilidade (A) na partição de rede (P).
  - BASE: Alternativa elástica de Consistência Eventual para alta disponibilidade NoSQL.
  - Armazenamento: Bloco (discos VM), Arquivo (NFS/SMB), Objeto (HTTP APIs/S3), BD (DBaaS).

  [Segurança e Riscos]:
  - Propriedades: Confidencialidade, Integridade, Autenticidade, Disponibilidade.
  - Mecanismos: Criptografia, Hashing, IAM, SSO, Imagens Fortalecidas.
  - Ciclo de Gestão de Riscos: Avaliação -> Tratamento -> Controle.
```

---
