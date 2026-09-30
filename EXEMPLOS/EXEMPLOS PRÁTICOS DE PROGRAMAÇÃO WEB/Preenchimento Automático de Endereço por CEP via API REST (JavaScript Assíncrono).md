
**Problema:**  
Evitar que o usuário precise digitar manualmente logradouro, bairro, cidade e estado em um formulário de cadastro, preenchendo todos esses campos automaticamente assim que um CEP válido for informado.

**Conceito utilizado:**  
Requisição assíncrona com a Fetch API (`fetch`), manipulação de Promises via sintaxe `async/await` e consumo de serviço Web externo no formato JSON (API ViaCEP).

**Solução:**

1. Desenvolva uma função assíncrona (`async`) que monta a URL do serviço e faz a busca com `await fetch(url)`.
2. Converta a resposta bruta para um objeto JavaScript legível usando `await response.json()`.
3. Crie uma função auxiliar para distribuir os dados recebidos nos campos correspondentes do formulário via DOM.

```
// 1. Função assíncrona que consome a API do ViaCEP
const getBuscarCepAPI = async function(cep) {
    // Interpola o CEP digitado na URL da API
    let url = `https://viacep.com.br/ws/${cep}/json/`;

    try {
        // Aguarda a resposta da requisição de rede sem travar a interface
        let response = await fetch(url);
        // Converte a resposta enviada em formato JSON para objeto JS
        let dadosCep = await response.json();

        // Passa o objeto retornado para a função de atualização de tela
        setDadosForm(dadosCep);
    } catch (erro) {
        console.error("Falha ao buscar o CEP:", erro);
    }
};

// 2. Função para preencher os campos do formulário no HTML
const setDadosForm = function(dadosCep) {
    document.getElementById('logradouro').value = dadosCep.logradouro;
    document.getElementById('bairro').value     = dadosCep.bairro;
    document.getElementById('cidade').value     = dadosCep.localidade;
    document.getElementById('estado').value     = dadosCep.uf;
};
```

**Resultado:**  
Ao pesquisar pelo CEP `06422120`, o sistema busca as informações em segundo plano e preenche instantaneamente o logradouro com "Avenida Gupê", o bairro com "Jardim Belval", a cidade com "Barueri" e o estado com "SP".

**Por que essa solução funciona:**  
A instrução `await` suspende a execução interna da função assíncrona até que o pacote de dados vindo do servidor da API chegue, liberando o navegador para continuar executando outras tarefas da página normalmente. Quando o JSON retorna, ele é convertido em um objeto cujas propriedades (`dadosCep.logradouro`, etc.) são atribuídas diretamente aos elementos da tela.

**O que preciso aprender com esse exemplo:**

- Funções que realizam comunicação de rede exigem a palavra-chave `async` antes de sua definição.
- A instrução `await` só pode ser utilizada dentro de funções declaradas como `async`.
- `fetch(url)` realiza requisições HTTP do tipo `GET` por padrão e precisa ter sua resposta convertida com `.json()`.
