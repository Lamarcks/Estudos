**Problema:** Criar e carregar em uma página web uma renderização de gráficos bidimensionais contendo a sobreposição de dois retângulos (um vermelho e um azul), aplicando transparência para exibir uma mescla de cores no ponto exato em que eles se cruzam no documento.

**Conceito utilizado:** API do elemento gráfico Canvas, instanciação de contexto (`getContext("2d")`), preenchimento de formas com padrões de cores RGB e RGBA (canal de transparência alfa) e mapeamento cartesiano de coordenadas bidimensionais (`fillRect`).

**Solução:** _HTML de estrutura básica:_

```
<body onload="draw();">
    <canvas id="canvas"></canvas>
    <script src="exercicio3.js"></script>
</body>
```

_CSS de layout:_

```
canvas {
    width: 150;
    height: 150;
}
```

_JavaScript de lógica de renderização (`exercicio3.js`):_

```
function draw() {
    var canvas = document.getElementById("canvas");

    // Verifica se o navegador dá suporte de contexto gráfico ao Canvas
    if (canvas.getContext) {
        var ctx = canvas.getContext("2d"); // Ativa o objeto de contexto 2D

        // 1. Define cor sólida vermelha e desenha o primeiro retângulo
        ctx.fillStyle = "rgb(200,0,0)";
        ctx.fillRect(10, 10, 85, 80); // Parâmetros: (X, Y, Largura, Altura)

        // 2. Define cor azul com transparência (canal alfa de 0.5) e sobrepõe
        ctx.fillStyle = "rgba(0, 0, 200, 0.5)";
        ctx.fillRect(30, 30, 85, 80);
    }
}
```

**Resultado:** Dois quadrados são renderizados na tela de pintura do Canvas. Na área geométrica comum de cruzamento das coordenadas, surge um retângulo menor de cor arroxeada devido à fusão de transparência dos elementos.

**Por que essa solução funciona:** O método `getContext("2d")` retorna as referências e funções necessárias para desenho vetorial. `fillRect` deforma e preenche o espaço geométrico na tela com base nas coordenadas de grade informadas. A diretiva `rgba` atribui o valor `0.5` de opacidade ao canal alfa, fazendo com que o navegador mescle os valores matemáticos de cores primárias na rasterização de pixels.

**O que preciso aprender com esse exemplo:** Como ativar e manipular instâncias de desenho dentro do contêiner do Canvas e operar com transparência de canais alfa.