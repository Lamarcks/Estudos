**Problema:** Criar um protótipo leve de Chatbot em uma página web em que o usuário digita uma pergunta em uma caixa de texto e ela é encaminhada assincronamente por meio de requisições do tipo POST autenticadas contendo parâmetros estruturados ao modelo de IA `text-davinci-002` da OpenAI, imprimindo a resposta textualmente na tela de forma interativa sem recarregar o browser.

**Conceito utilizado:** Chamada à API via método POST estruturado com Fetch API, passagem de cabeçalhos HTTP customizados (`Authorization: Bearer`), transformação de dados para formato JSON textual (`JSON.stringify`), e encadeamento sequencial e tratamento de erros de promises (`then`/`catch`).

**Solução:** _HTML de estrutura básica:_

```
<form id="formQuestion">
    <h1>Pergunte ao chatGPT</h1>
    <label>Formule a pergunta</label><br>
    <input type="text" id="question"><br><br>
    <button type="button" onclick="consultaChat()">Perguntar</button><br><br>
    <div id="pergunta"></div><br><br>
    <div id="resposta"></div>
</form>
<script src="chatgpt.js"></script>
```

_JavaScript de lógica de integração com OpenAI (`chatgpt.js`):_

```
// Substitua o sk-v3Q... pela sua chave real de acesso à API obtida do console OpenAI
const CHATGPT_KEY = "sk-v3QZgqyU6y................8ihnWeudyRK";

const consultaChat = async () => {
    let question = document.getElementById('question').value;
    document.getElementById('pergunta').innerHTML = question; // Exibe o que foi perguntado na tela

    // Efetua a requisição assíncrona POST enviando dados e chaves
    await fetch("https://api.openai.com/v1/completions", {
        method: "POST",
        headers: {
            "Accept": "application/json",
            "Content-Type": "application/json",
            "Authorization": "Bearer " + CHATGPT_KEY, // Cabeçalho essencial de Token de validação
        },
        body: JSON.stringify({
            model: "text-davinci-002",
            prompt: question,
            max_tokens: 1024,
            temperature: 0.5 // Define a consistência ou grau criativo das respostas
        })
    })
    // Converte e trata o retorno dos dados da promise
    .then((response) => response.json())
    .then((data) => {
        // Insere o texto gerado na div de resposta mapeada
        document.getElementById('resposta').innerHTML = data.choices.text;
    })
    .catch(() => {
        document.getElementById('resposta').innerHTML = "reformule a pergunta"; // Lida com falhas físicas de rede
    });
}
```

**Resultado:** O usuário entra com a frase "O que é javascript?" e clica em "Perguntar". A aplicação exibe a resposta textual formatada gerada pela inteligência artificial de forma limpa inline no centro do formulário.

**Por que essa solução funciona:** O método `fetch` envia uma requisição complexa do tipo POST parametrizando os cabeçalhos HTTP necessários para autenticar no gateway da OpenAI. O corpo do objeto é serializado em cadeia JSON por `JSON.stringify`. As promises encadeadas por `.then` capturam e convertem os dados no momento exato em que são transmitidos na resposta final, enquanto o `.catch` assegura que problemas físicos de conexão ou chaves inválidas não quebrem o código, dando retorno controlado ao usuário.

**O que preciso aprender com esse exemplo:** Como estruturar requisições complexas do tipo POST com dados serializados, gerenciar tokens e chaves privadas de segurança através de cabeçalhos HTTP de autorização e blindar fluxos assíncronos contra erros usando `.catch`.