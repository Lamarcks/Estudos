**Problema:** Criar uma experiência rica e fluida de interface para validar múltiplos campos (Nome, Telefone, E-mail e CPF). Caso qualquer campo esteja em branco, o formulário físico deve sofrer um efeito visual de tremor na tela (causado por animação CSS) para chamar a atenção do usuário.

**Conceito utilizado:** Seletores do tipo `querySelectorAll`, operador de desestruturação spread (`[...]`), varredura por laço `forEach`, controle dinâmico de classes do CSS (`classList.add`/`remove`), interrupção de envio de formulários nativos (`preventDefault`) e capturador de término de animação CSS (`animationend`).

**Solução:** _HTML de estrutura:_

```
<div class="container">
    <form>
        <h2>Cadastre-se</h2>
        <div class="blocoInput">
            <label>Nome</label>
            <input type="text" id="nome" class="form-input">
        </div>
        <div class="blocoInput">
            <label>Fone</label>
            <input type="tel" id="fone" class="form-input">
        </div>
        <div class="blocoInput">
            <label>Email</label>
            <input type="email" id="email" class="form-input">
        </div>
        <div class="blocoInput">
            <label>CPF</label>
            <input type="text" id="cpf" class="form-input">
        </div>
        <button type="submit" class="btn">Login</button>
    </form>
</div>
```

_CSS de estilo e animação de tremor:_

```
form.validateErro {
    animation: preenche 200ms linear;
    animation-iteration-count: 2; /* Executa a animação duas vezes */
}

@keyframes preenche {
    0%, 100% { transform: translateX(0); }
    35% { transform: translateX(-15%); } /* Move para a esquerda */
    70% { transform: translateX(15%); }  /* Move para a direita */
}
```

_JavaScript de lógica (`cadastro.js`):_

```
const btnLogin = document.querySelector(".btn");
const form = document.querySelector("form");

btnLogin.addEventListener("click", event => {
    event.preventDefault(); // Impede o recarregamento natural da página

    // Coleta todos os inputs de dentro dos blocos e os joga em um Array com spread operator
    const fields = [...document.querySelectorAll(".blocoInput input")];

    // Varre cada campo e, se encontrar algum vazio, adiciona a classe de erro CSS
    fields.forEach(field => {
        if (field.value === "") {
            form.classList.add("validateErro");
        }
    });

    const formError = document.querySelector(".validateErro");
    if (formError) {
        // Escuta o fim da animação física de tremor no navegador
        formError.addEventListener("animationend", event => {
            if (event.animationName === "preenche") {
                // Remove a classe para que ela possa ser reativada no próximo clique
                formError.classList.remove("validateErro");
            }
        });
    } else {
        alert('Tudo certo');
    }
});
```

**Resultado:** Se algum campo de texto estiver em branco, o formulário inteiro "treme" horizontalmente na tela por duas vezes. Se todos os campos estiverem preenchidos corretamente, o navegador dispara o pop-up "Tudo certo".

**Por que essa solução funciona:** O seletor `querySelectorAll` obtém uma lista estática de elementos. O operador `[...]` converte essa coleção em um Array Javascript legítimo para que possamos usar o método de iteração `forEach`. Caso a validação encontre strings vazias, a classe CSS que executa o tremor geométrico por `@keyframes` é acoplada ao elemento. O evento `animationend` avisa o motor JS quando a oscilação acabou, removendo a classe para habilitar novos ciclos de teste.

**O que preciso aprender com esse exemplo:** Como manipular coleções inteiras de elementos usando iterações (`forEach`), usar o operador spread e integrar eventos de renderização física de transições visuais CSS (`animationend`) com lógica dinâmica.