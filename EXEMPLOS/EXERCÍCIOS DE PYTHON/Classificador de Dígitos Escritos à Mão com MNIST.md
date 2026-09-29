**Problema:**  
Construir um classificador de imagens capaz de identificar de forma automatizada dígitos manuscritos (de 0 a 9) com base em matrizes bidimensionais de pixels de imagem de teste.

**Conceito utilizado:**  
Normalização vetorial de escala de pixels, vetorização de matrizes bidimensionais (`Flatten`), camadas neurais totalmente conectadas, regularização para prevenção de overfitting (`Dropout`), distribuição de probabilidades multiclasse (`softmax`) e banco de dados de referência acadêmica **MNIST**.

**Solução:**

```
import tensorflow as tf

# Passo 1: Importa e carrega o banco de imagens MNIST de dígitos manuscritos
mnist = tf.keras.datasets.mnist
(x_train, y_train), (x_test, y_test) = mnist.load_data()

# Passo 2: Normalização dos pixels da imagem para a escala de 0.0 a 1.0
x_train, x_test = x_train / 255.0, x_test / 255.0

# Passo 3: Criação da arquitetura da rede neural profunda
model = tf.keras.models.Sequential([
  # Achata a imagem bidimensional (matriz 28x28) em um vetor unidimensional de 784 pixels
  tf.keras.layers.Flatten(input_shape=(28, 28)),
  # Camada interna densa com ativação de limiar ReLU
  tf.keras.layers.Dense(128, activation='relu'),
  # Desativa aleatoriamente 20% dos neurônios para evitar vício de memorização
  tf.keras.layers.Dropout(0.2),
  # Saída com 10 neurônios gerando probabilidades de classificação unificada (softmax)
  tf.keras.layers.Dense(10, activation='softmax')
])

# Passo 4: Compilação parametrizada da perda multiclasse
model.compile(optimizer='adam',
              loss='sparse_categorical_crossentropy',
              metrics=['accuracy'])

# Passo 5: Treinamento por 5 épocas
model.fit(x_train, y_train, epochs=5)

# Passo 6: Avaliação de desempenho nos dados não vistos de testes
print("\n--- Avaliação de Precisão no Conjunto de Teste ---")
model.evaluate(x_test, y_test)
```

**Resultado:**  
Treinamento rápido da rede neural com acurácia de classificação no conjunto de teste superior a 95%.

**Por que essa solução funciona:**

- A camada `Flatten` transforma a estrutura de dados espacial (imagem 28x28 pixels) em formato linear compatível com as camadas densas.
- O neurônio `Dropout` força a rede a aprender caminhos de pesos alternativos, evitando vício de overfitting.
- A função `softmax` normaliza as saídas para que somem 1.0, gerando uma distribuição probabilística real para cada uma das 10 classes de dígitos.

**O que preciso aprender com esse exemplo:**  
O pipeline de classificação de imagem do TensorFlow permite construir modelos de classificação multiclasses rápidos, precisos e com excelente capacidade de generalização.