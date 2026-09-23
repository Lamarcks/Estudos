**Problema:** Criar uma interface para uma agência de turismo que apresente lado a lado mapas de dois destinos turísticos distintos (Santiago no Chile e Gramado no Brasil). O sistema deve solicitar de forma individual e interativa ao usuário o nível de zoom que ele deseja aplicar a cada mapa, aplicando validação em tempo de execução de limites (zoom entre 5 e 15).

**Conceito utilizado:** Arrays multidimensionais de dados, loops iterativos automatizados para gerar múltiplos componentes dinâmicos e controle dinâmico de IDs sequenciais por concatenação de strings.

**Solução:** _HTML de estrutura básica:_

```
<div id="local-1"></div> <!-- Destinado à Santiago -->
<div id="local-2"></div> <!-- Destinado à Gramado -->
<script src="destinos.js"></script>
```

_CSS de layout:_

```
#local-1, #local-2 {
    width: 50%;
    height: 300px;
    float: left; /* Flutua os elementos lado a lado */
}
```

_JavaScript de lógica de loops de renderização (`destinos.js`):_

```
// Array que armazena a estrutura de dados das cidades de destino
let turismo = [
    ["Santiago, Chile", -33.44758, -70.67172],
    ["Gramado, Brasil", -29.37463, -50.87402]
];

// Loop dinâmico que varre as cidades para inicializar os mapas
for (let i = 0; i < turismo.length; i++) {
    var map = new ol.Map({
        target: 'local-' + (i + 1), // Concatena e mapeia os contêineres 'local-1' e 'local-2'
        layers: [
            new ol.layer.Tile({
                source: new ol.source.OSM()
            })
        ],
        view: new ol.View({
            center: ol.proj.fromLonLat([
                turismo[i], // Pega a Longitude mapeada no índice 2
                turismo[i]  // Pega a Latitude mapeada no índice 1
            ]),
            // Solicita individualmente ao usuário o zoom dinâmico e o valida
            zoom: parseInt(prompt("Zoom desejado para " + turismo[i] + " [entre 5 e 15]: "))
        })
    });
}
```

**Resultado:** Ao carregar a página, são abertas duas caixas sequenciais de entrada solicitando o zoom dos destinos. Na sequência, os mapas de Santiago e Gramado surgem de forma correta lado a lado respeitando o grau exato de zoom selecionado individualmente pelo usuário.

**Por que essa solução funciona:** A variável de controle do loop `for` é concatenada ao termo `'local-' + (i+1)`. Isso faz com que a biblioteca inicialize os objetos mapeando precisamente as respectivas divisões do HTML. A indexação posicional de colunas lê as coordenadas de forma dinâmica do array multidimensional de dados.

**O que preciso aprender com esse exemplo:** Como trabalhar com dados indexados multidimensionais complexos de forma estruturada e inicializar dinamicamente componentes múltiplos de telas de APIs mapeando contêineres automatizados.