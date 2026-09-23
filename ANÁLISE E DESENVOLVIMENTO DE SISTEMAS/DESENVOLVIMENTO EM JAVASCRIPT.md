[[EXEMPLOS-PRÁTICOS DO DESENVOLVIMENTO EM JAVASCRIPT]]
#ASSUNTO

## Visão geral

O **JavaScript** é uma das linguagens mais importantes para o desenvolvimento web moderno, permitindo a criação de aplicações altamente dinâmicas e interativas. Esta nota de estudo aborda os princípios fundamentais da linguagem — incluindo sua sintaxe básica, operadores, estruturas de controle e estruturas de dados —, avança para o estudo das **APIs do navegador (DOM, Canvas e áudio)**, examina a **programação orientada a eventos**, detalha a **comunicação assíncrona cliente-servidor** e, por fim, compara os principais **frameworks de mercado (Angular, Vue.js e React)**.

---

## Conceitos principais

- **JavaScript (ECMAScript):** Linguagem de programação de alto nível, dinâmica, interpretada e não tipada. Foi criada originalmente pela Netscape com o nome ECMAScript. Ela opera em conjunto com o HTML (conteúdo) e CSS (estilo) para injetar interatividade no ecossistema web.
- **DOM (Document Object Model):** API global do navegador que representa a estrutura de um documento HTML ou XML em forma de árvore, permitindo que scripts manipulem dinamicamente seu conteúdo, estrutura e estilo.
- **Programação Orientada a Eventos:** Paradigma de programação no qual o fluxo de execução do sistema é determinado pela ocorrência de eventos (como interações do usuário via mouse ou teclado, ou alterações no estado da página).
- **AJAX (Asynchronous JavaScript and XML):** Modelo de arquitetura de software para aplicações web que utiliza requisições assíncronas via HTTP/HTTPS para atualizar partes de uma página web a partir do servidor, sem a necessidade de recarregá-la por completo.
- **Frameworks:** Plataformas estruturadas de desenvolvimento que fornecem modelos básicos de arquitetura e funcionalidades pré-implementadas, visando reduzir o esforço e acelerar a produtividade do programador.

---

## Conteúdo explicado

### 1. Princípios Básicos e Sintaxe do JavaScript

#### Como Vincular o JavaScript ao HTML

O código JavaScript pode ser escrito diretamente em um arquivo com extensão `.js`. Para associar este arquivo a uma página HTML, utiliza-se a tag `<script>`:

```
<script src="nome_do_arquivo.js"></script>
```

> **Regra de Performance:** Recomenda-se inserir essa tag logo antes do fechamento do elemento `</body>`. Isso garante que todos os elementos visuais do HTML sejam renderizados pelo navegador antes que o código JavaScript seja interpretado, evitando erros de carregamento e melhorando o desempenho.

#### Tipos de Dados e Variáveis

O JavaScript possui tipagem dinâmica. Suas variáveis podem ser declaradas usando as palavras-chave `var` ou `let`. Os principais tipos aceitos incluem:

- **Numbers:** Representa valores numéricos, unificando inteiros e reais sob o mesmo tipo.
- **Strings:** Cadeias de texto delimitadas por aspas duplas (`" "`) ou apóstrofos/aspas simples (`' '`).
- **Booleans:** Valores lógicos representados estritamente por `true` (verdadeiro) ou `false` (falso).

#### Operadores

O JavaScript utiliza operadores para manipulações lógicas e matemáticas básicas:

|Categoria|Operador|Descrição|Exemplo|
|:--|:--|:--|:--|
|**Aritméticos**|`+`|Soma (ou concatenação de strings)|`x + y`|
||`-`|Subtração|`x - y`|
||`*`|Multiplicação|`x * y`|
||`/`|Divisão|`x / y`|
||`**`|Exponenciação (potência)|`x ** y`|
||`%`|Resto de uma divisão inteira|`x % y`|
||`=`|Atribuição de valor|`x = 5`|
|**Relacionais (Comparação)**|`==`|Igualdade de valor (converte tipos se necessário)|`x == y`|
||`===`|Igualdade estrita (mesmo valor e mesmo tipo)|`x === y`|
||`!=`|Diferente de|`x != y`|
||`<` / `>`|Menor que / Maior que|`x < y`|
||`<=` / `>=`|Menor ou igual / Maior ou igual|`x <= y`|
|**Lógicos**|`&&`|Operador E (AND) – requer todas as condições verdadeiras|`condA && condB`|
||`\|\|`|
||`!`|Operador NÃO (NOT) – inverte o valor lógico da condição|`!condA`|

---

### 2. Estruturas de Controle e Repetição

#### Estruturas Condicionais (Controle de Fluxo)

- **`if`:** Determina que um bloco de código delimitado por chaves `{ }` seja executado apenas se a condição associada for estritamente verdadeira.
- **`if...else`:** Adiciona um bloco alternativo de comandos (`else`) para ser executado quando a condição testada no `if` for avaliada como falsa.
- **`if...else` aninhado ou encadeado:** Permite testar sequencialmente múltiplas condições complexas por meio de ramificações compostas (`else if`).

#### Estruturas de Repetição (Laços e Iterações)

- **`for`:** Utilizado para repetir um bloco de comandos um número predeterminado de vezes.
    - _Sintaxe:_ `for(inicialização; condição_parada; incremento/decremento) { ... }`.
    - _Funcionamento:_ Inicializa uma variável contadora, testa a condição antes de cada iteração e atualiza o contador ao final do bloco.
- **`while`:** Executa repetidamente o bloco associado enquanto a condição de parada estabelecida dentro dos parênteses for verdadeira. A validação é feita **antes** da execução dos comandos.
- **`do...while`:** Executa os comandos descritos no bloco e apenas realiza a verificação lógica da condição de parada ao final da iteração.
    - _Regra Importante:_ Devido à ordem de checagem, o código dentro de um bloco `do...while` é executado **obrigatoriamente pelo menos uma vez**, mesmo que a condição de parada já seja falsa de início.

---

### 3. Estruturas de Dados Avançadas: Funções, Arrays e Objetos

#### Funções

Blocos isolados de código que executam uma tarefa específica quando invocados. São declaradas com a palavra-chave `function` e podem aceitar argumentos/parâmetros para processamento interno.

- **Arrow Functions:** Uma sintaxe mais limpa, enxuta e elegante para declaração de funções no JavaScript moderno.
    - _Sintaxe clássica:_
        
        ```
        function soma(n1, n2) { return n1 + n2; }
        ```
        
    - _Sintaxe reduzida (Arrow Function):_
        
        ```
        soma = (n1, n2) => n1 + n2
        ```
        

#### Arrays

Estruturas semelhantes a listas que armazenam coleções ordenadas de elementos acessados por um índice numérico que inicia em zero (`0`).

- **Principais Métodos e Propriedades de Manipulação de Arrays:**
    - `length`: Retorna o número total de elementos presentes no array.
    - `push()`: Adiciona um novo elemento ao final do array.
    - `pop()`: Remove o último elemento do array.
    - `shift()`: Remove o primeiro elemento do array (posição zero).
    - `splice()`: Remove ou substitui elementos de partes específicas de um array, podendo gerar sub-arrays a partir de índices definidos.
    - `sort()`: Ordena os elementos do array em ordem alfabética crescente.

#### Objetos

Coleções que agrupam múltiplos valores (atributos/propriedades) e métodos (funções) que operam sobre estes valores. Podem ser criados por instanciação genérica (`new Object()`) ou de modo direto e literal, assemelhando-se ao formato de pares de chave e valor:

```
var carro = { marca: "Ford", modelo: "Fiesta" }; // Declaração literal
```

---

### 4. APIs de Navegador: DOM, Canvas, Áudio e Gráficos

O navegador fornece APIs nativas que estendem as capacidades do JavaScript, permitindo interações complexas com o ambiente de exibição.

#### Manipulação de Documentos via DOM

A manipulação dos elementos da árvore DOM baseia-se em métodos de acesso que retornam referências aos objetos do documento HTML:

- `getElementById('id_do_elemento')`: Retorna um único elemento correspondente ao ID informado.
- `getElementsByClassName('classe')`: Retorna um vetor/coleção com todos os elementos filhos que possuem a classe CSS especificada.
- `getElementsByName('nome')`: Retorna uma coleção de objetos filtrada pelo atributo `name`.
- `querySelectorAll('seletor')`: Retorna uma lista estática de elementos que coincidem com os seletores CSS informados.

#### Alteração Dinâmica de Estilo (CSS) via DOM

Cada elemento acessado possui propriedades do objeto `style` e do objeto `className`, que permitem atualizar estilos inline ou alterar a classe do elemento dinamicamente:

```
var elemento = document.getElementById('mensagem');
elemento.style.color = 'red'; // Modifica diretamente a cor do texto inline
```

#### Renderização Gráfica com `<canvas>` (HTML5)

O elemento `<canvas>` atua como uma tela branca de pintura cujos gráficos são controlados via scripts.

- `getContext('2d')`: Método fundamental que retorna o contexto bidimensional para habilitar funções de desenho de texto e formas geométricas na tela do canvas.
- `fillStyle`: Propriedade utilizada para definir a cor ativa de preenchimento dos objetos gráficos.
- `fillRect(x, y, largura, altura)`: Desenha um retângulo preenchido na tela do canvas com base nas coordenadas de posição inicial `(x, y)` e tamanho definidos.
- `fillText('texto', x, y)`: Adiciona uma cadeia de texto renderizada em coordenadas específicas do canvas.

#### Áudio no HTML5

Permite a reprodução simplificada de arquivos multimídia (como MP3) no navegador. É representado pelo elemento `<audio>` no HTML e suporta controle dinâmico via propriedades.

---

### 5. Programação Orientada a Eventos no Navegador

#### Ciclo do Evento

Um evento é a manifestação física de um comportamento sofrido pelo documento web. Para responder a um evento, registra-se uma função em JS chamada de **escutador** ou **tratador de eventos** utilizando o método `addEventListener()`.

#### Categorias de Eventos Legados e Modernos

- **Eventos de Formulário:** Associados diretamente à interação com elementos de preenchimento de dados.
    - `submit` / `onsubmit`: Disparado quando os dados de um formulário são enviados. Crucial para interceptar e validar dados localmente antes de enviá-los ao servidor web.
    - `formdata`: Disparado após a construção da lista de dados que representam o formulário.
    - `reset`: Acionado quando o formulário é limpo ou redefinido.
- **Eventos de Interface de Usuário / Janela:** Controlam o estado geral do documento.
    - `focus` (ou `onfocus`): Disparado quando um elemento (como um campo de formulário) ganha foco de entrada.
    - `blur` (ou `onblur`): Disparado quando o elemento perde o foco de entrada.
    - `change`: Disparado quando o usuário modifica o valor de elementos como `<input>` ou `<select>`.
    - `onload`: Acionado no momento em que a página web é completamente carregada.
    - `onunload`: Acionado quando a página é fechada ou o usuário navega para fora.
    - `onresize`: Disparado sempre que as dimensões de largura e altura da janela do navegador são redimensionadas.
    - `onerror`: Disparado em falhas inesperadas de carregamento ou rede.
    - `ononline` / `onoffline`: Disparados quando o navegador detecta alteração de conectividade de rede.
- **Eventos de Mouse:**
    - `onclick`: Executado ao clicar uma vez em um elemento.
    - `ondbclick`: Executado ao clicar duas vezes.
    - `onmousedown` / `onmouseup`: Pressionar / soltar o botão do mouse sobre o elemento.
    - `onmouseover` / `onmouseout`: Mover o ponteiro para dentro / fora dos limites do elemento.
    - `onmousemove`: Disparado continuamente à medida que o ponteiro se move dentro da tela.
- **Eventos de Teclado:**
    - `onKeyDown`: Disparado quando o usuário está pressionando qualquer tecla (incluindo teclas de controle que não geram caracteres visuais).
    - `onKeyPress`: Disparado apenas quando a tecla pressionada produz um caractere de texto legível.
    - `onKeyUp`: Disparado quando a tecla é solta.
- **Eventos Mobile e de Toque (Touch):** Essenciais para dispositivos sensíveis ao toque.
    - `touchstart`: Disparado no instante em que um ou mais dedos entram em contato físico com a tela.
    - `touchmove`: Disparado conforme o dedo se move pela superfície da tela.
    - `touchend`: Acionado quando o dedo é removido da tela.
    - `touchcancel`: Disparado quando o toque é interrompido repentinamente.
    - _Eventos de Gesto (Apple):_ `gesturestart`, `gesturechange`, `gestureend` mapeiam rotação e mudança de escala executadas com dois dedos.
- **Eventos CSS (Animações):**
    - `animationstart`: Ocorre quando uma animação definida por CSS começa.
    - `animationiteration`: Disparado entre os ciclos de iteração de uma animação contínua.
    - `animationend`: Disparado no instante exato em que a animação CSS é concluída.
    - `animationcancel`: Disparado se a animação for abortada inesperadamente.

---

### 6. Comunicação Assíncrona (XMLHttpRequest e AJAX)

#### Classe XMLHttpRequest

É a classe do navegador responsável por instanciar objetos que efetuam a comunicação assíncrona HTTP/HTTPS diretamente com o servidor web. Cada instância representa um ciclo isolado de requisição e resposta.

- **Propriedades e Métodos Básicos:**
    - `open(método, URL, async)`: Inicializa os parâmetros de uma requisição definindo o verbo HTTP (como `GET` ou `POST`), a URL de destino e se o processo será assíncrono.
    - `send()`: Envia de fato a solicitação configurada para o servidor.
    - `readyState`: Indica o estado atual da transação da requisição.
    - `status`: Retorna o código de status numérico da resposta HTTP enviada pelo servidor.
    - `response`: Retorna o corpo do conteúdo recebido na resposta.

#### Códigos de Status de Resposta HTTP (Metas de Validação)

Ao analisar o status de uma requisição via `XMLHttpRequest.status`, os códigos são divididos em faixas de classes para representar a situação do envio:

|Classe de Código|Tipo de Resposta|Descrição|
|:--|:--|:--|
|**100 – 199**|Informativas|Comunicação em nível inicial de protocolo.|
|**200 – 299**|Bem-sucedidas|O pedido foi recebido, compreendido e aceito com sucesso (Ex: `200 OK`).|
|**300 – 399**|Mensagens de redirecionamento|Recursos movidos para outra URL.|
|**400 – 499**|Erro do Cliente|O pedido contém sintaxe incorreta ou não pôde ser atendido (Ex: `404 Not Found`).|
|**500 – 599**|Erro do Servidor|O servidor falhou ao processar uma requisição válida.|

---

### 7. Consumo de APIs de Terceiros

As APIs de terceiros fornecem bibliotecas ou serviços que residem fora do navegador do usuário, exigindo a obtenção de chaves de acesso e leitura atenta de sua documentação.

- **APIs Populares de Mercado:**
    - **ViaCEP:** Serviço gratuito que consulta e retorna dados estruturados de endereço (rua, bairro, cidade, estado) no formato JSON a partir de um CEP válido.
    - **OpenLayers:** API gratuita sob licença BSD para carregamento e manipulação de mapas interativos, blocos de imagem e marcadores geográficos vetoriais em páginas web.
    - **OpenAI API (ChatGPT):** API assíncrona que processa consultas em modelos neurais e retorna textos gerados via inteligência artificial em formato JSON.

---

### 8. Frameworks JavaScript de Mercado

Os frameworks de segunda geração surgiram para solucionar problemas de complexidade arquitetural em aplicações web dinâmicas.

#### Vue.js

É classificado como um **framework progressivo** de front-end para construção de interfaces. Foi projetado para ser adotado de modo incremental, de forma que o desenvolvedor possa importar apenas parte de seus recursos em projetos existentes. É mantido ativamente pela comunidade.

#### Angular

Plataforma de desenvolvimento robusta e componentizada baseada em **TypeScript**. Historicamente derivado do AngularJS (versão legada), evoluiu para uma plataforma escalável com controle forte de diretivas diretamente nos templates HTML. Seu ecossistema inclui ferramentas CLI integradas para testar, compilar e implantar sistemas de forma padronizada.

- **Principais Diretivas do Angular:**
    - `ng-app`: Designa e inicializa o elemento raiz (root) de uma aplicação Angular.
    - `ng-controller`: Atribui uma classe de controlador TypeScript a uma visualização (View).
    - `ng-disabled`: Desativa ou ativa um elemento visual HTML de acordo com condições lógicas.
    - `ng-show`: Oculta ou exibe elementos HTML dinamicamente avaliando expressões fornecidas.

#### React

React é classificado como uma **biblioteca declarativa** de código aberto para a construção de interfaces de usuário. Sua principal característica é a velocidade de desempenho propiciada pelo uso do DOM Virtual, atualizando apenas os elementos modificados da tela. Utiliza propriedades chamadas `props` para que os componentes se comuniquem hierarquicamente entre si.

#### Quadro Comparativo dos Frameworks:

|Critério|Angular|Vue.js|React|
|:--|:--|:--|:--|
|**Padrão Arquitetural**|Não impõe padrão específico em sua documentação.|Inspirado no padrão **MVVM** (Model-View-ViewModel).|Baseado no padrão tradicional **MVC** (Model-View-Controller).|
|**Comunidade / Suporte**|Destaca-se negativamente por não possuir fórum oficial para dúvidas na sua documentação.|Comunidade oficial ativa no Discord.|Comunidade oficial ativa no Discord.|
|**Tamanho de Pacotes**|Gera arquivos maiores em um mesmo projeto web.|Apresenta tamanho de arquivos intermediário.|É o framework que gera o **menor tamanho** de arquivos de projeto.|
|**Tempo de Renderização**|Apresenta o desempenho de renderização mais lento entre os três.|Apresenta desempenho de renderização intermediário.|Apresenta o **melhor e mais rápido** desempenho de renderização.|

---

## Conceitos que não posso confundir

```
  ┌─────────────────────────────────────────────────────────────────────────┐
  │                           JAVASCRIPT vs JAVA                            │
  │ Apesar da semelhança nominal histórica (ligada à empresa Netscape), são  │
  │ linguagens totalmente distintas em sua arquitetura e execução.      │
  └─────────────────────────────────────────────────────────────────────────┘
```

- **`==` vs `===`:** O operador `==` compara apenas o valor final das variáveis, permitindo que o JS converta os tipos por baixo dos panos (ex: `5 == "5"` é verdadeiro). O operador `===` é de **igualdade estrita**, exigindo o mesmo valor e o mesmo tipo de dado para retornar verdadeiro (ex: `5 === "5"` é falso).
- **`while` vs `do...while`:** O laço `while` faz o teste lógico da condição _antes_ de executar a primeira instrução. O laço `do...while` executa o bloco de instruções e faz o teste lógico _depois_, garantindo que os comandos rodem **pelo menos uma vez**.
- **`Mutation Event` vs `Mutation Observer`:** `Mutation Event` é uma abordagem legada de escuta a alterações estruturais do DOM que apresentava problemas de inconsistência grave entre navegadores. `Mutation Observer` é a API global moderna baseada em um construtor padronizado e robusto para reagir eficientemente às modificações do DOM.
- **Framework vs API:** Um **Framework** é uma plataforma que estrutura a arquitetura da sua aplicação, fornecendo as fundações sobre as quais o seu código é construído. Uma **API** é uma interface de programação de aplicativos que atua fornecendo recursos, dados ou funcionalidades externas prontas para serem consumidas pelo seu sistema (como a API ViaCEP, que apenas fornece dados de endereço a partir de requisições).

---

## Pontos importantes para prova

1. **Ordem da tag `<script>`:** O local ideal de inserção de scripts vinculados é no encerramento da tag `</body>` para garantir que o DOM esteja completamente montado e renderizado, evitando exceções de elementos nulos ao carregar a página.
2. **Operador de Igualdade Estrita (`===`):** Questões de prova cobram com frequência o comportamento de tipos no JavaScript. Lembre-se que `"10" === 10` é estritamente **falso**, enquanto `"10" == 10` é **verdadeiro**.
3. **Garantia de Iteração Mínima:** O laço `do...while` é a única estrutura de repetição que tem execução mínima garantida de **uma rodada**, independentemente da condição lógica inicial ser falsa.
4. **Método de Renderização Virtual:** O React deve seu excelente desempenho em renderização em relação ao Angular e Vue devido ao uso do **Virtual DOM**, atualizando estritamente as partes modificadas da página.
5. **Classes de Status HTTP:** Estude as faixas de status HTTP: requisições bem-sucedidas são identificadas na faixa **200 a 299**, enquanto erros gerados no lado do cliente (como parâmetros de requisição incorretos) situam-se na faixa **400 a 499**.
6. **Tratamento de Animações CSS com JS:** O evento `animationend` é crucial para criar lógica sequencial em páginas dinâmicas, pois permite executar funções JavaScript exatamente quando uma animação de estilo CSS é concluída.

---

## Revisão rápida

- **Sintaxe Básica:** JavaScript é dinâmico, não tipado e interpretado. Variáveis usam `let` ou `var`. Tipos básicos: Number, String e Boolean.
- **Laços:** `for` pré-determina iterações; `while` valida antes de iterar; `do...while` valida após iterar (executa ao menos 1 vez).
- **Arrays & Objetos:** Arrays iniciam no índice `0`. Métodos: `push` (insere), `pop` (remove fim), `shift` (remove início). Objetos armazenam chaves e valores estruturados.
- **DOM:** Representação em árvore do HTML. Seletores principais: `getElementById` e `querySelectorAll`. Estilização via `style`.
- **Eventos:** Capturados por `addEventListener()`. Principais: `submit` (envio), `onblur` (perda de foco), `onclick` (clique), `onresize` (redimensionar janela).
- **XMLHttpRequest:** Executa requisições assíncronas (AJAX). Métodos: `open()` (configura) e `send()` (envia). Status `200` indica requisição concluída com sucesso.
- **Frameworks:** Angular é modular e baseado em TypeScript; React é biblioteca leve com Virtual DOM que atualiza de forma rápida e eficiente; Vue.js é progressivo e incremental.

---

## Perguntas para revisão

1. **Por que o JavaScript é classificado como uma linguagem de tipagem dinâmica e não tipada?**
    - _Resposta Esperada:_ Porque não exige que o desenvolvedor declare explicitamente o tipo de dados de uma variável (como string ou número) durante sua criação. O tipo é interpretado dinamicamente no momento da execução com base no valor atribuído à variável.
2. **Qual a diferença crucial entre a forma de validação lógica do laço `while` e do laço `do...while`?**
    - _Resposta Esperada:_ O laço `while` valida se a condição é verdadeira antes de executar qualquer bloco de código. O laço `do...while` executa primeiro o bloco de instruções e apenas realiza a verificação de parada ao final, garantindo que o bloco seja executado pelo menos uma vez.
3. **Como o método `addEventListener` contribui para a experiência dinâmica do usuário em páginas de formulário?**
    - _Resposta Esperada:_ Ele permite registrar funções tratadoras no navegador que respondem dinamicamente a ações como o envio de um formulário (`submit`). Isso permite que o JavaScript valide os dados localmente, evite requisições desnecessárias ao servidor e forneça feedback em tempo real para o usuário.
4. **Em termos de arquitetura e velocidade de renderização de telas, por que o React apresenta melhor desempenho que o Angular?**
    - _Resposta Esperada:_ Porque o React utiliza um padrão de representação de DOM Virtual que atualiza apenas os elementos pontuais da interface que sofreram alteração. O Angular, além de gerar pacotes de arquivos substancialmente maiores, processa e renderiza as mudanças de forma mais pesada, resultando no pior desempenho comparativo de renderização entre os dois.
5. **O que caracteriza uma API como sendo de "terceiros" e como ela difere das APIs nativas do navegador?**
    - _Resposta Esperada:_ APIs de terceiros não são nativas do navegador e exigem que o desenvolvedor obtenha dados ou códigos de fontes externas na web. Diferente de APIs de navegador (como o DOM, que já está embutido), as de terceiros (como OpenAI ou ViaCEP) exigem chamadas de requisição em rede para servidores externos.
6. **Descreva a função das propriedades `readyState` e `status` na classe `XMLHttpRequest`.**
    - _Resposta Esperada:_ A propriedade `readyState` rastreia o estado atual do ciclo da requisição assíncrona HTTP/HTTPS. Já a propriedade `status` armazena o código numérico de retorno do servidor (como `200` para sucesso e `404` para recurso não encontrado), indicando o resultado do processamento da solicitação.

---
