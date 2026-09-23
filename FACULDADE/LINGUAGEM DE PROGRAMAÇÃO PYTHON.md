[[EXERCÍCIOS DE PYTHON]]
#ASSUNTO

## Visão geral

**Python** é uma linguagem de programação de alto nível, amplamente utilizada na indústria tecnológica devido à sua legibilidade, simplicidade sintática e versatilidade. Essa linguagem atua de forma eficiente em diversas áreas do conhecimento, abrangendo desde o **desenvolvimento de sistemas web e mobile** até **testes automatizados**, **análise e visualização de dados estruturados**, interações com **bancos de dados relacionais** e implementação de modelos de **Machine Learning**. O ecossistema Python destaca-se tanto pelo uso de recursos nativos robustos quanto pela integração de poderosas bibliotecas de terceiros.

---

## Conceitos principais

- **Filosofia Pythonic e PEP 8:** O código Python deve ser estruturado para ser facilmente legível. O **PEP 8** é o guia de estilo oficial que estabelece as regras de formatação, indentação e organização do código para que ele seja considerado "pythonic".
- **Tipagem Dinâmica:** O interpretador Python define o tipo de dado de uma variável em tempo de execução de forma automática, baseando-se no valor que lhe é atribuído.
- **Tudo é Objeto:** Em Python, todos os dados são representados por objetos ou pela relação direta entre eles.
- **Paradigma Orientado a Objetos (POO):** Abordagem que organiza o código em classes (projetos/modelos) e objetos (instâncias do mundo real), aplicando conceitos de abstração, encapsulamento, herança e polimorfismo.
- **Modularização:** Prática de dividir o código em arquivos independentes (`.py`), chamados **módulos**, permitindo organizar, reutilizar e compartilhar componentes de software de forma limpa e manutenível.
- **Análise de Dados Tabulares (Pandas & NumPy):** Manipulação eficiente de matrizes multidimensionais e tabelas estruturadas através de DataFrames e Series, otimizando o processamento estatístico e a preparação de dados.
- **Operações CRUD em SQL:** Execução padronizada das quatro operações essenciais de banco de dados: _Create_ (inserção), _Read_ (recuperação), _Update_ (modificação) e _Delete_ (exclusão).

---

## Conteúdo explicado

### 1. Fundamentos e Sintaxe Básica

- **Origem:** Criada por **Guido van Rossum** e lançada em 1991.
- **Variáveis e Alocação:** Uma variável é um espaço alocado na memória RAM. A verificação de tipo é feita com a função nativa `type()`.
- **Entrada e Saída:**
    - `print()` exibe saídas formatadas.
    - `input()` lê strings digitadas pelo usuário. Para ler valores numéricos, deve-se realizar a coerção de tipo (ex: `int(input())` ou `float(input())`).
    - **f-strings (PEP 498):** Mecanismo de interpolação literal de strings recomendado para formatação de textos (ex: `f"Texto {variavel}"`).

### 2. Estruturas de Controle e Decisão

- **Operadores Relacionais:** Utilizados para comparar valores. Retornam dados booleanos (`True` ou `False`).
    - `<` (menor), `<=` (menor ou igual), `>` (maior), `>=` (maior ou igual), `==` (igual), `!=` (diferente).
    - `is` (identidade do objeto), `is not` (negação da identidade).
- **Estruturas Lógicas (Operadores Booleanos):**
    - `and` (E): Retorna `True` apenas se ambos os argumentos forem verdadeiros.
    - `or` (OU): Retorna `True` se pelo menos uma condição for verdadeira.
    - `not` (NÃO): Inverte o valor lógico do argumento.
- **Condicionais (`if`, `elif`, `else`):** Desviam o fluxo de execução com base no atendimento de critérios booleanos. O `elif` permite avaliar múltiplos cenários em sequência de forma otimizada e legível.

### 3. Estruturas de Repetição (Loops)

- **Loop `for`:** Utilizado quando o número de iterações é previamente conhecido ou para percorrer coleções ordenadas (iteráveis).
- **Loop `while`:** Executado repetidamente enquanto uma determinada condição lógica for verdadeira. É ideal para cenários onde a quantidade de repetições não é conhecida previamente. A técnica `while True` cria loops que dependem de condições internas de parada.
- **Ferramentas de Controle de Iteração:**
    - `range()`: Cria sequências numéricas. Pode receber um parâmetro (`range(stop)`), dois parâmetros (`range(start, stop)`) ou três parâmetros com incremento (`range(start, stop, step)`).
    - `break`: Interrompe imediatamente a execução da estrutura de repetição, saindo do loop.
    - `continue`: Ignora o restante do bloco de código na iteração atual e avança para a próxima etapa do loop.

### 4. Funções

- **Built-in (Nativas):** Python vem equipado com um conjunto de cerca de 70 funções pré-instaladas no núcleo da linguagem (ex: `len()`, `sum()`, `int()`, `round()`).
- **Definidas pelo Usuário:** Criadas usando a palavra-chave `def`, seguidas do nome da função, parâmetros e opcionalmente uma instrução `return` para devolver um valor calculado.
- **Funções Anônimas (Expressões Lambda):** Funções simples, sem nome definido por `def`, escritas em uma única linha usando a palavra reservada `lambda`. São úteis para ações rápidas de uso único.

```
# Exemplo de Função Lambda
soma = lambda a, b: a + b
print(soma(3, 4)) # Saída: 7
```

### 5. Estruturas de Dados Coletivas (Sequências, Mappings e Sets)

- **Sequências:** Armazenam dados de forma ordenada e indexada por inteiros não negativos (começando em 0 até \(n-1\)). Operações comuns: `x in s` (pertencimento), `s + t` (concatenação), `s[i:j]` (fatiamento) e `s.count(x)` (contagem).
    - **Strings (`str`):** Sequências de texto estritamente **imutáveis**.
    - **Listas (`list`):** Coleções mutáveis indexadas.
        - **List Comprehensions:** Sintaxe pythônica otimizada para transformar ou filtrar dados de um iterável e gerar uma nova lista.
        - `map()`: Aplica uma função a todos os itens de uma lista.
        - `filter()`: Filtra elementos de um iterável com base em um teste lógico.
    - **Tuplas (`tuple`):** Sequências indexadas totalmente **imutáveis**. Podem ser criadas de três formas: `()`, elementos separados por vírgula em parênteses `('a', 'b')` ou via construtor `tuple()`. São muito usadas para desempacotamento e retorno múltiplo de funções.
- **Conjuntos (`set`):** Coleções não ordenadas de elementos **estritamente únicos** (eliminam repetições automaticamente). Habilitam operações matemáticas de conjunto (união, interseção, diferença). Métodos principais: `add(valor)` e `remove(valor)`. Podem ser declarados com chaves contendo valores `{1, 2, 3}` ou pelo construtor `set(iterable)`.
- **Mapeamentos / Dicionários (`dict`):** Estruturas mutáveis que associam chaves exclusivas a valores específicos. Existem 4 formas comuns de criação: chaves vazias `{}`, pares `chave: valor` separados por vírgulas, listas de tuplas usando o construtor `dict()`, ou combinando listas de chaves e valores com a função `zip()`.
- **Arrays NumPy:** Coleções multidimensionais altamente eficientes para processamento científico e matemático em massa, fundamentais para a ciência de dados.

### 6. Programação Orientada a Objetos (POO)

- **Pilares Fundamentais:**
    1. **Abstração:** Representação simplificada de entidades complexas do mundo real no código.
    2. **Encapsulamento:** Agrupamento de atributos (dados) e métodos (comportamentos) em uma classe, controlando e restringindo o acesso direto a esses dados.
    3. **Herança:** Criação de classes-filhas (subclasses) que herdam características e comportamentos de classes-pai (superclasses), permitindo extensibilidade e reúso de código. Python suporta **herança múltipla** (herdar de mais de uma classe-pai simultaneamente).
    4. **Polimorfismo:** Capacidade de subclasses responderem de maneiras distintas a uma mesma chamada de método, alterando ou especializando seu comportamento.
- **Sintaxe de Classes:**
    - Declarada pela palavra `class`.
    - O método especial `__init__` atua como o **construtor**, inicializando os atributos do objeto durante a instanciação.
    - O termo `self` é uma convenção para fazer referência à própria instância ativa do objeto dentro dos métodos da classe.
    - A chamada `super().__init__()` permite que a classe-filha execute o construtor de sua superclasse.

```
class Veiculo:
    def __init__(self, marca, modelo):
        self.marca = marca
        self.modelo = modelo

class Carro(Veiculo):
    def __init__(self, marca, modelo, potencia):
        super().__init__(marca, modelo) # Herança do construtor pai
        self.potencia = potencia
```

### 7. Organização e Extensões de Código (Módulos e Importações)

- **Módulos:** Arquivos `.py` individuais que agrupam funções ou classes.
- **Bibliotecas:** Conjunto prático de módulos integrados.
- **Formas de Importação:**
    - `import modulo`: Importa o módulo completo na memória, exigindo o prefixo `modulo.funcao()`.
    - `import modulo as apelido`: Permite encurtar a chamada usando um alias `apelido.funcao()`.
    - `from modulo import funcao`: Importa diretamente os elementos específicos, eliminando a necessidade de usar prefixos.
- **Classificação dos Módulos:**
    1. **Built-in:** Embutidos nativamente no núcleo do interpretador (ex: `math`, `os`, `random`, `datetime`).
    2. **De Terceiros:** Desenvolvidos de forma externa e disponibilizados no **PyPI** (Python Package Index). São instalados via gerenciador de pacotes `pip` (ex: `pip install requests`). Projetos maiores usam o arquivo `requirements.txt` para mapear dependências e **ambientes virtuais** para isolar as versões dos pacotes.
    3. **Próprios:** Módulos personalizados construídos pelo programador.

### 8. Banco de Dados Relacional em Python

- **Instruções SQL:** Dividem-se em três grupos principais:
    1. **DDL (Data Definition Language):** Define e modifica estruturas físicas de bancos e tabelas (ex: `CREATE`, `ALTER`, `DROP`).
    2. **DML (Data Manipulation Language):** Gerencia e manipula os registros armazenados (ex: `SELECT`, `INSERT`, `UPDATE`, `DELETE`).
    3. **DCL (Data Control Language):** Controla a segurança e autorizações de acesso aos dados (ex: `GRANT`, `REVOKE`).
- **Conexão e a especificação PEP 249:**
    - A conexão direta de uma aplicação Python a um SGBD é regulada pelas normas do **PEP 249 (Database API Specification v2.0)**.
    - Os módulos de banco de dados devem, obrigatoriamente, implementar o método `connect(parameters...)`.
- **SQLite e Módulo `sqlite3`:**
    - O **SQLite** é um banco completo em C, compacto e que opera diretamente em disco (em um único arquivo no sistema), dispensando a necessidade de um servidor independente de banco de dados.
    - O módulo nativo `sqlite3` permite gerenciar bancos SQLite diretamente no Python.

> [!info] **Passo a Passo Padrão para Operações de Banco de Dados (sqlite3):**
> 
> 1. Conectar ao banco (`conn = sqlite3.connect('nome.db')`).
> 2. Criar um objeto cursor (`cursor = conn.cursor()`) para enviar instruções SQL.
> 3. Executar o comando SQL desejado usando `cursor.execute()`.
> 4. Gravar a transação no disco com `conn.commit()` (necessário em inserções, atualizações e exclusões).
> 5. Fechar o cursor e a conexão utilizando `conn.close()`.

### 9. Análise e Manipulação de Dados (Pandas)

- **Estruturas Fundamentais:**
    - **Series:** Coleções estruturadas de dados unidimensionais indexadas.
    - **DataFrames:** Estruturas bidimensionais tabulares organizadas em linhas e colunas.
- **Leitura e Escrita de Dados:** O Pandas fornece métodos padronizados com o prefixo `pd.read_XXXX()` e `.to_XXXX()` para interagir com formatos de arquivo como CSV, Excel, JSON, XML, HTML e bancos SQL. Exemplo: `pd.read_html()` lê tabelas contidas em tags HTML `<table>` de sites.
- **Processamento e Limpeza de Dados:**
    - `drop_duplicates()`: Função utilizada para remover registros duplicados. Parâmetros importantes: `keep='last'` (preserva apenas a última ocorrência) e `inplace=True` (grava as alterações diretamente no DataFrame original na memória).
    - `df['nova_coluna'] = dado`: Cria novas colunas de dados de forma simplificada em lote para todas as linhas.
    - `df.info()`: Exibe metadados estruturais sobre o DataFrame (linhas, tipos das colunas, memória e valores não nulos).
    - `df.head()`: Retorna as 5 primeiras linhas dos dados tabulares para rápida inspeção visual.
- **Filtro e Extração de Informações:**
    - `loc[]`: Ferramenta para filtrar e extrair linhas e registros de forma direta usando índices de localização.
    - **Testes Booleanos:** Retorna séries de booleanos (`True`/`False`) para cada registro com base em um critério de filtragem condicional.

### 10. Visualização Gráfica de Dados

- **Matplotlib:** Biblioteca fundamental de plotagem em Python. O módulo `pyplot` (apelidado como `plt`) facilita a customização gráfica. O gráfico básico é desenhado em figuras e eixos através de dois estilos de desenvolvimento principais:
    1. **Funcional (Estilo Pyplot):** O próprio módulo cria e coordena de forma automática a figura e os eixos da plotagem.
    2. **Orientado a Objetos (OO):** Cria explicitamente os objetos de figuras e eixos (`fig, ax = plt.subplots()`), aplicando diretamente métodos sobre eles para maior controle e customização.
- **Pandas Plot:** Os objetos DataFrame e Series possuem o método embutido `.plot()` (com base no Matplotlib) para gerar de forma nativa e ágil gráficos simples como barras (`kind='bar'`), pizza (`kind='pie'`) e linhas (`kind='line'`).
- **Seaborn:** Biblioteca de visualização estatística especializada integrada sobre a infraestrutura do Matplotlib.
    - Possui repositório embutido de bases de dados acadêmicas úteis para prática (ex: dataset de gorjetas 'tips').
    - A função `barplot()` desenha gráficos de barras estatísticos.
    - **O Parâmetro `estimator`:** Atributo fundamental do `barplot()` do Seaborn. Por padrão, ele realiza e exibe o cálculo estatístico da **média** de dados de cada categoria. No entanto, oferece alta flexibilidade e pode ser personalizado de forma explícita com outras funções estatísticas, como `sum` (soma acumulada dos valores das barras) ou `len` (contagem do volume de registros representados).

### 11. Tecnologias e Aplicações Avançadas

- **Desenvolvimento de Sistemas Web:**
    - **Front-end:** Interface visível construída com HTML, CSS e JavaScript. Em projetos Python específicos, podem ser integradas bibliotecas de interface gráfica como **Dash** ou **Flask**.
    - **Back-end:** Gerenciamento lógico, processamento de dados do servidor e conexões a bancos. Python destaca-se nessa área pelo uso de frameworks como **Django** (framework full-stack, robusto, com convenções rígidas) e **Flask** (estrutura minimalista e flexível).
    - **APIs (Application Programming Interfaces):** Otimizam a integração de dados e a comunicação entre as camadas de front-end e back-end. Frameworks populares: **FastAPI** e **Django Rest Framework**.
- **Desenvolvimento de Aplicativos Mobile:**
    - **Kivy:** Framework de código aberto, multiplataforma (Android, iOS, Windows, Linux, macOS) focado no desenvolvimento rápido de softwares multitouch.
    - **KivyMD:** Extensão avançada do Kivy que incorpora as diretrizes estéticas e padrões de design do **Material Design do Google**. Oferece uma ampla gama de elementos gráficos pré-construídos e consistentes (como barras de navegação, botões flutuantes, diálogos e o widget estruturado **MDTabs** para organizar o conteúdo em abas de navegação simples).
- **Testes Automatizados de Software:**
    - **Assertions (Assertivas):** Instruções de verificação pontuais no decorrer do código que validam suposições e condições lógicas essenciais. Caso a expressão avaliada seja falsa, o Python interrompe a execução com um erro de assertiva `AssertionError` (ex: `assert divisor != 0, "Divisão por zero!"`).
    - **Doctests:** Abordagem que aninha os testes funcionais de forma direta na documentação (docstring) da função utilizando o prompt de console virtual `>>>`. A função executada `doctest.testmod()` processa os exemplos da docstring e valida automaticamente se a saída gerada em tempo de execução condiz com o resultado documentado.
    - **Módulo Unittest:** Estrutura corporativa avançada para testes formais em projetos de larga escala. Permite estruturar e aninhar suítes de testes complexas em classes que herdam de `unittest.TestCase`. Os métodos de validação internos da classe devem começar obrigatoriamente com o prefixo `test_` (ex: `def test_soma_positivos(self):`) e usam assertions de validação ricas (como `self.assertEqual()`).
- **Machine Learning (ML):** Campo de inteligência artificial voltado ao desenvolvimento de modelos matemáticos e algoritmos que aprendem padrões diretamente de dados brutos sem receber regras de programação rígidas e explícitas.
    - **Modelos Populares:** Árvores de Decisão, Redes Neurais (inspiradas no cérebro), Support Vector Machines (SVM) e K-Means.
    - **TensorFlow:** Biblioteca avançada de código aberto criada pela Google para construir e executar arquiteturas complexas de ML e redes neurais profundas (Deep Learning).

---

## Conceitos que não posso confundir

> [!warning] **Diferenças Críticas de Estrutura de Dados:**
> 
> - **Lista (`list`):** Coleção **ordenada**, **mutável** (permite inserção, exclusão e alteração de elementos) e indexada iniciada em 0. Declarada com colchetes: ``.
> - **Tupla (`tuple`):** Coleção **ordenada**, estritamente **imutável** (não permite alterações após criada) e indexada. Declarada com parênteses ou construtor: `(1, 2, 3)`.
> - **Conjunto (`set`):** Coleção **não ordenada** e mutável de elementos **estritamente únicos** (sem duplicações na memória). Não possui índices e não aceita chaves ou elementos repetidos. Declarada com chaves contendo elementos: `{1, 2, 3}`.
> - **Dicionário (`dict`):** Coleção estruturada de mapeamentos mutáveis que associam chaves exclusivas a valores (`chave: valor`).

> [!warning] **Django vs. Flask:**
> 
> - **Django:** Framework web corporativo completo (_full-stack_), caracterizado por uma arquitetura robusta, convenções predefinidas rígidas e soluções prontas de fábrica.
> - **Flask:** Framework/estrutura web minimalista (_microframework_), focado em leveza, adaptabilidade e extrema flexibilidade para acoplar componentes adicionais.

> [!warning] **Tipos de Treinamento em Machine Learning:**
> 
> - **Treinamento Supervisionado:** O modelo aprende a mapear entradas com base em conjuntos de dados rotulados, que já contêm pares de entrada e saída esperada corretas (ex: classificar e-mails em _spam_ ou _não spam_).
> - **Treinamento Não Supervisionado:** O modelo busca por si só padrões, correlações e estruturas ocultas em dados sem qualquer rotulagem ou informação de saída anterior (ex: agrupamento de clientes por perfil de compras com o algoritmo K-Means).
> - **Treinamento por Reforço:** Um agente ativo interage diretamente com um ambiente dinâmico, aprendendo a tomar decisões sequenciais para maximizar recompensas cumulativas e pontuações ao longo do tempo (ex: IA aprendendo a jogar um videogame).

---

## Pontos importantes para prova

1. **Regra de Identificação do Unittest:** Para que o módulo `unittest` reconheça e processe de forma automática as rotinas de validação aninhadas em uma classe derivada de `unittest.TestCase`, **todos os métodos de teste devem iniciar obrigatoriamente com o prefixo literal `test_`**.
2. **Sintaxe Obrigatória do Doctest:** Para que o processador do `doctest` consiga mapear e simular os testes descritos nas docstrings das funções, os blocos de simulação devem conter estritamente o caractere de prompt de comando interativo do console Python: `>>>`.
3. **Persistência e Arquitetura do SQLite:** O banco de dados SQLite é embutido e **não depende de servidores externos** para gerenciar transações. Ele lê e escreve registros estruturados de forma direta em **um único arquivo no disco local**.
4. **Assinatura PEP 249:** Todo conector de banco relacional em Python deve implementar a API padrão PEP 249. Um de seus princípios cruciais é que todos esses módulos devem possuir o método chamado `connect()` para iniciar as interações.
5. **Funcionamento de `drop_duplicates` no Pandas:** Ao limpar dados duplicados com o método `.drop_duplicates()`, deve-se atentar ao parâmetro `inplace=True`. Por padrão, métodos do Pandas geram cópias modificadas. O uso do `inplace=True` altera diretamente a estrutura original na memória, sobrescrevendo-a.
6. **O Estimador Padrão do Seaborn:** Ao gerar gráficos estatísticos usando a função `barplot()` do Seaborn, lembre-se de que se o parâmetro `estimator` for omitido, **a métrica calculada e exibida por padrão nas barras do gráfico será sempre a Média**.

---

## Revisão rápida

```
graph TD
    A[Python: Tudo é Objeto] --> B[Sequências]
    A --> C[Mappings]
    A --> D[Sets]
    B --> B1[str: Imutável]
    B --> B2[list: Mutável]
    B --> B3[tuple: Imutável]
    C --> C1[dict: Chave/Valor]
    D --> D1[set: Elementos Únicos]
```

- **PEP 8:** Guia estilístico oficial do Python focado em legibilidade (indentação, nomes e formatação).
- **Controle de Loop:** `break` (encerra o loop), `continue` (pula para a próxima iteração).
- **Lambdas:** Funções anônimas de linha única.
- **POO:** `class` define o modelo, `__init__` constrói o objeto, `self` referencia a própria instância, `super()` acessa elementos da superclasse.
- **SQL no Python:** `connect()` conecta, `cursor()` permite execução de comandos via `.execute()`, `commit()` grava transações em disco.
- **Estruturas Pandas:** Series (1D), DataFrame (2D/Tabela), `loc` (filtra registros pelo índice).
- **Bibliotecas Gráficas:** Matplotlib (base de plotagem nativa), Seaborn (estatística, constrói gráficos complexos de forma ágil).
- **Bibliotecas Mobile:** Kivy (multiplataforma multitouch), KivyMD (Kivy estendido com padrões do Material Design da Google).

---
