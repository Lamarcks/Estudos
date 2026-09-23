[[EXEMPLOS-PRÁTICOS DE POO]]
#ASSUNTO

## Visão geral

A **Programação Orientada a Objetos (POO)** é um paradigma de programação que surgiu na década de 1960 para solucionar as limitações da abordagem procedural no desenvolvimento de sistemas complexos, facilitando a organização, modularidade, escalabilidade e reutilização de código. Esse paradigma estrutura o software como um conjunto de **objetos** que integram características (atributos/dados) e comportamentos (métodos/operações) e interagem entre si, aproximando a arquitetura do software de conceitos do mundo real. O domínio desse modelo de desenvolvimento permite que aplicações cresçam de forma sustentável e resiliente sem comprometer a qualidade interna do código.

---

## Conceitos principais

Para dominar a POO, é essencial internalizar suas definições fundamentais:

- **Classe:** Funciona como um "molde", plano ou esqueleto básico que descreve as propriedades e os comportamentos comuns a todos os objetos criados a partir dela. Ela define os atributos e métodos que caracterizam um conceito abstrato ou uma entidade do mundo real.
- **Objeto / Instância:** Um objeto é uma instância concreta de uma classe. Ao instanciarmos uma classe, "damos vida" a um objeto que possui um estado individual (valores específicos para seus atributos) e ocupa um espaço reservado na memória do sistema.
- **Atributo:** Variáveis que descrevem o estado e as características específicas de um objeto em um determinado momento.
- **Método (Operação):** Funções implementadas dentro de uma classe que definem as ações, comportamentos e interações que os objetos gerados por ela são capazes de realizar, podendo alterar seu estado interno.
- **Abstração:** O pilar que permite simplificar sistemas complexos ao focar apenas nos aspectos e características essenciais de um objeto para o domínio do problema, ocultando detalhes de implementação desnecessários.
- **Encapsulamento:** Técnica que protege a integridade dos dados de um objeto ao restringir o acesso direto aos seus atributos internos, permitindo que eles sejam manipulados apenas por métodos públicos e controlados.
- **Herança:** Mecanismo pelo qual uma classe filha (subclasse) deriva e herda os atributos e métodos de uma classe pai (superclasse), promovendo a reutilização de código e a criação de hierarquias lógicas.
- **Polimorfismo:** Capacidade que permite que o mesmo método ou comportamento assuma diferentes formas em classes distintas que compartilham uma mesma base comum ou contrato, dependendo do objeto no qual é invocado.
- **Interface:** Um contrato formal de design que define quais métodos uma classe implementadora deve possuir (suas assinaturas), mas sem especificar como eles funcionam.
- **Classe Abstrata:** Modelo base conceitual que serve como ponto de partida para outras classes, podendo conter uma mescla de métodos concretos (com lógica definida) e métodos abstratos (apenas declarados).

---

## Conteúdo explicado

### 1. Fundamentos, Evolução e Ferramentas de Desenvolvimento

#### Histórico e Motivação

Antes da POO se consolidar, a programação era dominada pelo paradigma **procedural**, fundamentado em sequências lineares de instruções estruturadas em funções. Conforme os sistemas cresceram, essa abordagem revelou-se de difícil manutenção. Na década de 1960, a linguagem **Simula** (desenvolvida na Noruega) introduziu as classes pela primeira vez, permitindo agrupar dados e comportamentos afins. Mais tarde, linguagens como **Smalltalk** e **C++** popularizaram o paradigma e confirmaram as vantagens da modularidade de código.

#### O Ecossistema de Desenvolvimento

O desenvolvimento moderno de software sob o paradigma orientado a objetos apoia-se em três pilares instrumentais:

1. **Linguagens de Programação:**
    - **Java:** Popular e robusta, projetada sob a premissa de portabilidade: "escrever uma vez, rodar em qualquer lugar" (WORA).
    - **Python:** Linguagem versátil e de aprendizagem intuitiva que oferece suporte para o desenvolvimento OO, mesmo sem ser puramente orientada a objetos.
    - **C++:** Baseada na linguagem C clássica, introduz suporte à POO sendo essencial para sistemas que demandam extrema eficiência e controle de recursos (como jogos e sistemas operacionais).
2. **Ambientes de Desenvolvimento Integrado (IDEs):** Centralizam as etapas de criação, compilação, navegação hierárquica e depuração do código. Exemplos amplamente empregados incluem o **Eclipse** (com forte ecossistema para Java e desenvolvimento de interfaces gráficas), o **IntelliJ IDEA**, o **NetBeans** e o **PyCharm** (específico para manipulação ágil de Python).
3. **Frameworks:** Estruturas modulares pré-definidas para acelerar o desenvolvimento corporativo:
    - **Spring (Java):** Simplifica o design de aplicações empresariais robustas.
    - **Django (Python):** Direcionado para o desenvolvimento web pragmático focado em classes de dados e seus relacionamentos.
    - **Qt (C++):** Biblioteca de alto desempenho para interfaces gráficas interativas e multiplataforma.

---

### 2. Classes, Objetos e a Arquitetura de Memória

#### Estrutura de uma Classe

Graficamente ou em código, uma classe representa formalmente uma entidade com três divisões essenciais:

1. **Nome da Classe:** Substantivo que identifica a classe, iniciando obrigatoriamente com letra maiúscula e sem caracteres de espaçamento.
2. **Atributos:** Variáveis de instância que representam as propriedades internas que descrevem a entidade.
3. **Métodos (ou Operações):** Representam os comportamentos da classe.

```
// Estrutura básica em Java
public class Pessoa {
    // Atributos
    String nome;
    int idade;

    // Método
    void apresentar() {
        System.out.println("Meu nome é " + nome + " e tenho " + idade + " anos.");
    }
}
```

#### Instanciação de Objetos e Alocação na Memória

A classe serve apenas como modelo estático e não ocupa memória física voltada ao armazenamento de dados. O processo de criação de um objeto, chamado **instanciação**, é realizado pela palavra-chave `new` em Java. O ciclo de criação segue as etapas:

1. **Declaração:** Definição do tipo da variável de referência (o tipo da Classe).
2. **Instanciação:** Alocação dinâmica de memória via operador `new`.
3. **Inicialização:** Execução do método construtor para definir o estado de partida.

Cada objeto instanciado possui suas próprias cópias de atributos na memória heap do sistema. No ecossistema Java, o programador é poupado da liberação manual de recursos pelo **Garbage Collector**, um mecanismo que limpa automaticamente os objetos que perderam suas referências ativas, prevenindo lentidão por vazamento de memória.

---

### 3. Construtores e Sobrecarga

#### Métodos Construtores

O construtor é um bloco de inicialização obrigatório cuja função primária é preparar o objeto para ser utilizado de maneira consistente logo no momento da criação. Em Java, o construtor possui duas regras sintáticas invioláveis:

1. Deve possuir **exatamente o mesmo nome da classe**.
2. **Nunca possui tipo de retorno**, nem mesmo `void`.

Se nenhum construtor for explicitamente escrito pelo programador, o compilador fornece um construtor padrão vazio.

#### Sobrecarga (Overloading) de Construtores e Métodos

A **sobrecarga** consiste em fornecer múltiplas versões de um mesmo método ou construtor dentro da mesma classe, alterando exclusivamente o número, a ordem ou o tipo de seus parâmetros de entrada.

```
public class Carro {
    private String modelo;
    private int ano;
    private String cor;

    // Construtor sem parâmetros (Padrão) - Atribui valores padrão
    public Carro() {
        this("Modelo desconhecido", 0, "Cor indefinida"); // Reutilização de construtor
    }

    // Construtor com um único parâmetro
    public Carro(String modelo) {
        this(modelo, 2022, "Cor padrão"); // Encaminhamento lógico
    }

    // Construtor com parâmetros completos
    public Carro(String modelo, int ano, String cor) {
        this.modelo = modelo;
        this.ano = ano;
        this.cor = cor;
    }
}
```

> [!TIP] **Boas Práticas:** Use a palavra-chave `this()` no início de seus construtores adicionais para invocar o construtor principal com maior número de parâmetros. Isso centraliza a lógica de validação de estado, reduz a repetição e evita listas longas e confusas de variáveis desorganizadas.

---

### 4. Controle de Fluxo: Decisão e Repetição no Contexto OO

#### Estruturas de Decisão e Lógica Limpa (Clean Code)

Para dar dinamismo ao comportamento das instâncias, as estruturas de seleção avaliam expressões condicionais lógicas ou relacionais:

- **`if` (Desvio Simples):** Executa o bloco se o booleano for verdadeiro.
- **`if-else` (Desvio Composto):** Fornece dois caminhos exclusivos de fluxo de acordo com a lógica.
- **`if-else if` (Desvio Encadeado):** Ideal para verificar múltiplas expressões sequencialmente.
- **`switch-case`:** Executa um bloco de código específico comparando diretamente uma única variável de teste contra uma lista estática de casos. É indispensável o uso da palavra-chave `break` ao fim de cada bloco para evitar que o fluxo seja indevidamente propagado pelos casos seguintes.

#### Operadores Relacionais e Lógicos

|Operador|Significado|Exemplo Java|
|:-:|:-:|:-:|
|`==`|Igual a|`if (valor == 10)`|
|`!=`|Diferente de|`if (valor != 10)`|
|`>`|Maior que|`if (valor > 10)`|
|`<`|Menor que|`if (valor < 10)`|
|`>=`|Maior ou igual a|`if (valor >= 10)`|
|`<=`|Menor ou igual a|`if (valor <= 10)`|
|`&&`|E lógico (Todas verdadeiras)|`if (idade >= 18 && exp >= 2)`|
|`\|\|`|
|`!`|NÃO lógico (Inverte o booleano)|`if (!ativo)`|

> [!IMPORTANT] **Condições Limpas (Clean Code):** Dê preferência por lógica linear sequencial com `else if` ao invés de estruturas condicionais aninhadas (`if` dentro de `if`), as quais prejudicam seriamente a leitura e o entendimento do código por outros desenvolvedores. Use variáveis com nomes lógicos claros para explicitar o propósito da validação.

#### Estruturas de Repetição (Laços de Iteração)

- **`while`:** Executado repetidamente enquanto a sua condição condicional permanecer verdadeira. Apropriado quando não se conhece de antemão o total exato de iterações requeridas.
- **`for`:** Estrutura sintática compacta contendo inicialização, expressão condicional de parada e incremento. Altamente indicado quando o número de iterações é previamente conhecido.
- **`do-while`:** Difere do laço `while` clássico pois garante que o bloco de código interno seja executado **pelo menos uma vez** antes que a verificação condicional de parada seja realizada.
- **Comandos de Interrupção de Laço:**
    - **`break`:** Interrompe a execução do laço de repetição imediatamente, pulando para a linha subsequente ao escopo do laço.
    - **`continue`:** Aborta a iteração corrente, ignorando o restante das instruções internas daquela passagem, e salta diretamente para o cálculo de incremento ou próxima validação do laço.

---

### 5. Herança, Interfaces e Classes Abstratas

#### Herança (Inheritance)

Estabelece uma relação lógica de especialização do tipo **"é-um"** entre classes. A subclasse herda as definições de métodos e atributos de sua superclasse por meio da declaração `extends`:

```
// Superclasse
public class Animal {
    protected String nome; // Acessível à subclasse

    public void emitirSom() {
        System.out.println("O animal faz um som.");
    }
}

// Subclasse
public class Cachorro extends Animal {
    @Override
    public void emitirSom() { // Sobrescrita (Override)
        System.out.println("O cachorro late.");
    }
}
```

Apesar de poupar esforço e duplicidade de código, o uso irrefletido de herança causa acoplamento forte (qualquer mudança estrutural na classe pai propaga-se de maneira rígida pelas classes herdeiras, o que pode causar falhas imprevistas em partes do sistema).

#### Interfaces como Contratos de Comportamento

Uma interface especifica quais métodos devem existir sem impor nenhuma lógica interna, atuando como um contrato. As classes implementam esse contrato usando `implements`. O Java permite que uma única classe implemente **múltiplas interfaces**, superando a barreira da herança única.

#### Classes Abstratas

Uma classe abstrata (declarada com `abstract`) não pode ser diretamente instanciada via `new`. Ela estabelece um esqueleto comum que serve como ponto de partida para outras subclasses. Pode conter:

- **Métodos Concretos:** Possuem corpo de execução predefinido que é herdado ou redefinido pelas classes filhas.
- **Métodos Abstratos:** Possuem apenas a assinatura declarada e **devem ser obrigatoriamente implementados** pelas subclasses concretas.

---

### 6. Tratamento de Exceções (Exception Handling)

Exceções são eventos anômalos que rompem o andamento regular de execução de um sistema. O tratamento profissional impede encerramentos abruptos e preserva a integridade de dados corporativos.

#### Categorias de Exceções em Java

1. **Checked Exceptions (Exceções Verificadas):** São validadas pelo compilador em tempo de compilação. O código é obrigado a declarar que as lança ou a envolvê-las em tratamento. Exemplos: `IOException` e `SQLException`.
2. **Unchecked Exceptions (Exceções Não Verificadas):** Erros de lógica que ocorrem em tempo de execução e não são forçados pelo compilador. Exemplos: `ArithmeticException` (ex: divisão por zero), `NullPointerException` (referência a objetos nulos) e `ArrayIndexOutOfBoundsException` (índices inválidos).

#### A Estrutura Try-Catch-Finally

```
try {
    // Código de risco que pode disparar uma exceção
    int resultado = 10 / 0;
} catch (ArithmeticException e) {
    // Escopo que trata a ocorrência da falha
    System.out.println("Erro: Divisão por zero.");
} finally {
    // Executado SEMPRE, ocorrendo erro ou não. Essencial para liberar recursos abertos
    System.out.println("Liberação de recursos concluída.");
}
```

#### Exceções Personalizadas

É possível criar exceções sob medida estendendo a classe básica `Exception` (checked) ou `RuntimeException` (unchecked), permitindo isolar a sinalização de erros de negócio.

```
// Criação da exceção de negócio
class SaldoInsuficienteException extends Exception {
    public SaldoInsuficienteException(String msg) {
        super(msg);
    }
}
```

---

### 7. Arrays, Coleções Dinâmicas e Persistência de Arquivos

#### Arrays Unidimensionais e Multidimensionais

- **Arrays Unidimensionais (Vetores):** Estruturas lineares de tamanho fixo, homogêneas (elementos do mesmo tipo de dado) acessíveis por índices numéricos sequenciais de partida zero. Garantem alto desempenho de leitura e escrita por mapeamento de endereço físico de memória.
- **Arrays Multidimensionais (Matrizes):** Estruturas tabulares organizadas sob linhas e colunas.

```
int[] notas = new int; // Unidimensional estático
int[][] matriz = { {1, 2}, {3, 4} }; // Bidimensional
```

- **Limitações dos Arrays:** Possuem tamanho imutável após a declaração, exigindo estruturas alternativas dinâmicas quando a volumetria de dados varia em tempo de execução.

#### Coleções Dinâmicas (Framework `java.util.Collection`)

Oferecem interfaces e classes flexíveis para gerenciar coleções de dados cujo tamanho varia dinamicamente:

- **Listas Dinâmicas (`ArrayList`):** Mantêm dados em ordem linear sequencial permitindo duplicidade.
- **Conjuntos (`Set` / `HashSet`):** Impedem a inserção de elementos duplicados no conjunto.
- **Filas (`Queue`):** Operam no regime clássico FIFO (_First-In, First-Out_), onde o primeiro que entra é o primeiro a ser processado e removido.
- **Mapas (`Map` / `HashMap`):** Mapeiam chaves exclusivas para determinados valores associados, fornecendo buscas eficientes por chaves.

#### Manipulação de Arquivos e Serialização

- **Persistência de Arquivos:** Realizada de forma performática pelas classes buffered:
    - **Leitura:** `FileReader` acoplado ao `BufferedReader` para ler e processar arquivos linha a linha.
    - **Escrita:** `FileWriter` acoplado ao `BufferedWriter` para gravação eficiente e modular.
- **Serialização de Dados:** Processo que transforma objetos ativos em fluxos binários persistíveis ou enviáveis pela rede de dados. A classe deve implementar a interface estampa `Serializable`. Utiliza-se `ObjectOutputStream` para gravação de estado e `ObjectInputStream` para recuperação posterior.

---

### 8. Integração com Banco de Dados Relacional

Bancos de dados relacionais organizam informações em tabelas de linhas e colunas de forma interligada.

#### Elementos e Restrições de Integridade

- **Chave Primária (Primary Key - PK):** Identificador exclusivo e obrigatório para cada linha de uma tabela.
- **Chave Estrangeira (Foreign Key - FK):** Estabelece conexões relacionais entre tabelas distintas.
- **Integridade Referencial:** Restrição de banco que impede que registros órfãos ou inconsistentes existam nos relacionamentos.

#### Organização da Linguagem SQL (Structured Query Language)

A linguagem SQL divide-se em subgrupos funcionais específicos:

- **DDL (Data Definition Language):** Modifica a infraestrutura estrutural do banco. Instruções: `CREATE`, `ALTER`, `DROP`.
- **DML (Data Manipulation Language):** Executa alterações de dados nas tabelas. Instruções: `INSERT`, `UPDATE`, `DELETE`.
- **DQL (Data Query Language):** Realiza a recuperação seletiva de informações. Instrução principal: `SELECT`.
- **DCL (Data Control Language):** Administra permissões de acesso. Instruções: `GRANT`, `REVOKE`.

#### Integração no Java via API JDBC (Java Database Connectivity)

Permite que o programa conecte-se a um banco de dados relacional e execute comandos SQL:

- **`Statement`:** Utilizado para processamento direto de instruções estáticas simples.
- **`PreparedStatement`:** Garante desempenho superior e proteção de segurança por parametrização de argumentos contra injeção SQL nociva.

```
// Exemplo de atualização de dados parametrizada no Java
String sql = "UPDATE Clientes SET Email = ? WHERE ID = ?";
try (Connection conn = DatabaseConnection.getConnection();
     PreparedStatement pstmt = conn.prepareStatement(sql)) {
    pstmt.setString(1, "novo.email@example.com");
    pstmt.setInt(2, 2);
    int rowsAffected = pstmt.executeUpdate();
} catch (SQLException e) {
    e.printStackTrace();
}
```

---

## Conceitos que não posso confundir

Para fixar as diferenças conceituais e evitar confusões comuns em provas ou desenvolvimento real, analise as comparações diretas na tabela abaixo:

|Conceito A|Conceito B|Diferença Crucial|
|:--|:--|:--|
|**Classe**|**Objeto (Instância)**|A **classe** é a planta abstrata (estática). O **objeto** é a representação física ativa e alocada em memória (com estado de dados próprio).|
|**Classe Abstrata**|**Interface**|Uma **classe abstrata** pode possuir atributos, construtores e métodos com implementação concreta. A **interface** não possui variáveis de instância e define apenas contratos sem implementação.|
|**Sobrecarga (Overloading)**|**Sobrescrita (Overriding)**|A **sobrecarga** mantém métodos de mesmo nome no mesmo escopo com parâmetros diferentes. A **sobrescrita** altera o comportamento interno de um método herdado da superclasse na subclasse, com a mesma assinatura.|
|**Checked Exception**|**Unchecked Exception**|A exceção **checked** é obrigatoriamente validada pelo compilador no código. A **unchecked** decorre de falhas de lógica em execução e o compilador não força tratamento.|
|**Array**|**ArrayList (Lista Dinâmica)**|O **array** possui dimensão fixa e imutável após alocado. O **ArrayList** redimensiona seu tamanho dinamicamente conforme itens são inseridos ou removidos.|
|**Comando `break`**|**Comando `continue`**|O `break` aborta e encerra o laço de repetição completamente. O `continue` ignora apenas o passo corrente e reinicia o loop do próximo incremento.|

---

## Pontos importantes para prova

> [!WARNING] **Foco na Avaliação!** Memorize os tópicos abaixo, pois costumam ser o foco de questões teóricas e práticas de desenvolvimento.

### 1. Etapas do Ciclo de Vida de uma Aplicação OO

1. **Análise:** Etapa de levantamento conceitual voltada a mapear entidades do mundo real no domínio do problema.
2. **Design:** Atividade de design do software onde as classes são estruturadas e suas interações projetadas.
3. **Implementação:** Transposição lógica do planejamento em código-fonte Java funcional.
4. **Teste e Manutenção:** Atividades de validação para sanar defeitos e evolução continuada do sistema.

### 2. Os Modificadores de Acesso do Java

- **`public`:** O elemento é acessível irrestritamente por qualquer classe no programa.
- **`private`:** Escopo restrito unicamente aos limites internos da própria classe onde foi declarado.
- **`protected`:** Acessível unicamente por classes pertencentes ao mesmo pacote ou subclasses (classes filhas) mesmo situadas em pacotes externos.

### 3. As Quatro Divisões do SQL

- **DDL (Data Definition):** Define estruturas física e lógica de tabelas. Comandos: `CREATE`, `ALTER`, `DROP`.
- **DML (Data Manipulation):** Realiza ações de conteúdo nas linhas da tabela. Comandos: `INSERT`, `UPDATE`, `DELETE`.
- **DQL (Data Query):** Obtém dados estruturados. Comando: `SELECT`.
- **DCL (Data Control):** Determina níveis de acesso. Comandos: `GRANT`, `REVOKE`.

### 4. Padrões de Projeto (Design Patterns) Básicos

- **Singleton:** Garante que apenas **uma única instância ativa** de uma determinada classe exista em memória em todo o ciclo do programa, criando um ponto global de referência de acesso. Útil para conexões de rede ou bancos de dados.
- **Factory Method:** Isolamento de criação de novos objetos de forma flexível sem que o cliente necessite saber as particularidades internas da lógica de instanciação da classe concreta.
- **Observer:** Permite o desacoplamento de componentes, definindo que múltiplos objetos observadores (_Observers_) sejam automaticamente sinalizados e atualizados sempre que o estado lógico de um objeto monitorado (_Subject_) se altera.

---

## Revisão rápida

```
mindmap
  root((POO))
    Pilares Fundamentais
      Abstracao [Simplificar e isolar caracteristicas do dominio]
      Encapsulamento [Modificadores public / private / protected]
      Heranca [Reuso de codigo via extends]
      Polimorfismo [Mesmo metodo com comportamentos distintos]
    Controles de Fluxo
      Decisao [if, else if, switch-case]
      Repeticao [while, for, do-while]
    Tratamento de Erros
      Checked [Excecao validada pelo compilador]
      Unchecked [Execucao try-catch-finally]
    Persistencia de Dados
      Colecoes [List, Set, Queue, Map]
      Banco Relacional [Tabelas, Chaves PK / FK, CRUD via JDBC]
```

- **Classes vs. Interfaces:** Use **classe abstrata** se as subclasses precisarem herdar atributos comuns e implementações internas prontas; use **interfaces** se precisar impor um padrão de contrato estrito entre componentes que não compartilham a mesma hierarquia estrutural.
- **Encapsular é Proteger:** Sempre defina atributos como `private`. Utilize métodos acessores públicos (`getters` e `setters`) para monitorar acessos adicionando regras consistentes de validação contra estados corrompidos.
- **Controle de Laço Limpo:** Loops aninhados elevam a complexidade computacional do sistema de maneira exponencial. Prefira utilizar o laço otimizado `for-each` para ler de forma clara e legível todos os dados em coleções e arrays sem a necessidade de índices manuais.
- **CRUD no Banco:** Criar (`INSERT`), Ler (`SELECT`), Atualizar (`UPDATE`) e Excluir (`DELETE`) representam as ações primordiais de manipulação de dados que mantêm a persistência e a evolução das regras corporativas.

---
