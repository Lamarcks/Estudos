**Problema:** Ao carregar a página da internet de um serviço local, coletar (com a devida permissão física) as coordenadas reais de latitude e longitude do dispositivo do usuário e instanciar um mapa interativo do OpenLayers focado precisamente naquela geolocalização.

**Conceito utilizado:** API nativa do navegador de Geolocalização de hardware (`navigator.geolocation`), importação e instanciação de componentes georreferenciados do OpenLayers SDK (`ol.Map`, `ol.layer.Tile`, `ol.View`).

**Solução:** _HTML de estrutura básica:_

```
<head>
    <!-- Importando as dependências do OpenLayers via CDN -->
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/openlayers/openlayers.github.io@master/en/v6.9.0/css/ol.css" type="text/css">
    <script src="https://cdn.jsdelivr.net/gh/openlayers/openlayers.github.io@master/en/v6.9.0/build/ol.js"></script>
</head>
<body>
    <div id="mapa"></div>
    <script src="geolocalizacao.js"></script>
</body>
```

_CSS de layout:_

```
#mapa {
    width: 600px;
    height: 600px;
}
```

_JavaScript de lógica de integração (`geolocalizacao.js`):_

```
// 1. Obtém as coordenadas geográficas de hardware fornecidas pelo dispositivo do usuário
navigator.geolocation.getCurrentPosition(position => {
    const { latitude, longitude } = position.coords; // Extrai latitude e longitude

    // 2. Instancia o mapa e renderiza os blocos dentro da div 'mapa'
    var map = new ol.Map({
        target: 'mapa',
        layers: [
            new ol.layer.Tile({
                source: new ol.source.OSM() // Importa blocos do mapa aberto OpenStreetMap
            })
        ],
        view: new ol.View({
            // Transforma e projeta as coordenadas decimais no sistema espacial do OpenLayers
            center: ol.proj.fromLonLat([longitude, latitude]),
            zoom: 10 // Determina o grau de aproximação inicial
        })
    });
});
```

**Resultado:** O navegador emite um alerta pedindo permissão de acesso à geolocalização. Ao aceitar, o mapa do OpenLayers carrega focado de forma integrada na localidade exata do usuário.

**Por que essa solução funciona:** `navigator.geolocation.getCurrentPosition` é o canal integrado do navegador para coleta de dados de localização fornecidos pelo dispositivo móvel ou rede do usuário. O OpenLayers recebe as coordenadas e usa o método `fromLonLat` para centrar visualmente a tela do mapa com base nos dados georreferenciados no carregamento inicial.

**O que preciso aprender com esse exemplo:** Como trabalhar com dados e permissões nativas de sensores do navegador e implementar bibliotecas de processamento cartográfico em interfaces HTML.