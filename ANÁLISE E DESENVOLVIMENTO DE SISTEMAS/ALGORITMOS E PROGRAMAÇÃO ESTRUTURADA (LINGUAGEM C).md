[[EXEMPLOS-PRÁTICOS DE ALGORITMOS E PROGRAMAÇÃO ESTRUTURADA]]
#ASSUNTO

## Conceitos principais

- **Algoritmo**: É uma sequência lógica, ordenada e finita de etapas ou instruções que devem ser seguidas para realizar uma tarefa específica ou solucionar um problema computacional.
- **Modularização ("Dividir para Conquistar")**: Estratégia de design de software que consiste em fragmentar um problema complexo em subproblemas menores, facilitando sua resolução, legibilidade e manutenção por meio de funções independentes.
- **Variável**: Localização temporária e física reservada na memória RAM para armazenar um dado que pode ser alterado durante a execução do programa.
- **Constante**: Valor que permanece fixo e imutável ao longo de toda a execução do programa.
- **Ponteiro**: Tipo especial de variável que armazena exclusivamente endereços de memória de outros recursos ou variáveis, permitindo manipulação direta e baixo nível.
- **Recursividade**: Capacidade de uma função chamar a si mesma sucessivamente até que um critério de parada (caso base) seja satisfeito.

---

## Conteúdo explicado

### 1. Representação de Algoritmos

A construção de um algoritmo é a etapa prévia ao desenvolvimento do software. O fluxo de desenvolvimento adequado compreende: **Análise do problema**, **Definição de entradas**, **Processamento dos dados** e **Apresentação das saídas**. As principais formas de representação são:

- **Linguagem Natural**: Descrição do fluxo de passos em idioma convencional (como o português). Embora não exija aprendizado de novas sintaxes, apresenta desvantagens como ambiguidades e múltiplas interpretações, o que dificulta a tradução direta para um código fonte.
- **Diagramas de Bloco (Fluxogramas)**: Representação gráfica padronizada pela ANSI (American National Standards Institute) que estabelece a lógica do programa de forma visual. Suas vantagens incluem facilidade de interpretação e baixa ambiguidade. Os principais símbolos são:
    - _Terminal_ (elipse): Representa o início ou o fim do fluxo.
    - _Entrada manual_ (trapezoide): Entrada de dados via teclado pelo usuário.
    - _Processamento_ (retângulo): Execução de cálculos, atribuições ou ações internas.
    - _Exibição_ (bloco com base arredondada à direita): Mostra de resultados na tela.
    - _Decisão/Condicional_ (losango): Desvios condicionais de fluxo e laços de repetição.

---

### 2. Fundamentos da Linguagem C

Criada por Dennis Ritchie em 1972 e padronizada pela ANSI para garantir portabilidade, a linguagem C possui uma sintaxe rígida.

#### Estrutura Básica de um Código C:

```
#include <stdio.h> // 1. Inclusão de biblioteca de Entrada e Saída

int main() {       // 2. Função principal (ponto de entrada)
    // 3. Bloco de comandos
    return 0;      // 4. Retorno ao Sistema Operacional (0 indica sucesso)
}
```

- **Função `main`**: Ponto de partida obrigatório de qualquer aplicação em C. O comando `return 0;` indica ao sistema operacional que o programa terminou corretamente, enquanto qualquer retorno diferente de zero aponta erros na execução.
- **Bibliotecas**: Código previamente estabelecido que incorpora funções prontas ao projeto. São incluídas com `#include`. Exemplos:
    - `stdio.h`: Funções de entrada e saída padrão, como `printf` e `scanf`.
    - `stdlib.h`: Alocação de memória, controle de processos e conversões.
    - `string.h`: Funções de manipulação de strings.
    - `math.h`: Operações matemáticas avançadas (como `pow` e `fabs`).
    - `stdbool.h`: Suporte a variáveis booleanas (`true` ou `false`).

#### Entrada e Saída de Dados:

- **`printf`**: Comando de saída utilizado para exibir textos ou conteúdos de variáveis. Códigos de controle específicos são posicionados no texto para representar variáveis:
    - `%d`: Números inteiros.
    - `%f`: Números decimais (ponto flutuante).
    - `%.2f`: Decimal formatado e arredondado para duas casas decimais.
    - `%c`: Caractere único.
    - `%s`: Sequência de caracteres (string).
- **`scanf`**: Comando de entrada que recebe dados digitados pelo usuário e os armazena na memória utilizando o **operador de referência `&`** antes da variável, o qual indica o seu endereço de memória.

---

### 3. Gerenciamento de Memória: Variáveis, Constantes e Modificadores

Toda variável em C ocupa um tamanho fixo de memória (em bytes) determinado por seu tipo.

|Tipo Primitivo|Tamanho Padrão|Intervalo de Valores|
|:--|:--|:--|
|`char`|1 byte|-128 a 127|
|`int`|4 bytes|-2.147.483.648 a 2.147.483.647|
|`float`|4 bytes|-3,4E38 a 3,4E38|
|`double`|8 bytes|-1,7E308 a 1,7E308|

- **Modificadores de Tipo**: Alteram a capacidade de armazenamento ou sinalização padrão dos tipos primitivos. São eles:
    
    - `unsigned`: Elimina a representação de valores negativos, permitindo armazenar apenas positivos (duplica o limite superior positivo). Exemplo: `unsigned int` vai de `0` a `4.294.967.296`.
    - `short`: Reduz o espaço reservado em memória (ex: `short int` ocupa 2 bytes, cobrindo `-32.768` a `32.767`).
    - `long`: Aumenta a capacidade de armazenamento do tipo primitivo (ex: `long double` ocupa 16 bytes).
- **Regras para Nomeação de Identificadores (Variáveis e Constantes)**:
    
    1. Devem iniciar obrigatoriamente com uma letra.
    2. Os caracteres seguintes podem conter letras, números ou caracteres de sublinhado (`_`).
    3. Não podem conter espaços em branco, acentos ou caracteres especiais.
    4. A linguagem C é **sensível a maiúsculas e minúsculas (_case-sensitive_)**, tratando identificadores como `valor` e `Valor` de forma totalmente distinta.
- **Declaração de Constantes**:
    
    1. **Diretiva `#define`**: Processada antes da compilação (pré-processador). Cria um rótulo que substitui todas as ocorrências do termo no código por seu valor equivalente. **Não consome espaço de memória física**, não tem ponto e vírgula ao final e não permite o uso do operador `&`. Exemplo: `#define PI 3.14`.
    2. **Palavra-chave `const`**: Declara uma constante de forma idêntica à de uma variável, mas cujo valor não pode ser alterado durante a execução do código. **Aloca espaço físico na memória RAM** conforme o seu tipo de dado. Exemplo: `const float g = 9.8;`.

---

### 4. Operadores e Expressões

Os operadores realizam operações computacionais básicas e formam expressões lógicas.

- **Aritméticos**: `+` (soma), `-` (subtração), `*` (multiplicação), `/` (divisão) e `%` (módulo: resto da divisão inteira de um número por outro).
- **Unários (Incremento e Decremento)**:
    - _Pré-incremento/decremento_ (`++x`, `--x`): O valor da variável é alterado antes de ser avaliado na expressão principal.
    - _Pós-incremento/decremento_ (`x++`, `x--`): O valor original é usado na expressão atual e só depois a variável é incrementada ou decrementada.
- **Atribuição Composta**: Sintaxe simplificada que combina aritmética e atribuição. Por exemplo, `num /= 2` equivale matematicamente a `num = num / 2`. **Regra**: Não pode haver espaços entre o operador aritmético e o sinal de igual.
- **Relacionais**: Realizam comparações que geram resultados booleanos. Na linguagem C, resultados verdadeiros retornam o valor `1` e falsos retornam `0`. Os operadores são `==` (igual a), `!=` (diferente de), `>` (maior que), `<` (menor que), `>=` (maior ou igual) e `<=` (menor ou igual).
- **Lógicos**: Utilizados para construir condições complexas:
    - `!` (Negação/NOT): Inverte o resultado booleano de uma expressão.
    - `&&` (Conjunção/AND): O resultado final é verdadeiro apenas se **todas** as condições individuais forem verdadeiras.
    - `||` (Disjunção/OR): O resultado final é verdadeiro se pelo menos **uma** das condições for verdadeira.

#### Ordem de Precedência dos Operadores (Execução):

1. Parênteses (forçam prioridade específica)
2. Operadores unários (`++`, `--`, `!`)
3. Multiplicação (`*`), Divisão (`/`) e Módulo (`%`)
4. Adição (`+`) e Subtração (`-`)
5. Operadores relacionais (`<`, `>`, `<=`, `>=`, `==`, `!=`)
6. Operadores lógicos (`&&`, `||`)

---

### 5. Estruturas de Controle Condicional

Estruturas lógicas que direcionam o fluxo do programa a partir de testes condicionais.

- **Estrutura Simples (`if`)**: Avalia um teste lógico. Executa o bloco de comandos entre chaves apenas se o resultado do teste for verdadeiro. Se for falso, ignora o bloco e prossegue.
- **Estrutura Composta (`if-else`)**: Garante um desvio padrão para o fluxo. Se a condição do `if` for verdadeira, executa o bloco `if`. Caso contrário (senão), executa obrigatoriamente o bloco pertencente ao `else`.
- **Estrutura Encadeada (`if-else-if`) / IFs Aninhados**: Executa testes em sequência de cima para baixo. No instante em que uma condição verdadeira é encontrada, o bloco associado é imediatamente executado, e todo o restante da estrutura subsequente é ignorado. Se nenhuma condição for atendida, o último bloco `else` (se houver) será acionado.
- **Estrutura de Seleção (`switch-case`)**: Avalia sucessivamente o valor de uma única expressão em relação a uma lista de constantes inteiras ou caracteres (`cases`). Quando o valor correspondente é encontrado, os comandos associados começam a ser executados.
    - **Regra**: É fundamental o uso do comando `break` ao final de cada bloco de caso. Se omitido, o programa continuará executando as instruções de todos os casos subsequentes sequencialmente, até encontrar o final do bloco `switch` ou encontrar um comando `break`.
    - **Tratamento Padrão**: Se nenhum valor da lista de casos for compatível com a expressão avaliada, o bloco identificado pela diretiva `default` será executado.

---

### 6. Estruturas de Repetição (Laços)

Executam blocos de comandos repetidamente com base em critérios lógicos.

- **Laço com Teste no Início (`while`)**: A condição lógica é testada antes de qualquer execução de comandos. Se a condição for inicialmente falsa, o bloco interno nunca será executado.
    - _Risco_: Falta de atualização da condição de parada pode prender o fluxo em um **loop infinito**. Para evitar isso, os laços dependem de variáveis de controle:
        - `Contador`: Variável incremental que controla de forma explícita o número de repetições.
        - `Acumulador`: Variável que realiza a soma sucessiva de dados inseridos em cada iteração.
- **Laço com Teste no Fim (`do...while`)**: Executa todos os comandos internos do bloco **pelo menos uma vez** antes de avaliar a condição lógica de permanência.
- **Laço Determinístico (`for`)**: Concentra a inicialização, a condição de permanência e a instrução de incremento/decremento da variável de controle em uma única linha estruturada. É ideal para repetições em que o limite ou número exato de loops já é previamente conhecido.
    - _Aninhamento de Laços (`for` aninhados)_: Consiste na colocação de um comando `for` interno dentro de um bloco de `for` externo. Cada iteração única do loop externo executa todo o ciclo de repetições do loop interno. É amplamente empregado para processamento de matrizes multidimensionais.

---

### 7. Comandos de Desvio e Controle de Repetição

Instruções que alteram de forma abrupta e não estruturada o fluxo padrão dos laços.

- **`break`**: Força a interrupção imediata da execução de um loop (`for`, `while`, `do-while`) ou de um bloco `switch-case`, transferindo o controle do processamento para a primeira instrução externa após o bloco encerrado.
- **`continue`**: Pula apenas as instruções restantes da **iteração atual** de um laço de repetição, forçando o programa a avançar imediatamente para a próxima iteração do ciclo (reavaliando a condição lógica de permanência), sem contudo encerrar o laço.
- **`goto`**: Realiza um desvio incondicional e não estruturado no fluxo, saltando diretamente para um ponto marcado do código identificado por um rótulo seguido de dois pontos (`nome_do_rotulo:`).
    - **Limitação**: Possui escopo local, o que significa que o salto só pode ser realizado entre pontos que estejam dentro do mesmo bloco de código ou da mesma função.
    - **Aviso**: Seu uso indiscriminado é fortemente desencorajado na engenharia de software estruturada, pois prejudica a legibilidade, dificulta depurações de erros e torna a manutenção de software propensa a falhas complexas.

---

### 8. Estruturas de Dados Homogêneas (Arrays)

Coleções que agrupam elementos do mesmo tipo de dado e os organizam sequencialmente na memória RAM.

#### Vetores (Unidimensionais):

Sua criação exige a definição explícita do tamanho máximo do array entre colchetes. Exemplo: `int idade;`.

- **Índices**: O acesso a cada elemento em memória para leitura ou escrita é feito exclusivamente por meio de índices. Em C, os índices de um vetor de tamanho `N` obrigatoriamente iniciam em `0` e variam até `N-1`.
- **Estáticos**: O tamanho de alocação de memória reservado para um vetor é definido rigidamente durante a escrita do código e não pode sofrer variações ou redimensionamentos em tempo de execução.
- **Lixo de Memória**: O compilador apenas reserva os blocos de bytes solicitados em memória, mas não limpa os valores que estavam ali previamente. Consequentemente, posições não inicializadas conterão resíduos de dados antigos ("lixo de memória").

#### Strings (Vetores de Caracteres):

Constituem cadeias de caracteres dispostas em um vetor do tipo `char`.

- **Caractere Finalizador (`\0`)**: O compilador utiliza a última posição física da string para armazenar automaticamente o caractere nulo `\0` para marcar o término da sequência textual. Assim, um vetor `char nome` possui efetivamente apenas 15 espaços úteis disponíveis para caracteres.
- **Funções de Entrada**:
    - `scanf("%s", nome)`: Realiza a leitura até encontrar o primeiro caractere de espaço em branco. O operador de referência `&` é opcional na leitura de strings.
    - `fgets(destino, tamanho, stdin)`: Permite a leitura segura de strings com espaços inclusos. Recebe três parâmetros: o vetor de destino, o tamanho máximo do buffer de caracteres e o fluxo de entrada (teclado = `stdin`).
    - `fflush(stdin)`: Função recomendada para ser executada antes de chamadas de leitura como `fgets` para realizar a limpeza completa do buffer de entrada do teclado.
- **Remoção da Quebra de Linha**: A leitura com `fgets` captura também a quebra de linha gerada pela tecla Enter (`\n`). A remoção desse caractere para evitar falhas em buscas e comparações é feita localizando seu índice por meio da função `strcspn` da biblioteca `<string.h>`:
    
    ```
    frase[strcspn(frase, "\n")] = 0; // Substitui o '\n' por nulo, encerrando a string
    ```
    

#### Matrizes (Multidimensionais):

Extensões multidimensionais de vetores representadas por tabelas de linhas e colunas.

- **Sintaxe de Criação**: `<tipo> <nome>[linhas][colunas];`. Exemplo: `float notas;`.
- **Estrutura de Armazenamento**: Embora sejam visualizadas de forma tabular (bidimensional), **as matrizes são alocadas e dispostas de forma linear e contígua na memória RAM**, de modo que as linhas são posicionadas consecutivamente uma após a outra.

---

### 9. Estruturas de Dados Heterogêneas (Structs)

Tipos de dados personalizados e compostos definidos pelo desenvolvedor que permitem agrupar diferentes tipos primitivos sob um único rótulo.

```
struct Cadastro {
    char cpf;
    char nome;
    int idade;
}; // O ponto e vírgula é obrigatório ao término da struct
```

- **Acesso aos Membros**: O acesso aos campos de dados internos de uma variável estruturada é feito através da utilização do operador de ponto (`.`). Exemplo: `cliente1.idade = 19;`.
- **Vetores de Estruturas**: Podem ser declarados para armazenar registros em lote de forma sequencial. Exemplo: `struct Cadastro clientes;`. O acesso à propriedade de uma posição específica é feito posicionando os colchetes do índice antes do operador de ponto:
    
    ```
    clientes.idade = 25;
    ```
    
- **Uso da Palavra-chave `typedef`**: Cria um apelido ou novo identificador simplificado para tipos existentes, poupando a necessidade de repetir o termo `struct` na declaração de novas variáveis.
    
    ```
    typedef struct {
        char nome;
        int idade;
    } Aluno; // "Aluno" torna-se o novo tipo de dado
    
    Aluno aluno1; // Declaração limpa, sem a palavra "struct"
    ```
    

---

### 10. Ponteiros e Operações em Baixo Nível

Os ponteiros constituem o recurso mais poderoso de controle e manipulação de memória RAM em linguagem C.

- **Declaração**: O asterisco (`*`) indica que a variável criada é um ponteiro. Exemplo: `int *ptr;`. O tipo associado (como `int`) especifica que o ponteiro guardará o endereço de memória de uma variável daquele tipo.
- **Operador de Referência (`&`)**: Utilizado para extrair o endereço de memória físico de uma variável existente, permitindo associá-la a um ponteiro.
    
    ```
    int ano = 2018;      // Aloca uma variável de valor 2018
    int *ptr = &ano;     // Ponteiro "ptr" recebe o endereço físico de "ano"
    ```
    
- **Acesso ao Conteúdo de um Ponteiro**:
    - `printf("%p", ptr)`: Exibe o endereço de memória armazenado dentro do ponteiro em formato hexadecimal (usando especificador `%p` ou `%x`).
    - `printf("%d", *ptr)`: Usar o asterisco antes do ponteiro acessa e exibe diretamente o conteúdo armazenado no endereço de destino para o qual o ponteiro aponta.
- **Ponteiro Nulo (`NULL`)**: Constante que representa o valor "zero" para ponteiros, indicando explicitamente que ele não aponta para nenhum local de memória válido. É fundamental para inicialização e prevenção de acessos indevidos à memória.
- **Aritmética de Ponteiros**: A linguagem C restringe as operações aritméticas com ponteiros apenas a **adição e subtração de valores inteiros**. A alteração avança ou retrocede posições físicas na memória contígua proporcionalmente ao tamanho do tipo de dado associado:
    - `ptr++`: Adiciona 1 endereço físico ao ponteiro, deslocando-o para o próximo bloco contíguo de dados de mesmo tipo.
    - `(*ptr)++`: Incrementa em 1 o valor de dados contido dentro da variável que é apontada pelo ponteiro.
- **Ponteiros para Structs**: O acesso aos campos internos de uma estrutura através de seu ponteiro é feito de forma direta e limpa com a utilização do operador de seta (`->`), que substitui a sintaxe de desreferenciação por ponto. Exemplo: `ptr->idade = 30;`.

---

### 11. Modularização por Funções e Procedimentos

A divisão estruturada divide um software em funções independentes.

```
<tipo_de_retorno> <nome_da_funcao> (<parametros>) {
    // Bloco de comandos
    return <valor>; // Obrigatório se retorno não for void
}
```

- **Tipos de Sub-rotinas**:
    - **Função**: Possui tipo de retorno definido (ex: `int`, `float`), retornando obrigatoriamente um valor compatível ao final de sua execução por meio da instrução `return`.
    - **Procedimento**: Executa instruções sem gerar valor de retorno direto. Declara-se utilizando o tipo de retorno reservado `void` e dispensa a instrução `return` ao final.
- **Retorno de Arrays**: É proibido em C definir tipos de retorno direto como `int obterVetor()`. A única maneira de retornar arrays de funções é **retornando um ponteiro** que aponta para o endereço físico inicial do vetor criado internamente.
    - **Regra de Ouro**: O vetor criado dentro da função deve ser marcado obrigatoriamente com o atributo de escopo de duração **`static`**. Caso contrário, ao término da execução da função, todas as variáveis locais são desalocadas da memória pelo compilador, e o ponteiro retornado apontará para endereços vazios ou inválidos.

---

### 12. Escopo de Variáveis

O escopo define a área de visibilidade e o tempo de vida útil de uma variável no programa.

- **Variáveis Locais**: São declaradas dentro de uma função específica. Sua alocação e existência ocorrem apenas durante a execução daquela função, sendo permanentemente destruídas e liberadas da memória ao término de seu processamento.
- **Variáveis Globais**: São declaradas fora de qualquer função. Ficam permanentemente acessíveis a todas as funções de processamento do programa e permanecem ativas na memória RAM do computador durante todo o tempo de execução da aplicação.
- **Colisão de Nomes e Palavra-chave `extern`**: Se uma variável global e uma variável local forem criadas contendo exatamente o mesmo nome, o compilador dará prioridade e precedência total de uso ao valor da variável local dentro daquela função. Para que o desenvolvedor possa ignorar a variável local e acessar diretamente o valor da variável global de mesmo nome, utiliza-se a palavra-chave declarativa **`extern`** dentro de um bloco de chaves específico.

---

### 13. Mecanismos de Passagem de Parâmetros

- **Passagem por Valor**: É o mecanismo padrão da linguagem C. O programa principal gera e envia uma **cópia idêntica** do valor de dados contido nas variáveis originais para a função. A função de destino cria variáveis locais independentes na memória para trabalhar com essas cópias. Qualquer alteração de dados efetuada pela função ocorre exclusivamente nessas cópias e **não altera** em hipótese alguma o valor armazenado nas variáveis originais do programa principal.
- **Passagem por Referência**: O programa principal envia o **endereço de memória físico** da variável original para a função utilizando ponteiros na assinatura e o operador `&` na chamada. A função manipula diretamente a célula de memória RAM original, de modo que todas as alterações efetuadas em seu conteúdo pela função de destino **modificam permanentemente** os valores das variáveis originais correspondentes no programa principal.
- **Passagem de Vetores e Matrizes**: Em C, a passagem de vetores e matrizes para funções ocorre **sempre de forma implícita por referência**. O compilador não gera cópias do vetor; em vez disso, passa apenas o endereço físico do bloco inicial do array.
    - _Sintaxe na Assinatura_:
        - Para vetores: `void processa(int v[])` ou usando ponteiro `void processa(int *v)`.
        - Para matrizes: A dimensão das colunas deve ser obrigatoriamente informada na assinatura para garantir a linearidade do acesso físico: `void processaMatriz(int m[])`.

---

### 14. Recursividade

Técnica em que uma função chama a si própria para decompor um problema complexo em instâncias ou subproblemas idênticos, mas de menor escala.

- **Mecanismo na Memória RAM**: A cada nova auto-chamada recursiva efetuada, o sistema operacional cria e empilha na memória RAM uma **nova instância isolada da função**, alocando novos endereços e variáveis locais para o processamento de forma independente. As execuções ficam pendentes de finalização na pilha.
- **Caso Base (Critério de Parada)**: É a condição lógica mais simples que interrompe as chamadas recursivas subsequentes. Toda função recursiva deve conter obrigatoriamente um caso base explícito. Se o caso base for implementado de forma incorreta ou omitido, a função entrará em um laço infinito de auto-chamadas, criando novas instâncias consecutivamente até exaurir os recursos físicos do computador, gerando um **estouro de memória (estouro de pilha / _stack overflow_)** e travando a aplicação.

---

## Conceitos que não posso confundir

Para consolidar seu aprendizado e evitar equívocos clássicos em provas, atente-se às comparações detalhadas na tabela de conceitos fundamentais abaixo:

|Conceito A|Conceito B|Principais Diferenças|
|:--|:--|:--|
|**Constante `#define`**|**Constante `const`**|O `#define` é uma substituição direta de texto em nível de pré-compilação e não ocupa bytes físicos em memória RAM. A constante `const` comporta-se como uma variável estática, alocando memória real conforme seu tipo primitivo de dados.|
|**Laço `while`**|**Laço `do...while`**|O `while` testa a condição de permanência no topo, podendo nunca executar o bloco interno se o teste for falso. O `do...while` garante a execução do bloco de instruções no mínimo uma vez, pois realiza seu teste lógico somente no final.|
|**Passagem por Valor**|**Passagem por Referência**|Na passagem por valor, a função recebe apenas cópias e suas alterações não afetam as variáveis originais. Na passagem por referência, o endereço de memória RAM original é alterado de forma permanente através de ponteiros.|
|**Comando `break`**|**Comando `continue`**|O `break` interrompe e encerra de forma definitiva a execução de todo o laço ou switch atual. O `continue` apenas interrompe a iteração corrente, saltando os comandos restantes e avançando para o próximo ciclo do mesmo laço.|
|**Função**|**Procedimento**|Uma função processa instruções e retorna obrigatoriamente um único valor lógico ao final. Um procedimento é declarado com tipo `void` e apenas executa um conjunto de comandos locais, sem devolver nenhum valor direto.|
|**Variável Local**|**Variável Global**|Variáveis locais existem apenas dentro da função onde foram criadas. Variáveis globais residem na memória RAM durante toda a execução da aplicação e podem ser manipuladas livremente por qualquer função.|
|**Vetor (Array)**|**Matriz (Multidimensional)**|O vetor organiza dados de mesmo tipo de forma sequencial unidimensional. A matriz organiza os dados homogêneos de forma bidimensional (linhas e colunas), embora fisicamente ambos residam contiguamente na memória RAM.|
|**Operador `&`**|**Operador `*`**|O operador `&` extrai o endereço físico de memória RAM de uma variável. O operador `*` é utilizado tanto para declarar variáveis do tipo ponteiro quanto para acessar o valor armazenado no endereço apontado.|

---

## Pontos importantes para prova

- **Case Sensitivity**: Em C, a diferenciação entre maiúsculas e minúsculas é estrita. Se você declarar uma variável com o nome `nota` e tentar chamá-la de `Nota`, o compilador acusará erro de compilação.
- **Limites de Índice**: Um vetor em C de tamanho `N` possui seus índices indexados estritamente na faixa de `0` até `N-1`. Tentativas de acessar a posição `vetor[N]` constituem violação clássica e erro de acesso inválido à memória RAM.
- **Ausência de Break no `switch-case`**: A falta do comando de interrupção `break` não gera erros de compilação, mas causa desvio de lógica, fazendo o programa executar consecutivamente todos os blocos de comando seguintes até achar um break.
- **Sintaxe do Ponteiro de Struct**: A desreferenciação explícita de um ponteiro de estrutura com operador de ponto deve ser escrita obrigatoriamente entre parênteses: `(*ptr).propriedade`. Para evitar essa sintaxe complexa, utilize o operador de seta: `ptr->propriedade`.
- **Lixo de Memória**: Variáveis locais e vetores que não foram explicitamente inicializados herdam lixo de memória residual da memória RAM. Sempre inicialize variáveis de controle como acumuladores com o valor `0` (ou `1` para multiplicações acumuladas) para evitar desvios lógicos em cálculos.
- **Operador de Endereço no `scanf`**: É obrigatório o uso do caractere `&` antes de variáveis primitivas passadas ao `scanf`. A única exceção de sintaxe ocorre na leitura de strings e vetores, cujo identificador já constitui intrinsecamente um ponteiro para a primeira posição.
- **Teto de Contribuição de Vetor Estático**: Toda função que retorna vetores deve obrigatoriamente utilizar o modificador `static` na declaração local do array interno para preservar seu endereço de alocação de memória RAM após o encerramento do bloco de execução.

---

## Revisão rápida

```
graph TD
    A[Algoritmo] --> B[Entrada, Processamento e Saída]
    B --> C[Estruturas de Decisão: if-else, switch]
    B --> D[Laços de Repetição: while, do-while, for]
    D --> E[Desvios: break, continue]
    C --> F[Estruturas de Dados: Vetores e Matrizes]
    D --> F
    F --> G[Tipos Compostos: Structs]
    G --> H[Gerenciamento: Ponteiros * e &]
    H --> I[Modularização: Funções e Procedimentos]
    I --> J[Comunicação: Passagem por Valor e Referência]
    I --> K[Recursividade: Caso Base e Empilhamento]
```

1. **Algoritmo**: Etapas lógicas e finitas (entrada, processamento e saída).
2. **Sintaxe C**: Sensível a maiúsculas, finalizada com `;`, inicializada no `main()` com inclusão de bibliotecas.
3. **Controle de Fluxo**: Condições direcionam caminhos (`if-else`, `switch-case`); repetições realizam ciclos iterativos (`while`, `do-while`, `for`).
4. **Desvios**: `break` interrompe de forma abrupta; `continue` pula direto para a iteração seguinte.
5. **Vetores e Matrizes**: Estruturas homogêneas sequenciais contíguas em memória, indexadas de `0` até `N-1`.
6. **Structs**: Estruturas de dados heterogêneas personalizadas.
7. **Ponteiros**: Armazenam endereços RAM (`ptr = &var`) e dão acesso ao conteúdo de baixo nível (`*ptr`).
8. **Funções**: Modularizam tarefas complexas. Podem receber parâmetros copiados (por valor) ou referências diretas de endereços de memória (por referência).
9. **Recursividade**: Auto-chamadas que utilizam empilhamento físico e exigem um caso base para evitar falhas graves de estouro de pilha.

---
