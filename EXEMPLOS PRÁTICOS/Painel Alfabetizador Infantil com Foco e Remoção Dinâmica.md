**Problema:** Em um protótipo didático para alfabetização infantil, ao clicar sobre uma letra de uma tabela de opções (letras de A à F), a letra correspondente deve desaparecer da tabela de escolhas. De forma síncrona, a aplicação deve mudar a cor de fundo do campo de texto referente àquela letra e dar o foco de digitação automática nele para que a criança digite a palavra correspondente sem se perder no processo.

**Conceito utilizado:** Eventos do mouse, rastreamento de nós ativos de disparo de eventos (`event.target.id`), mudança de foco (`focus()`), estilos inline dinâmicos e temporizadores de retardo (`setTimeout`) para execução de exclusão no DOM (`event.target.remove()`).

**Solução:** _HTML de estrutura básica:_

```
<table class="table table-bordered" id="table">
    <thead>
        <tr class="table-success text-center">
            <th colspan="6" scope="row">Letras</th>
        </tr>
    </thead>
    <tbody>
        <tr class="text-center">
            <td id="A">A</td>
            <td id="B">B</td>
            <td id="C">C</td>
            <td id="D">D</td>
            <td id="E">E</td>
            <td id="F">F</td>
        </tr>
    </tbody>
</table>
<script src="selecionaletra.js"></script>
```

_JavaScript de lógica (`selecionaletra.js`):_

```
var letraA = document.getElementById('letraA');
var letraB = document.getElementById('letraB');
var letraC = document.getElementById('letraC');
var letraD = document.getElementById('letraD');
var letraE = document.getElementById('letraE');
var letraF = document.getElementById('letraF');
var table = document.getElementById('table');

table.addEventListener("click", function (event) {
    // 1. Identifica e valida qual ID foi clicado e altera seu respectivo estilo e foco
    if (event.target.id == "A") {
        letraA.style.backgroundColor = 'rgb(191, 234, 215)';
        letraA.focus();
    }
    if (event.target.id == "B") {
        letraB.style.backgroundColor = 'rgb(191, 234, 215)';
        letraB.focus();
    }
    if (event.target.id == "C") {
        letraC.style.backgroundColor = 'rgb(191, 234, 215)';
        letraC.focus();
    }
    if (event.target.id == "D") {
        letraD.style.backgroundColor = 'rgb(191, 234, 215)';
        letraD.focus();
    }
    if (event.target.id == "E") {
        letraE.style.backgroundColor = 'rgb(191, 234, 215)';
        letraE.focus();
    }
    if (event.target.id == "F") {
        letraF.style.backgroundColor = 'rgb(191, 234, 215)';
        letraF.focus();
    }

    // 2. Remove o caractere de opção clicado do painel inferior após 500 milissegundos
    setTimeout(function () {
        event.target.remove();
    }, 500);
});
```

**Resultado:** Se a criança clicar sobre a célula "D", o campo de input associado a "D" assume a cor verde-água e o cursor de digitação começa a piscar nele. Meio segundo depois, a opção visual "D" some da tabela inferior de seleções.

**Por que essa solução funciona:** O evento de clique registrado na tabela pai é herdado. O interpretador JavaScript identifica exatamente qual elemento originou a ação por meio do ID dinâmico exposto por `event.target.id`. A chamada de `focus()` reposiciona o cursor do sistema operacional naquele nó. O temporizador `setTimeout` atrasa o método `event.target.remove()` para garantir que o usuário veja visualmente a confirmação do clique antes do desaparecimento do elemento da tela.

**O que preciso aprender com esse exemplo:** Como trabalhar com delegação de eventos (ouvir eventos no pai para manipular os filhos), gerenciar o foco de elementos do formulário e programar atrasos no encadeamento visual por meio de `setTimeout`.