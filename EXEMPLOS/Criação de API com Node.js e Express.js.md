**Problema:** Montar uma estrutura modular e flexível para retornar conjuntos de dados em JSON dinamicamente para consumo de telas de front-end modernas de forma desacoplada.

**Conceito utilizado:** Roteamento ágil com o framework **Express.js** no lado do servidor.

**Solução:** Criar instâncias do Express, configurar interceptação de pacotes JSON (`app.use`) e definir rotas específicas utilizando verbos HTTP nativos.

```
const express = require('express');
const app = express();

app.use(express.json()); // Middleware para interpretar JSON

const produtos = [
  { id: 1, nome: 'Notebook', preco: 3200 },
  { id: 2, nome: 'Teclado', preco: 150 }
];

// Mapeia chamadas lógicas do método GET no endpoint produtos
app.get('/produtos', (req, res) => {
  res.status(200).json(produtos);
});

app.listen(3000, () => {
  console.log('API executando em http://localhost:3000');
});
```

- **`app.use(express.json())`:** Middleware nativo estruturado para tratar e decodificar dados trafegados no formato de dados JSON.
- **`app.get('/produtos', ...)`:** Rota lógica que escuta o verbo GET no endpoint `/produtos`.
- **`res.status(200).json()`:** Responde a requisição definindo o código de status HTTP correspondente e enviando dados estruturados serializados.

**Resultado:** Aplicações front-end desenvolvidas em React, Angular ou Vue podem consumir dados estruturados em JSON vindos do back-end ao chamar a API em `http://localhost:3000/produtos`.

**Por que essa solução funciona:** O Express simplifica o tratamento lúdico de rotas interceptando dados em tempo de execução de forma nativa e segura.

**O que preciso aprender com esse exemplo:** O Express.js funciona como uma camada flexível que acelera a criação de APIs RESTful estruturando rotas por endpoints claros.