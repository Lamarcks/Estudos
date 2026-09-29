**Problema:** Criar uma rotina simples para consultar uma API pública de teste e obter o título de um post específico em formato de texto estruturado sem recarregar a visualização da tela atual do navegador.

**Conceito utilizado:** Requisições assíncronas de rede com `XMLHttpRequest`, tratamento de respostas assíncronas por gatilho de carga (`onload`), validação de códigos de status de requisição HTTP (`status === 200`) e decodificação textual JSON (`JSON.parse`).

**Solução:** _HTML de estrutura básica:_

```
<button type="button" onclick="Conexao()">Testar</button>
<script src="exercicio5.js"></script>
```

_JavaScript de lógica de requisição (`exercicio5.js`):_

```
function Conexao() {
    // 1. Instancia o objeto responsável por gerenciar a comunicação de rede
    const xhr = new XMLHttpRequest();

    // 2. Prepara os parâmetros da transação: tipo GET, url de post público e modo assíncrono (true)
    xhr.open("GET", "https://jsonplaceholder.typicode.com/posts/1", true);

    // 3. Registra a função de retorno a ser disparada quando os dados chegarem
    xhr.onload = function () {
        // Valida se o status de retorno HTTP é sínclito com sucesso (200 OK)
        if (xhr.status === 200) {
            // Decodifica a string JSON de retorno em um dicionário utilizável no JS
            const response = JSON.parse(xhr.responseText);
            console.log("Título do post:", response.title); // Exibe o valor do atributo 'title'
        } else {
            console.log("Ocorreu um erro durante a solicitação.");
        }
    };

    // 4. Executa de fato a saída e envio do sinal de rede
    xhr.send();
}
```

**Resultado:** Ao clicar no botão "Testar", o script dispara a requisição e exibe no console do desenvolvedor o texto decodificado (Ex: "Título do post: [Texto do Post]") de forma instantânea sem interferir em outras lógicas em execução na página.

**Por que essa solução funciona:** A classe `XMLHttpRequest` atua em uma thread de processamento paralela à visualização do DOM. O manipulador de evento `onload` monitora a chegada e integridade do pacote de rede. O uso de `JSON.parse` converte o formato de texto plano retornado em um objeto literal JS dinâmico.

**O que preciso aprender com esse exemplo:** Fundamentos da arquitetura cliente-servidor, manipulação de tráfego de dados estruturados em rede e tratamento de códigos de status de comunicação HTTP.