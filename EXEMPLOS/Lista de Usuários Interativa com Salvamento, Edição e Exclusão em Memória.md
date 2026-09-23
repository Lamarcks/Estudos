**Problema:** Criar uma aplicação que simule um gerenciador de banco de dados para controlar cadastros de usuários. O sistema deve permitir:

1. Digitar o nome e salvar em uma lista na memória do navegador.
2. Gerar dinamicamente linhas na tabela HTML contendo o nome e dois botões de ação ("Editar" e "Excluir").
3. Clicar em "Excluir" e apagar o registro físico e lógico.
4. Clicar em "Editar" e recuperar o dado para alteração na caixa de texto original.

**Conceito utilizado:** Arrays estruturais, inclusão com `push()`, remoção e manipulação precisa de posições em vetores com `splice()`, regeneração dinâmica do DOM (`innerHTML`), manipulação da árvore de elementos pais e filhos para captura do índice numérico da linha da tabela (`rowIndex`).

**Solução:** _HTML de estrutura básica:_

```
<div>
    <label id="nome">Nome:</label>
    <input id="nomeUser" type="text">
    <button type="button" onclick="salvarUser()">Salvar</button>
</div>
<div>
    <table id="tabela">
        <tr>
            <th>Nome Usuario</th>
            <th>Ações</th>
        </tr>
    </table>
</div>
<script src="controller.js"></script>
```

_JavaScript de controle (`controller.js`):_

```
var dadosLista = []; // Banco de dados local na memória ativa do script

// 1. Função que coleta o valor inserido e salva no array
function salvarUser() {
    let nomeUser = document.getElementById("nomeUser").value;

    if (nomeUser) {
        dadosLista.push(nomeUser); // Insere no final do vetor
        criaLista(); // Força a atualização da tabela no HTML
        console.log(dadosLista);
        document.getElementById("nomeUser").value = ""; // Limpa a caixa de texto
    } else {
        alert("Usuário favor preencher o campo nome");
    }
}

// 2. Função que varre o array e renderiza as linhas no DOM
function criaLista() {
    // Redefine o cabeçalho original da tabela limpando resquícios de repetição
    let tabela = document.getElementById("tabela").innerHTML = "<tr><th>Nome Usuario</th><th>Ações</th></tr>";

    for (let i = 0; i <= (dadosLista.length - 1); i++) {
        // Concatena as novas linhas passando o índice rowIndex dinamicamente para as funções de botão
        tabela += "<tr><td>" + dadosLista[i] + "</td><td><button class='btn btn-success' onclick='editar(this.parentNode.parentNode.rowIndex)'>Editar</button> <button class='btn btn-danger' onclick='excluir(this.parentNode.parentNode.rowIndex)'>Excluir</button></td></tr>";
        document.getElementById("tabela").innerHTML = tabela;
    }
}

// 3. Função que exclui o usuário da memória e da tela
function excluir(i) {
    dadosLista.splice((i - 1), 1); // Remove 1 item correspondente na memória
    document.getElementById("tabela").deleteRow(i); // Exclui a linha visualmente do documento
    console.log(dadosLista);
}

// 4. Função que move o usuário de volta para edição
function editar(i) {
    // Joga o dado selecionado de volta na caixa de input do usuário
    document.getElementById("nomeUser").value = dadosLista[(i - 1)];
    dadosLista.splice((i - 1), 1); // Retira da memória enquanto está sendo editado
    console.log(dadosLista);
}
```

**Resultado:** Ao digitar nomes e clicar em salvar, os dados acumulam de forma organizada em uma tabela logo abaixo. Ao clicar nos botões que acompanham as linhas, o usuário exclui o registro dinamicamente ou re-edita no input.

**Por que essa solução funciona:** O array global `dadosLista` armazena e mantém a persistência dos estados dos dados. A chamada `this.parentNode.parentNode.rowIndex` navega do botão (`this`), sobe para a célula `<td>` (`parentNode`), sobe para a linha `<tr>` (`parentNode`) e obtém sua coordenada matemática de posição na tabela. O método `splice(index, count)` permite injetar e retirar elementos de locais arbitrários do array de dados.

**O que preciso aprender com esse exemplo:** Como orquestrar lógicas CRUD básicas de forma cliente-side utilizando o ciclo completo de gerenciamento de coleções locais em arrays vinculados a elementos estruturais do DOM.