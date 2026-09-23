[[EXERCÍCIOS DE LÓGICA E MATEMÁTICA COMPUTACIONAL]]
#ASSUNTO

## Visão geral

Esta nota de estudo consolida os fundamentos da **Lógica Matemática e Computacional** e da **Teoria de Conjuntos**. O conteúdo abrange desde os conceitos básicos de conjuntos e proposições lógicas até tópicos avançados como a construção e simplificação de tabelas-verdade, demonstrações pelo método dedutivo e análise combinatória estruturada. Desenvolvida com foco em aprendizagem ativa e revisão sistemática, esta nota integra definições rigorosas, exemplos práticos do cotidiano e do desenvolvimento de software, fórmulas detalhadas e as melhores práticas para provas.

---

## Conceitos principais

Para dominar a matéria, é crucial compreender com clareza as definições fundamentais que servem de base para toda a disciplina:

- **Proposição**: Uma sentença declarativa que exprime um pensamento completo e que pode ser classificada unicamente como verdadeira (\(V\) ou \(1\)) ou falsa (\(F\) ou \(0\)), mas nunca ambas.
- **Premissa**: Uma proposição declarativa assumida como verdadeira que serve de ponto de partida ou sustentação para construir um raciocínio lógico.
- **Argumento**: Um conjunto de proposições estruturado composto por uma ou mais premissas e uma conclusão, onde a última deriva logicamente das primeiras.
- **Silogismo**: Um tipo clássico de raciocínio dedutivo mediado, formalizado por Aristóteles, que consiste em exatamente duas premissas (maior e menor) e uma conclusão que se infere necessariamente delas.
- **Conjunto**: Uma coleção ou agrupamento bem definido de elementos, membros, objetos ou números distintos, considerada como uma entidade única.
- **Cardinalidade**: O tamanho de um conjunto, definido pelo número total de elementos distintos contidos nele, representado por barras de valor absoluto (ex: \(|A|\)).
- **Fórmula Bem-Formulada (fbf)**: Uma expressão lógica composta por proposições, conectivos e delimitadores que respeita estritamente as regras de sintaxe da lógica proposicional.
- **Tabela-Verdade**: Uma representação sistemática em formato tabular que exibe todas as possíveis combinações de valores de verdade das variáveis de entrada e os respectivos resultados de uma expressão lógica ou função booleana.
- **Tautologia**: Uma proposição composta ou expressão lógica cujo resultado final é sempre verdadeiro, independentemente dos valores lógicos individuais das proposições que a compõem.
- **Inferência Lógica**: O processo sistemático de aplicar regras de dedução formais para derivar novas conclusões lógicas a partir de premissas conhecidas ou aceitas.

---

## Conteúdo explicado

### 1. Teoria e Álgebra de Conjuntos

#### A. Definição e Representação de Conjuntos

Um conjunto é denotado convencionalmente por letras maiúsculas (\(A, B, C\)). Para listar e descrever os elementos, que são representados por chaves, existem três métodos principais:

1. **Listagem Direta**: Listar todos os elementos individualmente. Recomendado para conjuntos finitos pequenos.
    - _Exemplo_: \(A = {0, 1, 2, 3, 4}\).
2. **Identificação de Padrão (Reticências)**: Indicar os primeiros termos para sugerir um padrão infinito ou extenso.
    - _Exemplo_: \(B = {2, 4, 6, \dots}\) (números inteiros positivos pares).
3. **Por Propriedade Característica**: Descrever uma condição lógica que todos os elementos devem cumprir.
    - _Exemplo_: \(C = {x \mid x \text{ é um número inteiro e } 4 < x \leq 9}\). Listando seus elementos, temos: \(C = {5, 6, 7, 8, 9}\).

Também utilizamos a representação visual dos **Diagramas de Venn** (ou círculos eulerianos), em que círculos sobrepostos ilustram graficamente as relações e partilhas entre conjuntos.

#### B. Pertinência (\(\in\)) versus Continência (\(\subset\))

- **Pertinência (\(\in\), \(\notin\))**: Relaciona um **elemento** a um **conjunto**. Indica se o elemento é membro ou não do conjunto.
    - _Exemplo_: No conjunto de cores da bandeira do Brasil \(A = {\text{verde}, \text{amarelo}, \text{azul}, \text{branco}}\), temos que \(\text{verde} \in A\) e \(\text{vermelho} \notin A\).
- **Continência (\(\subseteq\), \(\subset\))**: Relaciona **conjunto** a **conjunto**. Indica se um conjunto é subconjunto de outro (ou seja, se todos os elementos de um pertencem ao outro).
    - Se \(A \subseteq B\) mas \(A \neq B\) (existe pelo menos um elemento em \(B\) que não pertence a \(A\)), então \(A\) é um **subconjunto próprio** de \(B\) (notação: \(A \subset B\)).

#### C. Conjuntos Numéricos Fundamentais

Os números são classificados em conjuntos com características específicas:

- **Naturais (\(\mathbb{N}\))**: Contagem de inteiros não negativos. \(\mathbb{N} = {0, 1, 2, 3, 4, \dots}\).
- **Inteiros (\(\mathbb{Z}\))**: Números naturais somados aos inteiros negativos. \(\mathbb{Z} = {\dots, -2, -1, 0, 1, 2, 3, \dots}\).
- **Racionais (\(\mathbb{Q}\))**: Números que podem ser expressos como frações de inteiros (inclui dízimas periódicas). \(\mathbb{Q} = { \frac{a}{b} \mid a, b \in \mathbb{Z} \text{ e } b \neq 0}\).
- **Irracionais (\(\mathbb{I}\))**: Números decimais não periódicos e infinitos (como \(\pi\), \(\sqrt{2}\), \(\sqrt{3}\)).
- **Reais (\(\mathbb{R}\))**: A união dos números racionais e irracionais.

```
Representação de inclusão: N ⊂ Z ⊂ Q ⊂ R (e I ⊂ R)
```

#### D. Quantificadores Lógicos

Utilizados para indicar a extensão em que uma propriedade se aplica sobre um conjunto:

- **Quantificador Universal (\(\forall\))**: Lê-se "para todo", "para cada" ou "qualquer que seja".
    - _Exemplo_: \(\forall x \in \mathbb{Z}, x \text{ é par ou } x \text{ é ímpar}\).
- **Quantificador Existencial (\(\exists\))**: Lê-se "existe", "existe algum" ou "há".
    - _Exemplo_: \(\exists x \in \mathbb{N}, x \text{ é primo e par}\).

#### E. Cardinalidade e o Teorema dos Subconjuntos

Um conjunto é **finito** quando sua cardinalidade é um número inteiro, e **infinito** caso contrário. Um conjunto desprovido de elementos é o **conjunto vazio**, denotado por \(\emptyset\) ou \({}\), possuindo cardinalidade \(0\).

- **Teorema dos Subconjuntos**: Se um conjunto finito \(A\) possui cardinalidade \(|A| = n\), o número total de subconjuntos possíveis que podem ser formados a partir de \(A\) é dado por: \[\text{Número de subconjuntos} = 2^{|A|} = 2^n\]
- _Exemplo_: Para o conjunto de chaves de acesso \(A = {1, 2, 3, 4}\), temos \(|A| = 4\). Logo, ele possui \(2^4 = 16\) subconjuntos. Estes incluem o conjunto vazio \(\emptyset\) e o próprio conjunto \(A\).

#### F. Operações Básicas com Conjuntos

As operações clássicas permitem manipular coleções de dados de forma rigorosa:

|Operação|Símbolo|Definição Matemática|Explicação Simples|Exemplo (\(A = {1, 2, 3}, B = {3, 4, 5}\))|
|:--|:-:|:--|:--|:--|
|**União**|\(\cup\)|\(A \cup B = {x \mid x \in A \text{ ou } x \in B}\)|Elementos que estão em \(A\), em \(B\) ou em ambos.|\(A \cup B = {1, 2, 3, 4, 5}\)|
|**Interseção**|\(\cap\)|\(A \cap B = {x \mid x \in A \text{ e } x \in B}\)|Apenas os elementos comuns a ambos.|\(A \cap B = {3}\)|
|**Diferença**|\(-\)|\(A - B = {x \mid x \in A \text{ e } x \notin B}\)|Elementos exclusivos de \(A\), excluindo os de \(B\).|\(A - B = {1, 2}\)|
|**Complemento**|\(A^C\) ou \(A'\)|\(U - A = {x \in U \mid x \notin A}\)|O que "falta" para \(A\) alcançar o Conjunto Universo \(U\).|Se \(U = {1,2,3,4,5,6}\), então \(A^C = {4,5,6}\).|
|**Diferença Simétrica**|\(\Delta\)|\(A \Delta B = (A - B) \cup (B - A)\)|Elementos que pertencem a apenas um dos conjuntos.|\(A \Delta B = {1, 2, 4, 5}\)|

_Nota sobre o Complementar_: Para que o complementar de \(B\) em relação a \(A\) (\(C_A^B\)) exista, **\(B\) deve ser subconjunto de \(A\) (\(B \subseteq A\))**. Se os conjuntos forem disjuntos (interseção vazia), o cálculo é impossível.

#### G. Princípio de Inclusão-Exclusão (Contagem)

Para evitar a dupla contagem de elementos na união de conjuntos sobrepostos, aplicamos a fórmula: \[|A \cup B| = |A| + |B| - |A \cap B|\]

- _Exemplo Prático (Startup de TI)_: Um aplicativo tem 60 comandos no total (\(|A \cup B| = 60\)). 20 comandos realizam buscas no Banco \(A\) (\(|A| = 20\)) e 12 comandos em ambos os Bancos \(A\) e \(B\) (\(|A \cap B| = 12\)). Quantos realizam busca no Banco \(B\)? \[60 = 20 + |B| - 12 \implies |B| = 52 \text{ comandos}\]

#### H. Produto Cartesiano e Relações Arbitrárias

- **Produto Cartesiano (\(A \times B\))**: O conjunto de todos os pares ordenados \((a, b)\) gerados de modo que \(a \in A\) e \(b \in B\). A ordem importa, portanto, \((a, b) \neq (b, a)\).
    - _Fórmula da Cardinalidade_: \(|A \times B| = |A| \times |B|\).
    - _Exemplo_: Se \(A = {2, 3}\) and \(B = {4, 5}\), então \(A \times B = {(2, 4), (2, 5), (3, 4), (3, 5)}\).
- **Relações Arbitrárias por Codificação Binária**: Um método lógico-diagramático para mapear compartimentos em Diagramas de Venn com 3 conjuntos (\(A, B, C\)):
    - Usa-se um código binário de 3 bits: cada bit (\(1\) ou \(0\)) representa se um elemento pertence ou não a um determinado conjunto na ordem \(A, B, C\).\n * \(100\): Pertence exclusivamente a \(A\).
    - \(110\): Pertence a \(A\) e \(B\), mas não a \(C\) (\(A \cap B \cap C^C\)).
    - \(111\): Pertence à interseção dos três conjuntos (\(A \cap B \cap C\)).
    - \(000\): Não pertence a nenhum dos conjuntos (\(A^C \cap B^C \cap C^C\)).

---

### 2. Fundamentos da Lógica Proposicional

#### A. O que é Proposição?

A proposição é a unidade fundamental da lógica. Para ser considerada uma proposição válida no estudo da lógica, a frase **obrigatoriamente deve ser declarativa**.

- **Sentenças que NÃO são proposições lógicas**:
    - _Sentenças Imperativas (ordens)_: "Segure firme!"
    - _Sentenças Interrogativas (perguntas)_: "Que horas são?"
    - _Sentenças Exclamativas_: "Que lindo!"

#### B. Os Três Princípios Básicos das Proposições

Qualquer proposição formal deve obedecer rigorosamente a três princípios lógicos fundamentais:

1. **Princípio da Identidade**: Toda proposição é idêntica a si mesma (\(P\) é \(P\)).
2. **Princípio da Não Contradição**: Uma proposição não pode ser verdadeira e falsa ao mesmo tempo.
3. **Princípio do Terceiro Excluído**: Toda proposição ou é verdadeira ou é falsa, não existindo um terceiro valor que ela possa assumir (\(P\) ou não \(P\)).

#### C. Proposições Simples versus Compostas

- **Proposição Simples**: Apresenta uma única afirmação lógica isolada.
    - _Exemplo_: \(A\): "O Sol é uma estrela".
- **Proposição Composta**: Constituída pela união de duas ou mais proposições simples ligadas por conectivos lógicos.
    - _Exemplo_: \(C\): "11 é um número ímpar e 11 é um número primo".

---

### 3. Operadores Lógicos e Ordem de Precedência

Os operadores lógicos combinam e transformam os valores de verdade das proposições simples para formar expressões complexas:

|Conectivo|Operação Lógica|Símbolo|Equivalência Textual|Regra de Valoração|
|:--|:--|:-:|:--|:--|
|**Negação**|Negação|\(\neg\) ou \(\sim\)|"Não...", "É falso que..."|Inverte o valor lógico original (\(V \to F\) e \(F \to V\)).|
|**Conjunção**|Conjunção (AND)|\(\wedge\)|"... e ..."|Só é **verdadeira se ambas** as proposições forem verdadeiras.|
|**Disjunção**|Disjunção Inclusiva (OR)|\(\vee\)|"... ou ..."|Só é **falsa se ambas** as proposições forem falsas.|
|**Condicional**|Implicação Lógica|\(\rightarrow\)|"Se..., então..."|Só é **falsa no caso \(V \rightarrow F\)** (antecedente \(V\) e consequente \(F\)).|
|**Bicondicional**|Equivalência|\(\leftrightarrow\)|"... se, e somente se, ..."|É **verdadeira quando os valores lógicos forem iguais** (\(V \leftrightarrow V\) ou \(F \leftrightarrow F\)).|

#### Ordem de Precedência Estrita das Expressões Lógicas

Em uma fórmula com múltiplos conectivos e sem parênteses, a avaliação deve respeitar a ordem de prioridade estabelecida:

1. **Parênteses internos**: Expressões dentro dos parênteses mais internos sempre se resolvem primeiro.
2. **Negação (\(\neg\))**.
3. **Conjunção (\(\wedge\)) e Disjunção (\(\vee\))** (se emparelhadas, resolve-se da esquerda para a direita).
4. **Condicional (\(\rightarrow\))**.
5. **Bicondicional (\(\leftrightarrow\))**.

_Exemplo de Impacto_:

- A expressão \(A \wedge B \rightarrow A\) equivale sintaticamente a \((A \wedge B) \rightarrow A\) devido à precedência da conjunção sobre a condicional. Esta fbf resulta em uma Tautologia.
- Caso se queira forçar a condicional primeiro, o uso de parênteses é obrigatório: \(A \wedge (B \rightarrow A)\). Esta fbf não é uma tautologia.

---

### 4. Tabela-Verdade e Classificação de Fórmulas

#### A. Estrutura e Número de Linhas

O número de linhas de uma tabela-verdade depende diretamente da quantidade de proposições simples (\(n\)) existentes na fórmula: \[\text{Número de linhas} = 2^n\]

- Para 2 proposições ($A, B$): \(2^2 = 4\) linhas.
- Para 3 proposições (\(A, B, C\)): \(2^3 = 8\) linhas.

#### B. Construção por Proposições Intermediárias

Para evitar erros em fórmulas complexas, criamos colunas para cada etapa do cálculo, de dentro para fora dos parênteses.

- _Exemplo_: Avaliar a fbf \(Z = \neg(A \vee B)\) para as variáveis \(A\) e \(B\):

|\(A\)|\(B\)|Proposição Intermediária: \((A \vee B)\)|Fórmula Final: \(Z = \neg(A \vee B)\)|
|:-:|:-:|:-:|:-:|
|\(V\)|\(V\)|\(V\)|\(F\)|
|\(V\)|\(F\)|\(V\)|\(F\)|
|\(F\)|\(V\)|\(V\)|\(F\)|
|\(F\)|\(F\)|\(F\)|\(V\)|

#### C. Classificação de Fórmulas Lógicas

- **Tautologia**: O resultado lógico final é verdadeiro em todas as linhas da tabela-verdade.
    - _Exemplo clássico_: \(A \vee \neg A\) ("hoje está chovendo ou hoje não está chovendo").
- **Contradição**: O resultado lógico final é falso em todas as linhas.
    - _Exemplo clássico_: \(B \wedge \neg B\) ("hoje é segunda-feira e hoje não é segunda-feira").
- **Contingência**: O resultado apresenta valores verdadeiros e falsos misturados a depender das entradas.

#### D. Propriedades Algébricas da Equivalência Lógica

Duas proposições compostas são equivalentes (\(\equiv\) ou \(\Leftrightarrow\)) quando produzem tabelas-verdade idênticas para as mesmas entradas. As principais propriedades são:

1. **Comutatividade**: A ordem dos fatores não altera o resultado lógico.
    - \(P \vee Q \Leftrightarrow Q \vee P\)
    - \(P \wedge Q \Leftrightarrow Q \wedge P\)
2. **Associatividade**: Permite reagrupar os conectivos idênticos.
    - \((P \vee Q) \vee R \Leftrightarrow P \vee (Q \vee R)\)
    - \((P \wedge Q) \wedge R \Leftrightarrow P \wedge (Q \wedge R)\)
3. **Distributividade**: Semelhante à "distribuição" matemática.
    - \(P \vee (Q \wedge R) \Leftrightarrow (P \vee Q) \wedge (P \vee R)\)
    - \(P \wedge (Q \vee R) \Leftrightarrow (P \wedge Q) \vee (P \wedge R)\)
4. **Equivalência do Condicional**: Uma condicional pode ser reescrita como uma disjunção:
    - \(P \rightarrow Q \Leftrightarrow \neg P \vee Q\)
5. **Dupla Negação**: Negar uma negação retorna à afirmação original:
    - \(\neg(\neg P) \Leftrightarrow P\)

#### E. Leis de De Morgan

Essenciais para simplificar expressões e circuitos eletrônicos, essas leis ensinam como aplicar a negação sobre conjunções e disjunções:

- **Primeira Lei (Negação da Conjunção)**: A negação de uma conjunção é equivalente à disjunção das negações. \[\neg(P \wedge Q) \Leftrightarrow \neg P \vee \neg Q\]
- **Segunda Lei (Negação da Disjunção)**: A negação de uma disjunção é equivalente à conjunção das negações. \[\neg(P \vee Q) \Leftrightarrow \neg P \wedge \neg Q\]

---

### 5. Métodos Dedutivos, Prova Formal e Regras de Inferência

#### A. O que é um Argumento Válido?

Diferente das proposições (que são verdadeiras ou falsas), **um argumento só pode ser válido ou inválido**. Ele é válido quando a sua estrutura lógica garante que, assumindo as premissas como verdadeiras, a conclusão é necessariamente verdadeira. A validade depende estritamente da **forma lógica** e não do conteúdo semântico.

- _Exemplo de Argumento Inválido com Proposições Verdadeiras_: "D. Pedro I proclamou a independência do Brasil. Thomas Jefferson escreveu a Declaração de Independência dos EUA. Portanto, o dia tem 24 horas." As três afirmações são verdades factuais, mas o argumento é inválido porque a conclusão não é consequência lógica das premissas.

#### B. Sequência de Demonstração

Provamos a validade de um argumento construindo uma sequência numerada de fbfs em linhas individuais. Cada linha deve conter uma **hipótese (premissa)** ou ser o resultado da aplicação de uma **regra de dedução** sobre linhas anteriores, avançando até alcançar a conclusão procurada.

#### C. Regras de Inferência Cruciais

##### 1. Modus Ponens (MP) — "Método de Afirmação"

Dada uma implicação e a afirmação do seu antecedente, deduz-se o consequente. \[\frac{P \rightarrow Q, \quad P}{Q}\]

- _Exemplo_: Se o papel de tornassol ficar vermelho, a solução é ácida (\(P \rightarrow Q\)). O papel ficou vermelho (\(P\)). Logo, a solução é ácida (\(Q\)).

##### 2. Modus Tollens (MT) — "Método de Negação"

Dada uma implicação e a negação do seu consequente, deduz-se a negação do antecedente. \[\frac{P \rightarrow Q, \quad \neg Q}{\neg P}\]

- _Exemplo_: Se treino, venço o campeonato (\(P \rightarrow Q\)). Não venci o campeonato (\(\neg Q\)). Logo, não treinei (\(\neg P\)).

##### 3. Silogismo Hipotético (SH) — "Lei de Transitividade"

Dadas duas implicações em que o consequente da primeira é o antecedente da segunda, deduz-se uma nova implicação direta. \[\frac{P \rightarrow Q, \quad Q \rightarrow R}{P \rightarrow R}\]

##### 4. Outras Regras de Inferência Importantes:

- **Conjunção**: Dadas duas proposições independentes, elas podem ser unidas em um "e" lógico. \[\frac{P, \quad Q}{P \wedge Q}\]
- **Simplificação**: Dada uma conjunção verdadeira, pode-se deduzir qualquer uma de suas partes de forma isolada. \[\frac{P \wedge Q}{P}\]
- **Adição**: Dada uma proposição verdadeira, pode-se adicionar qualquer outra proposição à expressão usando uma disjunção inclusiva. \[\frac{P}{P \vee Q}\]

---

### 6. Análise Combinatória (Técnicas de Contagem)

A análise combinatória foca na contagem de agrupamentos de elementos com base nas propriedades do problema:

#### A. Arranjo Simples

Seleção ordenada de \(p\) elementos distintos de um conjunto maior de \(n\) elementos disponíveis (\(n > p\)), em que a **ordem dos elementos importa** e **não há repetição**. \[A_{n, p} = \frac{n!}{(n-p)!}\]

- _Exemplo (Senhas)_: Quantas senhas de 4 algarismos distintos podemos formar usando os algarismos de 0 a 9? Temos \(n=10\) e \(p=4\). \[A_{10, 4} = \frac{10!}{(10-4)!} = \frac{10!}{6!} = \frac{10 \times 9 \times 8 \times 7 \times 6!}{6!} = 5040 \text{ senhas}\]

#### B. Arranjo com Repetição

Semelhante ao arranjo simples, mas **permite a repetição** dos elementos em diferentes posições do agrupamento. $$AR_{n, p} = n^p$$

- _Exemplo (Cartão Bancário)_: Uma senha bancária de 4 dígitos usando algarismos de 0 a 9 (\(n=10, p=4\)) onde números podem se repetir. $$AR_{10, 4} = 10^4 = 10.000 \text{ senhas possíveis}$$

#### C. Permutação Simples

Um caso especial de arranjo em que o número de elementos selecionados é idêntico ao número de posições disponíveis (\(n = p\)). Consiste em simplesmente **reordenar todos os elementos** do grupo. $$P_n = n!$$

- _Exemplo (Anagramas)_: Quantas palavras (com ou sem sentido) podem ser formadas reordenando as letras de "MATE"? Temos \(n=4\) letras. $$P_4 = 4! = 4 \times 3 \times 2 \times 1 = 24 \text{ permutações}$$

#### D. Combinação Simples

Seleção de um subconjunto de $k$ elementos a partir de um conjunto maior de $n$ elementos, em que **a ordem dos elementos NÃO importa**. $$C_{n, k} = \left(\begin{matrix} n \ k \end{matrix}\right) = \frac{n!}{k!(n-k)!}$$

- _Exemplo (Comissões)_: De quantas maneiras podemos selecionar um grupo de 4 funcionários a partir de uma equipe de 10 pessoas? A ordem de escolha não importa. $$C_{10, 4} = \frac{10!}{4!(10-4)!} = \frac{10 \times 9 \times 8 \times 7 \times 6!}{4! \times 6!} = \frac{5040}{24} = 210 \text{ grupos distintos}$$

---

## Conceitos que não posso confundir

No Obsidian, use esta seção como um guia visual rápido para evitar os erros mais comuns em avaliações:

> [!danger] **Pertinência (\(\in\)) vs. Continência (\(\subseteq\))**
> 
> - **Pertinência (\(\in\))**: liga um **elemento individual** a um conjunto.
> - _Correto_: $3 \in {1, 2, 3}$.\n> * _Incorreto_: ${3} \in {1, 2, 3}$ (a menos que o conjunto contivesse outro conjunto lá dentro).
> - **Continência (\(\subseteq\))**: liga **conjunto** a **conjunto** (subconjuntos).
> - _Correto_: ${3} \subseteq {1, 2, 3}$.
> - _Incorreto_: $3 \subseteq {1, 2, 3}$.

> [!warning] **Lógica Indutiva vs. Lógica Dedutiva**
> 
> - **Lógica Dedutiva**: Parte de leis gerais ou premissas universais para inferir conclusões particulares. **A conclusão é garantida** (100% de certeza) se as premissas forem verdadeiras e a forma for válida.
> - **Lógica Indutiva**: Parte de observações particulares para chegar a uma conclusão geral. **A conclusão é provável**, mas não garantida de forma absoluta (um único contraexemplo a invalida).

> [!abstract] **Arranjo vs. Permutação vs. Combinação** Pergunte-se sempre: _A ordem importa? Quantos elementos vou usar?_
> 
> 1. **A ordem importa?**
> 
> - **Não**: É **Combinação** (ex: escolher sabores de pizza, comitês).
> - **Sim**: Vá para a próxima pergunta.
> 
> 2. **Vou usar TODOS os elementos do conjunto nas posições disponíveis (\(n = p\))?**
> 
> - **Sim**: É **Permutação** (ex: anagramas, organizar livros na estante, fila indiana).
> - **Não (\(n > p\))**: É **Arranjo** (ex: pódio de corrida, senhas, cargos de gerência).

> [!info] **Tautologia vs. Contradição vs. Contingência**
> 
> - **Tautologia**: Coluna final da tabela-verdade tem **apenas $V$**.
> - **Contradição**: Coluna final da tabela-verdade tem **apenas $F$**.
> - **Contingência**: Coluna final possui **tanto $V$ quanto $F$**.

> [!tip] **Conjunto ${a, b}$ vs. Par Ordenado $(a, b)$**
> 
> - No **conjunto**, a ordem dos elementos não importa: ${3, 8} = {8, 3}$.
> - No **par ordenado**, a ordem dos elementos é estrita: $(3, 8) \neq (8, 3)$ pois representam coordenadas diferentes em um plano cartesiano.

---

## Pontos importantes para prova

1. **A Armadilha do Condicional (\(P \rightarrow Q\))**: Lembre-se de que a condicional só é falsa quando o antecedente é verdadeiro e o consequente é falso (\(V \rightarrow F = F\)). **Se o antecedente (\(P\)) for falso, o condicional é automaticamente verdadeiro (\(V\))**, independentemente do valor de $Q$.
2. **Equivalência Clássica**: A condicional $P \rightarrow Q$ cai muito em provas para ser reescrita usando a equivalência $\neg P \vee Q$.
3. **Diferença entre Equivalência e Inferência**:
    - As regras de equivalência funcionam em **via de mão dupla** (bi-direcionais), ex: você pode trocar \(\neg(P \vee Q)\) por \(\neg P \wedge \neg Q\) e vice-versa.
    - As regras de inferência são de **via única** (unidirecionais), ex: a partir de \(P \wedge Q\) você pode deduzir \(P\) (simplificação), mas a partir de \(P\) você não pode retornar para \(P \wedge Q\) sem informações adicionais.
4. **Cuidado com os Parênteses em Negações**: $\neg(P \wedge Q)$ (negação de toda a operação) é completamente diferente de $P \wedge \neg Q$ (negação agindo apenas sobre $Q$). A primeira inverte o resultado da conjunção, enquanto a segunda exige que $P$ seja verdadeiro e $Q$ seja falso para ser verdadeira.
5. **A Condição do Complementar**: O complementar de um conjunto $B$ em relação a $A$ (\(C_A^B\)) exige obrigatoriamente que $B \subseteq A$. Se a questão na prova der conjuntos disjuntos, a resposta correta é que o complementar não está definido.

---

## Revisão rápida

### Fórmulas de Análise Combinatória

- **Permutação Simples**: \(P_n = n!\)
- **Arranjo Simples**: \(A_{n, p} = \frac{n!}{(n-p)!}\)
- **Arranjo com Repetição**: \(AR_{n, p} = n^p\)
- **Combinação Simples**: \(C_{n, p} = \frac{n!}{p!(n-p)!}\)

### Tabela-Verdade Resumida dos Operadores

|\(P\)|\(Q\)|\(\neg P\)|\(P \wedge Q\)|\(P \vee Q\)|\(P \rightarrow Q\)|\(P \leftrightarrow Q\)|
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
|**V**|**V**|F|V|V|V|V|
|**V**|**F**|F|F|V|F|F|
|**F**|**V**|V|F|V|V|F|
|**F**|**F**|V|F|F|V|V|

### As Leis de De Morgan

- \(\neg(P \wedge Q) \Leftrightarrow \neg P \vee \neg Q\)
- \(\neg(P \vee Q) \Leftrightarrow \neg P \wedge \neg Q\)

### Os 3 Princípios Lógicos

1. **Identidade**: $P \equiv P$.
2. **Não Contradição**: $\neg(P \wedge \neg P)$.
3. **Terceiro Excluído**: $P \vee \neg P$.

---
