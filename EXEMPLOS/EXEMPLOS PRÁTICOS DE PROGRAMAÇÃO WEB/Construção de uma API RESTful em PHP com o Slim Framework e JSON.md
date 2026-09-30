
**Problema:**  
Transformar o sistema de cadastro e consulta de livros em uma API RESTful capaz de receber requisições de aplicações externas (como sistemas web ou aplicativos mobile) e responder utilizando dados padronizados no formato JSON com códigos de status HTTP corretos.

**Conceito utilizado:**  
Micro-framework Slim (Slim 4), padrão RESTful, verbos HTTP (`GET` e `POST`), serialização em JSON (`json_encode` e `json_decode`) e tratamento de cabeçalhos CORS.

**Solução:**

1. Instale o Slim Framework via Composer.
2. Crie o arquivo de rotas `index.php` configurando a resposta JSON e definindo os pontos de acesso (_endpoints_) `/livros` para os métodos `GET` e `POST`.
3. No método `GET`, converta o resultado do banco de dados para JSON com `json_encode()` e retorne status `200 OK`.
4. No método `POST`, leia o corpo da mensagem (`body`), converta o JSON enviado com `json_decode()`, grave no banco e retorne status `201 Created`.

```
<!-- Arquivo: index.php (API RESTful com Slim Framework 4) -->
<?php
require __DIR__ . '/vendor/autoload.php';
require __DIR__ . '/model/bd/conexaoMYSQL.php';
require __DIR__ . '/model/livros.php';

use Psr\Http\Message\ResponseInterface as Response;
use Psr\Http\Message\ServerRequestInterface as Request;
use Slim\Factory\AppFactory;

$app = AppFactory::create();

// Configuração de cabeçalhos globais e suporte a CORS
header('Access-Control-Allow-Origin: *');
header('Access-Control-Allow-Methods: GET, POST, PUT, DELETE, OPTIONS');
header('Content-Type: application/json');

// ENDPOINT 1: Listar Livros (Método GET)
$app->get('/livros', function(Request $request, Response $response, $args) {
    // Consulta o banco e retorna uma string em formato JSON
    $dados = listarLivrosJSON();
    $response->getBody()->write($dados);
    return $response->withHeader('Content-Type', 'application/json')->withStatus(200);
});

// ENDPOINT 2: Cadastrar Novo Livro (Método POST)
$app->post('/livros', function(Request $request, Response $response, $args) {
    // Captura a string JSON enviada no corpo da requisição pelo cliente
    $bodyJSON = $request->getBody()->getContents();

    // Converte a string JSON para um array associativo PHP
    $arrayDados = json_decode($bodyJSON, true);

    // Insere os dados no banco usando a função da model
    inserir($arrayDados);

    // Responde com mensagem de sucesso e Código HTTP 201 (Created)
    $response->getBody()->write('{"message": "Item criado com sucesso"}');
    return $response->withHeader('Content-Type', 'application/json')->withStatus(201);
});

$app->run();
?>
```

```
<!-- Função auxiliar no model para formatar a saída em JSON -->
<?php
function listarLivrosJSON() {
    $sql = "SELECT * FROM tbl_livro";
    $conexao = conexaoMysql();
    $rsLivros = mysqli_query($conexao, $sql);

    $arrayLivros = array();
    while ($livro = mysqli_fetch_assoc($rsLivros)) {
        $arrayLivros[] = $livro;
    }

    // Converte o array do PHP em uma string estruturada JSON
    return '{"books": ' . json_encode($arrayLivros) . '}';
}
?>
```

**Resultado:**

- Ao realizar uma requisição `GET` para `http://localhost:8000/livros` utilizando o Postman ou o navegador, o servidor responde com o código **`200 OK`** e a lista completa de livros no corpo da resposta:

```
{
  "books": [
    {
      "id": "1",
      "title": "Livro de PHP 8",
      "subtitle": "Desenvolvimento Server-Side",
      "price": "59.90"
    }
  ]
}
```

- Ao enviar um payload JSON via `POST` para `http://localhost:8000/livros`, a API insere o registro e retorna o status **`201 Created`** com a mensagem `{"message": "Item criado com sucesso"}`.

**Por que essa solução funciona:**  
O Slim Framework intercepta a URL requisitada e direciona o fluxo para a função correspondente baseando-se no verbo HTTP utilizado (`GET` ou `POST`). A função `json_encode()` serializa estruturas do PHP para o formato estruturado texto JSON, enquanto `json_decode(..., true)` faz o caminho inverso, transformando a requisição externa em um array legível pelo PHP.

**O que preciso aprender com esse exemplo:**

- APIs REST usam métodos HTTP para definir ações: `GET` para buscar/listar e `POST` para inserir/criar.
- `json_encode()` transforma arrays do PHP em formato JSON.
- `json_decode($json, true)` converte strings JSON recebidas em arrays associativos do PHP.
- Respostas de API devem sempre incluir o cabeçalho `Content-Type: application/json` e retornar os códigos de status HTTP adequados (`200` para sucesso simples, `201` para recurso criado).