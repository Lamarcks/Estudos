# Front-End, Back-End e Arquitetura de Aplicações

## Visão geral

A programação web abrange a construção completa de aplicações virtuais, dividindo-se entre a camada de interface e interatividade do usuário (**Front-End**) e a camada de processamento, regras de negócio e persistência de dados no servidor (**Back-End**). A estrutura e semântica das páginas são estabelecidas pelo **HTML5**, enquanto a apresentação visual, layouts responsivos e estilização modular são controlados pelo **CSS3**. A dinâmica comportamental e a manipulação assíncrona da interface ficam a cargo do **JavaScript (ES6+)**. No servidor, a execução lógica é suportada pelo **PHP**, integrando bancos de dados relacionais (**MySQL**) por meio do padrão **CRUD**, estruturando-se através da arquitetura **MVC** e disponibilizando recursos via **APIs RESTful** em formato **JSON**.

---

## Conceitos principais

- **Linguagem de Marcação vs. Programação vs. Estilo**: Linguagens de marcação (como o **HTML**) utilizam etiquetas (_tags_) para estruturar e organizar o conteúdo de um documento. Linguagens de estilo (como o **CSS**) descrevem a apresentação gráfica e o layout do documento. Já as linguagens de programação (como **JavaScript** e **PHP**) implementam algoritmos, lógica de decisão, manipulação de dados e processamento.
- **DOM (Document Object Model)**: Interface de programação que representa o documento HTML como uma **árvore hierárquica de nós** em memória. Permite que scripts como o JavaScript leiam, alterem, adicionem ou removam elementos, estilos e atributos em tempo real.
- **Box Model (Modelo de Caixa)**: Conceito fundamental do CSS onde cada elemento renderizado é tratado como uma caixa retangular composta por quatro camadas concêntricas: **Conteúdo (Content)**, **Preenchimento interno (Padding)**, **Borda (Border)** e **Margem externa (Margin)**.
- **Design Responsivo e Mobile-First**: Filosofia de design onde a aplicação adapta seu layout ao tamanho e características da tela (_viewport_) do dispositivo do usuário. A estratégia _Mobile-First_ estabelece a codificação primária para telas menores, expandindo a complexidade para telas maiores usando _Media Queries_.
- **Programação Assíncrona (Promises / Async-Await)**: Modelo de execução não bloqueante onde operações demoradas (como requisições de rede) ocorrem em segundo plano sem congelar a interface do usuário, devolvendo o resultado futuramente por meio de _Callbacks_, _Promises_ ou sintaxe `async/await`.
- **Arquitetura Cliente-Servidor e Protocolo Stateless**: Modelo onde o cliente (navegador) envia requisições HTTP e o servidor processa e retorna respostas. Por padrão, o protocolo HTTP é _stateless_ (sem estado), significando que o servidor não retém a memória de requisições anteriores sem mecanismos auxiliares como Sessões e Cookies.
- **Arquitetura MVC (Model-View-Controller)**: Padrão arquitetural que divide a aplicação em três camadas interdependentes para isolar responsabilidades: o **Model** lida com dados e regras de negócio; a **View** gerencia a apresentação de interface ao usuário; o **Controller** intermedeia o fluxo, recebendo requisições e coordenando a resposta.
- **API RESTful e Formato JSON**: Conjunto de rotas (_endpoints_) baseadas em recursos que utilizam verbos HTTP padronizados (`GET`, `POST`, `PUT`, `DELETE`) para troca de dados leves e estruturados em **JSON** (JavaScript Object Notation).

---

## Conteúdo explicado

### 1. Fundamentos de Estruturação e Semântica Web (HTML5)

#### Estrutura Básica do Documento

Todo documento HTML5 deve ter um esqueleto primordial delimitado por elementos estruturais cruciais:

- `<!DOCTYPE html>`: Declaração que informa ao navegador a versão do HTML utilizada.
- `<html>`: Elemento raiz que envolve todo o documento.
- `<head>`: Contém metainformações não exibidas diretamente no palco visual, como a codificação de caracteres (`<meta charset="UTF-8">`), a configuração da janela de exibição (`<meta name="viewport" ...>`), títulos da aba (`<title>`) e links para folhas de estilo CSS externas.
- `<body>`: Palco visível contendo todos os textos, imagens, vídeos, tabelas e formulários que compõem a interface acessível ao usuário.

#### Semântica, Hierarquia e Aninhamento

A semântica consiste na escolha de etiquetas com base no seu significado e propósito real, e não pela sua aparência visual. O uso adequado de marcas semânticas melhora a **acessibilidade** para leitores de tela e a indexação em **motores de busca (SEO)**.

- **Cabeçalhos (`<h1>` a `<h6>`)**: Estabelecem a hierarquia de tópicos do documento, onde `<h1>` é o título principal e os demais representam subníveis hierárquicos.
- **Blocos e Seções**: `<article>` representa um conteúdo autônomo; `<section>` agrupa blocos temáticos; `<aside>` guarda informações secundárias/laterais; `<header>` e `<footer>` definem cabeçalho e rodapé da página ou seção.
- **Aninhamento**: O encadeamento de marcas exige uma estrutura LIFO (_Last In, First Out_ — o último elemento aberto deve ser o primeiro a ser fechado). O elemento genérico `<div>` atua como um contêiner de agrupamento sem valor semântico próprio.

#### Formulários, Tabelas e Mídias

- **Formulários (`<form>`)**: Mecanismo de coleta de dados do usuário. Agrupa campos de entrada (`<input>`) mapeados por etiquetas (`<label for="...">`) e organizados em grupos lógicos com `<fieldset>` e `<legend>`. O HTML5 fornece validações nativas do lado do cliente por meio de atributos como `required`, `pattern` (expressões regulares), `type="email"`, `minlength` e `maxlength`.
- **Tabelas (`<table>`)**: Exibição de dados tabulares organizados em linhas (`<tr>`), células de cabeçalho (`<th>`) e células de dados (`<td>`), divididos nas seções semânticas `<thead>`, `<tbody>` e `<tfoot>`.
- **Mídias e Hiperlinks**:
    - `<img>`: Inserção de imagens auto-fechável via atributo `src`, acompanhada obrigatoriamente da alternativa textual `alt` para acessibilidade.
    - `<video>`: Reprodução de mídia audiovisual com atributos `controls`, `autoplay`, `loop` e suporte a legendas de acessibilidade via marcação `<track kind="subtitles">` em formato WebVTT.
    - `<a>`: Elemento de ancoragem para links absolutos (com protocolo `https://` completo) ou relativos, podendo utilizar o atributo `target="_blank"` para abertura em nova aba.

---

### 2. Estilização, Layouts e Design Responsivo (CSS3)

#### Sintaxe e Seletores CSS

A regra CSS é composta por um **Seletor** apontando para o alvo HTML e um bloco de declarações com pares de **Propriedade: Valor;** encerrados por ponto e vírgula.

- **Seletor de Tipo/Elemento**: Seleciona todas as marcas do tipo no documento (ex: `p { color: blue; }`).
- **Seletor de Classe (`.classe`)**: Estiliza grupos de elementos que compartilham o atributo `class`.
- **Seletor de ID (`#id`)**: Aponta para um único elemento exclusivo identificado pelo atributo `id`.
- **Seletores Combinadores e Atributos**: Permitem selecionar filhos diretos (`ul > li`), descendentes gerais (`div p`) ou elementos por atributo (`a[target="_blank"]`).

#### Hierarquia, Cascata e Especificidade

Quando múltiplas regras conflitantes disputam o mesmo elemento, a **Cascata** resolve o conflito avaliando a **Origem**, a **Ordem de Declaração** (a última regra prevalece) e o peso da **Especificidade** do seletor: \[\text{Especificidade: } \text{Inline Style} > \text{ID } (#) > \text{Classe } (.) / \text{Atributo} > \text{Elemento/Tag}\]

- _Atenção_: A diretiva `!important` força a prioridade absoluta da regra, quebrando a cascata natural, devendo ser evitada para não dificultar a manutenção do código.

#### Modelo de Caixa e Posicionamento

- **Dimensionamento (`box-sizing`)**:
    - `content-box` (padrão): A largura e altura declaradas aplicam-se apenas ao conteúdo. O tamanho total visual é recalculado somando `largura + padding + border`.
    - `border-box`: A largura e altura declaradas já incluem o `padding` e a `border`, facilitando o cálculo exato de layout.
- **Propriedade `position`**:
    - `static`: Fluxo normal padrão de renderização do documento; ignora propriedades `top`, `left`, `right`, `bottom`.
    - `relative`: Mantém o espaço original no fluxo, deslocando-se a partir da sua posição inicial.
    - `absolute`: Removido do fluxo normal da página; posiciona-se em relação ao ancestral posicionado mais próximo (com `position` diferente de `static`).
    - `fixed`: Removido do fluxo; fixa-se em relação à janela do navegador (_viewport_), permanecendo estático durante a rolagem.
    - `sticky`: Comporta-se como `relative` até atingir um limite de rolagem definido, fixando-se na tela como `fixed` a partir daquele ponto.

#### Flexbox e Design Responsivo

- **Flexbox**: Módulo de layout unidimensional (linha ou coluna) ativado por `display: flex` no contêiner pai. Permite alinhar e distribuir espaço entre itens dinamicamente utilizando propriedades como `flex-direction`, `justify-content` (alinhamento no eixo principal) e `align-items` (alinhamento no eixo cruzado).
- **Media Queries e Tipografia Flexível**: Diretivas `@media screen and (min-width: ...)` aplicam regras condicionais conforme a largura da tela. O uso de unidades relativas como `rem` (baseado na fonte do elemento `html`) combinado com `max-width: 100%` para imagens garante flexibilidade total sem transbordamento.
- **Variáveis CSS e Modularização**: Declaradas no pseudo-seletor `:root` (ex: `--cor-primaria: #007bff;`) e consumidas via `var(--cor-primaria)`, facilitando a criação de temas (Light/Dark Mode). A modularização organiza os arquivos em pastas lógicas e os unifica no arquivo principal usando `@import` ou organizadores de arquitetura (BEM, SMACSS).

---

### 3. Programação Client-Side e Interatividade (JavaScript ES6+)

#### Fundamentos da Linguagem e Tipos

O JavaScript é uma linguagem orientada a objetos e de tipagem dinâmica, executada no cliente para manipulação da interface ou no servidor por ambientes como Node.js.

- **Variáveis**:
    - `var`: Declaração antiga com escopo abrangente.
    - `let`: Declaração moderna (ES6) com escopo de bloco.
    - `const`: Declaração de constante de valor imutável com escopo de bloco.
- **Tipos Primitivos**: `Number`, `String`, `Boolean`, `null` (ausência intencional de valor), `undefined` (variável não inicializada) e `Symbol`.
- **Tipos de Objetos**: Arrays (`[]`), Objetos Literais (`{ chave: valor }`) e Funções.

#### Manipulação do DOM e Eventos

- **Seleção de Elementos**:
    - `document.getElementById("id")`: Seleciona por ID único.
    - `document.querySelector("seletor_css")`: Retorna o primeiro elemento correspondente ao seletor CSS.
    - `document.querySelectorAll("seletor_css")`: Retorna uma lista com todos os elementos correspondentes.
- **Alteração de Conteúdo e Estilo**:
    - `elemento.textContent = "Texto"`: Altera com segurança apenas o texto contido.
    - `elemento.innerHTML = "<strong>HTML</strong>"`: Interpreta e insere tags HTML dentro do nó.
    - `elemento.classList.add("classe")` e `remove("classe")`: Manipula classes CSS sem sobrescrever a lista inteira.
- **Escuta de Eventos**:
    - `elemento.addEventListener('click', function)`: Registra executores para interações de mouse (`click`), teclado (`keydown`), formulários (`submit`, `focus`, `blur`) e eventos da janela ou documento (`load`, `DOMContentLoaded`).

#### Programação Assíncrona e Consumo de APIs

Operações que envolvem comunicação externa utilizam o modelo assíncrono para evitar o travamento da interface:

- **Promises**: Objetos representando a conclusão ou falha de uma operação futura.
- **`async / await`**: Açúcar sintático sobre Promises que permite escrever código assíncrono com aparência síncrona.
- **`fetch(url)`**: API nativa do navegador para emissão de requisições HTTP assíncronas.

```
// Exemplo de busca assíncrona em API usando async/await e Fetch
const buscarDadosCEP = async function(cep) {
    let url = `https://viacep.com.br/ws/${cep}/json/`;
    let response = await fetch(url);
    let dados = await response.json(); // Converte a resposta bruta em objeto JSON
    console.log(dados);
};
```

---

### 4. Desenvolvimento Server-Side, Persistência e Integração (PHP & MySQL)

#### Ambiente Server-Side e Processamento PHP

Diferente das linguagens client-side, o código **PHP (Hypertext Preprocessor)** é processado inteiramente no servidor web (ex: Apache através do ambiente XAMPP) antes que o resultado puro em HTML/CSS/JS seja entregue ao navegador do cliente.

- **Delimitadores**: Todo bloco de código PHP deve estar delimitado por `<?php ... ?>`.
- **Comandos e Variáveis**: A instrução `echo` exibe dados na saída da página. As variáveis são declaradas obrigatoriamente com o prefixo do cifrão (ex: `$nome = "Maria";`) e possuem tipagem dinâmica.

#### Superglobais, Formulários e Controle de Estado

- **Interpretação de Formulários**:
    - `$_GET`: Array superglobal com os parâmetros recebidos visivelmente pela URL.
    - `$_POST`: Array superglobal contendo os dados enviados de forma embutida no corpo da requisição HTTP (ideal para senhas e formulários extensos).
- **Gerenciamento de Estado (Stateless)**:
    - **Sessões (`$_SESSION`)**: Armazenam dados temporários no lado do servidor vinculados a um identificador único de usuário. Exige a chamada `session_start()` no topo de cada script.
    - **Cookies (`$_COOKIE`)**: Arquivos de dados gravados diretamente no navegador do cliente por meio da função `setcookie()` executada antes de qualquer saída de texto.

#### Banco de Dados Relacional e Padrão CRUD

O armazenamento de informações dinâmicas e permanentes exige a conexão com um Sistema Gerenciador de Banco de Dados como o **MySQL**. As operações básicas do modelo **CRUD** mapeiam-se diretamente para a linguagem SQL:

|Operação CRUD|Ação SQL|Função PHP / Exemplo|
|:--|:--|:--|
|**Create (Criar)**|`INSERT INTO tbl (...) VALUES (...)`|Insere uma nova linha de registro na base de dados.|
|**Read (Ler)**|`SELECT * FROM tbl`|Consulta dados. Processados via `mysqli_fetch_assoc()`.|
|**Update (Atualizar)**|`UPDATE tbl SET col=val WHERE id=x`|Altera os registros existentes identificados por uma chave.|
|**Delete (Excluir)**|`DELETE FROM tbl WHERE id=x`|Apaga permanentemente a instância de registro do banco.|

Conexão no PHP utilizando a biblioteca `mysqli`:

```
$conexao = mysqli_connect("localhost", "root", "senha", "db_nome"); // Conecta ao MySQL
$resultado = mysqli_query($conexao, "SELECT * FROM tbl_livro"); // Executa script SQL
while ($linha = mysqli_fetch_assoc($resultado)) {
    echo $linha['title']; // Retorna cada linha como array associativo
}
```

#### Arquitetura MVC e Desenvolvimento de APIs RESTful

- **Estruturação MVC**:
    - **Model**: Comunica-se com o banco de dados (`mysqli`/`PDO`) e executa as regras de validação e persistência.
    - **View**: Camada visual e modelo de apresentação entregue ao usuário.
    - **Controller**: Recebe a requisição, solicita o processamento ao Model e envia a resposta apropriada para a View.
- **APIs RESTful**: Endpoints organizados com o uso de micro-frameworks como o **Slim Framework**. O servidor trata requisições interpretando o JSON enviado no corpo da mensagem (`json_decode`) e responde codificando os arrays do banco com `json_encode` e retornando códigos de status HTTP apropriados.

---

## Conceitos que não posso confundir

- **HTML vs. CSS vs. JavaScript vs. PHP**:
    - **HTML**: Estrutura e semântica do documento (Esqueleto).
    - **CSS**: Apresentação visual, estilos e layout (Decoração).
    - **JavaScript**: Comportamento, dinâmica e manipulação da interface (Sistema Nervoso / Interatividade).
    - **PHP**: Regras de negócio, processamento no servidor e acesso a banco de dados (Cérebro do Servidor).
- **`box-sizing: content-box` vs. `border-box`**:
    - `content-box`: As propriedades `width` e `height` definem **apenas** a área de conteúdo; bordas e preenchimentos são somados por fora.
    - `border-box`: As propriedades `width` e `height` definem o tamanho **total** da caixa visual, absorvendo o `padding` e a `border` internamente.
- **Tipos de Posicionamento CSS**:
    - `relative`: Move-se mantendo o espaço do seu lugar original reservado na página.
    - `absolute`: Sai do fluxo normal e posiciona-se em relação ao ancestral pai posicionado mais próximo.
    - `fixed`: Sai do fluxo e cola-se na janela do navegador (_viewport_), imune à rolagem da tela.
    - `sticky`: Flutua no fluxo normal até atingir a margem estipulada no topo/fundo, passando a agir como fixo.
- **`var` vs. `let` vs. `const` (JavaScript)**:
    - `var`: Possui escopo global/funcional e permite redeclarações (obsoleto).
    - `let`: Possui escopo de bloco e permite reatribuição de valor.
    - `const`: Possui escopo de bloco e impede qualquer reatribuição de valor.
- **`textContent` vs. `innerHTML` (Manipulação DOM)**:
    - `textContent`: Trata a entrada estritamente como texto puro, escapando qualquer tag.
    - `innerHTML`: Interpreta e insere código HTML, renderizando novas marcas dentro da árvore.
- **GET vs. POST (Métodos HTTP)**:
    - `GET`: Solicita e recupera dados. Anexa todos os parâmetros de forma visível na URL.
    - `POST`: Envia novos dados embutidos de forma oculta no corpo (_body_) da requisição.
- **Sessões (`$_SESSION`) vs. Cookies (`$_COOKIE`)**:
    - `$_SESSION`: Guardada no servidor. Mais segura para controlar autenticação e dados sensíveis.
    - `$_COOKIE`: Gravado no navegador do cliente. Vulnerável a edições ou exclusões diretas pelo usuário.
- **Camadas da Arquitetura MVC**:
    - **Model**: Regras de negócio, SQL e tabelas do banco de dados.
    - **View**: Páginas e componentes de interface visual exibidos ao usuário.
    - **Controller**: Camada intermediária que processa as requisições e coordena o fluxo entre Model e View.

---

## Pontos importantes para prova

- **Hierarquia e Regra de Especificidade do CSS**:
    - A especificidade determina qual regra de estilo ganha prioridade. A ordem de peso decrescente é: Estilo Inline > Seletor de ID (`#`) > Seletor de Classe (`.`) / Atributo > Seletor de Tag.
    - A instrução `!important` anula os cálculos habituais de especificidade e cascata.
- **Validação de Formulários HTML5**:
    - A validação nativa ocorre diretamente no cliente através de atributos na marca `<input>` (como `required`, `type="email"`, `pattern="{5}"`).
    - _Atenção em prova_: A validação no cliente **não substitui** a validação no lado do servidor, pois pode ser desabilitada ou burilada no navegador pelo usuário.
- **Atributos Obrigatórios de Acessibilidade**:
    - Imagens (`<img>`) necessitam do atributo `alt` contendo a descrição funcional ou texto alternativo.
    - Formulários exigem a correspondência exata entre o atributo `for` da tag `<label>` e o atributo `id` da tag `<input>`.
    - Tabelas exigem o atributo `scope="col"` ou `scope="row"` na marca `<th>` para orientação dos leitores de tela.
- **Posicionamento e Camadas `z-index`**:
    - A propriedade `z-index` ajusta a sobreposição vertical dos elementos em tela, mas só surte efeito em elementos que possuem a propriedade `position` declarada explicitamente como `relative`, `absolute`, `fixed` ou `sticky`.
- **Eventos da Janela e do Documento em JavaScript**:
    - `DOMContentLoaded`: Disparado no instante em que a estrutura da árvore HTML é completamente carregada e analisada, sem aguardar o carregamento de imagens ou CSS externo.
    - `load`: Disparado apenas quando todo o documento HTML, arquivos CSS, imagens e quadros adicionais foram integralmente carregados.
- **Códigos de Status HTTP Frequentes em APIs REST**:
    - `200 OK`: Requisição de consulta ou atualização realizada com sucesso.
    - `201 Created`: Novo recurso criado com êxito na base de dados.
    - `204 No Content`: Requisição bem-sucedida (geralmente exclusão), mas sem corpo de retorno.
    - `400 Bad Request`: Requisição malformada ou falha na validação de parâmetros de entrada.
    - `401 Unauthorized`: Ausência de autenticação do usuário.
    - `403 Forbidden`: Usuário autenticado, mas sem permissão de acesso ao recurso.
    - `404 Not Found`: Recurso ou rota não encontrada no servidor.
    - `500 Internal Server Error`: Falha genérica ou erro não tratado na execução do código do servidor.
- **Boas Práticas de Rotas RESTful**:
    - Endpoints devem utilizar obrigatoriamente **substantivos no plural** para indicar coleções de recursos (ex: `GET /api/v1/livros`), evitando expressar verbos ou ações diretas na URL (ex: evitar `/api/getLivros`).

---

## Revisão rápida

- **HTML5**: Marcação semântica e esqueleto visual (`<html>`, `<head>`, `<body>`, `<article>`, `<form>`, `<table>`).
- **CSS3**: Estilização gráfica, seletores (`tag`, `.classe`, `#id`), regra de cascata e especificidade.
- **Box Model**: Estruturação de caixas retangulares compostas por `Content + Padding + Border + Margin`.
- **`border-box`**: Configuração que força a largura declarada a absorver `padding` e `border`.
- **Posicionamento**: `static` (padrão no fluxo), `relative` (deslocamento com espaço reservado), `absolute` (fora do fluxo em relação ao pai posicionado), `fixed` (preso na viewport), `sticky` (fixação ao rolar).
- **Flexbox**: Sistema de layout unidimensional orientado a alinhamentos com `display: flex`.
- **Design Responsivo**: Adaptação para múltiplos dispositivos usando `@media` e abordagem _Mobile-First_.
- **JavaScript**: Linguagem dinâmica client-side para lógica e manipulação interativa da árvore do DOM.
- **Variáveis JS**: `const` para valores imutáveis de bloco; `let` para valores mutáveis de bloco.
- **DOM**: Estrutura em árvore de nós acessada principalmente via `document.querySelector()`.
- **Assincronia JS**: `async/await` com `fetch()` para consumo de APIs remotas sem travar a interface.
- **PHP**: Linguagem server-side executada no servidor web Apache/XAMPP.
- **Estados PHP**: Sessões (`$_SESSION`) salvas no servidor; Cookies (`$_COOKIE`) salvos no cliente.
- **MySQL + CRUD**: Persistência relacional acionada no PHP via comandos SQL (`INSERT`, `SELECT`, `UPDATE`, `DELETE`).
- **Arquitetura MVC**: Divisão de responsabilidades entre **Model** (dados), **View** (interface) e **Controller** (mediação).
- **API REST**: Comunicação client-server padronizada por verbos HTTP (`GET`, `POST`, `PUT`, `DELETE`) trafegando payloads estruturados em **JSON**.

