
**Problema:**  
Construir um layout de artigos que exiba 1 coluna em telas de smartphones, transforme-se em 2 colunas em tablets e expanda para 3 colunas em monitores de alta resolução, ajustando também a tipografia proporcionalmente.

**Conceito utilizado:**  
Estratégia _Mobile-First_, CSS Grid Layout, unidades relativas (`rem`) e Media Queries (`@media screen and (min-width: ...)`).

**Solução:**  
Defina a estrutura base sem media query visando telas pequenas (1 coluna). Adicione regras condicionais progressivas usando `min-width` para telas maiores. Configure o elemento `html` com tamanho base em pixels e adapte os demais elementos usando unidades `rem`.

```
/* Estilos Base: Mobile-First (Dispositivos Pequenos) */
html {
    font-size: 14px; /* Base reduzida para telas pequenas */
}

.grid-container {
    display: grid;
    grid-template-columns: 1fr; /* 1 coluna no celular */
    gap: 20px;
}

.conteudo {
    padding: 1rem;
}

/* Ajustes para Tablets e Telas Médias (acima de 768px) */
@media screen and (min-width: 768px) {
    html {
        font-size: 16px; /* Aumenta a base de fonte global */
    }
    .grid-container {
        grid-template-columns: 1fr 1fr; /* 2 colunas */
    }
}

/* Ajustes para Desktops (acima de 1200px) */
@media screen and (min-width: 1200px) {
    .grid-container {
        grid-template-columns: 1fr 1fr 1fr; /* 3 colunas */
    }
}
```

**Resultado:**  
Em celulares, os artigos são empilhados verticalmente para facilitar a leitura. Em tablets, organizam-se lado a lado em pares e, em telas grandes, dividem-se perfeitamente em três colunas com tipografia proporcionalmente ampliada.

**Por que essa solução funciona:**  
O navegador aplica os estilos base por padrão. Quando a largura da janela atinge os pontos de interrupção (_breakpoints_) definidos pelas `@media queries`, o CSS substitui as propriedades necessárias (como a quantidade de colunas do grid e o tamanho da fonte raiz `rem`), re-renderizando a interface sem recarregar a página.

**O que preciso aprender com esse exemplo:**

- A abordagem _Mobile-First_ declara o código sem `@media` para celulares e usa `@media (min-width: ...)` para expandir o layout em telas maiores.
- A unidade `rem` refere-se ao `font-size` definido na tag `html`. Mudar a fonte do `html` em uma media query ajusta proporcionalmente todo o site.
