**Problema:**
Delinear os limites geométricos exatos e saber precisamente "onde" um tumor está localizado dentro de um exame de imagem médica (como uma imagem complexa de resolução 3x256x256 pixels).

**Conceito utilizado:**
U-Net com Conexões de Skip (*Skip Connections* ou Conexões de Atalho).

**Solução:**
Utilizar uma rede estruturada em formato de "U" constituída por dois caminhos simétricos:
1. **Caminho de Contração (Encoder)**: Realiza convoluções e operações de max-pooling para reduzir as dimensões físicas da imagem e entender o contexto geral (o que é o tumor).
2. **Caminho de Expansão (Decoder)**: Aplica upsampling para reconstruir as dimensões da imagem de saída original.
3. **Conexões de Skip**: Interligam diretamente os níveis correspondentes do Encoder ao Decoder, injetando as informações espaciais de alta resolução que foram perdidas durante a contração para que sejam integradas à máscara final de segmentação.

**Resultado:**
Uma máscara de pixel a pixel que delimita perfeitamente as fronteiras de estruturas complexas como tumores médicos ou detalhes topográficos de satélites.

**Por que essa solução funciona:**
O encoder ajuda a identificar a presença da anomalia de forma global, enquanto as conexões de skip fornecem os "atalhos" necessários para recuperar detalhes geométricos finos das camadas anteriores, permitindo que o decoder determine a localização espacial precisa de cada pixel.

**O que preciso aprender com esse exemplo:**
A U-Net é a rede padrão para segmentação porque as conexões de skip resolvem a perda de detalhes espaciais provocada pela redução dimensional do codificador, garantindo precisão milimétrica de posicionamento.