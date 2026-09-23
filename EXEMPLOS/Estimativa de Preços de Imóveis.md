**Problema:**
Estimar valores numéricos contínuos correspondentes aos preços de venda de residências em uma determinada região.

**Conceito utilizado:**
Redes Neurais de Perceptron Multicamadas (MLP) aplicadas a problemas de Regressão.

**Solução:**
Construir e treinar uma rede do tipo MLP utilizando um conjunto de dados estruturado (dados tabulares). A camada de entrada recebe as variáveis explicativas coletadas da região, incluindo características físicas dos imóveis e coordenadas/variáveis geográficas. Os dados passam pelas conexões densas das camadas ocultas e geram o valor final estimado na camada de saída (que conta com um único neurônio para regressão).

**Resultado:**
Obtenção de estimativas numéricas de preços para novas casas cadastradas no sistema, baseando-se estritamente em suas variáveis preditoras.

**Por que essa solução funciona:**
As MLPs possuem a propriedade matemática de aproximar qualquer função contínua a partir do mapeamento não linear de suas camadas ocultas densamente conectadas, o que lhes permite capturar relações geográficas e estruturais complexas no preço de venda.

**O que preciso aprender com esse exemplo:**
A arquitetura MLP é a escolha padrão quando trabalhamos com dados tabulares/estruturados e nosso objetivo é prever uma saída contínua (regressão).