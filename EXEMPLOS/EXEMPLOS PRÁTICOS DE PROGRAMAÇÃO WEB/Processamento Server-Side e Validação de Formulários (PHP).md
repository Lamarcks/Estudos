
**Problema:**  
Receber quatro notas enviadas por um formulário HTML, verificar se todos os campos foram devidamente preenchidos, validar se os valores digitados são numéricos e calcular a média escolar do aluno no lado do servidor.

**Conceito utilizado:**  
Variável superglobal `$_POST`, diretiva de inclusão de arquivos (`require_once`), funções de validação de tipo (`is_numeric`) e estrutura condicional `if/else` no PHP.

**Solução:**

1. Crie o arquivo de lógica `media.php` contendo a função responsável pela validação e pelo cálculo matemático da média.
2. Crie o arquivo de interface `index.php` contendo o formulário HTML com o método `post` e importe a função de cálculo usando `require_once`.
3. Verifique se o formulário foi submetido consultando a presença do botão de envio com `isset($_POST['btncalc'])`.

```
<!-- Arquivo: media.php (Regras de Negócio no Servidor) -->
<?php
function calcularMedia($nota1, $nota2, $nota3, $nota4) {
    // 1. Tratamento para campos vazios
    if ($nota1 == "" || $nota2 == "" || $nota3 == "" || $nota4 == "") {
        return false;
    }

    // 2. Validação se as entradas são números válidos
    if (is_numeric($nota1) && is_numeric($nota2) && is_numeric($nota3) && is_numeric($nota4)) {
        $media = ($nota1 + $nota2 + $nota3 + $nota4) / 4;
        return $media;
    } else {
        return false;
    }
}
?>
```

```
<!-- Arquivo: index.php (Interface e Processamento de Envio) -->
<?php
require_once("media.php");

$media = null;
// Valida se a requisição foi disparada pelo botão do formulário
if (isset($_POST['btncalc'])) {
    $nota1 = $_POST['txtn1'];
    $nota2 = $_POST['txtn2'];
    $nota3 = $_POST['txtn3'];
    $nota4 = $_POST['txtn4'];

    // Executa a função de cálculo contida no arquivo importado
    $media = calcularMedia($nota1, $nota2, $nota3, $nota4);
}
?>

<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <title>Cálculo de Médias</title>
</head>
<body>
    <form name="frmMedia" method="post" action="index.php">
        <label>Nota 1:</label> <input type="text" name="txtn1"><br>
        <label>Nota 2:</label> <input type="text" name="txtn2"><br>
        <label>Nota 3:</label> <input type="text" name="txtn3"><br>
        <label>Nota 4:</label> <input type="text" name="txtn4"><br>
        <input type="submit" name="btncalc" value="Calcular">
    </form>

    <?php if ($media !== null && $media !== false): ?>
        <h2>A média é: <?php echo $media; ?></h2>
    <?php elseif ($media === false): ?>
        <h2 style="color:red;">Por favor, digite valores numéricos válidos em todos os campos!</h2>
    <?php endif; ?>
</body>
</html>
```

**Resultado:**  
Se o usuário digitar as notas `10`, `9`, `8` e `10` e clicar em "Calcular", o formulário dispara os dados para o servidor PHP via protocolo `POST`, que processa a equação e imprime na tela: **A média é: 9.25**. Se algum campo estiver vazio ou contiver letras, a função retorna `false` e exibe uma mensagem de alerta.

**Por que essa solução funciona:**  
O método `POST` envia os valores digitados de maneira embutida no corpo da requisição HTTP. O PHP lê esses valores através do array associativo superglobal `$_POST['nome_do_input']`. A função `is_numeric()` garante a segurança dos dados antes de executar operações aritméticas no servidor.

**O que preciso aprender com esse exemplo:**

- Para capturar dados do formulário no PHP, o atributo `name` do `<input>` HTML é obrigatório, pois servirá como chave do array `$_POST['name']`.
- O comando `require_once()` carrega dependências de outros arquivos PHP sem duplicar a inclusão.
- Sempre valide os dados no servidor (`is_numeric`), pois a validação do cliente pode ser desativada pelo usuário.
