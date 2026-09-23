**Problema:**  
Renderizar e testar uma página web estática inicial de boas-vindas diretamente dentro das células do Jupyter Notebook ou do Google Colab sem depender de servidores de hospedagem dedicados ou navegadores externos.

**Conceito utilizado:**  
Strings multilinha, objetos de exibição de mídia ricos do IPython (`HTML`) e tags estruturadas de marcação web (HTML5).

**Solução:**

```
# Módulo especial para visualização de conteúdo rico no Colab
from IPython.display import HTML

# String formatada que define o esqueleto estático em HTML
html_code = """
<!DOCTYPE html>
<html>
<head>
  <title>Exemplo de Front-end com Python</title>
</head>
<body>
  <h1>Olá, mundo!</h1>
  <p>Esta é uma página web criada usando Python no Google Colab.</p>
</body>
</html>
"""

# Executa o interpretador de exibição e renderiza a tela
HTML(html_code)
```

**Resultado:**  
Visualização instantânea de um cabeçalho estilizado `<h1>` e um parágrafo de texto renderizados dentro da célula do Notebook.

**Por que essa solução funciona:**  
O módulo `IPython.display.HTML` atua de forma integrada com o navegador web do usuário, que hospeda a própria interface do Google Colab, injetando e interpretando o código HTML de forma local e segura.

**O que preciso aprender com esse exemplo:**  
Podemos testar e interagir rapidamente com códigos front-end simples utilizando strings Python e a biblioteca IPython no Colab.