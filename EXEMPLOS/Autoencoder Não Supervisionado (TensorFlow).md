**Problema:**  
Treinar um modelo matemático para aprender a comprimir e reconstruir dados brutos de entrada sem a utilização de rótulos ou classificações prévias.

**Conceito utilizado:**  
Modelagem não supervisionada, camadas de input/output, processador de arquitetura funcional de modelo de codificação e reconstrução (**Autoencoder**).

**Solução:**

```
import tensorflow as tf
from tensorflow.keras.layers import Input, Dense
from tensorflow.keras.models import Model

# Dados brutos de teste sem rótulo ou indicação de classe correspondente
X_unsupervised = tf.constant([[1.0, 2.0], [2.0, 3.0], [3.0, 4.0], [4.0, 5.0]])

# Define a camada de entrada para processar vetores bidimensionais
input_layer = Input(shape=(2,))

# Camada Codificadora: Reduz a dimensionalidade de 2 valores para 1 valor comprimido
encoded = Dense(units=1)(input_layer)

# Camada Decodificadora: Reconstrói o vetor original contendo 2 valores
decoded = Dense(units=2)(encoded)

# Cria e compila o Autoencoder Funcional
autoencoder = Model(inputs=input_layer, outputs=decoded)
autoencoder.compile(optimizer='adam', loss='mean_squared_error')

# Treinamento não supervisionado (a entrada e a saída desejada são idênticas)
autoencoder.fit(X_unsupervised, X_unsupervised, epochs=1000, verbose=0)

# Previsão e reconstrução de dados
prediction_unsupervised = autoencoder.predict(X_unsupervised)
print("Dados reconstituídos pelo Autoencoder:")
print(prediction_unsupervised)
```

**Resultado:**  
O modelo reconstrói os vetores de entrada tentando preservar ao máximo as correlações intrínsecas identificadas nos dados brutos originais.

**Por que essa solução funciona:**  
Ao tentar comprimir a entrada em uma dimensão menor (gargalo de representação) e depois reconstruí-la na dimensão original, o modelo é forçado a identificar as principais características e estruturas comuns presentes nos dados de entrada.

**O que preciso aprender com esse exemplo:**  
O aprendizado não supervisionado foca em estruturar, agrupar ou reconstruir conjuntos de dados brutos sem depender de marcações ou labels previamente conhecidos.
