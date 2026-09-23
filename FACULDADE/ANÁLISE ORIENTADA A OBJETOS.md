[[EXEMPLOS-PRÁTICOS DE ANÁLISE ORIENTADA A OBJETOS]]
#ASSUNTO

# Modelagem e Análise Orientada a Objetos com UML e Processo Unificado

## Visão geral

A **Linguagem de Modelagem Unificada (UML)** é um padrão visual universal adotado pela indústria para especificar, visualizar, construir e documentar os artefatos de sistemas de software orientados a objetos. Ela não se constitui como um processo de desenvolvimento ou metodologia própria, mas sim como uma linguagem independente de processos. Para que sua eficácia seja maximizada, a UML deve ser integrada a um processo de desenvolvimento de software, sendo o **Processo Unificado (UP)** o modelo iterativo e incremental idealmente concebido para essa finalidade. Juntos, UML, UP e o paradigma de **Orientação a Objetos (OO)** fornecem um framework robusto para transformar requisitos complexos de negócios em soluções tecnológicas funcionais, consistentes e escaláveis.

---

## Conceitos principais

Para dominar a matéria, é preciso compreender claramente os seguintes fundamentos:

- **UML (Unified Modeling Language)**: Uma ferramenta de modelagem baseada inteiramente em modelos. Captura aspectos críticos do sistema e omite detalhes irrelevantes por meio da abstração. É composta por 14 diagramas divididos em perspectivas estruturais e comportamentais (que englobam as de interação).
- **Processo Unificado (UP)**: Metodologia de desenvolvimento de software de ciclo de vida iterativo e incremental. É **dirigido por casos de uso** (foco no cliente), **centrado na arquitetura** e **orientado a riscos**.
- **Paradigma Orientado a Objetos (OO)**: Modelo de desenvolvimento centrado na organização do software em torno de entidades do mundo real chamadas **objetos**, os quais combinam dados (atributos) e comportamentos (métodos).
- **Classe**: Definição abstrata, molde, plano ou "receita" genérica que especifica as características e ações comuns a um grupo de objetos. Não existe concretamente por si só.
- **Objeto**: Instância física e concreta de uma classe, criada seguindo o plano definido por ela. Cada objeto possui valores específicos para seus atributos e responde aos mesmos comportamentos estipulados pela classe.
- **Abstração**: Princípio que simplifica a complexidade, isolando as características essenciais de uma entidade e ocultando detalhes técnicos desnecessários de sua implementação interna.

---

## Conteúdo explicado

### 1. Os Quatro Pilares da Orientação a Objetos (OO)

A OO sustenta-se sobre quatro conceitos estruturais que garantem modularidade e manutenibilidade ao código:

```
                     ┌────────────────────────┐
                     │     PILAREES DA OO     │
                     └───────────┬────────────┘
         ┌───────────────────────┼───────────────────────┐
┌────────▼───────┐      ┌────────▼───────┐      ┌────────▼───────┐
│   Abstração    │      │Encapsulamento  │      │    Herança     │
│Foco no         │      │Ocultamento do  │      │Reuso de código │
│essencial │      │estado interno  │      │e hierarquias   │
└────────────────┘      │            │      │            │
                        └────────────────┘      └────────┬───────┘
                                                ┌────────▼───────┐
                                                │ Polimorfismo   │
                                                │Comportamentos  │
                                                │variáveis  │
                                                └────────────────┘
```

1. **Abstração**: Focar no "o que" o objeto faz, em vez de "como" faz. _Exemplo: Um designer define que um boneco de ação deve mover os braços e falar, sem detalhar o circuito eletrônico interno que fará isso._
2. **Encapsulamento**: Esconder os detalhes internos de funcionamento do objeto, expondo somente uma interface externa segura (métodos de acesso). _Exemplo: O compartimento de bateria de um brinquedo é protegido por um parafuso (privado); o usuário interage apenas com os botões externos (públicos) para fazê-lo falar._
3. **Herança (Generalização)**: Mecanismo que permite a uma classe (**subclasse**) herdar características (atributos) e comportamentos (métodos) de outra classe (**superclasse**). Promove o reuso direto de código. _Exemplo: A subclasse "Aventureiro" herda os atributos de "Boneco de ação" e adiciona o atributo "mochila" e o método "escalar"._
4. **Polimorfismo**: Propriedade que permite tratar diferentes subclasses de forma uniforme sob uma mesma interface de superclasse, respondendo a um mesmo comando de maneiras específicas. _Exemplo: Chamar o método `moverBraço()` no objeto "Super Max" faz com que ele dispare um raio; no objeto "Explorador Jack", faz com que ele segure uma corda._

### 2. O Processo Unificado (UP) e sua Integração com a UML

O ciclo de vida do UP é dividido em **quatro fases consecutivas**, distribuídas no tempo, que realizam múltiplos miniprojetos chamados **iterações**:

```
   Concepção ──► Elaboração ──► Construção ──► Transição ──► Produção
  (Iniciação)   (Arquitetura)  (Desenvolvimento)  (Entrega)  (Suporte Operacional)
```

1. **Concepção (Iniciação)**: Define o escopo do projeto, elabora os casos de uso iniciais e o modelo de negócios, identifica riscos críticos e planeja o orçamento.
    - _UML utilizada_: Principalmente Diagrama de Casos de Uso e de Atividades para mapear o negócio.
2. **Elaboração**: Detalha a arquitetura do sistema e os requisitos funcionais, expandindo os casos de uso e mitigando riscos técnicos e de negócio.
    - _UML utilizada_: Esboço do Diagrama de Classes, Objetos, Sequência, Colaboração e Componentes para consolidar a arquitetura técnica.
3. **Construção**: Implementa as funcionalidades do software com base na arquitetura estabelecida. O desenvolvimento ocorre em iterações curtas de programação e testes concorrentes.
    - _UML utilizada_: Refinamento detalhado de Diagramas de Classes (tipos de dados e visibilidade), Sequência, Colaboração, Máquina de Estados e Implantação.
4. **Transição**: Prepara o software finalizado para entrega aos usuários. Realiza testes de aceitação (fase beta), correções finais de bugs, documentação e treinamento.
    - _UML utilizada_: Finalização do Diagramas de Implantação, Componentes e Pacotes.
5. **Produção (Pós-Transição)**: Monitoramento contínuo do software em ambiente operacional e suporte de infraestrutura.

---

### 3. Modelagem de Requisitos: Diagrama de Casos de Uso

É tradicionalmente o primeiro diagrama a ser construído. Seu principal propósito é capturar as interações de forma visual para validação de requisitos funcionais com o cliente.

- **Ator**: Entidade externa (usuário, hardware ou outro sistema) que desempenha um papel interagindo com o sistema. É representado por um boneco ("stick figure").
- **Caso de Uso**: Representado por uma elipse. Descreve uma funcionalidade de alto nível do sistema. Recomenda-se nomeá-lo com a estrutura **VERBO + SUBSTANTIVO** (_Exemplo: `sacarDinheiro()`_).
- **Relacionamentos de Casos de Uso**:
    - **Associação**: Linha contínua ligando um ator a um caso de uso, denotando interação. No modelo, um único caso de uso não pode ser iniciado simultaneamente por dois atores.
    - **Generalização**: Representada por uma linha contínua com uma seta vazia na ponta, apontando do caso de uso filho para o caso de uso pai. O filho herda e especializa o comportamento do pai. _Exemplo: "Efetuar Pagamento" (pai) especializado por "Pagar com Cartão" e "Pagar com Cheque" (filhos)._
    - **Inclusão (`<<include>>`)**: Representa uma dependência **obrigatória**. A execução do caso de uso de origem obriga a execução do caso de uso incluído. _Exemplo: `Realizar Compra` inclui obrigatoriamente `Autenticação`._
    - **Extensão (`<<extend>>`)**: Representa uma dependência **opcional/condicional**. O caso de uso estendido só executa sob condições específicas definidas em um ponto de extensão (_extension point_). _Exemplo: `Visualizar Item` pode ser estendido condicionalmente por `Colocar no Carrinho` se o cliente clicar no botão correspondente._
- **Multiplicidade**: Indica quantos atores podem executar um caso de uso simultaneamente. Representada na linha de associação por intervalos (_Exemplo: `2..4` para indicar entre 2 e 4 participantes_).

---

### 4. Modelagem Estrutural Básica a Avançada

Os diagramas estruturais focam na organização estática e estável das partes do sistema:

#### A. Diagrama de Classes

Diagrama estrutural mais importante.

- **Atributos**: Devem ser **atômicos** (indivisíveis), sem agrupar subcampos compostos como endereço completo em um único campo.
- **Modificadores de Acesso (Encapsulamento)**:
    - `+` **Public**: Manipulação livre por qualquer classe do sistema.
    - `-` **Private**: Acesso restrito apenas à própria classe que o declarou.
    - `#` **Protected**: Acesso restrito à própria classe e às suas subclasses (herança).
    - `~` **Package**: Visibilidade limitada aos membros de um mesmo namespace/pacote.
- **Perspectivas de Detalhamento do Diagrama**:
    1. _Conceitual_: Modela relacionamentos entre entidades lógicas do negócio.
    2. _Especificação_: Foca nas responsabilidades das interfaces e assinaturas de métodos (nível arquitetural).
    3. _Implementação_: Nível físico e detalhado. Define tipos de dados exatos dos atributos, visibilidade dos métodos e parâmetros de retorno em concordância com a linguagem de programação final.
- **Agregação (`Todo-Parte Fraco`)**: Representada por um losango sem preenchimento na extremidade da classe "Todo". Indica que a "Parte" pode existir independentemente da destruição da classe "Todo". _Exemplo: Um `Carro` e seu `Estepe`._
- **Composição (`Todo-Parte Forte`)**: Representada por um losango preenchido na extremidade da classe "Todo". Significa que a "Parte" **não possui existência independente** fora do ciclo de vida da classe "Todo". _Exemplo: Um `Prédio` e seus `Apartamentos`._

#### B. Diagrama de Objetos

Retrata uma "fotografia" ou instantâneo estático do estado físico das instâncias em tempo de execução.

- **Convenção de Nomenclatura**: Exibida em um retângulo dividido, onde os dados do cabeçalho são sublinhados e podem usar os formatos: `nomeDoObjeto : NomeDaClasse` (detalhado), `: NomeDaClasse` (objeto anônimo) ou simplesmente `nomeDoObjeto`.
- **Vínculos (Links)**: Instâncias das associações de classes. Ligam um único objeto a outro sem multiplicidade, ilustrando o estado exato dos relacionamentos em um dado momento.
- **Estereótipo `<<instantiate>>`**: Representa graficamente, por meio de uma dependência direcionada, a ação de uma classe instanciar um objeto dinamicamente.

#### C. Diagrama de Pacotes

Agrupa elementos lógicos relacionados para modularizar e reduzir a complexidade arquitetural de sistemas complexos.

- **Relacionamentos**: Setas tracejadas que indicam dependência, importação ou direitos de acesso entre pacotes. Se o pacote de origem sofrer modificações, o pacote dependente pode ser diretamente impactado.

#### D. Diagrama de Componentes

Modela as partes físicas, lógicas e modulares que são encapsuladas e interagem por meio de interfaces explícitas.

- **Portas**: Pequenos quadrados na borda do componente que funcionam como pontos de entrada e saída, isolando o funcionamento interno de acessos externos diretos.
- **Interfaces**:
    - _Fornecida_ (Notação "pirulito" ou esfera): Representa o serviço disponibilizado pelo componente para consumo.
    - _Requerida_ (Notação "soquete" ou semicírculo): Indica os serviços externos dos quais o componente depende para operar.
- **Visões de caixa**:
    - _Caixa preta_: Oculta as classes internas do componente, exibindo apenas as portas e conexões de interface externas.
    - _Caixa branca_: Expõe detalhadamente as classes, componentes menores e dependências que implementam as funções do componente principal.
- **Estereótipos do Diagrama**: `<<executable>>` (arquivo executável ou bytecode), `<<library>>` (biblioteca de reuso), `<<table>>` (persistência em banco de dados), `<<document>>` (manuais/arquivos texto) e `<<file>>` (qualquer tipo de arquivo).

#### E. Diagrama de Estrutura Composta

Foca especificamente em ilustrar colaborações estruturais de instâncias de classes e componentes que cooperam dinamicamente para a execução de um caso de uso, sem se preocupar em detalhar o comportamento sequencial em si.

---

### 5. Modelagem Comportamental e Dinâmica

Os diagramas comportamentais detalham os fluxos de processos, eventos e troca de mensagens no decorrer do tempo:

#### A. Diagrama de Atividades

Funciona como um gráfico de fluxo que detalha o comportamento lógico interno de casos de uso complexos e processos de negócios.

- **FORK (Bifurcação)**: Uma barra transversal sólida que divide um único fluxo de controle sequencial em múltiplos fluxos executados de forma paralela/concorrente.
- **JOIN (Junção)**: Uma barra transversal sólida que atua sincronizando os fluxos paralelos em um único fluxo final consolidado.
- **Swimlanes (Partições/Raias)**: Divisões lógicas verticais ou horizontais que organizam as atividades, atribuindo responsabilidade específica para cada unidade, objeto ou ator do processo.

```
                     ┌────────────────────────┐
                     │ DIAGRAMA DE ATIVIDADES │
                     └───────────┬────────────┘
                                 │
                            ● Estado Inicial
                                 │
                            ┌────▼────┐
                            │ Passo 1 │
                            └────┬────┘
                                 │
                           ══════╧══════ FORK (Inicia fluxos concorrentes)
                                ┌┴┐
         ┌──────────────────────▼─▼──────────────────────┐
   ┌─────▼─────┐                                   ┌─────▼─────┐
   │ Passo 4.1 │ (Fluxo Concorrente)               │ Passo 4.2 │
   └─────┬─────┘                                   └─────┬─────┘
         └──────────────────────┬─┬──────────────────────┘
                                └┬┘
                           ══════╤══════ JOIN (Sincroniza fluxos concorrentes)
                                 │
                            ┌────▼────┐
                            │ Passo 5 │
                            └────┬────┘
                                 │
                            ◉ Estado Final
```

#### B. Diagrama de Máquina de Estados

Especifica o ciclo de vida dos objetos de uma determinada classe que possuem comportamento dependente de estado relevante.

- **Eventos**: Ocorrência de estímulos em um determinado momento que disparam alterações de estado nos objetos.
- **Escolha (Choice)**: Ponto de decisão representado por um losango que ramifica a transição de estados sob diferentes condições de guarda.
- **Ações de Estado**:
    - `entry`: Operação executada imediatamente quando o objeto entra em um determinado estado.
    - `exit`: Operação ativada no momento exato em que o objeto deixa um estado.
    - `do`: Atividade que ocorre continuamente enquanto o objeto permanece ativo em um determinado estado.
- **Pseudostates de Histórico**:
    - _Histórico Superficial (Shallow)_: Representado por um círculo com a letra **H**. Lembra qual estado composto estava ativo antes de uma interrupção, mas descarta o estado interno de seus subestados.
    - _Histórico Profundo (Deep)_: Representado por um círculo com a letra **H***. Salva e restaura toda a configuração de estados e subestados internos.

#### C. Diagrama de Sequência

Diagrama de interação mais utilizado. Foca estritamente na representação da **ordenação temporal das mensagens** trocadas entre objetos ao longo do eixo vertical cronológico.

- **Mensagem Síncrona**: O emissor bloqueia o seu fluxo e aguarda obrigatoriamente a resposta do receptor para continuar a interação. Representada por uma linha sólida com seta preenchida.
- **Mensagem Assíncrona**: O emissor continua seu processamento sem esperar o retorno do receptor. Representada por uma linha sólida com seta aberta.
- **Mensagem de Retorno**: Retorna dados ao emissor. Representada por uma linha tracejada com seta aberta.
- **Foco de Controle**: Barra retangular vertical estreita que marca o tempo em que o objeto está executando uma ação.
- **Mensagem de Autochamada (Reflexiva)**: Mensagem em que o objeto remetente é também o receptor, executando um comportamento interno.
- **Fragmentos Combinados**: Quadros de interação que organizam condições: `alt` (se-então-senão), `opt` (comportamento condicional opcional) e `loop` (iteração repetitiva).

#### D. Diagrama de Comunicação (antigo Colaboração)

Representação alternativa ao Diagrama de Sequência. Foca em destacar a **organização estrutural** e as associações entre os objetos dinâmicos.

- **Numeração Sequencial Obrigatória**: Como não possui uma escala de tempo vertical, a ordem lógica das mensagens deve ser explicitada por números compostos nos rótulos (_Exemplo: `1`, `1.1`, `1.1.1`_).
- **Multiobjeto**: Representa graficamente, por meio de retângulos sobrepostos, uma coleção de dados (uma lista ou associação de um-para-muitos) envolvida no fluxo de mensagens.

---

### 6. Transição de Análise para Projeto

A modelagem de análise (lógica e independente de tecnologia) evolui gradualmente para a modelagem de projeto (física e específica do ambiente computacional).

#### Atividades Críticas de Transição:

- **Refinamento de Classes**: Classes de análise abstratas podem ser desmembradas em múltiplos módulos físicos específicos.
- **Definição Exata dos Tipos de Dados**: Substitui pseudocódigos conceituais por especificações exatas da linguagem final (_Exemplo: atributos String, BigDecimal, Date em Java_).
- **Estereotipagem Detalhada**: Classificação das classes de acordo com as responsabilidades arquiteturais do sistema:
    - `<<boundary>>` (**Fronteira**): Interfaces de usuário ou pontos de integração de entrada e saída.
    - `<<control>>` (**Controle**): Classes intermediárias que gerenciam a lógica de negócios e o fluxo da aplicação.
    - `<<entity>>` (**Entidade**): Dados persistentes do domínio do negócio, armazenados em bancos de dados.
- **Estereótipo `<<enumeration>>`**: Criação de classes para representar o conjunto limitado de estados de atributos de situação (_Exemplo: Enumerados de situação de contratos, carros e pessoas_).
- **Arquitetura e Reuso**: Incorporação de frameworks, componentes reaproveitáveis de terceiros, definição física de algoritmos de processamento de interface (IHC) e adoção de Padrões de Projeto (_Design Patterns_).

---

### 7. Persistência de Objetos no Modelo Relacional (Mapeamento Objeto-Relacional - MOR)

Procedimento fundamental para traduzir a estrutura orientada a objetos (UML) em tabelas, colunas e chaves de Bancos de Dados Relacionais (SGBDR):

```
                    ┌─────────────────────────┐
                    │ CLASSES DO MODELO DE OO │
                    └────────────┬────────────┘
                                 │  Se persistente
                                 ▼
                     Mapeado para tabelas
                                 │
         ┌───────────────────────┼───────────────────────┐
┌────────▼───────┐      ┌────────▼───────┐      ┌────────▼───────┐
│ Atributos ──►  │      │Associação 1..* │      │Associação *..* │
│ Colunas  │      │Chave Estrang.  │      │Tabela Interm.  │
│                │      │(FK)      │      │com PK composta │
└────────────────┘      └────────────────┘      │           │
                                                └────────────────┘
```

#### Regras de Ouro de Mapeamento:

1. **Identificação de Objetos**: Apenas objetos **persistentes** (principalmente entidades) são mapeados em tabelas físicas. Objetos **transientes** (fronteiras e controles) duram apenas a sessão e não são persistidos.
2. **Mapeamento de Atributos**: Cada atributo simples vira uma coluna. Atributos derivados de cálculos dinâmicos não são mapeados em colunas permanentes.
3. **Identidade de Objeto (Id)**: Toda tabela deve possuir um atributo único sublinhado representando a Chave Primária (PK), garantindo o princípio de identidade independente dos objetos.
4. **Chave Estrangeira (FK)**: Representada com sublinhado tracejado.

#### Estratégias de Relacionamentos:

- **Associação Binária 1..* (Um-para-Muitos)**: O identificador (PK) da tabela do lado "1" é inserido como chave estrangeira (FK) na tabela do lado "Muitos".
- **Associação Binária 1..1 (Um-para-Um)**: É possível mapear as classes em tabelas distintas ligadas por FK ou unificar todos os atributos em uma única tabela de banco de dados.
- **Associação *..* (Muitos-para-Muitos)**: Cria-se uma terceira tabela intermediária (tabela de junção) cuja Chave Primária é composta pelas PKs de ambas as tabelas originais.
- **Classe Associativa**: Cada classe vira uma tabela. A classe associativa vira uma terceira tabela contendo as FKs das classes originais.
- **Agregação**: Segue as mesmas regras das associações binárias (PK do todo inserida como FK na tabela da parte).
- **Composição**: As tabelas do "Todo" e da "Parte" são criadas de forma separada. A PK da classe "Todo" deve fazer parte integrante da PK composta da tabela que representa a "Parte".

#### Três Abordagens para Mapeamento de Generalização (Herança):

|Estratégia de Herança|Descrição|Vantagens|Desvantagens|
|:--|:--|:--|:--|
|**Alternativa 1 (Tabelas Compartilhadas)**|Cria tabelas individuais para a superclasse e para cada subclasse, compartilhando o mesmo "Id" (PK). Um atributo discriminador de `tipoPessoa` é adicionado à tabela da superclasse.|Alta normalização de dados; evita colunas em branco.|Exige navegação (JOINs) complexos entre as tabelas, afetando o desempenho.|
|**Alternativa 2 (Tabelas por Subclasse)**|Elimina a tabela da superclasse. Cria tabelas apenas para as subclasses, copiando todos os atributos herdados da superclasse em cada tabela resultante.|Excelente desempenho de consulta direta para registros de tipos específicos; sem JOINs.|Desperdício de reuso; redundância na definição de colunas; tabelas duplicando herança.|
|**Alternativa 3 (Tabela Única/Mesa Diretora)**|Unifica todos os atributos das subclasses e da superclasse em uma única tabela contendo uma coluna para o discriminador de tipo.|Máxima velocidade de consulta; sem JOINs; extremamente simples de ler.|Muitas colunas nulas (em branco) no banco de dados para os atributos que não pertencem à subclasse do registro.|

---

## Conceitos que não posso confundir

A tabela de mapeamento de diferenças ajuda a blindar a memorização contra conceitos parecidos:

```
┌────────────────────────────────────────────────────────┐
│               DIFERENÇAS CRUClAIS                      │
├────────────────────────────────────────────────────────┤
│ Associação 1..* ──► FK na tabela do lado "Muitos"│
│ Associação *..* ──► Terceira tabela (Junção)     │
│ Agregação ───────► PK do Todo é FK na Parte      │
│ Composição ──────► PK do Todo é parte da PK da Parte   │
│                                                  │
└────────────────────────────────────────────────────────┘
```

- **Diagrama de Sequência vs. Diagrama de Comunicação**:
    - _Sequência_: Eixo do tempo evidente, focado na ordem temporal vertical de mensagens.
    - _Comunicação_: Sem eixo de tempo. Foca na organização estrutural e vínculos físicos entre objetos. A ordem cronológica exige numeração manual.
- **Agregação vs. Composição**:
    - _Agregação_: Relacionamento fraco. O objeto parte pode sobreviver se o todo for destruído (_Exemplo: O estepe continua existindo se o carro for destruído_).
    - _Composição_: Relacionamento forte. O objeto parte morre junto com o todo (_Exemplo: Apartamentos deixam de existir se o prédio for demolido_).
- **Inclusão (`<<include>>`) vs. Extensão (`<<extend>>`)**:
    - _Inclusão_: Comportamento obrigatório. O caso incluído sempre é executado.
    - _Extensão_: Comportamento opcional. O caso extensivo só é ativado se atender a condições pré-estabelecidas no ponto de extensão.
- **Símbolo Final vs. Símbolo Terminal (Diagrama de Atividades)**:
    - _Final_ (Círculo preto com borda branca envolta): Encerra completamente todos os processos e fluxos concorrentes ativos no diagrama.
    - _Terminal_ (Círculo azul com um X interno): Encerra apenas um único fluxo de processo concorrente específico. Os outros processos concorrentes continuam executando.
- **Histórico Superficial (`H`) vs. Histórico Profundo (`H*`) (Máquina de Estados)**:
    - _Superficial_: Guarda o último estado ativo de um estado composto antes de uma interrupção, mas descarta detalhes sobre os subestados internos.
    - _Profundo_: Guarda o último estado ativo e recupera inclusive todo o histórico de subestados e caminhos internos percorridos.

---

## Pontos importantes para prova

### 1. Regras de Consistência entre Diagramas UML

Erros de consistência são clássicos em provas. Memorize as regras essenciais para manter os modelos sincronizados:

- O **número de objetos** representados no Diagrama de Sequência deve corresponder exatamente ao número de classes que os instanciaram no Diagrama de Classes.
- Qualquer **atualização ou deleção** na estrutura do Diagrama de Classes deve ser sincronizada e refletida imediatamente no Diagrama de Sequência.
- Se uma **relação de dependência** é expressa no Diagrama de Classes, deve ocorrer ao menos uma troca de mensagem entre os objetos dessas classes no Diagrama de Sequência. Caso não exista nenhuma mensagem, a dependência deve ser removida do Diagrama de Classes.
- O **nome dos métodos** e operações de classe invocados deve ser estritamente idêntico entre os diagramas de classe e sequência.
- Cada situação mapeada no Diagrama de Casos de Uso deve possuir uma **operação de negócios correspondente** em termos de métodos no Diagrama de Classes.
- Cada Caso de Uso relevante precisa estar representado por pelo menos um **Diagrama de Sequência de cenário principal**.
- Os atores representados interagindo no caso de uso precisam aparecer como **linhas de vida atuantes** no Diagrama de Sequência.

### 2. Detalhes de Implementação e Visibilidade UML

Lembre-se da notação visual exata dos operadores de escopo:

- `+` : Public
- `-` : Private
- `#` : Protected
- `~` : Package

---

## Revisão rápida

### UML e UP

- **UML** = linguagem visual baseada em modelos estáticos e dinâmicos.
- **OMG (1996)** = padronizou a UML criada pelos "three amigos" (Grady Booch, Ivar Jacobson e James Rumbaugh).
- **UML 2.5** = retirou Casos de Uso dos diagramas comportamentais e os alocou como conceitos suplementares.
- **UP** = processo interativo, incremental, dirigido por casos de uso e orientado a riscos.
- **4 Fases do UP** = Concepção, Elaboração, Construção e Transição.

### Diagramas Estruturais

- **Classes** = estrutura de classes, atributos, métodos e visibilidade.
- **Objetos** = instantâneo físico dos atributos e vínculos dinâmicos das instâncias no tempo Y.
- **Componentes** = portas, interfaces fornecidas e requeridas em módulos de software físicos ou lógicos.
- **Pacotes** = organização lógica modular do sistema por pastas/namespaces.

### Diagramas Comportamentais

- **Atividades** = fluxogramas dinâmicos que suportam concorrência (FORK/JOIN) e raias (Swimlanes).
- **Máquina de Estados** = ciclo de vida de objetos reativos contendo ações internas (`entry`, `exit`, `do`).
- **Sequência** = interação de objetos baseada estritamente na ordenação temporal das mensagens.
- **Comunicação** = colaboração focada nas conexões físicas, numerando as mensagens em ordem lógica sequencial.

### Regras de Mapeamento Relacional

- **Classes** \(\rightarrow\) Tabelas.
- **Atributos** \(\rightarrow\) Colunas.
- **Atributos Derivados** \(\rightarrow\) **Não são mapeados** para colunas permanentes.
- **Herança (Generalização)** \(\rightarrow\) 3 alternativas: Tabelas separadas compartilhando ID, tabelas apenas para as subclasses copiando atributos ou tabela única (mesa diretora) contendo discriminador de tipo.

---
