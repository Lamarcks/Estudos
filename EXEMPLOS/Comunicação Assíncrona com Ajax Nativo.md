**Problema:** Atualizar as informações de uma determinada área da página de forma contínua e assíncrona ao carregar um arquivo externo (`dados.txt`) sem precisar forçar o navegador do usuário a recarregar toda a interface de apresentação.

**Conceito utilizado:** Requisições lógicas assíncronas do **Ajax** (_Asynchronous JavaScript and XML_).

**Solução:** Utilizar o componente nativo do navegador `XMLHttpRequest` para capturar os dados do servidor em segundo plano e injetá-los no documento de forma programática.

```
function carregarDados() {
  const xhttp = new XMLHttpRequest(); // Instancia o componente lúdico

  xhttp.onload = function() {
    // Função disparada assim que o retorno assíncrono ocorrer
    document.getElementById("resultado").innerHTML = this.responseText;
  };

  xhttp.open("GET", "dados.txt", true); // Abre conexão lógica de rede
  xhttp.send(); // Envia a solicitação
}
```

- **`new XMLHttpRequest()`:** Instancia o objeto responsável por disparar requisições em paralelo.
- **`xhttp.onload`:** Evento interceptador que escuta o retorno físico de sucesso do servidor.
- **`document.getElementById("resultado").innerHTML`:** Insere de forma dinâmica os dados recebidos no container sem interferir no restante do layout da interface do usuário.
- **`xhttp.open("GET", ..., true)`:** Define o endpoint lúdico que será buscado e o método de envio (GET de forma assíncrona).

**Resultado:** Ao chamar a função em qualquer tela do site, a região correspondente ao ID `resultado` se atualiza com o conteúdo do arquivo dinamicamente sem perdas de estado ou refreshes visíveis.

**Por que essa solução funciona:** O navegador abre uma thread em paralelo em segundo plano que gerencia a comunicação HTTP e devolve a resposta direto para que o script interaja com os nós lógicos do DOM da página.

**O que preciso aprender com esse exemplo:** Ajax é um conjunto de técnicas estruturadas de reatividade e de requisições de dados paralelas de rede em segundo plano.