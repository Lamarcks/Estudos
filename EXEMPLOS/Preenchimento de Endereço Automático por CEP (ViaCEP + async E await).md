**Problema:** Em um formulário de cadastro de endereço de e-commerce, o usuário digita o número do seu CEP. Ao clicar fora ou sair do campo, o sistema deve validar localmente por meio de expressões regulares (RegEx) se o CEP é válido e, em caso positivo, realizar uma requisição assíncrona ao serviço ViaCEP para preencher os campos de rua, bairro, cidade e estado automaticamente.

**Conceito utilizado:** Promessas assíncronas por blocos estruturados (`async/await`), consulta à API via Fetch API (`fetch`), expressões regulares de validação de padrões textuais (RegEx com `test()`), tratamento de erros por propriedades (`hasOwnProperty`) e eventos de saída de foco (`focusout`).

**Solução:** _HTML do Formulário de Endereço:_

```
<form>
    <h2>Cadastro de Endereço</h2>
    <div>
        <label>CEP</label>
        <input type="text" id="cep">
    </div>
    <div>
        <label>Rua</label>
        <input type="text" id="rua">
    </div>
    <div>
        <label>Bairro</label>
        <input type="text" id="bairro">
    </div>
    <div>
        <label>Cidade</label>
        <input type="text" id="cidade">
    </div>
    <div>
        <label>Estado</label>
        <input type="text" id="estado">
    </div>
</form>
<script src="viacep.js"></script>
```

_JavaScript de lógica assíncrona (`viacep.js`):_

```
'use strict'; // Ativa as validações de ambiente de código restrito do JS

// Limpa qualquer dado residual do formulário
const limparFormulario = () => {
    document.getElementById('rua').value = '';
    document.getElementById('bairro').value = '';
    document.getElementById('cidade').value = '';
    document.getElementById('estado').value = '';
}

// Insere os atributos retornados nos respectivos inputs do HTML
const preencherFormulario = (endereco) => {
    document.getElementById('rua').value = endereco.logradouro;
    document.getElementById('bairro').value = endereco.bairro;
    document.getElementById('cidade').value = endereco.localidade;
    document.getElementById('estado').value = endereco.uf;
}

// Regex: Valida se a string possui apenas caracteres numéricos de 0 a 9 do início ao fim
const eNumero = (numero) => /^+$/.test(numero);

// Valida se o CEP tem exatamente 8 caracteres de comprimento numérico
const cepValido = (cep) => cep.length === 8 && eNumero(cep);

// Processa a requisição assíncrona para a API ViaCEP
const pesquisarCep = async () => {
    limparFormulario();
    const cep = document.getElementById('cep');
    const url = `https://viacep.com.br/ws/${cep.value}/json/`;

    if (cepValido(cep.value)) {
        // Aguarda (await) o retorno físico da API externa de dados
        const dados = await fetch(url);
        const address = await dados.json(); // Aguarda a decodificação do pacote JSON

        // Verifica se a API retornou erro lógico interno de CEP inexistente
        if (address.hasOwnProperty('erro')) {
            alert('CEP não encontrado!');
        } else {
            preencherFormulario(address); // Realiza o auto-preenchimento
        }
    } else {
        alert('CEP incorreto!');
    }
}

// Ativa a lógica quando o usuário remove o cursor/foco do input de CEP
document.getElementById('cep').addEventListener('focusout', pesquisarCep);
```

**Resultado:** O usuário entra com o CEP "86050000" e sai do campo. Os dados de rua, bairro, cidade e estado aparecem de forma instantânea e mágica em suas respectivas caixas de entrada.

**Por que essa solução funciona:** O gatilho `focusout` dispara o processamento no momento ideal. A função assíncrona identificada por `async` utiliza a palavra-chave `await` para instruir o interpretador JavaScript a congelar momentaneamente a sequência lógica daquela tarefa até que a requisição em rede do `fetch` retorne, mantendo a responsividade do restante da página sem travar o browser.

**O que preciso aprender com esse exemplo:** Como usar a Fetch API moderna de forma assíncrona estruturada por blocos simplificados de `async/await`, validar formatos usando expressões regulares (RegEx) e mapear objetos de retorno estruturados em JSON.
