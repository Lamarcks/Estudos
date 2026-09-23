**Problema:**
Limpar ruídos aleatórios de imagens degradadas ou detectar outliers e anomalias raras em grandes conjuntos de dados brutos sem dados rotulados para treinamento.

**Conceito utilizado:**
Autoencoders e espaço latente comprimido (*bottleneck*) em aprendizado não supervisionado.

**Solução:**
Treinar uma rede contendo duas partes fundamentais:
1. **Codificador (Encoder)**: Recebe a imagem ruidosa e comprime seus dados até a menor camada dimensional chamada *bottleneck* (espaço latente), forçando a eliminação de redundâncias.
2. **Decodificador (Decoder)**: Reconstrói a imagem limpa a partir da camada latente, minimizando a diferença matemática entre a entrada original e a saída reconstruída durante o treino.
Para detecção de anomalias, dados normais são reconstruídos com erro mínimo, enquanto dados anômalos que fogem do padrão produzem erros de reconstrução visivelmente discrepantes.

**Resultado:**
Imagens limpas de imperfeições ou detecção precisa de anomalias críticas no sistema.

**Por que essa solução funciona:**
Ao força a informação a passar por um canal estreito (o *bottleneck*), o ruído (que é aleatório e sem padrão estrutural) não consegue ser codificado de forma eficiente, sendo descartado como redundância enquanto as informações estruturais essenciais permanecem.

**O que preciso aprender com esse exemplo:**
O Autoencoder força a compressão de dados para mapear as representações mais importantes no espaço latente, servindo perfeitamente para limpeza e triagem de anomalias sem necessidade de supervisão de rótulos.