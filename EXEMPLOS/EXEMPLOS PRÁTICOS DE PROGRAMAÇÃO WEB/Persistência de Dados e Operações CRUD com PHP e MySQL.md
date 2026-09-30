
**Problema:**  
Conectar o PHP a um banco de dados MySQL para cadastrar novos livros na tabela `tbl_livro` (operação _Create_) e consultar e exibir a lista dos livros gravados (operação _Read_).

**Conceito utilizado:**  
Conexão com MySQL via extensão `mysqli` (ou PDO), execução de comandos SQL (`INSERT INTO`, `SELECT *`) e varredura de dados com `mysqli_fetch_assoc`.

**Solução:**

1. crie o script de conexão `conexaoMYSQL.php` especificando o servidor, usuário, senha e nome da base de dados.
2. crie as funções para executar o comando `INSERT` e a consulta `SELECT`.
3. Percorra o conjunto de resultados retornado pela consulta SQL utilizando um laço de repetição `while` com `mysqli_fetch_assoc()`.

```
<!-- Arquivo: conexaoMYSQL.php -->
<?php
function conexaoMysql() {
    $server   = "localhost";
    $user     = "root";
    $password = "";
    $database = "db_livraria_cogna";

    // Abre a conexão com o banco de dados MySQL
    if ($conexao = mysqli_connect($server, $user, $password, $database)) {
        return $conexao;
    } else {
        echo("ERRO: Não foi possível conectar ao Banco de Dados.");
        return false;
    }
}
?>
```

```
<!-- Arquivo: livros.php (Operações de Inserção e Listagem) -->
<?php
require_once('conexaoMYSQL.php');

// 1. Função para INSERIR um novo registro (Create)
function inserir($arrayLivro) {
    $sql = "INSERT INTO tbl_livro (title, subtitle, isbn, price, image)
            VALUES (
                '". $arrayLivro['title'] ."',
                '". $arrayLivro['subtitle'] ."',
                '". $arrayLivro['isbn'] ."',
                '". $arrayLivro['price'] ."',
                '". $arrayLivro['image'] ."'
            )";

    $conexao = conexaoMysql();
    // Executa o comando SQL de inserção na base de dados
    if (mysqli_query($conexao, $sql)) {
        return true;
    } else {
        return false;
    }
}

// 2. Função para LISTAR os registros (Read)
function listar() {
    $sql = "SELECT * FROM tbl_livro";
    $conexao = conexaoMysql();
    // Executa a consulta e retorna o ponteiro de dados
    $rsLivros = mysqli_query($conexao, $sql);
    return $rsLivros;
}

// --- TESTANDO AS OPERAÇÕES NO SERVIDOR ---

// Teste de Inserção (Create)
$novoLivro = array(
    "title"    => "Livro de PHP 8",
    "subtitle" => "Desenvolvimento Server-Side",
    "isbn"     => "97812345678",
    "price"    => "59.90",
    "image"    => "capa_php.jpg"
);

if (inserir($novoLivro)) {
    echo "O livro foi inserido com sucesso!<br><br>";
}

// Teste de Leitura (Read)
$dadosLivros = listar();
while ($livro = mysqli_fetch_assoc($dadosLivros)) {
    echo "Livro: " . $livro['title'] . " - Preço: R$ " . $livro['price'] . "<br>";
}
?>
```

**Resultado:**  
O comando insere um novo registro no banco `db_livraria_cogna` e a mensagem _"O livro foi inserido com sucesso!"_ é impressa no navegador. Logo abaixo, o laço de repetição percorre a tabela do MySQL e imprime todos os livros cadastrados.

**Por que essa solução funciona:**  
`mysqli_connect()` estabelece um canal ativo com o serviço do MySQL rodando no servidor. A função `mysqli_query()` envia o texto SQL diretamente para a base de dados. Ao ler os dados, a função `mysqli_fetch_assoc()` converte cada registro do banco em um array associativo PHP onde os nomes das colunas viram as chaves do array (`$livro['title']`).

**O que preciso aprender com esse exemplo:**

- `mysqli_connect` exige 4 parâmetros: servidor, usuário, senha e nome do banco de dados.
- `mysqli_query($conexao, $sql)` executa instruções SQL no banco.
- Para ler os resultados de um `SELECT`, utiliza-se a estrutura `while($linha = mysqli_fetch_assoc($resultado))`.
