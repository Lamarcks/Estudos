
## Visão geral

A arquitetura **Transformers**, proposta em 2017 no clássico artigo _"Attention is All You Need"_ por pesquisadores do Google, revolucionou por completo o campo do Deep Learning e da Inteligência Artificial. Ao introduzir os **mecanismos de atenção** em substituição ao antigo processamento puramente sequencial, o Transformer viabilizou a **paralelização** no treinamento de grandes modelos de linguagem. Essa inovação permitiu que as sentenças inteiras fossem analisadas simultaneamente, elevando drasticamente a velocidade de treinamento e a capacidade de compreender o contexto profundo e as sutilezas da linguagem natural.

---

## Conceitos principais

- **Tokens**: Pedacinhos de palavras que mantêm o seu significado original após a quebra do texto de entrada.
- **Embeddings**: Sequências numéricas que representam o significado semântico, a posição e o contexto de uma palavra (ou token) dentro de um texto.
- **Mecanismo de Atenção (Self-Attention)**: Capacidade do modelo de calcular, simultaneamente, a relação de cada palavra com todas as outras palavras de uma frase, atribuindo pesos diferentes conforme a relevância mútua.
- **Multi-headed Attention (Atenção de Múltiplas Cabeças)**: Processamento simultâneo do contexto por múltiplos "cabeçotes" ou "mentes" de atenção, analisando a frase sob diferentes perspectivas ao mesmo tempo.
- **Encoder (Codificador)**: Mecanismo responsável por processar e "entender" o texto de entrada, gerando representações matemáticas sofisticadas.
- **Decoder (Decodificador)**: Mecanismo responsável por gerar a resposta de forma sequencial (uma palavra por vez), utilizando tanto o contexto vindo do encoder quanto as palavras que ele próprio já gerou.
- **Paralelização**: Capacidade de processar todos os elementos de uma frase simultaneamente (ao contrário do processamento sequencial das arquiteturas anteriores), otimizando o treinamento de padrões e dependências.

---

## Conteúdo explicado

### 1. Evolução Histórica: O Cenário Pré e Pós-Transformer

Antes do advento do Transformer, as tarefas de Processamento de Linguagem Natural (PLN) eram dominadas por **Redes Neurais Recorrentes (RNNs)** e **LSTMs**.

- **Limitações das RNNs/LSTMs**:
    - Funcionam em arquiteturas _sequence-to-sequence_, analisando sequencialmente **uma palavra após a outra**.
    - Exigem treinamento supervisionado específico para cada tarefa (como classificação ou análise de sentimento).
- **A Revolução do Transformer**:
    - Introduziu a **paralelização**, permitindo que a sentença inteira seja visualizada simultaneamente.
    - **Benefícios imediatos**: maior velocidade de treinamento, eficiência no reconhecimento de dependência entre palavras, melhoria no reconhecimento de padrões e capacidade de analisar problemas não sequenciais.
    - **Modelos derivados (2018)**: **BERT** (desenvolvido pelo Google e focado em buscas, traduções e SEO) e **GPT** (Pré-treinamento Generativo, desenvolvido pela OpenAI, que serve de base para o ChatGPT).

### 2. O Pré-processamento dos Dados: Tokens e Embeddings

A transformação dos dados começa antes mesmo da entrada na estrutura principal do Transformer:

1. **Tokenização**: A frase inserida (como o exemplo _"Dani gosta de café"_) é quebrada em **tokens**.
2. **Conversão em Embeddings**: Cada token é convertido em um **embedding** (vetor numérico). Esse vetor carrega a semântica, a posição e o contexto da palavra, sofrendo transformações contínuas ao longo do modelo.

### 3. Anatomia Detalhada do Encoder (O Codificador)

O encoder tem como objetivo "compreender" o input. Ele é composto por um empilhamento de blocos (comumente 6 blocos). Cada bloco do encoder contém:

- **Camada de Self-Attention**: Calcula as conexões de contexto entre as palavras.
- **Camada Feed Forward**: Uma rede neural tradicional com múltiplas camadas que refina as informações capturadas pelas camadas de atenção, sem analisar contexto diretamente (a informação flui em uma única direção).
- **Camadas Auxiliares (presentes em ambas as etapas acima)**:
    - **Conexões Residuais**: Somam os embeddings originais (não processados) à saída dos mecanismos de atenção/feedforward. Isso impede a perda do contexto original ao longo do empilhamento de blocos.
    - **Normalização**: Compacta as informações geradas pelas "múltiplas cabeças" de atenção de volta para uma entrada única adequada para a próxima camada.

### 4. Anatomia Detalhada do Decoder (O Decodificador)

O decoder gera a resposta palavra por palavra (sequencialmente), mas também considera o contexto. Assim como o encoder, é estruturado em blocos empilhados (comumente 6 blocos) e possui:

1. **Self-Attention (Mascarado/Autorregressivo)**: A atenção foca apenas nas palavras que **já foram geradas anteriormente**. As palavras futuras estão ocultas/mascaradas para que o modelo respeite a ordem de geração textual e não acesse dados futuros.
2. **Encoder-Decoder Attention**: Camada de atenção que recebe as informações processadas pelo encoder (input original completo) e as integra às palavras já geradas pelo decoder para produzir uma resposta coerente e consistente.
3. **Feed Forward, Normalização e Conexões Residuais**: Funcionam de forma semelhante ao encoder, refinando as representações matemáticas. As conexões residuais aqui conectam as informações processadas anteriormente dentro do próprio decoder.

### 5. Finalização: Language Modeling Head

É a camada final do Transformer, responsável por converter as representações matemáticas complexas (vetores dos decoders) em texto legível:

- **Camada Linear**: Mapeia os vetores gerados no vocabulário completo do modelo, atribuindo uma pontuação de relevância para cada palavra possível.
- **Camada Softmax**: Converte as pontuações geradas pela camada Linear em probabilidades. A palavra com a maior probabilidade é escolhida como a próxima na sequência.

### 6. Pipeline de Treinamento dos Modelos

O treinamento dos Transformers ocorre em fases bem definidas:

1. **Treinamento Auto-supervisionado**: O modelo aprende sem intervenção humana usando volumes massivos de dados não rotulados. Ele desenvolve uma compreensão estatística profunda do comportamento da linguagem natural, aprendendo a prever as próximas palavras ou preencher lacunas.
2. **Transfer Learning (Aprendizado por Transferência)**: O modelo pré-treinado é ajustado (fase supervisionada) para tarefas específicas (como tradução ou perguntas/respostas) usando conjuntos de dados menores rotulados por humanos.
3. **Refinamento Contínuo**: Pode contar adicionalmente com feedback humano.

---

## Conceitos que não posso confundir

|Conceito A|Conceito B|Diferença Fundamental|
|:--|:--|:--|
|**Encoder**|**Decoder**|O **Encoder** processa a entrada inteira em paralelo para "entender" o contexto. O **Decoder** gera a saída em sequência (palavra por palavra) e utiliza atenção mascarada autorregressiva.|
|**Self-Attention (Encoder)**|**Self-Attention (Decoder)**|No **Encoder**, a atenção é total e paralela (vê todas as palavras ao mesmo tempo). No **Decoder**, a atenção é parcial/mascarada (vê apenas o que já foi gerado para prever o próximo termo).|
|**Self-Attention**|**Encoder-Decoder Attention**|O **Self-Attention** relaciona palavras dentro do mesmo fluxo (do input no encoder ou do output no decoder). O **Encoder-Decoder Attention** conecta o processamento do input (vindo do encoder) com o fluxo de geração (no decoder).|
|**Embeddings**|**Tokens**|**Tokens** são pedaços de texto brutos que mantêm significado. **Embeddings** são a representação numérica vetorial desses tokens contendo informações semânticas e posicionais.|
|**Camada Linear**|**Camada Softmax**|A **Linear** mapeia os vetores de saída ao vocabulário total e gera pontuações brutas. A **Softmax** converte essas pontuações brutas em probabilidades reais de 0 a 100%.|

---

## Pontos importantes para prova

- **Mecanismo de Atenção como Diferencial**: É o mecanismo que permitiu a **paralelização**, superando o gargalo sequencial das RNNs e LSTMs.
- **Autorregressão e Mascaramento**: No decoder, os tokens futuros são ocultados (mascarados) durante o treinamento para forçar o modelo a prever a próxima palavra com base apenas no histórico anterior.
- **Conexões Residuais (A função do "Resgate")**: A soma do input original (sem processamento) à saída do processamento de atenção garante que a informação inicial não se dissipe ao longo de múltiplas camadas.
- **Hiperparâmetros**: Parâmetros configuráveis no treinamento que afetam o desempenho do modelo, tais como: número de camadas, número de cabeças de atenção (heads), tamanho do vocabulário e escolha de probabilidades.
- **Custos e Escala**: Modelos de grande escala como o GPT-4 utilizam trilhões de parâmetros (ex: 170 trilhões de parâmetros) e centenas de terabytes de dados. O treinamento é demorado (semanas a meses), exige infraestrutura robusta e causa impactos ambientais significativos.
- **Hugging Face**: Plataforma essencial na democratização da IA por disponibilizar repositórios de datasets e a biblioteca `Transformers` com modelos pré-treinados.
- **Multimodalidade Atual**: Embora criados para processamento de linguagem natural (PLN), os Transformers hoje atuam em visão computacional (ex: _Vision Transformer_ para processar matrizes de pixels), processamento de áudio e vídeo.
- **Diversidade de Tarefas**: Podem realizar classificação de imagens, geração de código, detecção de fraude, tradução automática, assistentes virtuais, busca semântica, correção gramatical, entre outras.

---

## Revisão rápida

1. **Entrada**: Texto \(\to\) Tokens \(\to\) Embeddings.
2. **Codificação (Encoder)**: Processamento paralelo via _Self-Attention_ (pesos contextuais) e _Feed Forward_ com conexões residuais e normalização.
3. **Decodificação (Decoder)**: Geração sequencial com _Self-Attention Mascarado_ (vê apenas o passado) e _Encoder-Decoder Attention_ (conecta com a entrada).
4. **Saída (Language Modeling Head)**: Camada Linear (pontuações do vocabulário) \(\to\) Softmax (probabilidades) \(\to\) Palavra gerada.
5. **Treinamento**: Auto-supervisionado (aprende padrões gerais e estatísticos) \(\to\) Transfer Learning (ajuste fino supervisionado para tarefas com dados rotulados).

