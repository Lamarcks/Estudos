**Problema:** Solicitar interativamente a idade do usuário e alterar dinamicamente o visual da página com base na resposta: se for menor de 18 anos, pintar a tela de vermelho escuro ("Darkred") com fonte clara; se for maior de idade, pintar de azul-esverdeado claro ("Aquamarine").

**Conceito utilizado:** Leitura de caixas de entrada de diálogo (`prompt`), conversão para tipo de dado numérico (`parseInt`), manipulação de estilo do corpo do documento direto pelo seletor root (`document.body`).

**Solução:** _HTML de estrutura básica:_

```
<div id="mensagem"></div>
<script src="exercicio1.js"></script>
```

_JavaScript de lógica (`exercicio1.js`):_

```
let idade = parseInt(prompt('Informe sua idade: '));
let body = document.body; // Referencia diretamente a tag <body> do HTML
let msg = document.getElementById('mensagem');

if (idade <= 18) {
    body.style.background = 'Darkred'; // Altera a cor de fundo do documento
    msg.style.fontSize = 'xx-large';
    msg.style.color = 'Cornsilk';
    msg.innerHTML = 'Você é menor de idade';
} else {
    body.style.background = 'Aquamarine';
    msg.style.fontSize = 'xx-large';
    msg.style.color = 'CadeBlue';
    msg.innerHTML = 'Você é maior de idade';
}
```

**Resultado:** Se o usuário digitar "15", o fundo do browser se torna vermelho escuro exibindo o texto de menoridade. Se digitar "21", o fundo se torna azul-claro com a mensagem de maioridade.

**Por que essa solução funciona:** `parseInt` força a conversão do input de texto em um valor de tipo numérico comparável. O JavaScript acessa diretamente as propriedades do elemento raiz do documento (`document.body`) alterando as variáveis de folha de estilo em tempo real.

**O que preciso aprender com esse exemplo:** Como interagir diretamente com o corpo global do documento (`document.body`) e modificar suas diretrizes de design baseado em decisões lógicas de código no lado do cliente.