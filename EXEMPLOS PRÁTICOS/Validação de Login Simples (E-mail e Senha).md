**Problema:** Na tela de login de um sistema administrativo, os campos de e-mail e senha devem ser preenchidos obrigatoriamente. Se algum deles for esquecido, a aplicação deve notificar o usuário com um aviso antes de enviar qualquer requisição desnecessária para o servidor.

**Conceito utilizado:** Operador lógico de conjunção alternativa (`||` - OU) para validação simultânea de campos e controle de eventos de clique simples.

**Solução:**

```
var button = document.getElementById('button');
var email = document.getElementById('email');
var senha = document.getElementById('senha');

button.addEventListener("click", function () {
    // Verifica se o e-mail OU a senha estão vazios
    if (email.value == '' || senha.value == '') {
        alert("Campo e-mail ou senha não preenchidos");
    } else {
        alert("Campos preenchidos com sucesso");
    }
});
```

**Resultado:** Se um ou ambos os inputs estiverem vazios ao clicar em "Login", o navegador emite um alerta nativo: "Campo e-mail ou senha não preenchidos". Se ambos estiverem populados, exibe: "Campos preenchidos com sucesso".

**Por que essa solução funciona:** O operador lógico `||` avalia múltiplas expressões relacionais. Caso a primeira seja verdadeira (`email.value == ''`) **ou** a segunda seja verdadeira (`senha.value == ''`), a condição global é considerada aceita, disparando o bloco interno de erro.

**O que preciso aprender com esse exemplo:** Como utilizar o operador lógico `||` para otimizar validações rápidas onde qualquer falha de campo deve barrar o avanço do usuário.