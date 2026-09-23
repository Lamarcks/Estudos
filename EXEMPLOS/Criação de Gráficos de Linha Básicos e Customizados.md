**Problema:**  
Plotar e configurar visualmente a curva de dados abstratos estabelecendo o fluxo das coordenadas nos eixos para análises rápidas no console.

**Conceito utilizado:**  
Biblioteca `matplotlib`, estilo de desenvolvimento funcional via módulo `pyplot`, customização de títulos de eixos e geração de dados sintéticos por meio de amostragem dinâmica com `random.sample`.

**Solução:**

```
import matplotlib.pyplot as plt
import random

# Geração de 20 números aleatórios de teste no intervalo de 0 a 100
dados1 = random.sample(range(100), k=20)
dados2 = random.sample(range(100), k=20)

# pyplot monta e coordena a figura e as eixos cartesianos
plt.plot(dados1, dados2)

# Adiciona legendas de controle e cabeçalhos visuais
plt.xlabel('Eixo X')
plt.ylabel('Eixo Y')
plt.title('Gráfico Gerado com Amostragem Aleatória')

# Renderiza a interface do gráfico criado
plt.show()
```

**Resultado:**  
Geração visual da plotagem cartesianas com todas as legendas e marcadores de dados bem organizados nos eixos.

**Por que essa solução funciona:**  
O módulo `pyplot` encapsula o gerenciamento de chamadas estáticas. Ele cria as figuras matemáticas em nível de back-end gráfico renderizando o plano de desenho e os eixos automaticamente ao invocar o método de plotagem `.plot()`.

**O que preciso aprender com esse exemplo:**  
O Matplotlib serve como a biblioteca principal de infraestrutura gráfica em Python, ideal para análises estatísticas e apresentações acadêmicas.