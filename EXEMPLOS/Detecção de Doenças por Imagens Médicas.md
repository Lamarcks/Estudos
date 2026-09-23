**Problema:** Analisar exames de imagem complexos, como tomografias computadorizadas ou raios-X, para identificar indícios visuais de patologias e realizar diagnósticos. A dificuldade reside na alta complexidade visual dos dados médicos e na necessidade de classificar essas informações em categorias bem definidas de forma confiável.

**Conceito utilizado:** Aprendizado Supervisionado (Classificação).

**Solução:**

1. **Rotulagem prévia:** Reúne-se um vasto banco de imagens que já foram analisadas e rotuladas por médicos especialistas humanos com as categorias "doente" ou "saudável".
2. **Processamento por camadas:** A rede neural recebe os pixels da imagem e, camada por camada, extrai características espaciais importantes (bordas, texturas, anomalias locais).
3. **Classificação Final:** A última camada de neurônios atribui a probabilidade de a imagem pertencer a uma das classes pré-definidas (diagnóstico).

**Resultado:** Diagnóstico automatizado rápido de novas imagens médicas, auxiliando na triagem e na tomada de decisão dos especialistas.

**Por que essa solução funciona:** A estrutura de conexões e neurônios é excelente no processamento de dados volumosos e complexos, conseguindo correlacionar padrões visuais não lineares que definem a presença física de uma doença com altíssima taxa de acerto.

**O que preciso aprender com esse exemplo:** A classificação é um problema supervisionado clássico. Ela sempre exige um conjunto de dados histórico rotulado com o gabarito correto ("classes") para treinar a rede a rotular novos dados não vistos.
