**Problema:** Em um fluxo de cadastro de e-commerce, é preciso validar se o usuário preencheu o campo de nome. Se não preencher, o sistema deve exibir uma mensagem vermelha de erro inline no formulário; se preencher, deve limpar o erro e cumprimentá-lo.

**Conceito utilizado:** Manipulação direta do DOM, seleção de elementos por ID (`document.getElementById`), leitura do tamanho de uma string (`value.length`), manipulação dinâmica de estilo CSS inline (`style.color`), manipulação de texto de elementos (`textContent`) e registro de escutadores de eventos (`addEventListener`).

**Solução:** _HTML de estrutura:_

```
<div id="cadNome">
    <h1>Validação</h1>
    <input type="text" id="nome">
    <div id="msgerro"></div>
    <button type="button" id="botao">Verificar</button>
</div>
<script src="validanome.js"></script>
```

_JavaScript de lógica (`validanome.js`):_

```
var msg = document.getElementById('msgerro');
var nome = document.getElementById('nome');

const validaNome = () => {
    // Verifica se a quantidade de caracteres do valor do campo é zero
    if (nome.value.length == 0) {
        msg.style.color = 'red'; // Altera a cor do texto do erro para vermelho
        msg.textContent = 'Informe o nome'; // Altera o texto da div de erro
    } else {
        msg.textContent = ''; // Limpa a mensagem de erro
        alert('Olá ' + nome.value); // Dispara um pop-up de boas-vindas
    }
}

// Vincula a função ao botão ao escutar o evento de clique
document.getElementById('botao').addEventListener('click', validaNome);
```

**Resultado:** Se o usuário clicar no botão com o campo vazio, o texto "Informe o nome" aparece instantaneamente em vermelho sob o formulário. Caso digite um nome e clique, o erro é limpo e um alerta de boas-vindas é exibido (Ex: "Olá Leonardo").

**Por que essa solução funciona:** Ao escutar o clique através do `addEventListener('click')`, o JavaScript aciona a função `validaNome`. A propriedade `value.length` lê o número de caracteres digitados na caixa de texto. O desvio condicional (`if`) avalia se o valor é igual a 0 para alternar dinamicamente as classes de renderização visual no navegador.

**O que preciso aprender com esse exemplo:** Como referenciar campos específicos usando IDs únicos, ler valores de inputs em tempo de execução e dar feedback de erros inline usando CSS e alteração de conteúdo com `textContent`.