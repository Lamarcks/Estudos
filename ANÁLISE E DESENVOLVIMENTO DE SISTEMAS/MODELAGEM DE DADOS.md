[[EXEMPLOS-PRÁTICOS DE MODELAGEM DE DADOS]]
#ASSUNTO

## Conceitos principais

- **Modelagem de Dados**: Estudo das informações existentes em um contexto sob observação para a construção de um modelo de representação e entendimento desse cenário, estruturando-as em um modelo lógico.
- **Minimundo**: Representação de uma parte do mundo real que é mapeada e refletida em um banco de dados; qualquer modificação realizada no minimundo reflete-se automaticamente no banco.
- **Abstração de Dados**: Níveis de visão de dados que omitem detalhes técnicos e físicos de armazenamento do usuário final, focando apenas na representação conceitual ou lógica.
- **SGBD (Sistema Gerenciador de Banco de Dados)**: Software responsável pelos processos de definição, construção, manipulação, compartilhamento e segurança de bancos de dados entre vários usuários e aplicações.
- **Data Warehouse (DW)**: Repositório centralizado e de longo prazo que armazena informações colhidas de várias origens heterogêneas sob um esquema unificado para apoiar decisões corporativas.
- **Mineração de Dados (Data Mining / KDD)**: Processo semiautomático de analisar grandes volumes de dados armazenados em disco para encontrar padrões e regras úteis.
- **Entidade (MER)**: Objeto ou evento do mundo real, identificável de forma única por meio de suas características (atributos).
- **Chave Primária (PK)**: Atributo ou conjunto de atributos (chave composta) que identifica exclusivamente um registro em uma tabela, impedindo a duplicidade de linhas.
- **Chave Estrangeira (FK)**: Atributo usado para estabelecer relações entre os registros de uma tabela com a chave primária de outra.
- **Dependência Funcional**: Restrição entre dois conjuntos de atributos de uma mesma relação, descrevendo em que medida um atributo depende (ou é determinado) por outro para a sua existência.
- **Normalização de Dados**: Técnica aplicada para avaliar e corrigir a estrutura das tabelas de um banco de dados, com o propósito de minimizar redundâncias, anomalias e garantir a integridade.
- **Engenharia Reversa**: Processo de análise e reconstrução da estrutura lógica/conceitual de um banco de dados a partir de um banco de dados físico existente.

---

## Conteúdo explicado

### 1. Fundamentos e Arquitetura de Bancos de Dados

#### Níveis de Abstração/Visão de Dados

Para modelar um banco de dados, devemos considerar três níveis de visão:

1. **Modelo Conceitual**: Primeira etapa do projeto. Representa a realidade de forma global e genérica, descrevendo as informações e seus relacionamentos de maneira completamente independente de aspectos de implementação tecnológica.
2. **Modelo Lógico**: Inicia-se após o conceitual. Estrutura os dados adotando uma abordagem tecnológica de SGBD (relacional, hierárquica, em rede ou orientada a objetos). É uma representação que já nomeia componentes e as ações que exercem uns sobre os outros.
3. **Modelo Físico**: Construído a partir do modelo lógico, descreve as estruturas físicas de armazenamento de dados (tabelas, campos, tipos, índices) conforme os requisitos de processamento físico.

#### Tipos/Modelos de Banco de Dados Históricos e Atuais

- **Hierárquico**: O primeiro tipo de banco de dados, desenvolvido com base na organização física de endereços de discos. É estruturado em formato de árvore (com nós pais e filhos). O registro pai pode corresponder a vários registros filhos, mas um filho possui apenas um pai. A navegação exige ponteiros estruturados (não há navegação livre por comandos relacionais).
- **Relacional**: Modelo mais utilizado atualmente, criado por Edgar F. Codd em 1968 com base na teoria dos conjuntos e na álgebra relacional. Organiza os dados em relações (**tabelas**), que são formadas por **linhas** (registros) e **colunas** (atributos/campos). As consultas geram tabelas virtuais temporárias.
- **Orientado a Objetos (ODB)**: Surgido na década de 1980 para tratar de tipos de dados complexos que os sistemas relacionais tradicionais não podiam armazenar facilmente (como dados de geoprocessamento GIS ou CAD/CAM/CAE). Define os dados por meio de objetos, com suas propriedades e operações (equivalentes a classes persistidas). Padronizado pelo ODMG.

#### SGBD (Sistemas Gerenciadores de Bancos de Dados)

O SGBD atua como um software intermediário para que as aplicações acessem fisicamente os dados, ocultando os detalhes de hardware.

- **Linguagem SQL no SGBD**:\
    - **DDL (Data Definition Language)**: Instruções que criam ou alteram estruturas de dados no banco (como `CREATE TABLE`, `ALTER TABLE`, definição de índices e stored procedures). Usualmente executadas pelo DBA (Database Administrator).
    - **DML (Data Manipulation Language)**: Instruções para manipulação e gerenciamento dos registros (como `SELECT`, `INSERT`, `UPDATE`, `DELETE`). Executadas interativamente por ferramentas ou dentro de programas aplicativos.

#### As Propriedades ACID das Transações

Uma transação é um processo ou programa que acessa e opcionalmente atualiza itens de dados. Para garantir a integridade do banco de dados, o SGBD deve assegurar as propriedades **ACID**:

1. **Atomicidade**: Garante que nenhuma ou a totalidade das operações da transação sejam realizadas com sucesso. O sistema mantém um log em disco dos antigos valores; se ocorrer um erro no meio da transação (como falta de luz), o SGBD realiza o _rollback_ restaurando os dados originais.
2. **Consistência**: Garante que todas as regras de integridade lógicas do banco sejam preservadas ao término de uma transação, deixando os dados em estado íntegro.
3. **Isolamento**: Garante que uma transação concorrente (simultânea) não interfira no trabalho de outra antes de sua conclusão, isolando modificações simultâneas de dados.
4. **Durabilidade (Persistência)**: Garante que os resultados de uma transação finalizada com sucesso fiquem gravados de forma permanente no armazenamento físico, sobrevivendo a falhas futuras do sistema.

#### Tipos Primitivos do SQL

As colunas de tabelas físicas no SGBD precisam ter seus formatos explicitamente definidos de acordo com os tipos primitivos disponíveis no SQL:

- **Numérico**:\
    - _Inteiro_: `TinyInt`, `SmallInt`, `Int`, `MediumInt`, `BigInt`.
    - _Real (Pontos flutuantes/Precisão)_: `Decimal`, `Float`, `Double`, `Real`.
    - _Lógico_: `Bit`, `Boolean`.
- **Data/Tempo**: `Date`, `DateTime`, `TimeStamp`, `Time`, `Year`.
- **Literal**:\
    - _Caractere_: `Char` (tamanho fixo), `VarChar` (tamanho variável).
    - _Texto_: `TinyText`, `Text`, `MediumText`, `LongText`.
    - _Binário (Arquivos/Imagens)_: `TinyBlob`, `Blob`, `MediumBlob`, `LongBlob`.
    - _Coleção_: `Enum`, `Set`.
- **Espacial**: `Geometry`, `Point`, `Polygon`, `MultiPolygon`.

---

### 2. Sistemas de Apoio à Decisão (Data Warehouse e Data Mining)

Quando as empresas crescem, seus dados operacionais tendem a ficar espalhados em sistemas heterogêneos. Consultar esses dados transacionais diretamente de forma centralizada prejudica os sistemas de processamento operacional diário, que também não preservam o histórico de dados passados. Daí surgem os sistemas analíticos:

- **Data Warehouse (DW)**: Repositório centralizado contendo informações coletadas de múltiplas origens heterogêneas, integradas sob um esquema unificado em um único local, permitindo acesso de longo prazo a dados históricos.
- **OLTP (On-Line Transaction Processing)**: Processamento de transações diárias operacionais (escritas, inserções, exclusões imediatas) com dados puros e sem tratamento analítico. É a fonte primária de dados para alimentar o DW.
- **OLAP (On-Line Analytical Processing)**: Tecnologia de processamento analítico focada em converter dados brutos em visões consistentes e multidimensionais, facilitando a compreensão para tomada de decisões rápidas.
- **ODS (Operational Data Store)**: Um repositório de dados intermediário, similar a um Data Warehouse, mas que não disponibiliza as informações tratadas para apoio à tomada de decisão de alto nível.

#### Arquitetura e Processo ETL vs ELT

Para extrair os dados operacionais das fontes e carregá-los no DW, utiliza-se um pipeline:

- **ETL (Extração, Transformação e Carga)**: Os dados são extraídos das fontes operacionais, limpos e transformados fora do banco de dados analítico e, por fim, carregados no DW.
- **ELT (Extração, Carga e Transformação)**: Os dados são extraídos e carregados diretamente no DW, permitindo que a transformação ocorra dentro do próprio repositório utilizando o poder de processamento paralelo ou frameworks de processamento distribuído (como MapReduce).

#### Técnicas e Etapas de Limpeza de Dados (Transformação)

No processo de transformação de dados, várias técnicas atuam para corrigir inconsistências dos dados de origem:

- **Pesquisa Difusa (Fuzzy Lookup)**: Algoritmo que ajuda a corrigir erros comuns de digitação em nomes e endereços ao compará-los com uma base de dados de referência (como nomes de ruas e CEPs).
- **Eliminação de Duplicidades (Merge-Purge)**: Operação que detecta e remove registros idênticos ou duplicados procedentes de fontes de dados distintas.
- **Householding**: Processo de agrupar múltiplos registros de indivíduos que residem sob o mesmo domicílio para unificar correspondências enviadas à residência.
- **Manutenção de Visão (View-Maintenance)**: Processamento necessário para propagar e refletir atualizações sofridas pelas tabelas operacionais diretamente no DW.

#### Modelagem Multidimensional: Fatos vs. Dimensões

Os esquemas de DW utilizam uma modelagem focada em análise:

- **Tabelas de Fatos**: Registram os eventos de negócio em si (como vendas, transações). Costumam ser tabelas volumosas. Possuem:\
    - _Atributos de Medição_: Informações quantitativas e numéricas que podem ser agregadas (como quantidade de itens, preço total).\
    - _Atributos de Dimensão_: Chaves estrangeiras associadas que servem de índice para as dimensões.
- **Tabelas de Dimensão**: Tabelas contextuais sob as quais as métricas da fato serão agrupadas, permitindo visualizar os dados por diferentes ângulos (ex: Dimensão Tempo, Cliente, Localização, Produto).

---

### 3. Segurança, Auditoria e Privacidade de Dados

#### Controle de Acesso e Segurança no Banco de Dados

A segurança opera primariamente em dois níveis gerenciados pelo DBA, com base nas permissões de cada usuário:

1. **Nível de Conta de Usuário**: Direitos individuais vinculados à conta do usuário, independente de tabelas específicas.
2. **Nível de Relação/Tabela**: Direitos de acesso e manipulação específicos aplicados a cada tabela do banco de dados.

- **Padrão SQL (ANSI/ISO)**: Estabelece os privilégios básicos de `SELECT`, `INSERT`, `UPDATE` e `DELETE`.
- **Comandos de Gerenciamento**:\
    - `CREATE USER`: Cria o registro do usuário.\
    - `GRANT`: Concede permissões específicas a uma conta.  
        _Exemplo_: `GRANT INSERT, DELETE ON CLIENTES TO user001;`\
    - `REVOKE`: Remove ou revoga privilégios previamente estabelecidos.  
        _Exemplo_: `REVOKE DELETE ON CLIENTES FROM user001;`

#### Trilhas de Auditoria (Audit Trail)

Refere-se ao log de auditoria que documenta as mudanças ocorridas no banco de dados (inserções, exclusões, alterações), informando qual usuário realizou a mudança, quando ocorreu e o que foi alterado.

- **Nível de Banco de Dados**: Criada por meio de mecanismos internos do SGBD ou definindo Triggers (gatilhos). Registra atualizações puramente físicas em nível de linha, sendo muitas vezes **insuficiente para as aplicações**, pois não captura qual usuário final da aplicação realizou a ação nem a lógica do negócio.
- **Nível de Aplicação**: Auditoria implementada no próprio código do software, registrando ações lógicas abstratas mais altas, o usuário real e o IP de origem.
- **Proteção de Logs**: Os logs de auditoria devem ser protegidos contra exclusão ou adulteração por invasores. Soluções robustas copiam logs instantaneamente para máquinas externas isoladas ou utilizam redes de **Blockchain**, que aplicam algoritmos de _hashing_ distribuído para impedir a modificação indetectada dos logs.

#### Privacidade de Dados (LGPD)

Leis de privacidade (como a LGPD) exigem proteção rigorosa dos dados confidenciais, aplicando penalidades severas ao descumprimento.

- **O Paradoxo da Utilidade vs. Privacidade**: Dados de saúde ou de consumo individual são sigilosos, mas agregá-los é vital para pesquisas públicas (como mapear epidemias ou efeitos colaterais de remédios).
- **Técnicas de Proteção de Privacidade**:\
    - _Risco de reidentificação_: Apenas ocultar o nome do paciente, mantendo a data de nascimento exata e o CEP, pode permitir que ele seja identificado cruzando os dados com bases externas.\
    - _Solução_: Aplicar técnicas de descaracterização, como fornecer apenas o **ano de nascimento** (em vez da data exata) e generalizar o CEP do indivíduo.

---

### 4. O Modelo Entidade-Relacionamento (MER)

O MER é a modelagem de representação conceitual gráfica amplamente utilizada para descrever de forma intuitiva como os dados do minimundo se organizam.

#### Classificação de Entidades

- **Entidade Forte (ou Fundamental)**: Existe independentemente de qualquer outra entidade no banco de dados (como `Cliente`, `Aluno`, `Empresa`). Grafada no singular e fácil de identificar nos substantivos da análise de requisitos.
- **Entidade Fraca (ou Atributiva)**: Depende obrigatoriamente da existência de outra entidade (forte) e da dependência de seu identificador. Possui restrição de participação total com a entidade forte correspondente.\
    - _Exemplo_: `Dependente` só existe se houver um `Funcionário` correspondente cadastrado. Se o funcionário for removido, o dependente perde a razão de existir. É representada graficamente por retângulos de borda dupla.
- **Entidade Associativa**: Entidade que surge para resolver e caracterizar um relacionamento muitos para muitos (M:N) entre duas ou mais tabelas. Ela abriga atributos próprios relacionados à ação de junção (ex: `Contrato` unindo `Cliente` e `Vendedor`, ou `Histórico` guardando notas).

#### Classificação de Atributos

- **Simples (ou Atômico)**: Atributo único e indivisível de significado próprio (ex: `CPF`, `RG`).
- **Composto**: Pode ser desmembrado em partes menores com significados próprios (ex: `Endereço`, desmembrado em rua, número, complemento e bairro).
- **Monovalor**: Atributo que possui apenas um valor válido na tabela (ex: `Matrícula` do aluno).
- **Atributo Multivalorado**: Atributo que pode comportar múltiplas informações (ex: `Telefone`, pois um mesmo funcionário pode ter vários números). Representado por elipse com borda dupla.
- **Atributo Derivado**: Possui valor calculado dinamicamente a partir de outros campos já existentes ou tabelas auxiliares (ex: `Idade`, derivada da data de nascimento em relação à data atual). Representado por elipse tracejada.
- **Atributo Chave**: Atributo escolhido ou criado para identificar exclusivamente a linha em uma tabela (ex: `ID`, `Código`).

#### Relacionamentos e Cardinalidade

- **Cardinalidade**: Quantidade de vezes que uma entidade se associa a outra. É descrita por valores mínimos e máximos.\
    - _Mínimo_: Pode ser **0** (conexão opcional) ou **1** (conexão obrigatória, que mapeia as regras de negócios da empresa).\
    - _Máximo_: Pode ser **1** ou **Muitos (M ou N)**.
- **Variações de Cardinalidades**:\
    - **Um para um (1:1)**: Cada registro de uma tabela se associa a apenas uma instância de outra (ex: um `Vendedor` possui um `Telefone Celular` corporativo e vice-versa).\
    - **Um para muitos (1:M)**: Um registro da tabela A associa-se a múltiplos registros da tabela B, mas cada registro de B aponta para no máximo um registro de A (ex: um `Responsável` pode ter múltiplos `Alunos` matriculados, mas cada aluno tem apenas um responsável cadastrado).\
    - **Muitos para muitos (M:N)**: Registros da tabela A se associam a múltiplos registros de B e vice-versa (ex: um `Aluno` cursa várias `Disciplinas` e uma disciplina possui vários alunos matriculados).

#### Generalização e Especialização (Hierarquia e Herança)

- **Generalização**: Processo de agrupar entidades distintas que possuem atributos idênticos em uma entidade genérica de nível mais alto (superclasse ou supertipo).\
    - _Indicador mais evidente_: Presença constante de atributos repetidos nas entidades durante a fase de modelagem.
- **Especialização**: Processo descendente inverso, criando novas entidades (subtipos ou subclasses) com atributos detalhados adicionais que as diferenciam da entidade genérica superior.\
- _Exemplo_: `Pessoa` é a superclasse genérica (nome, endereço, CPF, RG, nome do pai e da mãe). Seus subtipos especializados são `Professor` (valor da hora/aula) e `Aluno` (data de entrada e formatura). No diagrama, o relacionamento é representado por um círculo na intersecção das linhas.

---

### 5. Linguagem UML na Modelagem de Dados

A UML (Unified Modeling Language) é uma linguagem gráfica padronizada para modelar sistemas orientados a objetos. Surgiu da fusão das abordagens BOOCH, OMT (Rumbaugh) e OOSE (Jacobson). Não é uma metodologia, mas sim uma linguagem visual para documentar, desenhar e comunicar o projeto do software.

#### Tipos de Diagramas da UML

- **Diagrama de Classes**: O mais utilizado. Representa conjuntos de classes, seus atributos, métodos de execução e relações lógicas. É ideal para construir e modelar graficamente a etapa lógica do banco de dados.
- **Diagrama de Objetos**: Representa graficamente a instância de uma classe com dados reais guardados na memória RAM.
- **Diagrama de Casos de Uso**: Descreve os atores lógicos (usuários) e as funcionalidades expostas do sistema (requisitos funcionais).
- **Diagrama de Sequência**: Visão orientada ao longo do tempo, exibindo a ordem cronológica em que as mensagens são trocadas entre objetos.
- **Diagrama de Atividades**: Descreve graficamente o fluxo de tarefas que podem ser executadas pelo programa.
- **Diagrama de Estados**: Demonstra os estados de comportamento que um objeto assume e os eventos que disparam suas transições.
- **Diagrama de Componentes**: Exibe a organização e dependência dos arquivos físicos e componentes do sistema.

#### Correspondência entre UML e Modelo Entidade-Relacionamento

- A classe do Diagrama de Classes UML corresponde à **Entidade** (Tabela) do MER.
- Atributos da classe correspondem aos **Atributos** lógicos do banco de dados.
- O conceito de herança em Orientação a Objetos mapeia a relação de **Generalização/Especialização** do MER.
- **Símbolos de Cardinalidade**: Diferente do MER (que usa a letra "N"), a UML utiliza o caractere de **asterisco (*)** para representar "muitos". Ela também é mais precisa, permitindo declarar limites definidos (ex: `1..*` ou `1..5`).
- **Persistência**: Ao criar instâncias de classes em Orientação a Objetos, os dados ficam retidos temporariamente na memória RAM. O salvamento definitivo desse estado em um armazenamento persistente (arquivos ou tabelas do banco relacional) é chamado de persistência de dados.

---

### 6. Ferramentas CASE de Modelagem de Dados

Ferramentas CASE (_Computer Aided Software Engineering_) são recursos de software que oferecem automação e suporte no processo de planejamento, design, testes e documentação de sistemas.

#### Classificação de Ferramentas CASE

1. **Lower CASE**: Oferece suporte focado prioritariamente nas etapas de análise técnica e projeto conceitual.
2. **Upper CASE**: Oferece assistência prática nas etapas de construção física do software e análise/validação de testes.
3. **Integrated CASE (I-CASE)**: Combina de maneira integrada os recursos das categorias Lower e Upper CASE, apoiando o ciclo de vida completo do software.

#### Recursos Clássicos de Ferramentas CASE de Banco de Dados

- **Interface Gráfica**: Geração e edição visual de diagramas de entidade-relacionamento (DER), tabelas, atributos e chaves.
- **Forward Engineering (Engenharia Direta)**: Processo de conectar automaticamente o modelo visual (DER) ao banco de dados, gerando e criando fisicamente as tabelas por scripts SQL lógicos.
- **Reverse Engineering (Engenharia Reversa)**: Processo de gerar automaticamente o diagrama visual estruturado (DER) a partir de uma base física ativa de dados.
- **Geração de Documentação**: Criação automática de um dicionário de dados detalhando campos, tipos e propriedades do banco à medida que as tabelas são modeladas.

#### Comparativo de Ferramentas de Modelagem

- **Astah**: Focada em diagramas UML e muito forte no ecossistema Java (gera classes automaticamente). Na modelagem de bancos (versão paga), utiliza a notação **IDEF1X**, onde a cardinalidade de muitos é representada por uma bola preta. Permite gerar dicionários de dados exportando os metadados das entidades diretamente para o Microsoft Excel.
- **MySQL Workbench**: Mantido pela Oracle, gratuito e especializado na modelagem física e administração física de bases MySQL. Utiliza o padrão visual da notação **Pé de Galinha** (_Crow's Foot_).
- **Draw.IO**: Ferramenta de desenho online e gratuita. Permite modelar tabelas na categoria de entidade-relacionamento utilizando a **Notação de Setas**.
- **Lucidchart**: Ferramenta de diagramação online (gratuita para até 60 elementos). Utiliza a notação de **Pé de Galinha**. Permite exportar scripts de criação SQL lógicos específicos para MySQL, PostgreSQL, SQL Server e Oracle.

---

### 7. Normalização de Dados (Aprofundado)

A normalização aplica regras lógicas para corrigir falhas e redundâncias presentes nas tabelas operacionais do banco, otimizando o seu desempenho e minimizando custos de manutenção de dados.

#### O Conceito de Dependência Funcional e Determinante

A dependência funcional $X \rightarrow Y$ indica que o conjunto de atributos $X$ é o **determinante** (influencia exclusivamente) e determina o valor único do dependente $Y$.

- _Tipos de Dependências_:\
    1. **Total (ou Completa)**: Quando um atributo não chave depende exclusivamente de toda a chave primária concatenada e não de apenas uma parte dela (ex: em uma tabela de itens de pedido, a `Quantidade` depende de `{NumeroPedido, CodigoISBN}`).\
    2. **Parcial**: Quando um atributo depende de apenas parte de uma chave primária composta (ex: na mesma tabela de itens, o `Titulo` depende apenas de `CodigoISBN`, sem depender de `NumeroPedido`).\
    3. **Transitiva**: Quando o valor de um atributo depende funcionalmente de outra coluna não chave que, por sua vez, depende da chave primária (ex: em funcionários, a `DescricaoCargo` depende de `idCargo`, que não é a PK do funcionário).

#### As Formas Normais Passo a Passo

As formas normais são cumulativas: para que uma relação alcance a forma normal $N$, ela deve obrigatoriamente satisfazer todos os critérios de $1$ até $N-1$.

```
┌─────────────────────────────────────────────────────────┐
│              PRIMEIRA FORMA NORMAL (1FN)                │\
│    Garante que todos os atributos sejam atômicos e      │\
│     elimina a presença de grupos repetitivos.           │\
└────────────────────────────┬────────────────────────────┘\
                             ▼\
┌─────────────────────────────────────────────────────────┐\
│              SEGUNDA FORMA NORMAL (2FN)                 │\
│      Estar na 1FN e remover dependências parciais.      │\
│    Todos os atributos dependem da chave primária total.  │\
└────────────────────────────┬────────────────────────────┘\
                             ▼\
┌─────────────────────────────────────────────────────────┐\
│              TERCEIRA FORMA NORMAL (3FN)                │\
│     Estar na 2FN e remover dependências transitivas.     │\
│   Campos dependem exclusivamente da PK de forma direta. │\
└────────────────────────────┬────────────────────────────┘\
                             ▼\
┌─────────────────────────────────────────────────────────┐\
│          FORMA NORMAL DE BOYCE-CODD (FNBC)              │\
│    Todos os determinantes devem ser chaves candidatas.  │\
│      Corrige anomalias de chaves sobrepostas.           │\
└────────────────────────────┬────────────────────────────┘\
                             ▼\
┌─────────────────────────────────────────────────────────┐\
│               QUARTA FORMA NORMAL (4FN)                 │\
│    Estar na 3FN/FNBC e eliminar dependências            │\
│   multivaloradas (fatos multivalorados independentes).  │\
└─────────────────────────────────────────────────────────┘
```

##### Primeira Forma Normal (1FN)

- **Regra**: Uma tabela está na 1FN se, e somente se, todos os seus atributos contiverem apenas valores atômicos (indivisíveis), não contendo grupos repetitivos ou múltiplos valores na mesma célula.
- **Passos práticos**:
    1. Identificar a chave primária da tabela.
    2. Localizar atributos compostos ou não atômicos.
    3. Remover os dados repetitivos criando novas tabelas isoladas para esses dados.
    4. Estabelecer os relacionamentos lógicos por chaves estrangeiras.
- _Exemplo_: Na tabela `Funcionário` contendo o campo `Idade` e `Cidade`. Para adequar à 1FN, cria-se a tabela `Cidade` (`#idCidade`, `Cidade`) e adiciona-se o campo `&idCidade` como chave estrangeira no funcionário. Adicionalmente, substitui-se o campo `Idade` por `Data de Nascimento` (atômico e não alterável anualmente).

##### Segunda Forma Normal (2FN)

- **Regra**: Uma tabela está na 2FN se estiver na 1FN e todos os atributos que não fazem parte da chave primária dependerem funcionalmente de toda a chave primária (dependência funcional total), eliminando dependências parciais. Aplica-se a tabelas de chaves compostas.
- **Passos práticos**:
    1. Identificar colunas que não dependem da totalidade da chave primária composta.
    2. Remover essas colunas, criando uma nova tabela isolada.
    3. Garantir a integridade referencial.
- _Exemplo_: Na tabela `Funcionário` onde as informações de `Departamento` dependem apenas de parte das estruturas compostas do negócio, isola-se o campo criando a tabela `Departamento` (`#codDepart`, `Departamento`) e adicionando a chave estrangeira `&codDepart` na tabela principal.

##### Terceira Forma Normal (3FN)

- **Regra**: Uma relação está na 3FN se estiver na 2FN e todos os seus campos não chave forem independentes lógicos uns dos outros, dependendo exclusivamente da chave primária direta, sem dependências transitivas.
- **Passos práticos**:
    1. Localizar colunas que dependem de outras colunas que não são a chave primária.
    2. Remover essas colunas dependentes.
- _Exemplo_: A tabela `Funcionário` continha as colunas `#codFuncionario`, `Nome`, `idCargo` e `descCargo` (descrição do cargo). A `descCargo` possui dependência funcional transitiva de `idCargo` (que não é a PK de funcionário). Aplicando a 3FN, remove-se a coluna `descCargo` de `Funcionário`, movendo-a para a tabela isolada `Cargo` (`#idCargo`, `descCargo`) e ligando as tabelas por chave estrangeira.

##### Forma Normal de Boyce-Codd (FNBC)

- **Regra**: Uma relação está na FNBC se, e somente se, todos os seus determinantes forem chaves candidatas (tanto chaves candidatas quanto primárias). Elimina redundâncias que escapavam dos testes da 3FN.
- _Condições de Ocorrência da Falha_: Ocorre quando a tabela possui: (1) múltiplas chaves candidatas; (2) essas chaves candidatas são compostas por múltiplos atributos; e (3) essas chaves concatenadas compartilham atributos comuns entre si.
- _Exemplo_: Entidade professor associado a mais de uma escola e sala de aula. Para aplicar a FNBC, divide-se a entidade Filho em duas: uma contendo dados descritivos exclusivos do filho e a outra isolando a relação de professor e sala na escola.

##### Quarta Forma Normal (4FN)

- **Regra**: Uma tabela está na 4FN se estiver na 3FN e não contiver dependências multivaloradas (ou múltiplos fatos multivalorados independentes, como relacionamentos ternários desnecessários).
- _Exemplo_: Uma tabela de `Compra` com os atributos lógicos `#CodFornecedor`, `#CodProduto` e `#CodComprador` operando em um relacionamento ternário inadequado. Para migrar para a 4FN, divide-se a entidade em duas novas que compartilham a chave `CodFornecedor` separadamente (uma associando `CodFornecedor` a `CodProduto` e outra ligando `CodProduto` a `CodComprador`).

##### Quinta Forma Normal (5FN)

- **Regra**: Uma tabela alcança a 5FN se estiver na 4FN e não puder mais ser subdividida em relações menores sem que ocorra perda de integridade ou dados (decomposição por junção).
- _Uso prático_: Pouco utilizada em ambientes comerciais reais, pois gera um grande volume de tabelas que reduz severamente o desempenho das consultas operacionais físicas.

---

### 8. Engenharia Reversa de Bancos de Dados

Processo fundamental para modernização e análise estrutural de bancos legados quando a documentação técnica foi perdida ou não existe. Sistemas legados são aplicações obsoletas mantidas em uso operacional devido ao altíssimo risco e custo de substituição completa.

#### Estratégias de Substituição de Sistemas Legados

- **Wrappers (Invólucros)**: Camada que permite ao sistema legado ser acessado por aplicações modernas como se fosse uma base relacional, traduzindo as chamadas de bancos e suportando padrões de conexão como ODBC ou OLE-DB.
- **Abordagem Big-Bang**: Transição abrupta substituindo todo o backend antigo pela nova versão. Apresenta alto risco operacional de bugs indetectados e interrupção das transações do negócio.
- **Abordagem Incremental**: Substituição gradual e modular das funcionalidades. Os dois sistemas coexistem temporariamente por meio de wrappers operacionais.

#### Fluxo de Trabalho e Passos Práticos para Engenharia Reversa

O processo segue uma estratégia de construção **ascendente (Bottom-Up)**:

1. **Coleta de Informações**: Reunir metadados físicos, manuais, rotinas SQL, triggers e entrevistar usuários reais para extrair as regras de negócio lógicas.
2. **Representação Não Normalizada**: Desenhar a estrutura dos arquivos antigos físicos no formato de tabelas não normalizadas lógicas.
3. **Processo de Normalização**: Submeter os esquemas de tabelas não normalizadas lógicas às formas normais lógicas (1FN, 2FN, 3FN) para limpar redundâncias.
4. **Integração de Modelos**: Unificar os esquemas normalizados lógicos que possuem tabelas comuns para consolidar o esquema relacional integrado definitivo do banco de dados.
5. **Geração do DER**: Converter as tabelas relacionais consolidadas na etapa anterior para o modelo de representação conceitual gráfico final (DER).
6. **Validação e Ajustes**: Validar o modelo desenhado contra dados operacionais reais e ajustá-lo com feedback de usuários chaves.

---

## Conceitos que não posso confundir

|Conceito A|Conceito B|Diferença Crucial|
|:--|:--|:--|
|**Banco de Dados**|**SGBD**|O **Banco de Dados** é uma coleção de dados lógicos estruturados que representam o minimundo. O **SGBD** é o software (ex: MySQL, PostgreSQL, Oracle) que gerencia fisicamente o acesso a essa coleção.|
|**Dicionário de Dados**|**Metadados**|**Metadados** são os dados que fornecem descrições detalhadas da estrutura das informações. O **Dicionário de Dados** é o documento físico que abriga esse dicionário detalhado de metadados.|
|**Estratégia Top-Down**|**Estratégia Bottom-Up**|A abordagem **Top-Down** inicia identificando os conjuntos lógicos (entidades) para depois definir suas propriedades de atributos. A abordagem **Bottom-Up** inicia listando atributos atômicos para depois agrupá-los e formar as tabelas.|
|**Generalização**|**Especialização**|A **Generalização** é o agrupamento de múltiplos subtipos em uma superclasse genérica de alto nível. A **Especialização** é o detalhamento de uma classe mãe em subclasses específicas.|
|**Chave Primária (PK)**|**Chave Estrangeira (FK)**|A **Chave Primária** garante exclusividade de identificação de uma linha em sua própria tabela. A **Chave Estrangeira** referencia e conecta registros ao apontar para a PK de outra tabela.|
|**Superchave**|**Chave Primária**|Toda **Chave Primária** é uma superchave, mas nem toda superchave é PK. A **Superchave** pode conter atributos extras desnecessários para identificação exclusiva (ex: CPF + ID). A **Chave Primária** é a superchave mínima necessária.|
|**OLTP**|**OLAP**|O **OLTP** trata as transações instantâneas do dia a dia da operação de escrita imediata. O **OLAP** é projetado para análise analítica complexa e processamento de consultas históricas.|
|**Dependência Parcial**|**Dependência Transitiva**|A **Dependência Parcial** ocorre quando um atributo depende de apenas parte de uma chave primária composta. A **Dependência Transitiva** ocorre quando o atributo depende de outra coluna que não é chave primária.|

---

## Pontos importantes para prova

1. **Requisitos e características de um Banco de Dados**: Coleção organizada e lógica de dados com significado implícito; criado para atender a propósitos específicos e usuários predefinidos; representa de forma síncrona o minimundo real.
2. **Ciclo de Vida do Banco de Dados (Ordem Correta)**: $$\text{Planejamento} \rightarrow \text{Análise} \rightarrow \text{Desenvolvimento} \rightarrow \text{Implementação} \rightarrow \text{Manutenção}$$
3. **Estrutura básica de um Dicionário de Dados**: Nomes e propriedades de tabelas, atributos e chaves lógicas; domínios de dados e comprimentos físicos de caracteres; registros de acessos e permissões de privilégios de usuários.
4. **As 12 Regras de Codd para SGBDs Relacionais**: 1) Informações; 2) Acesso garantido; 3) Tratamento de nulos; 4) Catálogo ativo; 5) Escrita em bloco; 6) DML abrangente; 7) Independência física; 8) Independência lógica; 9) Atualização de visões; 10) Independência de integridade; 11) Independência de distribuição; 12) Regra não subversiva.
5. **Exceções e Critérios ao escolher Chaves Primárias**:\
    - _Tamanho_: Optar por atributos de tamanho reduzido para consultas físicas rápidas.\
    - _Estabilidade_: O valor deve ser constante. Se for necessário atualizar, deve-se gerar um log novo ou suportar o custo operacional alto de atualização em cascata.\
    - _Preenchimento_: Chaves primárias devem ser obrigatoriamente preenchidas (não nulas).
6. **Atributos com borda dupla no DER**: Representam atributos multivalorados (ex: telefones).
7. **Atributos com linha tracejada no DER**: Representam atributos derivados (ex: idade obtida dinamicamente da data de nascimento).
8. **Eliminação do precoTotal no processo de normalização (3FN)**: Campos derivados calculados matematicamente a partir de outros atributos (ex: `Quantidade * precoUnitario`) devem ser eliminados da modelagem física, pois podem ser extraídos de forma dinâmica em consultas.

---

## Revisão rápida

### 1. Elementos Básicos de Modelagem

- **Conceitual**: Regras de negócio de alto nível independente de tecnologia.
- **Lógico**: Estruturação lógicas das tabelas (relacional, OO, etc.).
- **Físico**: Implementação física detalhando tipos de campos, tamanhos e índices do SGBD.

### 2. Formas Normais Chave

- **1FN**: Atributos atômicos e indivisíveis. Sem grupos repetitivos.
- **2FN**: Estar na 1FN. Atributos não chave devem depender da totalidade de chaves primárias compostas.
- **3FN**: Estar na 2FN. Remover dependências transitivas (atributos não chave que dependem de outros atributos não chave).
- **FNBC**: Estar na 3FN. Todos os determinantes devem ser chaves candidatas.
- **4FN**: Estar na 3FN. Remover dependências multivaloradas (M:N ou relacionamentos ternários desnecessários).

### 3. Requisitos ACID (Transações SGBD)

- **A**tomicidade: Executa tudo com sucesso ou reverte totalmente lógicas parciais (_rollback_).
- **C**onsistência: Mantém a integridade e regras lógicas ao final da execução.
- **I**solamento: Transações simultâneas não interferem umas nas outras.
- **D**urabilidade: Informações gravadas persistem de forma segura mesmo em caso de falhas.

---
