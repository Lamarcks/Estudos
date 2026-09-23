**Problema:**
Traduzir um texto longo de um idioma para outro sem sofrer lentidão de processamento sequencial e sem perder o sentido de palavras distantes na frase original (limitação clássica de memória das RNNs/LSTMs).

**Conceito utilizado:**
Transformers e o Mecanismo de Atenção (*Self-Attention*).

**Solução:**
Utilizar uma arquitetura baseada inteiramente em paralelismo, composta de blocos de codificador (para mapear a entrada em representação interna) e decodificador (para traduzir). Em vez de processar palavra por palavra de forma linear, aplica-se o mecanismo de *self-attention* (auto-atenção), que calcula pesos de relevância simultâneos entre todas as palavras da sequência para focar nas conexões sintáticas mais importantes, independentemente da ordem em que aparecem.

**Resultado:**
Traduções rápidas, naturais e contextualizadas de grandes blocos de texto sem perdas de informação ao longo da sequência.

**Por que essa solução funciona:**
O processamento paralelo permite utilizar grandes volumes de dados ao mesmo tempo, enquanto o *self-attention* foca no contexto global da frase, estabelecendo conexões lógicas diretas entre termos distantes sem depender de uma passagem passo a passo.

**O que preciso aprender com esse exemplo:**
Os Transformers superam as RNNs e LSTMs em NLP porque eliminam a dependência de processamento ordenado rígido, utilizando auto-atenção para capturar relações contextuais complexas instantaneamente.