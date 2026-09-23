**Problema:**
Prever com coerência sintática e semântica a próxima palavra de uma frase inacabada iniciada por "Eu quero comer uma...".

**Conceito utilizado:**
Processamento de Linguagem Natural (NLP) e dependência contextual sequencial em RNNs.

**Solução:**
Alimentar a sequência de palavras da frase como entradas para os nós da rede recorrente. A rede avalia sequencialmente o contexto gerado pelas palavras anteriores ("Eu", "quero", "comer", "uma") para ajustar as probabilidades das palavras do seu vocabulário.

**Resultado:**
A rede completa a frase de forma provável e natural com a palavra "pizza", em vez de sugerir uma palavra gramaticalmente ou logicamente inviável como "britadeira".

**Por que essa solução funciona:**
A memória interna baseada em conexões recorrentes permite que a rede retenha o significado acumulado das palavras que vieram antes, mapeando a forte probabilidade lógica de um verbo como "comer" se ligar a um substantivo alimentício ("pizza") e não a uma ferramenta industrial ("britadeira").

**O que preciso aprender com esse exemplo:**
A linguagem humana funciona como uma sequência lógica ordenada onde o significado das palavras futuras depende do passado; redes com memória recorrente capturam essas dependências gramaticais internas de curto alcance.