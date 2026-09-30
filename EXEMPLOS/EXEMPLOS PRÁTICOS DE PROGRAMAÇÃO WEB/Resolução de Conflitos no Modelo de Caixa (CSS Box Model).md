
**Problema:**  
Duas caixas configuradas com a mesma largura declarada (`width: 200px`) exibem tamanhos visuais completamente diferentes na tela após a adição de preenchimentos internos (`padding`) e bordas (`border`), quebrando o alinhamento do layout.

**Conceito utilizado:**  
CSS Box Model e a propriedade `box-sizing` (diferença entre `content-box` e `border-box`).

**Solução:**

1. Aplique `box-sizing: content-box` para observar o comportamento padrão onde bordas e preenchimentos são somados por fora da largura declarada.
2. Aplique `box-sizing: border-box` na segunda caixa para forçar o navegador a absorver os valores de `padding` e `border` dentro da largura total de `200px`.

```
/* Caixa no padrão tradicional (content-box) */
.caixa-padrao {
    width: 200px;
    height: 150px;
    padding: 10px;
    border: 5px solid darkblue;
    box-sizing: content-box; /* Largura final renderizada: 200 + 10*2 + 5*2 = 230px */
}

/* Caixa otimizada para layouts exatos (border-box) */
.caixa-border-box {
    width: 200px;
    height: 150px;
    padding: 10px;
    border: 5px solid darkgreen;
    box-sizing: border-box; /* Largura final renderizada fixa em exatos 200px */
}
```

**Resultado:**  
A caixa com `content-box` expande seu tamanho visual total para `230px` de largura por `130px` de altura. A caixa configurada com `border-box` mantém-se estritamente com `200px` por `100px`, ajustando o espaço do conteúdo interno dinamicamente.

**Por que essa solução funciona:**  
Com `border-box`, o motor de renderização do CSS recalcula a área do conteúdo subtraindo as bordas e os espaçamentos internos da dimensão total informada, impedindo o estouro não planejado de elementos.

**O que preciso aprender com esse exemplo:**

- `content-box` soma: `Largura Total = width + padding_esquerdo/direito + border_esquerda/direita`.
- `border-box` fixa: `width` é a largura total máxima da caixa na tela.
- Utilizar `box-sizing: border-box` como regra global previne erros de dimensionamento e quebras indesejadas de layout.
