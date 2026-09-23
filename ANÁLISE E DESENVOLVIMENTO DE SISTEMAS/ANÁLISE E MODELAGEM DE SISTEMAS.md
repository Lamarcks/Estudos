[[EXEMPLOS-PRÁTICOS DE ANÁLISE E MODELAGEM DE SISTEMAS]]
#ASSUNTO 
## Visão geral

Esta nota de estudo abrange os pilares fundamentais da **Análise e Modelagem de Sistemas**, compreendendo a evolução histórica e o ciclo de vida do software, os processos metodológicos de desenvolvimento (tradicionais e ágeis), as práticas da **Engenharia de Requisitos**, o **Gerenciamento de Processos de Negócio (BPM/BPMN)** e a modelagem visual utilizando a **Linguagem de Modelagem Unificada (UML)**. O objetivo deste material é consolidar definições, classificações, metodologias e diagramas para dar suporte ao estudo teórico e prático de nível acadêmico e profissional.

## Conceitos principais

- **Software**: É composto por programas de computador acompanhados de documentação associada. Divide-se essencialmente em três elementos principais: **Instruções** (que fornecem as funções de desempenho desejadas), **Estruturas de Dados** (que permitem a manipulação adequada de informações) e **Documentação** (informação descritiva detalhando o uso e a operação do sistema).
- **Análise de Sistemas**: Investigação detalhada de sistemas existentes ou propostos com o intuito de determinar as reais necessidades e objetivos do usuário, estruturando soluções computacionais eficientes, adaptáveis e escaláveis.
- **Engenharia de Requisitos**: Conjunto de atividades estruturadas para produzir e manter um documento formal de requisitos. Define todas as funcionalidades que o sistema deve apresentar, juntamente com seus serviços e restrições de funcionamento, assegurando que desenvolvedores e clientes compartilhem do mesmo entendimento sobre o problema.
- **Processo de Negócio**: Sequência lógica, coordenada e estruturada de tarefas que utiliza entradas (_inputs_ como pessoas, equipamentos, recursos e informações) para processá-las e gerar saídas (_outputs_ como bens ou serviços) que agreguem valor real ao cliente final.
- **BPM (Business Process Management)**: Abordagem holística e horizontal focada no gerenciamento, mapeamento, otimização e controle dos processos de negócio de ponta a ponta, alinhando as operações aos objetivos estratégicos da organização.
- **UML (Unified Modeling Language)**: Linguagem de modelagem visual padronizada internacionalmente, de propósito geral, voltada para a especificação, visualização, construção e documentação de sistemas de software baseados no paradigma orientado a objetos.

---

## Conteúdo explicado

### 1. Evolução e Deterioração do Software

O software de computador evoluiu desde a década de 1940 (onde o programa executável tinha controle total do hardware) até a era moderna, marcada por computação em nuvem, aplicativos móveis integrados e inteligência artificial.

Diferentemente do hardware, que se desgasta fisicamente devido a fatores ambientais (vibração, poeira, temperatura), **o software não sofre deterioração física**. No entanto, o software sofre **deterioração lógica** decorrente das constantes modificações e acréscimos de funcionalidades implementados ao longo de sua vida útil.

```
Curva de Defeitos (Curva Real vs. Idealizada)
Taxa de Defeitos
  ^
  |  \                 /\             /\
  |   \               /  \           /  \      <- Curva Real (Picos gerados por efeitos
  |    \  Mudança    /    \         /    \        colaterais de modificações)
  |     *-----------/------\-------/------\---
  |      \_________/        \_____/        \__ <- Curva Idealizada (Estabilização teórica)
  +--------------------------------------------> Tempo
```

Cada mudança emergencial ou alteração mal documentada no software introduz novos erros, elevando a taxa de defeitos através de **efeitos colaterais** indesejados.

---

### 2. O Processo de Software e seus Modelos

Um **Processo de Software** é um conjunto de atividades inter-relacionadas que levam à criação do produto de software. Ele fornece uma abordagem flexível para garantir qualidade, prazos e controle de custos.

#### Atividades Fundamentais de Processo

Independentemente do modelo adotado, as teorias clássicas convergem em atividades metodológicas essenciais:

- **Visão de Sommerville**: **Especificação** (definição de escopo e restrições), **Projeto e Implementação** (desenho técnico e codificação), **Validação** (verificação de conformidade com os requisitos do cliente) e **Evolução** (adaptações ao longo do tempo).
- **Visão de Pressman**: **Comunicação**, **Planejamento**, **Modelagem**, **Construção** e **Entrega**.

#### Classificação dos Modelos de Ciclo de Vida

1. **Modelos Prescritivos (Tradicionais)**:
    - **Modelo Cascata (Ciclo de Vida Clássico)**: Abordagem linear e estritamente sequencial. Uma fase só se inicia quando a anterior está totalmente concluída. _Fases_: Definição de requisitos \(\rightarrow\) Projeto do sistema \(\rightarrow\) Implementação e teste de unidade \(\rightarrow\) Integração e teste de sistema \(\rightarrow\) Operação e manutenção. _Limitação_: Alta inflexibilidade para mudanças e longos períodos de espera para a primeira entrega ao cliente.
    - **Modelo Incremental**: O desenvolvimento é focado em entregar o software em módulos/versões funcionais de forma progressiva. O cliente valida e utiliza incrementos parciais ao longo do projeto, reduzindo riscos.
    - **Modelo Espiral (Evolucionário)**: Abordagem cíclica e iterativa que mescla a natureza incremental da prototipação com os controles sistemáticos do modelo cascata, destacando-se pela **análise proativa de riscos** em cada volta da espiral.
2. **Modelos Especializados**:
    - _Baseado em Componentes_: Utilização e integração de módulos de software pré-fabricados e reutilizáveis.
    - _Métodos Formais_: Emprego de especificações matemáticas formais para eliminar ambiguidades e inconsistências no código.
    - _Orientado a Aspectos (DSOA)_: Foco em modularizar preocupações transversais (aspectos) que afetam múltiplos componentes do sistema.
3. **Desenvolvimento Ágil (XP e Scrum)**:
    - **XP (Extreme Programming)**: Focado em ciclos rápidos, desenvolvimento incremental, feedback contínuo, programação em par (_pair programming_) e participação ativa de um representante do cliente na equipe de criação.
    - **Scrum**: Metodologia de gestão interativa estruturada em:
        - _Product Backlog_: Lista dinâmica e priorizada de todos os requisitos e histórias do sistema.
        - _Sprints_: Ciclos de trabalho com tempo fixo (_Time Box_) para produzir incrementos funcionais.
        - _Daily Scrum_: Reuniões diárias de 15 minutos para sincronização de progresso e identificação de impedimentos.
        - _Scrum Master e Product Owner_: Papéis de facilitação do processo e definição de prioridades de negócios, respectivamente.

---

### 3. O Processo Unificado (PU / RUP)

O **Processo Unificado** é uma metodologia adaptativa orientada por **Casos de Uso**, centrada na **Arquitetura** do sistema e de natureza **Iterativa e Incremental**. Sua versão comercial refinada é o **RUP (Rational Unified Process)**.

#### As 4 Fases do PU

1. **Concepção**: Estabelece o escopo geral, viabilidade do projeto, objetivos principais e riscos iniciais.
2. **Elaboração**: Detalhamento aprofundado de requisitos, análise de riscos críticos e **definição da arquitetura base do sistema**.
3. **Construção**: Desenvolvimento ativo e codificação progressiva do sistema, partindo do básico para o complexo, culminando em uma versão beta funcional.
4. **Transição**: Implantação e entrega do software em produção, treinamento de usuários, correção de falhas residuais e validação final.

#### Elementos e Disciplinas Fundamentais

O PU se estrutura em quatro eixos: **Papel** (quem faz), **Artefato** (o produto gerado), **Atividade** (como é feito) e **Disciplina/Fluxo de Trabalho** (quando é feito). Suas disciplinas dividem-se em:

- _Modelagem de Negócios_: Alinhamento do sistema às regras de negócios com casos de uso de negócios.
- _Requisitos_: Definição detalhada das necessidades do sistema sob a ótica dos atores.
- _Análise e Projeto_: Criação de diagramas lógicos, divisão do software em subsistemas estruturados e definição da arquitetura.
- _Implementação_: Codificação real dos componentes em arquivos-fonte e bancos de dados.
- _Teste_: Verificação de erros, integração e conformidade dos requisitos.
- _Implantação_: Distribuição do sistema, migração de dados e homologação formal.
- _Disciplinas de Suporte (RUP)_: Gerenciamento de mudanças e configurações, gerenciamento de projetos e ambiente de desenvolvimento.

---

### 4. Engenharia de Requisitos

Os requisitos descrevem as funções, serviços, restrições gerais e critérios de desenvolvimento que um sistema deve cumprir para satisfazer as necessidades do cliente.

#### Qualificação e Critérios de Qualidade dos Requisitos

Para ser considerado bem especificado, todo requisito deve atender a:

- **Exatidão**: Deve pertencer genuinamente ao produto contratado.
- **Precisão**: Deve apresentar uma interpretação unívoca (sem ambiguidades) para clientes e programadores.
- **Completude**: Deve documentar todas as decisões de projeto acordadas.
- **Consistência**: Não deve entrar em conflito direto com nenhum outro requisito.
- **Priorização**: Rotulado adequadamente por importância e estabilidade.
- **Verificabilidade**: Deve ser testável na prática para validação final.
- **Modificabilidade**: Sua estrutura deve permitir alterações de forma fácil e consistente.
- **Rastreabilidade**: Deve permitir determinar sua origem (antecedentes) e seus desdobramentos (implicações).

#### Classificação Fina dos Requisitos

- **Requisitos Funcionais (RF)**: Descrevem o comportamento explícito do sistema em resposta a entradas do usuário ou de outros sistemas (ex.: cadastrar clientes, emitir relatórios de vendas).
- **Requisitos Não Funcionais (RNF)**: Impõem restrições, níveis de qualidade e critérios de desempenho sobre as funcionalidades (ex.: banco de dados MySQL, tempo de resposta inferior a 2 segundos, linguagem JAVA). Dividem-se em:
    - _Requisitos de Produto_: Velocidade, espaço em disco, usabilidade, confiabilidade.
    - _Requisitos Organizacionais_: Políticas internas, procedimentos operacionais da empresa.
    - _Requisitos Externos_: Fatores regulatórios, conformidade legal, segurança de dados.
- **Requisitos de Domínio**: Condições específicas derivadas do ambiente ou regras de negócio do contexto do problema (ex.: regras de cálculo para aprovação acadêmica baseadas no somatório de notas de diferentes categorias).

#### O Processo de Elicitação e Análise

As atividades do processo englobam:

1. **Concepção**: Definição do escopo e identificação dos stakeholders.
2. **Elicitação (Coleta)**: Utilização de técnicas como:
    - _Entrevista_: Diálogos diretos guiados por questionários estruturados ou conversas livres.
    - _Pesquisa/Observação_: Análise do fluxo real de trabalho cotidiano e de softwares concorrentes.
    - _Etnografia_: Observação direta do comportamento e da rotina operacional dos usuários finais (muitas vezes revelando requisitos implícitos omitidos nas entrevistas).
    - _Reuniões/Brainstorming_: Sessões para identificação de novas ideias e alinhamento.
    - _Documentos_: Coleta de relatórios, planilhas e formulários antigos.
3. **Elaboração**: Refinamento dos requisitos e construção de modelos de especificação (ex.: diagramas UML).
4. **Negociação**: Resolução de conflitos de interesses e requisitos contraditórios entre stakeholders através de reuniões de consenso e análise de prioridades.
5. **Especificação**: Geração de tabelas formais ou documentos padronizados de especificação de requisitos.
6. **Validação**: Verificação crítica do documento de requisitos para detectar falhas como inconsistências, contradições, duplicações, ambiguidades e omissões. Métodos comuns incluem revisões formais de requisitos, prototipagem (descartável, evolutiva ou rápida), geração prévia de casos de testes e o uso de **checklists** de conformidade.
7. **Gerenciamento de Requisitos**: Controle do ciclo de vida, rastreamento de status (proposto, em progresso, aprovado) e **gerenciamento formal de mudanças**.

#### Rastreabilidade de Requisitos

A **Rastreabilidade** estabelece as conexões lógicas entre os diferentes níveis de desenvolvimento do software. Ela é classificada em:

- **Rastreabilidade para Trás (Backward)**: Conecta o requisito à sua origem estratégica ou ao stakeholder que o solicitou.
- **Rastreabilidade para Frente (Forward)**: Conecta o requisito aos artefatos subsequentes gerados na engenharia de software (diagramas, classes, código-fonte e casos de teste).
- **Rastreabilidade Horizontal**: Mapeia interdependências lógicas entre requisitos do mesmo nível (ex.: um RF01 que necessita de um RNF03 para ser executado). Normalmente, a representação de rastreabilidade é estruturada por meio de uma **Matriz de Rastreabilidade bidimensional**.

---

### 5. Processos de Negócio (BPM e BPMN)

#### Decomposição e Classificação de Processos

Um processo de negócio pode ser decomposto hierarquicamente para facilitar sua análise e modelagem em: **Macroprocesso** (operações amplas da organização) \(\rightarrow\) **Processo** (fluxo lógico de atividades) \(\rightarrow\) **Subprocesso** (etapas funcionais menores de um processo).

Os processos de negócios são categorizados de acordo com sua função na cadeia de valor da empresa em:

- **Processos Primários**: Diretamente ligados ao negócio principal (_core business_) da empresa. Eles cruzam as fronteiras organizacionais, agregam valor perceptível diretamente ao cliente final e iniciam/terminam no ambiente externo (ex.: produção, vendas, logística de entrega).
- **Processos de Suporte (Apoio)**: Sustentam a execução dos processos primários e de gerenciamento. Agregam valor aos processos internos, não ao cliente final de forma direta (ex.: recursos humanos, contas a pagar, gestão de TI).
- **Processos de Gerenciamento**: Supervisionam, medem e controlam as atividades organizacionais. Estão associados ao acompanhamento estratégico e à melhoria contínua das operações por meio de indicadores chaves de desempenho (KPIs).

#### Visão Funcional (Vertical) vs. Visão de Processos (Horizontal)

- **Visão Funcional (Silos)**: Organização estruturada verticalmente por departamentos ou hierarquias. A comunicação e as metas são restritas a cada setor de forma isolada, gerando silos organizacionais, baixa orientação para o mercado e falta de visibilidade sobre os processos interdependentes.
- **Visão de Processos (Ponta a Ponta)**: Organização estruturada horizontalmente, cruzando as fronteiras funcionais dos departamentos (_interfuncional_) e organizacionais (_interorganizacional_). Ela integra canais de fluxo de dados, foca na jornada de valor do cliente e analisa processos de ponta a ponta com base em tempo, custo e qualidade.

#### Gerenciamento de Processos (BPM, BPMS e CMMI)

O **BPM** é suportado pela tecnologia do **BPMS (Business Process Management Suite)**, um software integrador que apoia o mapeamento, execução e monitoramento em tempo real de fluxos e sistemas legados (frequentemente utilizando adaptadores em arquiteturas orientadas a serviços - **SOA**).

A maturidade organizacional em processos pode ser avaliada pelo modelo **CMMI**, dividido em 5 níveis básicos:

1. _Nível 1 - Inicial_: Sucesso depende de heróis individuais; sem padrões.
2. _Nível 2 - Gerenciado_: Implementação de planejamento, medição e controle de projetos básicos.
3. _Nível 3 - Definido_: Processos padronizados, amplamente documentados e previsíveis.
4. _Nível 4 - Gerenciado Quantitativamente_: Controle estatístico de desempenho e qualidade.
5. _Nível 5 - Em Otimização_: Foco explícito na melhoria contínua de processos e prevenção de falhas.

Para que o gerenciamento funcione, define-se um **Dono de Processo (Process Owner)** — um gestor responsável contínuo pelo ciclo de vida e pela eficácia de um processo específico ponta a ponta —, e estabelece-se metas com base no **método SMART**: \[\text{S (Specific) } \vert \text{ M (Measurable) } \vert \text{ A (Attainable) } \vert \text{ R (Relevant) } \vert \text{ T (Timely)} \]

#### Notação BPMN (Business Process Model and Notation)

BPMN é a notação gráfica padronizada internacionalmente para representar diagramas, mapas e modelos de processos de negócio. Seus principais elementos dividem-se em:

1. **Swinlanes (Raias)**: Dividem-se em:
    - _Pool (Piscina)_: Representa entidades de negócios ou atores independentes envolvidos no processo.
    - _Lane (Raia)_: Subdivisões internas de uma piscina para representar papéis, departamentos ou setores específicos (atores do processo).
2. **Atividades**: O trabalho realizado, representado por retângulos de cantos arredondados. Podem ser **Tarefas** (atômicas) ou **Subprocessos** (expandidos ou colapsados indicados pelo sinal de "\(+\)").
3. **Eventos**: Círculos que indicam ocorrências que impactam o fluxo do processo ao longo do tempo. Podem ser:
    - _Início_ (contorno claro).
    - _Intermediário_ (contorno duplo, ex.: envio de e-mail ou parada temporal).
    - _Fim_ (contorno escuro e espesso).
4. **Gateways**: Losangos de controle de fluxo de sequência para decisões e bifurcações:
    - _Exclusivo baseado em dados (XOR)_: Segue por apenas uma rota dependendo da resposta lúdica (sim/não) a uma condição.
    - _Exclusivo baseado em eventos_: A rota de desvio depende de um gatilho ou resposta externa enviada por um ator externo.
    - _Inclusivo (OR)_: Permite ativar múltiplos caminhos paralelos simultâneos se suas condições individuais forem atendidas.
5. **Conectores**: Linhas que estabelecem conexões:
    - _Fluxo de Sequência_ (linha contínua com seta): Indica a ordem de execução das atividades dentro de um mesmo pool.
    - _Fluxo de Mensagem_ (linha pontilhada com seta vazada): Indica a troca de informações entre participantes localizados em pools separados.
    - _Associação_ (linha pontilhada sem seta): Conecta anotações ou dados aos elementos gráficos.
6. **Artefatos**: Elementos que adicionam informações ao diagrama:
    - _Objeto de Dados_: Representa documentos lógicos que trafegam ou são gerados.
    - _Grupo_: Destaca visualmente uma área funcional do diagrama.
    - _Anotação_: Adiciona comentários ou lembretes sobre tarefas.

---

### 6. Linguagem de Modelagem Unificada (UML) e Paradigma OO

A UML é a linguagem padrão da indústria para modelar sistemas no **Paradigma Orientado a Objetos (OO)**.

#### Pilares do Paradigma Orientado a Objetos

- **Abstração**: Capacidade de focar nos aspectos essenciais de uma entidade do mundo real, ignorando detalhes supérfluos, e estruturar sua representação mental como uma classe genérica.
- **Classe**: Representação abstrata e estrutural de um grupo de objetos, definindo suas características técnicas (**atributos**) e suas funções operacionais (**métodos**).
- **Objeto (Instância)**: Realização concreta e única de uma classe na memória do computador, apresentando valores específicos e endereço próprio.
- **Herança**: Mecanismo que permite criar novas classes (subclasses/filhas) baseadas em classes preexistentes (superclasses/pais), herdando seus atributos e comportamentos sem duplicidade de código.
- **Encapsulamento**: Prática de ocultar detalhes de implementação interna e proteger o estado dos atributos contra acessos externos diretos, expondo apenas interfaces ou métodos públicos de manipulação (\(+\) para atributos/métodos públicos; \(-\) para atributos/métodos privados).
- **Polimorfismo**: Capacidade de que uma mesma operação tenha comportamentos e modos de atuação distintos e especializados em subclasses diferentes.

#### Classificação dos Diagramas UML (UML 2.5.1 fornece 13 diagramas)

```
                       Diagramas UML
                             |
         +-------------------+-------------------+
         |                                       |
Diagramas Estruturais               Diagramas Comportamentais
(Organização Estática)              (Dinâmica e Fluxos de Informações)
         |                                       |
  - Classes                         - Casos de Uso
  - Pacotes                         - Atividades
  - Componentes                     - Máquina de Estados
  - Instalação                      - Diagramas de Interação
  - Objetos                             - Sequência (Temporal)
  - Estrutura Composta                  - Comunicação (Estrutural)
                                              - Tempo
                                              - Visão Geral de Interação
```

#### Elementos do Diagrama de Casos de Uso

- **Atores**: Entidades externas (pessoas, outros sistemas, hardware integrado) que interagem com o sistema de forma direta e possuem metas específicas. São representados graficamente pelo símbolo do _boneco magro_ (_stick figure_).
- **Casos de Uso**: Elipses contendo descrições concisas das funcionalidades cruciais oferecidas aos atores.
- **Relacionamentos de Casos de Uso**:
    - _Inclusão (\(\langle\langle include \rangle\rangle\))_: Dependência obrigatória. Um caso de uso chama o outro como sub-rotina para evitar redundâncias na especificação de passos comuns.
    - _Extensão (\(\langle\langle extend \rangle\rangle\))_: Fluxo opcional ou condicional que só é acionado se circunstâncias específicas forem atendidas.
    - _Generalização/Especialização_: Relação de herança onde casos de uso especializados herdam os comportamentos e dependências de um caso de uso genérico pai.

#### Elementos do Diagrama de Atividades

- **Nó Inicial e Nó Final**: Indicam, respectivamente, o início do fluxo (círculo preenchido) e o término da atividade (círculo preenchido circundado por anel vazio).
- **Ações / Atividades**: Passos ou tarefas atômicas executadas, representadas por retângulos arredondados.
- **Fluxo de Controle e Fluxo de Objetos**: Indicam o direcionamento sequencial das ações e a transferência física de objetos e dados entre nós.
- **Nó de Decisão (Losango)**: Bifurcação que avalia condições de guarda escritas entre colchetes para decidir qual rota do algoritmo seguir.
- **Fork (Bifurcação em Barra)**: Divide um único fluxo de controle em duas ou mais atividades concorrentes/paralelas.
- **Join (Sincronização em Barra)**: Junta múltiplos fluxos de controle paralelos, impedindo a progressão do processo até que todas as vertentes paralelas estejam completamente concluídas.
- **Swimlanes (Partições)**: Divisões horizontais ou verticais para organizar graficamente as atividades sob a responsabilidade de papéis organizacionais distintos.

#### Elementos do Diagrama de Classes

- **A Classe**: Retângulo dividido em três compartimentos verticais: (1) Nome da classe, (2) Atributos com suas tipagens e níveis de visibilidade, (3) Métodos (assinaturas de operações e retornos).
- **Estereótipos**: Mecanismos de classificação de elementos lógicos:
    - \(\langle\langle entity \rangle\rangle\): Classe persistente para armazenamento de dados.
    - \(\langle\langle control \rangle\rangle\): Classe que processa lógica interna e regras de negócio.
    - \(\langle\langle boundary \rangle\rangle\): Classe de interface para fronteira de comunicação com o exterior.
- **Relacionamentos Estruturais entre Classes**:
    - _Associação_: Relacionamento lógico genérico entre instâncias.
    - _Dependência_ (linha tracejada com seta): Relacionamento semântico fraco, onde uma modificação na classe independente afeta diretamente a classe dependente.
    - _Agregação_ (losango vazio apontando para o pai): Relação de "todo-parte" onde a classe filha (parte) pode existir de forma independente da existência da classe pai (todo).
    - _Composição_ (losango preenchido apontando para o pai): Relação forte de copropriedade. Se a classe pai (todo) for excluída, todas as suas classes filhas associadas (partes) são destruídas automaticamente.
    - _Generalização/Especialização_ (seta vazada apontando para a superclasse): Herança estrutural pura de atributos e métodos.
    - _Multiplicidade_: Notações numéricas nas pontas das associações indicando quantas instâncias podem participar do relacionamento (ex.: \(1 \rightarrow 0..*\)).

---

## Conceitos que não posso confundir

|Conceito A|Conceito B|Diferença Crucial|
|:--|:--|:--|
|**Requisito Funcional (RF)**|**Requisito Não Funcional (RNF)**|O RF detalha **o que** o sistema faz (comportamento e ações lógicas); o RNF impõe restrições de qualidade sobre **como** o sistema faz (desempenho, tecnologia, segurança, usabilidade).|
|**Associação de Inclusão (Include)**|**Associação de Extensão (Extend)**|O _Include_ indica uma dependência **obrigatória** (sempre executa o caso incluído ao iniciar o caso pai); o _Extend_ indica um comportamento **opcional ou condicional** (só executa em circunstâncias específicas).|
|**Visão Funcional**|**Visão de Processos Ponta a Ponta**|A funcional é estruturada de forma **vertical e hierárquica por departamentos isolados (silos)**; a de processos é estruturada de forma **horizontal e interfuncional, focando no fluxo contínuo de valor ao cliente**.|
|**Ciclo de Vida do Produto**|**Modelo do Ciclo de Vida de Desenvolvimento**|O ciclo do produto engloba todas as fases de sua existência de mercado (Concepção, Crescimento, Maturidade e Declínio); o modelo de desenvolvimento é a **metodologia técnica estruturada para a criação do software** (Cascata, Incremental, etc.).|
|**Agregação (Classes)**|**Composição (Classes)**|Na agregação, a classe parte **pode existir sem o todo** (relação fraca); na composição, a parte **deixa de existir se o todo for destruído** (relação forte de dependência existencial).|
|**Diagramas Estruturais**|**Diagramas Comportamentais**|Os estruturais modelam a **organização estática** das partes lógicas do sistema (classes, arquivos, hardware); os comportamentais modelam a **dinâmica operacional e a troca temporal de eventos e dados**.|
|**BPM**|**BPMS**|O BPM é a **abordagem metodológica e gerencial** de processos; o BPMS é a **plataforma ou suíte de software tecnológica que executa, automatiza e monitora** os processos de BPM.|

---

## Pontos importantes para prova

1. **Curva de Defeitos de Software**: Lembre-se de que o software não se desgasta como o hardware. Ele se deteriora devido ao impacto de alterações sucessivas. Picos na curva real de defeitos são gerados por **efeitos colaterais** introduzidos no momento de alterações lógicas.
2. **Relação de herança na UML**: Representada por uma linha com **seta de ponta fechada vazada** apontando para a classe pai (superclasse).
3. **Encapsulamento de Atributos**: Na modelagem de classes, a visibilidade restrita ou privada é demarcada com o caractere de subtração (\(-\)), impedindo alterações externas diretas sobre a informação e garantindo a integridade dos dados através de métodos de encapsulamento (\(+\)).
4. **Métricas de RNF**: Para a prova, um requisito não funcional deve ser sempre **mensurável**. Use métricas formais: transações/segundo (velocidade), megabytes/RAM (tamanho), horas de treinamento (usabilidade), tempo médio para falhar (confiabilidade), tempo de restabelecimento (robustez) e número de sistemas operacionais suportados (portabilidade).
5. **Atores não são Usuários**: Ator é uma entidade que interage no contexto de um papel lúdico exclusivo na execução do caso de uso. Uma única pessoa física (usuário) pode assumir vários papéis de atores lógicos diferentes em momentos distintos de interação operacional.
6. **CMMI de Processos de Negócio**: Grave os cinco níveis de maturidade organizacionais (1 - Inicial, 2 - Gerenciado, 3 - Definido, 4 - Gerenciado Quantitativamente, 5 - Em Otimização).
7. **Metas SMART**: A sigla representa os cinco pilares essenciais na definição de indicadores estratégicos: Específico (S), Mensurável (M), Atingível (A), Relevante (R) e Temporal (T).
8. **Gateways em BPMN**: Lembre-se da diferença entre os desvios. O **XOR baseado em dados** toma a decisão internamente por dados preenchidos no sistema. O **XOR baseado em eventos** depende de um disparador de mensagem externa ou de uma resposta enviada de fora do pool.

---

## Revisão rápida

```
                        RESUMO DE MEMORIZAÇÃO

[SOFTWARE] = Instruções + Estruturas de Dados + Documentação
[DESGASTE] -> Hardware sofre desgaste FÍSICO; Software sofre deterioração LÓGICA

[PROCESSOS DE SOFTWARE]
- Sommerville: Especificação, Projeto/Implementação, Validação, Evolução
- Pressman: Comunicação, Planejamento, Modelagem, Construção, Entrega

[PROCESSOS DE NEGÓCIO]
- Classificação: Primários (valor ao cliente), Suporte (internos), Gerenciamento
- Decomposição: Macroprocesso -> Processo -> Subprocesso

[REQUISITOS]
- Funcionais (RF): O que o sistema faz (Ações)
- Não Funcionais (RNF): Restrições (JAVA, 2 seg) - Devem ser MENSURÁVEIS
- Engenharia: Concepção -> Elicitação -> Elaboração -> Negociação -> Especificação -> Validação -> Gerenciamento
- Rastreabilidade: Trás (Backward - Origem), Frente (Forward - Artefatos), Horizontal (Relações)

[UML - PARADIGMA OO]
- Pilares: Abstração, Classe, Objeto, Herança, Encapsulamento, Polimorfismo
- Diagramas Estruturais: Classes, Pacotes, Componentes, Instalação, Objetos, Estrutura Composta
- Diagramas Comportamentais: Casos de Uso, Atividades, Máquina de Estados, Sequência
- Casos de Uso: Include (Obrigatório), Extend (Opcional sob condição)
- Atividades: Forks (Paralelismo), Joins (Sincronização), Decisão (Losango)
- Classes: Associações, Dependências, Agregações (Separadas), Composições (Dependentes)
```

---