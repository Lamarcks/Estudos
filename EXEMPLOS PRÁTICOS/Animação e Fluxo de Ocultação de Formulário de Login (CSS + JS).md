**Problema:** Em uma tela de login, criar uma animação em que o formulário surge suavemente expandindo-se. Ao clicar no botão de confirmação, a aplicação deve disparar um efeito onde o formulário desliza verticalmente para cima saindo inteiramente da área visível e, apenas quando a animação de saída for de fato concluída, o navegador deve ocultar o formulário e carregar a nova página do sistema (`site.html`).

**Conceito utilizado:** Regras de animação por quadros-chave CSS (`@keyframes`), propriedades de transformação vertical (`translateY`), escutadores de fim de animações de transição do CSS no JavaScript (`animationend`) e controle de endereçamento de links de páginas (`window.location.href`).

**Solução:** _HTML de estrutura básica:_

```
<div id="login-container">
    <form>
        <h1>Login</h1>
        <label>E-mail</label>
        <input type="email" id="email">
        <label>Senha</label>
        <input type="password" id="senha">
        <button type="button" id="button">Login</button>
    </form>
</div>
<script src="login.js"></script>
```

_CSS de estilo e configurações `@keyframes`:_

```
/* Animação Inicial de Surgimento do Formulário */
form {
    animation: suave 0.7s;
}

@keyframes suave {
    from {
        opacity: 0;
        transform: scale(0.8);
    }
    to {
        opacity: 1;
        transform: scale(1);
    }
}

/* Animação que remove o formulário para o topo */
.oculta-form {
    animation: top 0.5s;
    animation-fill-mode: forwards; /* Mantém o elemento no estado final */
}

@keyframes top {
    from { transform: translateY(0); }
    to { transform: translateY(-100vh); } /* Joga 100% da altura da tela para cima */
}
```

_JavaScript de lógica de fluxo (`login.js`):_

```
const btnLogin = document.querySelector('#button');
const form = document.querySelector('form');

btnLogin.addEventListener('click', event => {
    event.preventDefault(); // Impede o recarregamento natural da página
    form.classList.add('oculta-form'); // Adiciona a classe que inicia o movimento de saída
});

form.addEventListener('animationend', event => {
    // Garante que o redirecionamento só ocorre após o fim da animação específica 'top'
    if (event.animationName == 'top') {
        form.style.display = 'none'; // Altera estilo inline ocultando o nó
        window.location.href = 'site.html'; // Altera o destino de link do navegador
    }
});
```

**Resultado:** O formulário aparece suavemente crescendo de escala. Ao clicar no botão, ele desliza para cima e desaparece de vista, abrindo automaticamente a página seguinte em sequência fluida.

**Por que essa solução funciona:** A classe CSS `.oculta-form` deforma a posição do formulário transladando-o em `-100vh` de sua posição inicial. O JavaScript escuta o evento `animationend` (disparado pelo navegador quando a animação CSS chega ao fim) e avalia qual animação terminou. Ao constatar que o movimento de saída vertical (`top`) acabou, conclui com segurança o redirecionamento da página (`window.location.href`).

**O que preciso aprender com esse exemplo:** Como usar o JavaScript como maestro de transições de telas complexas que dependem inteiramente do sincronismo e do término de animações físicas declaradas no CSS.