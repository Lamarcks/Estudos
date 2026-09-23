[[Cadastro de Aluno em Linguagem Natural]]
[[Média de Notas com Validação de Aprovação (Fluxograma para C)]]
[[Declaração de Tipos Primitivos de Variáveis]]
[[Cálculo do Caixa de uma Pizzaria]]
[[Verificação de Idade para Habilitação]]
[[Verificação de Número Positivo ou Negativo]]
[[Faixa de Grandeza de um Número]]
[[Aplicação de Desconto por Tipo de Opção]]
[[Cálculo de Deduções de INSS e IR (Estudo de Caso)]]
[[Tabuada Interativa com While]]
[[Cálculo de Área de Terreno com Reaproveitamento de Sessão]]
[[Menu de Conta Bancária]]
[[Algoritmo da Conjectura de Collatz]]
[[Cálculo de Média com Quantidade de Avaliações Variável]]
[[Tabuada Determinística com For]]
[[Tabuadas de 1 a 5 com For Aninhados]]
[[Sequência de Coordenadas Inversas Simultâneas]]
[[Cálculo de Fatorial Iterativo]]
[[Renderização de Padrão Geométrico (Triângulo de Asteriscos)]]
[[Previsão de Expansão Populacional (Fibonacci)]]
[[Comandos de Desvio de Fluxo (break, continue, goto)]]
[[Filtragem de Números Ímpares com Pulo de Laço (continue)]]
[[Validação de Entrada de Dados com Tratamento de Erro (goto)]]
[[Gestão de Alunos e Disciplinas (break e continue combinados)]]
[[Padronização de CPF (Limpeza de Strings)]]
[[Soma das Diagonais de uma Matriz Quadrada]]
[[Multiplicação de Matrizes]]
[[Sistema de Notas de Alunos com Média Geral]]
[[Gestão de Acervo de Biblioteca (Cadastro de Livros)]]
[[Sistema Geral de Gestão Escolar (Cadastro de Turmas)]]
[[Somar +10 com Aritmética de Ponteiro em Vetores]]
[[Seleção Inteligente de Guindaste (Funções e Procedimentos)]]
[[Geração de Vetor Aleatório com Ponteiro Estático]]
[[Otimização de Cálculo de Reação de Proteção Química (Passagem por Valor)]]
[[Mutação de Valores de Variáveis (Passagem por Referência)]]
[[Processamento Coletivo de Valores em Vetores (Dobro dos Valores)]]
[[Mutação de Registro de Dados Estruturados por Referência]]
[[Caixa Rápido de Supermercado com Cálculo Multi-Itens]]
[[Sistema Bancário Unificado (Bolsofurado Bank)]]
[[Recursividade]]
[[Fatorial Recursivo]]
[[Cálculo de Raiz Quadrada pelo Método de Aproximações de Newton]]

Conceitos que não posso confundir

|Termo ou Conceito|Termo ou Conceito Parecido|Principais Diferenças e Critérios de Escolha|
|---|---|---|
|**Passagem por Valor**|**Passagem por Referência**|Na **Passagem por Valor**, a função opera exclusivamente sobre cópias isoladas das variáveis, mantendo intactas as variáveis originais no programa principal. Na **Passagem por Referência**, a função manipula de forma direta os endereços físicos originais na memória RAM por meio de ponteiros, mutando os valores de forma definitiva.|
|**Ponteiro (*****ptr****)**|**Operador de Endereço (****&var****)**|O **Ponteiro (*********)** é uma variável criada especificamente para armazenar endereços físicos de memória RAM de outros elementos. O **Operador de Endereço (****&****)** é utilizado para extrair a localização hexadecimal de uma variável para fins de armazenamento ou leitura.|
|**Constante** **#define**|**Constante** **const**|O **#define** substitui termos de forma textual em nível de pré-compilação e não ocupa bytes físicos em memória RAM. A constante **const** aloca fisicamente espaço em memória conforme seu tipo primitivo de dados.|
|**Laço** **while**|**Laço** **do...while**|O laço **while** executa o teste lógico no topo e pode nunca rodar o bloco interno se a condição for falsa na inicialização. O laço **do...while** realiza a avaliação condicional somente após executar todo o bloco, garantindo que as instruções rodem no mínimo uma vez.|
|**Laço** **while**|**Laço** **for**|O laço **while** é ideal para repetições indeterminadas, onde não sabemos quando o laço irá parar. O laço **for** é determinístico, pois agrupa inicialização, condição e incremento de forma explícita na mesma instrução para iterações com limite previamente conhecido.|
|**Comando** **break**|**Comando** **continue**|O comando **break** força o encerramento imediato de todo o laço ou bloco condicional switch corrente. O comando **continue** apenas interrompe a execução da rodada ou iteração atual, forçando o programa a saltar para a próxima rodada do mesmo laço.|
|**Comando** **break**|**Comando** **return**|O comando **break** encerra a execução de loops e blocos switch-case. O comando **return** encerra de forma definitiva a execução de toda a função na qual está inserido, devolvendo o controle e um valor para o chamador.|
|**Função**|**Procedimento**|A **Função** possui um tipo primitivo associado e retorna de forma obrigatória um único valor lógico de saída pelo comando `return`. O **Procedimento** realiza tarefas e não retorna dados, sendo declarado com tipo `void`.|
|**Vetor**|**Struct**|O **Vetor** é uma estrutura de dados homogênea que reúne elementos do mesmo tipo primitivo em sequência contígua de memória. A **Struct** é uma estrutura de dados heterogênea que agrupa dados de tipos diferentes sob o mesmo identificador.|
|**Aritmética de Ponteiro (****ptr++****)**|**Aritmética de Conteúdo (****(*ptr)++****)**|O incremento **ptr++** avança o ponteiro para o próximo endereço de memória contíguo de mesmo tipo. O incremento **(*ptr)++** altera o valor da variável original que está sendo apontada.|

---

Pontos importantes para prova

- **Rígida Diferenciação (****Case Sensitivity****)**: A linguagem C trata letras maiúsculas e minúsculas como elementos totalmente diferentes. Declarar `float Nota;` e tentar lê-la utilizando `scanf("%f", &nota);` provocará erro de compilação.
- **Limites Físicos de Vetores**: Para um vetor de tamanho `N`, o acesso físico válido às posições na memória RAM está restrito aos índices de `0` até `N-1`. Tentar ler ou alterar o elemento `vetor[N]` provoca violação de memória e desvios de lógica.
- **A Queda em Cascata do** **switch**: Se você omitir o comando `break` ao término das instruções de um `case` do `switch`, o compilador continuará executando de forma incondicional todos os comandos dos casos de baixo, até encontrar um break ou o fim do switch.
- **O Operador de Endereço no** **scanf**: É obrigatório utilizar o caractere `&` antes de nomes de variáveis primitivas passadas ao comando `scanf()`. A única exceção de sintaxe aceita ocorre na leitura de strings, cujo identificador já se comporta como um ponteiro para a posição inicial do vetor de caracteres na memória.
- **Preservação de Memória RAM com** **static**: Toda sub-rotina que retorna o endereço de um vetor local para a função principal deve rotular esse vetor com o termo `static` para preservar seus blocos de bytes após o término de sua execução.
- **Remoção de** **\n** **em Capturas com** **fgets**: A função de leitura segura `fgets` captura também a quebra de linha (`\n`) gerada pela tecla Enter ao final do comando. Utilize sempre a instrução `string[strcspn(string, "\n")] = 0;` para evitar falhas na comparação de strings com `strcmp`.
- **Lixo de Memória**: O compilador apenas reserva posições de memória física para variáveis e vetores recém-criados, sem realizar a limpeza de valores antigos. Sempre inicialize acumuladores com o valor `0` (ou `1` para multiplicações) para evitar erros nos resultados de seus cálculos.

---

Revisão rápida

1. **Fundamentos de Algoritmos**: Mapeamento sequencial de passos lógicos baseados na tríade Entrada, Processamento e Saída.
2. **Sintaxe Básica de C**: Declarações rígidas de variáveis e constantes finalizadas com ponto e vírgula.
3. **Controle de Fluxo Condicional**: Direcionamento lógico de caminhos por `if-else` ou `switch-case`.
4. **Estruturas de Repetição**: Repetições controladas por contadores ou sentinelas utilizando os laços `while`, `do-while` ou `for`.
5. **Desvios de Fluxo**: Uso de `break` para interrupção imediata, `continue` para pulo de ciclo e `goto` para saltos incondicionais.
6. **Estruturas de Dados Homogêneas**: Vetores e matrizes que armazenam coleções de mesmo tipo primitivo em blocos contíguos de memória RAM.
7. **Estruturas de Dados Heterogêneas**: Tipos de dados personalizados criados por `struct` que encapsulam diferentes tipos lógicos.
8. **Ponteiros**: Variáveis especiais que armazenam localizações físicas de memória RAM de outras variáveis para manipulação direta.
9. **Modularização**: Fragmentação de grandes códigos em funções e procedimentos independentes que se comunicam por valor ou referência.
10. **Recursividade**: Auto-chamadas que dependem de uma condição de parada de caso base para evitar falhas graves de estouro de pilha.