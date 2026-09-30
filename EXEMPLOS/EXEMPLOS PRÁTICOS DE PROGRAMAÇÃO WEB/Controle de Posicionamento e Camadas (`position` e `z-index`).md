
**Problema:**  
Organizar diversos elementos em uma página com diferentes comportamentos visuais: um bloco de cabeçalho que cola no topo ao rolar a página, uma caixa fixa no canto da tela, uma caixa deslocada em relação à sua origem e um elemento posicionado especificamente dentro de um contêiner pai.

**Conceito utilizado:**  
Propriedade CSS `position` (`static`, `relative`, `absolute`, `fixed`, `sticky`) e empilhamento em camadas via `z-index`.

**Solução:**  
Combine os diferentes valores da propriedade `position` com coordenadas de deslocamento (`top`, `bottom`, `left`, `right`) e índices de profundidade:

```
/* Contêiner de referência para elementos absolutos */
.container-posicionado {
    position: relative;
    width: 400px;
    height: 200px;
}

/* Caixa com posicionamento relativo (desloca reservando espaço original) */
.relative-box {
    position: relative;
    top: 20px;
    left: 20px;
}

/* Caixa com posicionamento absoluto (amarrada ao pai .container-posicionado) */
.absolute-box {
    position: absolute;
    top: 50px;
    right: 10px;
}

/* Caixa fixa na janela de visualização do navegador */
.fixed-box {
    position: fixed;
    bottom: 20px;
    right: 20px;
    z-index: 1000; /* Fica acima dos demais elementos */
}

/* Caixa adesiva que cola no topo durante a rolagem */
.sticky-box {
    position: sticky;
    top: 0;
    z-index: 900;
}
```

**Resultado:**  
A `.relative-box` desloca-se sem alterar a posição inicial dos elementos ao redor. A `.absolute-box` posiciona-se precisamente no canto superior direito do contêiner pai. A `.fixed-box` permanece ancorada no canto do navegador independentemente do scroll. A `.sticky-box` flutua no fluxo normal até encostar no topo da tela, fixando-se a partir de então.

**Por que essa solução funciona:**

- `position: absolute` busca o ancestral com `position` diferente de `static` para usar como origem de coordenadas.
- `position: fixed` ignora os elementos da página e fixa-se à _viewport_ (janela gráfica do navegador).
- `position: sticky` alterna dinamicamente entre comportamento `relative` e `fixed` dependendo da posição atual da barra de rolagem.

**O que preciso aprender com esse exemplo:**

- Elementos com `position: absolute` só funcionam de forma controlada se o elemento pai tiver `position: relative`.
- O atributo `z-index` **só funciona** em elementos que possuem valor de `position` diferente de `static`.
