[[EXEMPLOS-PRÁTICOS DE ENGENHARIA DE SOFTWARE]]
#ASSUNTO

## Conceitos principais

- **Engenharia de Software**: Processo que inclui uma série de métodos e ferramentas que permitem aos profissionais criar software de excelente qualidade. Segundo a IEEE Computer Society, é a prática de aplicar abordagens sistemáticas, disciplinadas e quantificáveis para o desenvolvimento, a operação e a manutenção de software.
- **Software**: Composto de instruções executáveis que realizam funções específicas, estruturas de dados que permitem a manipulação de informações e a documentação relacionada ao sistema.
- **Crise do Software**: Período difícil nas décadas de 1960 e 1970, caracterizado pela incerteza, imprecisão de estimativas de custo/tempo e pela incapacidade de entregar projetos no prazo, no orçamento e com a qualidade esperada.
- **Garantia de Qualidade (SQA)**: Abordagem sistemática e proativa voltada à melhoria contínua de processos e produtos relacionados ao desenvolvimento de software, assegurando que as atividades estejam planejadas, implementadas e monitoradas de forma eficaz.
- **Verificação e Validação (V&V)**: Processos de garantia de qualidade. A **Verificação** busca garantir a construção correta do produto (atendendo às especificações técnicas predefinidas). A **Validação** busca garantir que o produto certo seja construído (satisfazendo às reais necessidades e expectativas do cliente).
- **Refatoração**: Modificação ou otimização do código sem alterar seu comportamento externo, servindo como uma prática contínua para melhoria interna do design do software.
- **Débito Técnico**: Custos invisíveis associados ao adiamento de atividades essenciais, como a documentação e a refatoração. Assim como os juros financeiros, o débito técnico aumenta ao longo do tempo se não for resolvido precocemente.

---

## Conteúdo explicado

### 1. Princípios da Engenharia de Software (SWEBOK/IEEE)

O SWEBOK (IEEE) identifica princípios estruturais para organizar os processos e padronizar soluções:

1. **Organização Hierárquica**: Apresentar os componentes de uma solução ou elementos de um problema em formato hierárquico, detalhado progressivamente em cada nível.
2. **Formalidade**: Abordagem rigorosa e padronizada na resolução de problemas.
3. **Completeza**: Garantia de que todos os elementos de um problema foram completamente contemplados na solução proposta.
4. **Dividir para Conquistar**: Divisão de problemas complexos em partes menores e gerenciáveis para criar soluções modulares.
5. **Ocultação (Information Hiding)**: Cada módulo de software deve ter acesso apenas às informações estritamente necessárias para sua operação, ocultando detalhes de implementação que sejam desnecessários para os outros componentes.
6. **Localização**: Agrupamento lógico de itens fortemente relacionados em um sistema.
7. **Integridade Conceitual**: Engenheiros de software devem seguir uma filosofia e arquitetura de projeto que sejam consistentes em todo o sistema.
8. **Abstração**: Concentração em isolar os aspectos essenciais de um problema específico, adiando questões secundárias ou relacionadas para um momento posterior.

### 2. Modelos de Processos de Desenvolvimento de Software

Os modelos tradicionais surgiram como respostas à "Crise do Software". Dividem-se em tradicionais (prescritivos) e ágeis:

#### A. Modelos Tradicionais (Prescritivos)

- **Modelo Cascata (Ciclo de Vida Clássico)**:
    - _Definição_: Abordagem estritamente linear e sequencial, em que cada fase deve ser totalmente concluída antes do início da seguinte.
    - _Fases_: Comunicação \(\rightarrow\) Planejamento \(\rightarrow\) Modelagem \(\rightarrow\) Construção \(\rightarrow\) Entrega.
    - _Aplicabilidade_: Eficaz para projetos com requisitos claros, bem definidos e estáveis.
    - _Desvantagem_: Baixa flexibilidade para acomodar mudanças de requisitos ao longo do projeto.
- **Modelo Incremental**:
    - _Definição_: O desenvolvimento é fracionado em iterações e o software é entregue gradualmente em incrementos operacionais (versões funcionais menores).
    - _Funcionamento_: Cada incremento adiciona novas funcionalidades ao produto, sendo construído sobre os incrementos anteriores.
    - _Aplicabilidade_: Excelente para projetos em que não é viável detalhar todos os requisitos de início e em que se busca um rápido retorno de investimento por meio de entregas funcionais antecipadas.
- **Modelo Espiral**:
    - _Definição_: Abordagem evolucionária de desenvolvimento em incrementos por meio de iterações ("espirais"), com foco proativo na análise e gestão de riscos.
    - _Funcionamento_: Cada ciclo engloba definição de objetivos, análise de riscos, desenvolvimento e teste de protótipos, e planejamento da próxima iteração.
    - _Aplicabilidade_: Ideal para sistemas de grande porte, complexos e com alta incerteza inicial.

### 3. Métodos Ágeis

O **Manifesto Ágil** (2001) mudou o foco do desenvolvimento de software, priorizando indivíduos e interações (sobre processos e ferramentas), software funcional (sobre documentação abrangente), colaboração com clientes (sobre negociações contratuais) e adaptabilidade a mudanças (sobre seguir um plano rígido).

#### A. Framework Scrum

Organiza o trabalho em ciclos curtos e regulares de tempo chamados **Sprints** (com duração típica de duas a quatro semanas).

- **Papéis**:
    - _Product Owner (PO)_: Figura central na definição do produto; responsável por identificar e priorizar as funcionalidades críticas no Product Backlog.
    - _Scrum Master_: Facilitador especializado no framework; atua garantindo a correta aplicação do Scrum e agindo como moderador para remover impedimentos.
    - _Scrum Team_: Grupo multidisciplinar de desenvolvimento (normalmente composto de 6 a 10 membros), auto-organizado e sem divisões rígidas de funções.
- **Artefatos**:
    - _Product Backlog_: Lista dinâmica e evolutiva que contém todas as funcionalidades desejadas para o produto.
    - _Sprint Backlog_: Relação de tarefas selecionadas do Product Backlog que a equipe se compromete a realizar durante a Sprint atual.
    - _Quadro Scrum_: Painel visual matricial estruturado em colunas para monitorar o progresso ("A Fazer", "Em Andamento/Em Execução" e "Concluído") por meio de post-its.
- **Cerimônias**:
    - _Sprint Planning (Planejamento)_: Reunião inicial na qual o PO e o time definem o que será trabalhado durante a Sprint.
    - _Daily Stand-up (Reunião Diária)_: Encontro diário rápido de 15 minutos em que o time alinha o progresso (o que foi feito, o que será feito hoje e impedimentos).
    - _Sprint Review (Revisão)_: Apresentação prática dos incrementos de software funcionando aos clientes e stakeholders para coleta de feedback.
    - _Sprint Retrospective (Retrospectiva)_: Encontro focado no aprimoramento contínuo dos processos internos do time.

#### B. Extreme Programming (XP)

Metodologia ágil com foco rigoroso nas práticas de engenharia de software e na qualidade do código-fonte. Divide suas ações em quatro áreas fundamentais:

- **Planejamento ("Jogo do Planejamento")**: Histórias de usuário são detalhadas em fichas pelo cliente e priorizadas por valor comercial. Os desenvolvedores estimam o custo (em semanas) e medem a "velocidade do projeto" para prever versões futuras.
- **Projeto (Design)**: Adere ao princípio **KISS (Keep It Simple, Stupid)**, mantendo a simplicidade absoluta no design do software. Utiliza cartões **CRC** (Classe-Responsabilidade-Colaborador) como única ferramenta de modelagem orientada a objetos. Aplica **Refatoração** constante do código para otimizar sua estrutura interna.
- **Codificação**: Defende a **Programação em Pares** (dois programadores trabalham em uma mesma máquina escrevendo e revisando código simultaneamente) e a **Integração Contínua** frequente para evitar problemas de compatibilidade.
- **Testes**: Exige a escrita de testes de unidade automatizados antes de começar a codificar, testes de regressão automatizados frequentes e testes de aceitação definidos pelo próprio cliente.

### 4. Engenharia de Requisitos

Processo que engloba a identificação, análise, documentação e validação das funcionalidades e limitações de um sistema de software.

#### A. Níveis de Requisitos

- **Requisitos de Usuário**: Especificações abstratas escritas em linguagem natural e complementadas por diagramas simples, descrevendo os serviços que o sistema deve fornecer aos clientes e as restrições operacionais.
- **Requisitos de Sistema**: Descrição técnica minuciosa de todas as funções, serviços, limitações operacionais e comportamentos de hardware, servindo como modelo de desenvolvimento e base contratual.

#### B. Classificação de Requisitos

- **Requisitos Funcionais (RF)**: Especificam as ações concretas e comportamentos diretos que o sistema deve realizar ao receber entradas. _Exemplos_: pesquisar livros por título/autor, autenticar usuários, gerar relatórios de vendas em PDF e enviar confirmações por e-mail.
- **Requisitos Não Funcionais (RNF)**: Restrições de caráter global impostas aos serviços oferecidos. Abrangem critérios de segurança, desempenho sistêmico, usabilidade, confiabilidade e interoperabilidade. _Exemplos_: tempo de resposta não superior a 2 segundos, compatibilidade entre navegadores e suporte para até 1000 acessos simultâneos.

#### C. Etapas do Processo de Engenharia de Requisitos (Espiral Iterativa)

1. **Estudo de Viabilidade**: Avalia se o sistema proposto atende aos objetivos estratégicos do negócio dentro do orçamento e prazos definidos.
2. **Elicitação e Análise**: Colaboração estreita com stakeholders para descobrir e negociar requisitos. Engloba descoberta, classificação, organização e priorização.
3. **Especificação**: Documentação formal dos requisitos utilizando notações como linguagem natural estruturada, diagramas da UML ou especificações matemáticas formais.
4. **Validação**: Verificação detalhada de validade, consistência, completude, realismo e verificabilidade das especificações. Utiliza técnicas como revisões de requisitos, prototipação operacional e geração de casos de teste.

### 5. Qualidade de Software e SQA

Garantir a qualidade implica aplicar processos eficazes para criar um produto útil com valor mensurável para desenvolvedores e usuários finais.

#### A. Níveis de Qualidade

1. **Organizacional**: Estabelece padrões de trabalho robustos para minimizar erros organizacionais.
2. **Projeto**: Adequação desses padrões por gestores, variando conforme a política da empresa.
3. **Planejamento**: Criação do plano de qualidade monitorado de forma imparcial.

#### B. Software Quality Assurance (SQA)

Abordagem sistemática e proativa com foco em prevenir defeitos em vez de apenas corrigi-los. Envolve auditorias formais, revisões de código, estabelecimento de métricas quantificáveis de conformidade e gestão unificada de mudanças.

#### C. Atributos da Qualidade de Produto (ISO 9126 / NBR 13596)

Define seis atributos principais de qualidade:

1. **Funcionalidade**: Adequação, acurácia, interoperabilidade, conformidade e segurança lógica contra acessos não autorizados.
2. **Confiabilidade**: Maturidade, tolerância a falhas e recuperabilidade.
3. **Usabilidade**: Inteligibilidade, apreensibilidade e atratividade das interfaces.
4. **Eficiência**: Comportamento de tempo e otimização de recursos de processamento.
5. **Manutenibilidade**: Analisabilidade, modificabilidade, estabilidade sistêmica pós-alterações e testabilidade.
6. **Portabilidade**: Adaptabilidade a novos ambientes, facilidade de instalação e conformidade de portabilidade.

#### D. Modelos de Maturidade e Gestão de Processos

- **ISO 9000**: Foco em governança corporativa baseado em oito princípios de gestão: foco no cliente, liderança, envolvimento de pessoas, abordagem por processos, visão sistêmica, melhoria contínua, tomada de decisões baseada em dados e benefícios com fornecedores.
- **ISO 9001**: Foco em tarefas administrativas corporativas, como controle documental rigoroso, auditorias internas, ações preventivas e tratamento de não conformidades.
- **CMMI (Capability Maturity Model Integration)**: Modelo para aprimorar processos de desenvolvimento de software de forma contínua. Apresenta duas representações: por Estágios (cinco níveis lineares estruturados de maturidade) ou Contínua (perfil granular de capacidade avaliado de zero a cinco para áreas de processos individuais).
- **MPS.BR**: Iniciativa nacional focada na melhoria e avaliação de processos, financeiramente acessível para micro, pequenas e médias empresas. É estruturada em sete níveis de maturidade progressiva (do nível G - Inicial ao nível A - Otimizado).

### 6. Testes de Software

Mecanismo de verificação dinâmica realizado em um conjunto finito de casos de teste em busca de comportamentos inesperados e erros sistêmicos.

#### A. Estratégia Caixa Preta (Teste Funcional)

Baseia-se unicamente nas especificações funcionais do software e nos requisitos de negócios. O testador avalia o comportamento externo do sistema (valores de entrada versus resultados de saída) sem necessitar de acesso ao código-fonte lógico.

#### B. Estratégia Caixa Branca (Teste Estrutural)

Exige acesso completo ao código-fonte e bancos de dados para submeter a estrutura lógicas e caminhos de controle internos a ferramentas automatizadas de avaliação.

- **Teste do Caminho Básico**:
    - Transforma o código procedural em um **Grafo de Fluxo** (em que os nós representam blocos sequenciais de código e as arestas representam as ramificações de controle de fluxo).
    - Determina os caminhos lógicos independentes que percorrem pelo menos uma nova aresta do grafo.
    - O cálculo da **Complexidade Ciclomática (\(V(G)\))** estabelece matematicamente o limite superior de casos de teste necessários para que todos os comandos lógicos do programa sejam executados pelo menos uma vez. É calculada de três formas equivalentes:
        1. $V(G) = \text{Número de regiões do grafo}$.
        2. $V(G) = E - N + 2$ (Arestas $E$ menos Nós $N$, somado com $2$).
        3. $V(G) = P + 1$ (Nós Predicados de decisão $P$ mais $1$).

#### C. Testes Baseados em Modelos (TBM)

Uso de modelos para descrever as ações estruturadas e automatizar a geração de scripts de teste.

- **Máquinas de Estados Finitos (MEF)**: Estados e transições são mapeados explicitamente no modelo para orientar a geração de caminhos de teste.
- **Métodos Clássicos**:
    - _Método TT (Teste de Transição)_: Garante a cobertura de todas as transições do modelo MEF.
    - _Método UIO (Unique Input/Output)_: Baseado em sequências lógicas de inputs e outputs únicos.
    - _Método W_: Algoritmo avançado que maximiza a cobertura de todos os estados representados no modelo MEF.
    - _Método DS (Domínio de Sequências)_: Baseado na identificação de classes de equivalência para testar domínios.

#### D. Desenvolvimento Orientado a Testes (TDD)

Incentiva o desenvolvedor a escrever testes unitários automatizados de forma contínua _antes_ da codificação lógica de produção. Baseia-se no ciclo **Vermelho-Verde-Refatorar**:

1. **Vermelho (Red)**: Escreve-se um teste automatizado destinado a falhar propositalmente (visto que o recurso ainda não foi codificado).
2. **Verde (Green)**: Escreve-se estritamente o código de produção mínimo suficiente para fazer o teste passar sem falhar.
3. **Refatorar (Refactor)**: Otimiza-se o código de produção (removendo duplicações de código, melhorando legibilidade) garantindo que toda a base de testes unitários permaneça verde.

- _Mock Objects_: Objetos simulados criados por meio de frameworks para imitar o comportamento de componentes reais complexos (como conexões pesadas com bancos de dados), agilizando a execução em memória volátil.

### 7. Gerenciamento de Configuração de Software (GCS)

Conjunto de práticas que controlam e notificam as correções, extensões e adaptações aplicadas ao software durante todo o seu ciclo de vida.

#### A. Conceitos Fundamentais

- **Repositório**: Local unificado onde todos os arquivos de código-fonte, dados e documentações ficam armazenados e podem ser acessados de forma controlada.
- **Baseline (Linha de Base)**: Um conjunto de itens de configuração formalmente aprovados e acordados que serve como ponto de partida estável para iterações futuras. Qualquer alteração em baselines requer procedimentos formais de controle de mudanças.
- **Branches (Ramificações)**: Linhas secundárias criadas no repositório a partir da linha principal (mainline) que permitem o isolamento de desenvolvedores trabalhando simultaneamente em novas funcionalidades.
- **Merge**: Operação de reintegração e fusão de modificações paralelas de volta para a mainline.
- **Tags (Etiquetas)**: Identificadores fixos inseridos no repositório para marcar pontos estáveis específicos, como baselines ou entregas parciais formais (releases).

#### B. Ferramentas de Configuração

- **Git**: Sistema descentralizado gratuito e open-source caracterizado pela segurança. Possui avançado modelo de branching local e aplica verificações rigorosas baseadas em checksum criptográfico a cada commit para assegurar a integridade total dos arquivos.
- **CVS (Concurrent Versions System)**: Ferramenta histórica centralizada. Cada alteração gera um número sequencial único de versão (revisão) de forma incremental (ex: 1.1, 1.2). Utiliza arquivos RCS caracterizados pela extensão ',v' contendo registros estruturados de modificações e usuários.

### 8. Manutenção e Evolução de Software

O envelhecimento sistêmico do software é inevitável e exige evolução coordenada para manter a sua conformidade.

#### A. Tipos de Envelhecimento

- _Falha de Adequação_: Ocorre por erro na adaptação dos requisitos estruturais a novos ambientes, acarretando perda de integridade funcional (ex: incompatibilidade de drivers pós-atualização de sistema operacional).
- _Falha na Mudança_: Quando uma nova implementação ou atualização técnica afeta e corrompe outros recursos que já funcionavam perfeitamente.

#### B. Tipos de Manutenção

- **Manutenção Corretiva**: Destinada a corrigir erros, bugs estruturais ou degradantes relatados no código de produção.
- **Manutenção Adaptativa**: Modificações necessárias para ajustar o software a mudanças físicas e lógicas externas (mudanças de leis, novas tecnologias de mercado ou de pagamentos).
- **Manutenção Evolutiva**: Focada em aprimorar o software inserindo novos recursos de negócios de forma contínua.

#### C. Modernização de Sistemas Legados

- **Engenharia Reversa**: Processo analítico de reconstrução lógica focado em examinar e recuperar a estrutura de funcionalidades e regras de negócios a partir de seu código-fonte legível, sem alterar a sua arquitetura base. É analisada em quatro níveis: implementação, estrutural, funcional e de domínio.
- **Reengenharia de Software**: Processo de reimplementação, modificação estrutural e otimização controlada de sistemas legados de alta criticidade. Visa atualizar pilhas tecnológicas obsoletas, refatorar códigos monolíticos complexos, modernizar interfaces de usuário (UX/UI) e otimizar gargalos para baratear futuras manutenções.

### 9. Gestão de Riscos (RMMM)

Qualquer risco sistêmico possui duas características mandatórias fundamentais: **Incerteza** (a probabilidade de ocorrer é maior que 0% e menor que 100%) e **Perda** (as consequências indesejadas e prejuízos que ocorrerão caso o risco de fato se concretize).

#### A. Classificação de Riscos

- _Riscos de Projeto_: Ameaças diretas ao orçamento, equipe e cronograma (atrasos na entrega).
- _Riscos Técnicos_: Ameaças à qualidade do código-fonte, arquitetura lógica ou compatibilidade física de infraestrutura.
- _Riscos de Negócio_: Ameaçam a viabilidade comercial do produto desenvolvido e fundos operacionais internos.
- _Riscos Conhecidos, Previsíveis e Imprevisíveis_: Classificados de acordo com a facilidade de antecipação e experiências adquiridas em projetos passados.

#### B. Processo RMMM (Mitigação, Monitoramento e Gestão)

- **Mitigação (Prevenção)**: Adoção sistemática de estratégias e atitudes preventivas proativas para reduzir drasticamente a probabilidade de um risco acontecer. _Exemplo_: para o risco de alta rotatividade de pessoal, pode-se padronizar os produtos e designar substitutos.
- **Monitoramento**: Acompanhamento rigoroso e contínuo de indicadores que apontam as tendências e evolução das probabilidades de cada risco ao longo do ciclo de vida.
- **Gestão de Riscos e Planos de Contingência**: Execução imediata de ações e planos de contingência previamente acordados caso as estratégias de mitigação falhem e o risco de fato se materialize.
- **Regra de Pareto (80-20)**: Recomenda concentrar os esforços de gestão de risco prioritariamente nos riscos mais críticos (que representam cerca de 20% das ameaças totais identificadas).
- _RIS (Risk Information Sheets)_: Formulários unificados de controle individual de risco, que substituem documentos formais volumosos de RMMM, sendo frequentemente mantidos em bancos de dados integrados de nuvem.

### 10. Medição de Software e Reúso

- **Métricas baseadas em metas (GQM do SEI)**: O Software Engineering Institute (SEI) indica uma estratégia de 10 etapas para implantar programas de medição orientados a metas comerciais e de engenharia de software de forma integrada, mapeando de forma estruturada: Meta de Negócio \(\rightarrow\) Questão \(\rightarrow\) Submeta de Engenharia \(\rightarrow\) Métricas de Medição.
- **Reúso de Software**: Prática sistemática de aproveitar partes e componentes lógicos de sistemas prévios para o desenvolvimento acelerado de novas soluções, garantindo redução de custos e maiores índices de confiabilidade. O reuso pode se dar nos níveis de sistemas, aplicações, componentes lógicos ou reuso de objetos e funções.
- **Reúso de Conceito**: Reaproveitamento de ideias de projeto estruturais abstratas, algoritmos genéricos ou padrões (Design Patterns) em vez do código em si.
- **Frameworks de Aplicação**: Conjunto robusto e integrado de classes abstratas e concretas que desenham uma arquitetura reaproveitável estrutural comum a uma família de aplicações de domínio similar. O desenvolvedor as estende e especializa de acordo com os requisitos específicos de sua aplicação.

---

## Conceitos que não posso confundir

|Conceito A|Conceito B|Diferença Crucial|
|:--|:--|:--|
|**Erro (Error)**|**Defeito (Defect)**|O **Erro** é uma execução incorreta ou ato humano/sistêmico, gerando resultados que não refletem a verdade. O **Defeito** representa um erro de lógica, anomalia física latente ou inconsistência inserida no código-fonte.|
|**Defeito (Defect)**|**Falha (Fault/Failure)**|O **Defeito** permanece estático e oculto nas linhas do código de um programa. A **Falha** é a manifestação dinâmica de um ou mais erros e defeitos no sistema durante a execução do programa, visível ao usuário.|
|**Verificação**|**Validação**|A **Verificação** avalia se os artefatos de cada fase estão em conformidade com as restrições e modelos técnicos estipulados anteriormente ("_estamos construindo o produto de forma correta?_"). A **Validação** avalia ao final se o software atende fielmente aos objetivos práticos do cliente ("_estamos construindo o produto correto?_").|
|**Requisitos Funcionais**|**Requisitos Não Funcionais**|Os **Funcionais** mapeiam de forma lógica ações específicas, comportamentos e serviços diretos de entrada e saída que o sistema deve cumprir. Os **Não Funcionais** limitam o desempenho, a usabilidade e a infraestrutura, aplicando-se de forma global à arquitetura do produto.|
|**Engenharia Reversa**|**Reengenharia**|A **Engenharia Reversa** destina-se unicamente ao mapeamento, análise abstrata e recuperação de modelos de design a partir do código legível, sem realizar modificações funcionais. A **Reengenharia** modifica, reorganiza e reconstrói as bases do software para modernizar o sistema.|
|**Método Cascata**|**Modelo Incremental**|O **Cascata** exige sequencialidade linear rígida, exigindo que cada etapa termine antes da próxima e com requisitos totalmente definidos. O **Incremental** fraciona o produto em iterações menores, entregando incrementos parciais e funcionais continuamente.|
|**Métricas Dinâmicas**|**Métricas Estáticas**|As **Dinâmicas** avaliam propriedades operacionais mensuradas exclusivamente com o código do software em execução (ex: número de falhas por hora, tempo de processamento). As **Estáticas** analisam as representações estruturais físicas de artefatos, projetos ou código estático (ex: número de linhas de código, complexidade ciclomática).|

---

## Pontos importantes para prova

1. **Regra de Ouro dos Testes de Ciclos (Loops) de Caixa Branca**:
    - _Ciclos Simples_: Para cobrir adequadamente um ciclo que aceita no máximo \(n\) passadas, os cenários de teste projetados devem testar: pular o ciclo completamente; passar 1 única vez; passar 2 vezes; passar \(m\) vezes (\(m < n\)); passar \(n-1\), \(n\) e \(n+1\) passadas pelo ciclo.
    - _Ciclos Aninhados_: Para conter a explosão exponencial de testes, deve-se: começar pelo ciclo mais interno (deixando os externos nos valores mínimos de iteração); aplicar a técnica de testes de ciclos simples ao mais interno; prosseguir para o próximo externo mantendo os mais externos nos mínimos e os aninhados internos em valores típicos.
2. **Cálculo Ciclomática Estrutural ($V(G)$)**: Sempre calcular $V(G)$ por três abordagens equivalentes no grafo de fluxo para validação:
    - \(V(G) = \text{Número de regiões do grafo}\).
    - \(V(G) = E - N + 2\) (Arestas \(E\) menos Nós \(N\), somado com \(2\)).
    - \(V(G) = P + 1\) (Nós Predicados \(P\) mais \(1\)).
3. **Mitos Clássicos do Desenvolvimento de Software (Mitos de Gestão/Técnicos)**:
    - Adicionar programadores tardiamente a um projeto atrasado piora os atrasos devido a custos adicionais e complexidades na comunicação estrutural de equipe.
    - O software que começou a rodar funcionalmente não está imediatamente pronto para liberação; testes rigorosos de regressão, usabilidade, aceitação e documentação estrutural são mandatórios.
    - Qualificações sólidas em codificação e programação pura não correspondem a habilidades efetivas de gestão de projetos.
4. **Técnicas de Auditoria de TI baseadas em Computador**:
    - _Ao redor do computador_: Restringe-se a validar se os inputs conferem com os outputs correspondentes sem acessar as lógicas de processamento ou a CPU.
    - _Através do computador_: Utiliza ferramentas (como "test data") para simular inputs reais e fictícios para monitorar ativamente o processamento dentro da infraestrutura lógica.
    - _Com o computador_: Usa plenamente as capacidades analíticas e matemáticas da CPU para gerar amostras estatísticas, automatizar auditorias cruzadas (TAAC/CAAT) e integrar relatórios.
5. **Etapas do Processo de Teste de Software**: Dividido formalmente em: Planejamento $\rightarrow$ Projeto de Casos de Teste $\rightarrow$ Execução com Casos de Teste $\rightarrow$ Análise de Resultados.
6. **Estrutura Obrigatória de um Caso de Teste Completo**: Nome do Caso de Teste, Pré-condições de ambiente, Passos de execução detalhados, Dados de teste/entrada, Resultado esperado e Critérios para a identificação de falhas.

---

## Revisão rápida

- **Fundamentos SWEBOK**: Hierarquia, Formalidade, Completeza, Dividir para Conquistar, Ocultação, Localização, Integridade Conceitual, Abstração.
- **Modelos**: Cascata (linear/estático), Incremental (gradual/iterativo), Espiral (riscos/evolucionário).
- **Manifesto Ágil**: Pessoas, software funcional, colaboração próxima e adaptabilidade rápida.
- **Scrum**: Sprints, PO, Scrum Master, Team. Reuniões: Daily, Planning, Review e Retrospective.
- **XP**: KISS, Cartões CRC, refatoração, pair programming, integração contínua e TDD.
- **Requisitos**: Funcionais (ações lógicas) e Não Funcionais (restrições físicas, segurança, dezenas de métricas quantificáveis).
- **Qualidade**: Níveis Organizacional, de Projeto e Planejamento. SQA foca em prevenção proativa.
- **ISO 9126**: Funcionalidade, Confiabilidade, Usabilidade, Eficiência, Manutenibilidade e Portabilidade.
- **CMMI e MPS.BR**: Modelos de melhoria contínua de processos organizacionais de software.
- **Testes**: Caixa Preta (funcional/inputs-outputs), Caixa Branca (estrutural/caminhos do código). TDD segue ciclo Red-Green-Refactor.
- **Controle de Versão (GCS)**: Repositório, Baselines (tags), Branches (linhas paralelas) e Merge (reintegração). Git (seguro/checksum).
- **Riscos**: Projeto, Técnico, Negócio. RMMM (Mitigação, Monitoramento, Gestão). Regra 80-20 (Pareto).
- **Evolução e Manutenção**: Corretiva, Adaptativa e Evolutiva. Modernização requer Engenharia Reversa (análise) e Reengenharia (reconstrução estrutural).
- **Métricas de Medição**: Processo (estratégico de longo prazo), Projeto (tático de monitoramento), Produto (previsão/atributos internos). GQM (SEI) orienta métricas por metas.

---
