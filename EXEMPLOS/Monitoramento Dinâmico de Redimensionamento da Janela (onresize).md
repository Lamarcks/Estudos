**Problema:** Ajustar layouts ou monitorar dimensões físicas da tela de exibição do usuário, capturando a alteração de tamanho sempre que o navegador for redimensionado e atualizando as medições textualmente de forma automática.

**Conceito utilizado:** Evento de layout de janela do navegador (`window.onresize`), propriedades de leitura física de largura e altura internas da tela (`window.innerHeight`, `window.innerWidth`).

**Solução:**

```
const saidaAlt = document.querySelector("#altura");
const saidaLarg = document.querySelector("#largura");

function redimensiona() {
    saidaAlt.textContent = window.innerHeight; // Lê a altura em pixels
    saidaLarg.textContent = window.innerWidth;  // Lê a largura em pixels
}

// Atribui a função diretamente à propriedade de evento onresize da janela
window.onresize = redimensiona;
```

**Resultado:** Sempre que o usuário arrasta os cantos do navegador mudando suas dimensões, os valores de pixels de altura e largura de tela visível na página atualizam-se instantaneamente de forma síncrona.

**Por que essa solução funciona:** `window.onresize` é o gatilho nativo do mecanismo de exibição do navegador para layouts responsivos. Ao vincular a função a esse manipulador, o JavaScript recalcula as propriedades de dimensão da janela de forma imediata.

**O que preciso aprender com esse exemplo:** Como monitorar o comportamento de exibição do dispositivo do usuário e realizar consultas de propriedades de tamanho de tela do próprio objeto `window`.