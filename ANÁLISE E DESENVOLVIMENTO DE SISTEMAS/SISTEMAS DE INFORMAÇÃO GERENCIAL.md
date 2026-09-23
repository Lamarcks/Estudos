[[EXEMPLO-PRÁTICO DE SISTEMAS DE INFORMAÇÃO GERENCIAL]]
#ASSUNTO

## Conceitos principais

- **Dado**: Elemento bruto, isolado e desorganizado que, de forma individual, não possui valor para o processo de tomada de decisão.
- **Informação**: Conjunto de dados tratado, filtrado e criteriosamente ordenado de forma significativa, atuando diretamente na redução da incerteza e permitindo decisões mais assertivas.
- **Conhecimento**: Compreensão, interpretação e aplicação prática da informação de forma estratégica. Pode ser **tácito** (quando reside na mente dos indivíduos) ou **explícito** (quando está codificado em documentos, processos e sistemas).
- **Sistema de Informação (SI)**: Um conjunto integrado de componentes (hardware, software, dados e pessoal) que coleta, processa, armazena e distribui dados, transformando-os em informações úteis para suporte à gestão e à tomada de decisão.
- **Business Intelligence (BI)**: Conjunto de técnicas e estratégias voltadas a adquirir, armazenar, recuperar e interpretar dados históricos estruturados para monitorar o desempenho, identificar oportunidades/ameaças e apoiar decisões estratégicas.

---

## Conteúdo explicado

### 1. Fundamentos da Informação e Fluxo de Entrada, Processamento e Saída

A eficácia de um SIG está diretamente atrelada ao fluxo de dados estruturado em três etapas básicas:

#### A. Entradas de Dados

Representam a matéria-prima do sistema e classificam-se em:

1. **Dados Operacionais**: Dados internos gerados pelas atividades diárias da empresa (vendas, custos, inventário, recursos humanos).
2. **Dados Externos**: Informações de fora da organização (tendências de mercado, dados econômicos, demográficos e legislação).
3. **Informações de Outras Fontes Gerenciais**: Integração com ferramentas existentes como ERPs e CRMs.

**Métodos de Coleta de Dados**:

- _Automáticos_: Utilizam softwares e ferramentas digitais (sensores em máquinas, análise de tráfego web). Garantem velocidade e reduzem falhas humanas.
- _Manuais_: Inserção de dados por indivíduos (preenchimento de formulários). São mais suscetíveis a erros, porém necessários quando a automação é inviável.

#### B. Processamento de Dados

Conversão de dados brutos em informações por meio de coleta, limpeza, classificação e análise. Utiliza softwares como SGBDs, plataformas de BI, e técnicas avançadas como algoritmos de _machine learning_ e análise preditiva para identificar padrões ocultos em grandes volumes de dados.

#### C. Saídas de Informação

Disseminação das informações processadas em formatos acessíveis:

- **Relatórios e Sumários Executivos**: Visão geral do desempenho organizacional.
- **Dashboards de Controle (Painéis) e KPIs**: Indicadores de desempenho em tempo real que facilitam decisões ágeis.
- **Alertas e Notificações Automáticas**: Avisos sobre eventos críticos ou desvios operacionais.

**Tipologias de Relatórios Gerados**:

- _Rotina vs. Ad hoc_: Os de rotina são gerados regularmente (visão contínua); os _ad hoc_ são produzidos sob demanda para responder a dúvidas imediatas.
- _Sumários vs. Detalhados vs. Analíticos_: Sumários dão uma visão geral; detalhados aprofundam aspectos específicos; analíticos incluem interpretações e análises para dar suporte à tomada de decisões.
- _Exceção vs. Regulatórios_: Os de exceção destacam desvios fora do padrão de desempenho; os regulatórios atendem a exigências legais e normativas.

---

### 2. Infraestrutura de TI e Gestão de Dados

A infraestrutura de TI é a espinha dorsal física e lógica de suporte ao SIG. É composta por quatro elementos principais:

- **Hardware**: Equipamentos físicos (computadores, servidores, scanners, mídias de armazenamento).
- **Software**: Programas que dividem-se em _software de entrada_ (captura de dados), _software de análise_ (consultas e operações) e _software de saída_ (geração de relatórios, gráficos e painéis).
- **Dados**: Elemento vital armazenado e estruturado eficientemente.
- **Pessoal (Peopleware)**: Usuários, administradores e desenvolvedores do sistema, responsáveis por operar e interpretar os dados com inteligência.

#### Gestão de Bancos de Dados e Engenharia de Dados

Para garantir a integridade dos dados, as organizações utilizam um **Sistema de Gerenciamento de Banco de Dados (SGBD)**, software que atua como interface para criar, manipular, consultar e auditar o banco de dados (ex: Oracle, PostgreSQL, MySQL).

A estruturação ocorre em duas frentes:

1. **Modelagem de Dados**: Processo de definição da estrutura lógica e conceitual (como os dados se relacionam: modelo relacional, orientado a objetos, entidade-relacionamento).
2. **Design de Banco de Dados**: Definição física de armazenamento, indexação e planos de segurança.

**Processamento de Dados para Carga Estratégica**: Antes de alimentar os sistemas de decisão, os dados passam por cinco fases cruciais de manipulação:

- _Extração_: Coleta de dados brutos de fontes diversas (APIs, sensores, sistemas legados).
- _Adequação_: Conversão dos dados extraídos para um formato padronizado e comum.
- _Limpeza_: Detecção e correção de erros, dados duplicados, incompletos ou corrompidos.
- _Derivação_: Criação de novas variáveis a partir das existentes (ex: calcular idade a partir da data de nascimento).
- _Agregação_: Resumo e agrupamento de dados para simplificar análises (ex: consolidar vendas diárias em totais mensais).

```
[Fontes Diversas] ➔ [Extração] ➔ [Adequação] ➔ [Limpeza] ➔ [Derivação] ➔ [Agregação] ➔ [Data Warehouse]
```

#### Estruturas Analíticas Avançadas

- **Data Warehouse (DW)**: Depósito central de informações que armazena dados atuais e históricos de toda a empresa para alimentar inteligência analítica e de BI.
- **Big Data**: Conjunto de dados que apresenta as características dos **5 Vs**:
    - _Volume_: Quantidade massiva de dados gerada (terabytes/petabytes).
    - _Variedade_: Diversidade de formatos e fontes (textos, vídeos, áudios, sensores).
    - _Velocidade_: Geração e análise de dados em tempo real ou quase real.
    - _Veracidade_: Níveis de precisão, qualidade e confiabilidade dos dados.
    - _Valor_: Capacidade de gerar retornos práticos e insights significativos.
- **Data Mining (Mineração de Dados)**: Aplicação de métodos estatísticos, computacionais e algoritmos de inteligência artificial para descobrir padrões, regras de associação, anomalias e tendências preditivas não evidentes em grandes bases de dados.

---

### 3. Classificação e Tipos de Sistemas de Informação

Os sistemas de informação dividem-se hierarquicamente segundo o nível de decisão e o propósito que atendem dentro da organização:

|Sigla|Nome do Sistema|Nível Organizacional|Funcionalidades Principais|
|:--|:--|:--|:--|
|**SPT**|Sistema de Processamento de Transações|**Operacional**|Gerencia e registra as transações cotidianas rápidas e volumosas da empresa (vendas, estoque, pagamentos).|
|**SIG**|Sistema de Informação Gerencial|**Tático**|Coleta dados operacionais para fornecer relatórios estruturados, periódicos e documentos de apoio ao gerenciamento.|
|**SAD**|Sistema de Apoio à Decisão|**Tático / Estratégico**|Auxilia na resolução de decisões semiestruturadas e não estruturadas complexas, com simulações de cenários e modelos analíticos avançados.|
|**SIE**|Sistema de Informação Executiva|**Estratégico**|Fornece visões consolidadas de alto nível (dashboards, KPIs), permitindo monitorar tendências de mercado e o rumo do negócio a longo prazo.|

#### Novos Conceitos em Sistemas de Informação

- **Sistemas de Gestão do Conhecimento (SGC)**: Softwares e processos projetados para capturar, armazenar e disseminar a inteligência coletiva (conhecimento tácito e explícito) da empresa, reduzindo as perdas decorrentes de rotatividade de funcionários.
- **Sistemas Especialistas (SE)**: Aplicações de Inteligência Artificial que emulam o raciocínio, comportamento e julgamento de um expert humano em uma área restrita do conhecimento por meio de uma base de dados rica e um motor de regras lógicas.
- **Inteligência Artificial (IA) nos SIGs**: Envolve o uso de técnicas como _Aprendizado de Máquina (Machine Learning)_ (algoritmos que aprendem e melhoram com a experiência, usados em análises preditivas), _Processamento de Linguagem Natural (PLN)_ (chatbots, análise de sentimentos) e _Robótica inteligente_.

---

### 4. Sistemas Empresariais (Back-Office e Logística)

Os sistemas corporativos modernos visam integrar de forma unificada os departamentos das empresas, eliminando as "ilhas de informação".

```
                     ┌───────────┐
                     │    ERP    │  <-- Sistema Central Integrado
                     └─────┬─────┘
         ┌─────────────────┼─────────────────┐
   ┌─────┴─────┐     ┌─────┴─────┐     ┌─────┴─────┐
   │    WMS    │     │   SCMS    │     │    TMS    │
   │ Armazém   │     │ Suprimentos│     │Transporte │
   └───────────┘     └───────────┘     └───────────┘
```

#### A. ERP (Enterprise Resource Planning - Sistemas Integrados de Gestão)

Softwares integrados alimentados por um banco de dados centralizado que unifica os processos de finanças, recursos humanos, manufatura, logística e vendas. Reduz redundâncias e garante qualidade e acurácia de dados.

#### B. Linha de Planejamento de Produção (MRP I e MRP II)

- **MRP I (Material Requirement Planning)**: Focado no cálculo das necessidades de materiais para a produção. Responde de forma precisa a três perguntas básicas:
    1. _O que_ produzir?
    2. _Quanto_ produzir?
    3. _Quando_ produzir?
- **MRP II (Manufacturing Resource Planning)**: Evolução do MRP I que amplia o escopo para integrar todos os recursos de manufatura, incluindo capacidade de maquinários, planejamento financeiro, escala de pessoal e qualidade de processos. Responde a uma quarta pergunta fundamental: 4. _Como_ produzir?

#### C. Cadeia de Suprimentos (SCM, CRM, PRM e E-Procurement)

- **SCMS (Supply Chain Management System)**: Software que oferece uma visão holística e integrada que otimiza as transações desde a aquisição de matérias-primas com fornecedores até a entrega final ao consumidor.
- **CRM (Customer Relationship Management)**: Gestão integrada do relacionamento direto com os clientes em todos os canais de atendimento, fornecendo uma visão 360 graus para fidelização e vendas cruzadas.
- **PRM (Partner Relationship Management)**: Sistema voltado para gerenciar interações com parceiros externos de negócios (fornecedores, revendedores, distribuidores), focando na coordenação operacional ao longo da cadeia de valor.
- **E-Procurement**: Automação digitalizada dos processos de compras corporativas (com leilões reversos, gestão de catálogos e contratos eletrônicos) com o objetivo de reduzir custos operacionais e acelerar ciclos de aquisição.

#### D. Sistemas de Apoio Logístico (WMS e TMS)

- **WMS (Warehouse Management System)**: Sistema voltado para gerir as operações físicas internas de um armazém ou centro de distribuição (recebimento, endereçamento automático de estoque, controle de inventário por radiofrequência - RFID, processos de _picking_ e _packing_ e expedição).
- **TMS (Transportation Management System)**: Sistema responsável por controlar e otimizar os fluxos de transportes (mapeamento de rotas mais econômicas, gestão de frotas, tabelas de fretes, auditoria de notas fiscais e rastreamento de cargas em tempo real).

---

### 5. Comércio Eletrônico (E-Commerce)

Representa a transação de compra, venda, transferência ou troca de produtos, serviços e informações de maneira virtual, utilizando plataformas conectadas à internet.

#### Modelos de Negócio no E-Commerce:

- **B2B (Business-to-Business)**: Transações comerciais exclusivamente entre empresas (fabricantes, distribuidores, fornecedores). Envolve negociações baseadas em altos volumes e contratos de longo prazo.
- **B2C (Business-to-Consumer)**: Venda direta da empresa para o consumidor final, caracterizada pela busca por alta personalização, conveniência de acesso e foco na experiência de usuário (UX).
- **C2B (Consumer-to-Business)**: Modelo em que os consumidores individuais geram valor e as empresas o consomem (ex: influenciadores digitais expondo marcas em suas redes ou sites de _crowdfunding_ / financiamento coletivo).
- **B2A (Business-to-Administration)**: Transações eletrônicas e fornecimento de serviços conduzidos entre empresas privadas e a administração pública (ex: declarações fiscais online, licitações eletrônicas e conformidade com normativas).

---

### 6. Governança de TI, Segurança e Legislação no Brasil

#### Plano Diretor de TI (PDTI)

O PDTI é uma ferramenta de planejamento estratégico responsável por diagnosticar, planejar e gerenciar os recursos de TI (hardware, software, pessoas e governança), alinhando os investimentos em tecnologia diretamente às metas estratégicas gerais da organização. Garante mitigação de riscos, otimização de orçamentos e conformidade legal.

#### Frameworks de Governança e Metodologias:

- **ITIL (Information Technology Infrastructure Library)**: Boas práticas focadas na eficiência e alinhamento do gerenciamento de serviços de TI.
- **COBIT (Control Objectives for Information and Related Technologies)**: Framework completo voltado para governança de TI e gestão de controle de riscos.
- **Scrum**: Metodologia ágil que preza pela flexibilidade, adaptabilidade e entrega ágil de valor nos projetos.

#### Legislações Digitais Brasileiras Vitais para SIG:

1. **Lei do E-commerce (Lei nº 7.962/2013)**: Regulamenta o funcionamento de lojas virtuais, marketplaces e o direito do consumidor no ambiente digital brasileiro.
2. **Marco Civil da Internet (Lei nº 12.965/2014)**: Estabelece princípios de uso da rede no país, garantindo neutralidade de rede (tratamento igualitário de dados sem discriminação de tráfego), liberdade de expressão e proteção de privacidade dos usuários.
3. **Lei Geral de Proteção de Dados - LGPD (Lei nº 13.709/2018)**: Regulamenta o tratamento ético de dados pessoais por meios físicos ou digitais, exigindo o consentimento explícito dos titulares de dados para fins de coleta, compartilhamento e armazenamento específico, garantindo direitos de acesso, correção e eliminação de registros.

---

## Conceitos que não posso confundir

```
  ┌────────────────────────────────────────────────────────┐
  │                    E-BUSINESS                          │
  │  (Processos internos, ERP, RH, CRM, Cadeia de Valor)   │
  │                                                        │
  │         ┌──────────────────────────────────────┐       │
  │         │             E-COMMERCE               │       │
  │         │       (Transações de Compra e        │       │
  │         │         Venda pela Internet)         │       │
  │         └──────────────────────────────────────┘       │
  └────────────────────────────────────────────────────────┘
```

- **E-Commerce vs. E-Business**: O _e-commerce_ foca estritamente na transação comercial de compra e venda online de produtos ou serviços. O _e-business_ é muito mais amplo: abrange todos os processos corporativos que operam digitalmente via internet, incluindo ERP, CRM, gestão de RH e processos internos.
- **Banco de Dados vs. Data Warehouse**: Um _banco de dados_ tradicional armazena dados transacionais de uma determinada área específica e opera em tempo real. Um _Data Warehouse_ centraliza dados históricos agregados e integrados de múltiplos sistemas de toda a empresa especificamente para análises gerenciais e BI.
- **MRP I vs. MRP II**: O _MRP I_ calcula estritamente a necessidade de materiais físicos para a produção (_o que, quanto e quando_ produzir). O _MRP II_ expande este escopo agregando restrições financeiras, capacidade produtiva de máquinas, mão de obra e planejamento estratégico (_como_ produzir).
- **WMS vs. TMS**: O _WMS_ otimiza e gerencia os processos internos de movimentação e armazenagem de produtos **dentro do armazém** (endereço, estoque, RFID). O _TMS_ planeja e otimiza os fluxos de mercadorias **fora do armazém** (rotas de entrega, controle de frotas e fretes).
- **CRM vs. PRM**: O _CRM_ é focado no controle das relações de venda e suporte entre a empresa e o **consumidor final**. O _PRM_ foca em administrar as parcerias operacionais e comerciais com os **parceiros de negócios** da cadeia de suprimentos (distribuidores, revendedores).

---

## Pontos importantes para prova

1. **A escala evolutiva do SIG**: SPT (nível operacional) ➔ SIG (nível tático, relatórios de rotina) ➔ SAD (nível tático/estratégico, simulações) ➔ SIE (nível estratégico, KPIs executivos).
2. **A Regra da LGPD**: Exige consentimento explícito para o tratamento de dados pessoais, além de impor auditorias e garantir aos titulares o direito de acesso, retificação e exclusão de seus dados.
3. **Os 5 Vs do Big Data**: Volume, Variedade, Velocidade, Veracidade e Valor. Questões de prova costumam trocar "Veracidade" ou "Valor" por termos errados como "Vulnerabilidade".
4. **A Neutralidade de Rede (Marco Civil)**: Proíbe os provedores de internet de criar conexões mais rápidas ou lentas dependendo do conteúdo que o usuário consome. Todos os dados devem ser tratados igualmente.
5. **Desafios Comuns na Implementação de Sistemas (ERP, WMS, SCMS, BI)**: Em todas as vertentes, as fontes destacam: resistência cultural/humana de colaboradores, custos de implantação/manutenção elevados, complexidade de integrar sistemas legados (antigos) e problemas na qualidade/integridade dos dados de origem.

---

## Revisão rápida

```
Dado (Bruto) ➔ Informação (Ordenada) ➔ Conhecimento (Prática) ➔ Decisão Estratégica
```

- **Pilar de TI**: Hardware (físico), Software (programas), Dados (ativo), Pessoal (operadores).
- **Modelos de Negócio**: B2B (Empresa-Empresa), B2C (Empresa-Consumidor), C2B (Consumidor-Empresa), B2A (Empresa-Governo).
- **Fases do Processamento Analítico**: Extração ➔ Adequação ➔ Limpeza ➔ Derivação ➔ Agregação.
- **Governança de TI**: PDTI (Alinhamento estratégico), ITIL (Serviços), COBIT (Governança global e risco).
- **Logística Inteligente**: WMS (gestão de armazém) e TMS (gestão de transportes), integrados ao ERP corporativo para eficiência máxima.

---

## Perguntas para revisão

### Questão 1

**Diferencie Dado, Informação e Conhecimento, explicando a relação de dependência lógica entre esses conceitos.**

- _Resposta sugerida_: O dado é a matéria-prima bruta e desestruturada sem valor decisório isolado (ex: o número "50"). A informação é o dado tratado, filtrado e contextualizado de forma lógica a fim de reduzir a incerteza (ex: "vendemos 50 unidades do produto X"). O conhecimento é a interpretação subjetiva ou estruturada da informação voltada à tomada de ação (ex: "as vendas do produto X cresceram 50%, logo devemos reforçar o estoque para o próximo período").

### Questão 2

**Quais as quatro perguntas essenciais respondidas, respectivamente, pelo MRP I e pelo MRP II no processo produtivo industrial?**

- _Resposta sugerida_: O MRP I responde a: (1) O que deve ser produzido? (2) Quanto deve ser produzido? e (3) Quando deve ser produzido?. O MRP II adiciona o controle de capacidade fabril e planejamento integrado de manufatura, respondendo a uma quarta pergunta: (4) Como deverá ser produzido?.

### Questão 3

**O que é neutralidade de rede e qual legislação nacional garante esse princípio?**

- _Resposta sugerida_: A neutralidade de rede garante que todos os dados que trafegam pela internet recebam o mesmo tratamento regulado, impedindo que provedores discriminem ou cobrem valores diferentes de tráfego com base no tipo de conteúdo, origem, destino ou aplicação consumida. Esse princípio é garantido pelo Marco Civil da Internet (Lei nº 12.965/2014).

### Questão 4

**Explique a diferença entre Sistemas Especialistas (SE) e Sistemas de Informação Executiva (SIE) em termos de público-alvo e funcionalidade.**

- _Resposta sugerida_: Os Sistemas Especialistas são baseados em IA e emulam o processo de tomada de decisões de um especialista humano em áreas técnicas específicas (como diagnóstico médico ou falha mecânica industrial) usando regras lógicas e base de conhecimento rica. Já os SIE são painéis de controle analítico voltados a executivos do topo hierárquico, apresentando visões resumidas, KPIs e dashboards em tempo real sobre a saúde estratégica do negócio e concorrentes.

### Questão 5

**Quais as fases do processo de manipulação de dados realizadas antes da carga em uma estrutura de Data Warehouse e qual a importância de cada uma?**

- _Resposta sugerida_:
    1. _Extração_: Coleta física dos dados brutos nas diversas fontes da organização.
    2. _Adequação_: Padronização de formatos estruturais comuns.
    3. _Limpeza_: Expurgar ou corrigir dados sujos, nulos ou duplicados.
    4. _Derivação_: Geração de novos atributos analíticos.
    5. _Agregação_: Consolidação e resumo lógico dos dados de acordo com critérios de negócio.

### Questão 6

**Como a integração entre o WMS (Warehouse Management System) e o TMS (Transportation Management System) gera eficiência operacional e otimização de recursos na logística de distribuição?**

- _Resposta sugerida_: A integração une as informações internas de armazenamento e as externas de transporte de forma sinérgica. Assim que o WMS gera a saída física de uma carga da doca (através de processos automatizados de picking e packing), o TMS aciona automaticamente o planejamento estratégico do transporte (configurando rotas, carregamentos em veículos, audição de frete e prazos) de modo a mitigar o tempo de espera e eliminar gargalos e falhas operacionais.

---

### 1. Introdução aos sistemas de informação gerencial (Unidade 1)

- **Fundamentos e Fluxo**: A transição lógica e a diferença entre dado, informação e conhecimento.
- **A Era da Informação e Evolução**: O papel da informação como ativo estratégico, a linha do tempo desde os cartões perfurados da década de 1950 até a computação em nuvem, IA e IoT atuais.
- **Componentes do SI**: O funcionamento integrado de hardware, software (entrada, análise, saída), dados e pessoal (_peopleware_).
- **Engenharia de Dados (ETL)**: O fluxo preparatório de dados brutos para o _Data Warehouse_ (Extração, Adequação, Limpeza, Derivação e Agregação).
- **Estruturas Analíticas**: A base conceitual e inter-relação de _Business Intelligence_ (BI), Big Data (5 Vs) e _Data Mining_.

### 2. Tipos de sistemas de informação gerencial (Unidade 2)

- **Entradas e Saídas**: Classificação dos dados (operacionais, externos e de outras fontes gerenciais) e métodos de coleta (manuais e automáticos).
- **Tipologias de Relatórios de Saída**: O detalhamento de relatórios de rotina, _ad hoc_, sumários, detalhados, analíticos, de exceção e regulatórios, além de dashboards e KPIs.
- **Pirâmide de Sistemas**: A divisão e propósitos dos sistemas SPT (operacional), SIG (tático), SAD (semiestruturadas) e SIE (estratégico).
- **Novos Conceitos**: Sistemas de Gestão do Conhecimento (SGC), Sistemas Especialistas (emulação de decisões de experts) e Inteligência Artificial corporativa (ML, PLN e Robótica).
- **Gestão de TI**: Alinhamento de infraestrutura e frameworks de governança (ITIL, COBIT e metodologias ágeis como Scrum).

### 3. Sistemas Empresariais (Unidade 3)

- **Integração Central**: O papel do ERP e o banco de dados unificado eliminando as "ilhas de informação".
- **Planejamento Industrial**: A evolução e as perguntas-chave respondidas pelo MRP I (necessidade de materiais) e MRP II (capacidade de manufatura).
- **Cadeia de Suprimentos (SCM)**: O funcionamento do SCMS e os sistemas integrados CRM (clientes), PRM (parceiros) e E-Procurement (compras eletrônicas/leilões reversos).
- **Logística**: O papel e os fluxos específicos do WMS (gerenciamento físico do armazém e RFID) e TMS (gestão de frotas, rotas e fretes).

### 4. Comércio eletrônico e gestão dos sistemas de informação (Unidade 4)

- **Fundamentos do E-Commerce**: Definição, evolução desde os anos 1960, vantagens (acesso global, operações 24/7, personalização) e limitações (falta de toque, segurança e fraude).
- **E-Commerce vs. E-Business**: A distinção crucial entre transação pura de vendas e a digitalização global de processos corporativos.
- **Modelos de Negócio**: Características operacionais de B2B, B2C, C2B e B2A.
- **Legislação e Segurança**: O alinhamento com a Lei do E-commerce (nº 7.962/2013), o Marco Civil da Internet (com foco em neutralidade de rede), a LGPD (consentimento e direitos de exclusão) e as práticas de segurança de dados (criptografia, firewalls, MFA, backup).

