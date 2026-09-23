**Problema:**  
Treinar um modelo matemático simples que aprenda a mapear uma relação linear direta entre dados numéricos de entrada e saída, prevendo um novo valor com base no padrão identificado.

**Conceito utilizado:**  
Estruturas de modelos sequenciais, camadas densas de rede (`Dense`), otimizadores estocásticos (`sgd`), erros quadráticos médios (`loss='mean_squared_error'`) e biblioteca de processamento tensorial **TensorFlow**.

**Solução:**

```
import tensorflow as tf
from tensorflow.keras.models import Sequential
from tensorflow.keras.layers import Dense

# Dados de Treinamento (X_train representará a entrada e y_train a saída esperada)
X_train = tf.constant([[1.0], [2.0], [3.0], [4.0]])
y_train = tf.constant([[2.0], [4.0], [6.0], [8.0]])  # Relação linear y = 2x

# Inicializa o Modelo Sequencial
model = Sequential()

# Adiciona uma camada com um único neurônio de entrada e saída
model.add(Dense(units=1, input_shape=(1,)))

# Compila parametrizando o otimizador SGD e o erro quadrático
model.compile(optimizer='sgd', loss='mean_squared_error')

# Executa o ajuste do algoritmo (treinamento) por 1000 épocas
model.fit(X_train, y_train, epochs=1000, verbose=0)

# Previsão lógica para um novo dado não visto anteriormente (5.0)
X_new = tf.constant([[5.0]])
prediction = model.predict(X_new)

print("Previsão do modelo supervisionado para 5.0 (Esperado próximo a 10):", prediction)
```

**Resultado:**  
O modelo prevê um valor extremamente próximo a `10.0` de forma autônoma após processar os parâmetros.

**Por que essa solução funciona:**  
A cada época de treinamento, o TensorFlow processa os erros gerados comparando os resultados calculados com as saídas reais, ajustando os pesos internos por meio do gradiente descendente stocástico (`sgd`) para reduzir a perda quadrática média total.

**O que preciso aprender com esse exemplo:**  
O aprendizado supervisionado mapeia padrões matemáticos entre entradas e saídas reais utilizando dados previamente rotulados para prever cenários futuros.