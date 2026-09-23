**Problema:** Criar um processo leve de rede de retaguarda (_back-end_) para gerenciar requisições e respostas sem carregar pacotes ou frameworks pesados.

**Conceito utilizado:** Arquitetura assíncrona orientada a eventos (_event-driven_) e o módulo nativo HTTP do **Node.js**.

**Solução:** Importar o componente de rede nativo do Node.js, configurar um callback assíncrono para tratar requisições lógicas de rede e colocá-lo para escutar conexões locais na porta `3000`.

```
const http = require('http'); // Importa o módulo interno nativo

const server = http.createServer((req, res) => {
  // Callback disparado a cada requisição externa recebida
  res.writeHead(200, {'Content-Type': 'text/plain'});
  res.end('Servidor Node.js em funcionamento!');
});

server.listen(3000, () => {
  console.log('Servidor rodando em http://localhost:3000');
});
```

- **`require('http')`:** Importação de biblioteca nativa de rede do Node.
- **`http.createServer`:** Define o comportamento básico de resposta quando chamadas externas ocorrerem.
- **`res.writeHead(200, ...)`:** Configura metadados de cabeçalho HTTP indicando sucesso lógico.
- **`res.end()`:** Conclui a transmissão e envia a resposta de texto de forma não-bloqueante.
- **`server.listen(3000)`:** Vincula o processo físico para monitorar portas locais específicas.

**Resultado:** O terminal exibe o log de inicialização e a máquina expõe uma API RESTful de texto na porta 3000 de forma altamente performática.

**Por que essa solução funciona:** A engine V8 do Node monitora e delega chamadas de rede à thread de eventos do sistema (_Event Loop_) sem travar o processamento ou consumo de recursos principais.

**O que preciso aprender com esse exemplo:** O Node.js permite unificar o ecossistema com o uso de JavaScript do lado servidor de maneira assíncrona, sendo ideal para APIs leves e serviços em tempo real.