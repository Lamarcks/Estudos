**Problema:** Construir um protótipo focado em acessibilidade para pessoas com baixa visão que rastreie continuamente a posição X e Y do cursor do mouse. Uma caixa dinâmica flutuante deve acompanhar o movimento do ponteiro exibindo as coordenadas em tempo real.

**Conceito utilizado:** Eventos da janela do navegador (`window.addEventListener`), leitura das propriedades físicas de posicionamento geométrico do cursor (`event.clientX`/`event.clientY`), posicionamento CSS absoluto no DOM e concatenação de pixels para coordenadas de estilo (`style.top`/`style.left`).

**Solução:** _HTML de estrutura básica:_

```
<div id="position">
    <p>x: <span id="posicaoX"></span></p>
    <p>y: <span id="posicaoY"></span></p>
</div>
<script src="movmouse.js"></script>
```

_JavaScript de lógica (`movmouse.js`):_

```
window.addEventListener('mousemove', (event) => {
    const localiza = document.getElementById('position');
    let posicaoX = document.getElementById('posicaoX');
    let posicaoY = document.getElementById('posicaoY');

    // Altera a posição da div fixed para que siga a coordenada real do mouse na página
    localiza.style.top = event.clientY + 'px';
    localiza.style.left = event.clientX + (5) + 'px'; // Desloca 5 pixels do ponteiro para evitar conflitos

    // Atualiza a exibição textual das coordenadas na tela
    posicaoY.innerText = event.clientY + 'px';
    posicaoX.innerText = event.clientX + 'px';
});
```

**Resultado:** À medida que o usuário arrasta o mouse pela janela do navegador, uma caixinha com a leitura atualizada das posições cartesianas segue o cursor, fornecendo feedback contínuo (Ex: "x: 307px", "y: 80px").

**Por que essa solução funciona:** O evento `mousemove` dispara continuamente com a transição do mouse. O navegador expõe as coordenadas exatas do cursor em relação à tela visível por meio de `event.clientX` e `event.clientY`. Atribuir esses valores dinamicamente nas propriedades de estilo `top` e `left` força a renderização em tempo real do elemento visual flutuante na tela.

**O que preciso aprender com esse exemplo:** Como capturar e manipular interações de ponteiro e usar geometria de coordenadas dinâmicas para ajustar posições físicas de elementos do DOM.