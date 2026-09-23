**Problema:**  
Exibir de forma simples o comportamento dinâmico de vendas mensais de uma distribuidora de mercadorias facilitando a avaliação das metas mensais para os diretores da empresa.

**Conceito utilizado:**  
Módulo `pyplot` do Matplotlib e criação prática de gráficos de barras horizontais simples (`plt.bar`).

**Solução:**

```
import matplotlib.pyplot as plt

# Listas de dados estruturados categorizados
meses = ['Janeiro', 'Fevereiro', 'Março', 'Abril', 'Maio']
vendas =

# Cria o gráfico de barras aplicando uma cor de preenchimento realçada
plt.bar(meses, vendas, color='royalblue')

# Define rótulos informativos dos eixos
plt.xlabel('Mês')
plt.ylabel('Vendas (em unidades)')
plt.title('Relatório de Vendas Mensais')

# Apresenta a janela de plotagem
plt.show()
```

**Resultado:**  
Geração de um gráfico de barras legível e esteticamente limpo ilustrando a evolução dinâmica das vendas.

**Por que essa solução funciona:**  
A função `plt.bar()` mapeia as strings informadas na lista `meses` diretamente no eixo X em coordenadas discretas, plotando a altura correspondente das barras baseando-se nos valores numéricos da lista de vendas.

**O que preciso aprender com esse exemplo:**  
Gráficos de barras são o formato mais simples e eficaz para ilustrar análises comparativas de dados categóricos discretos ou temporais simples.
