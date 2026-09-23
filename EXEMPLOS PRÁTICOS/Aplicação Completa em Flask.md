**Problema:** Desenvolver um protótipo leve e modular que receba novos nomes enviados dinamicamente por formulários em HTML e mostre os valores acumulados em tela.

**Conceito utilizado:** Roteamento dinâmico e microframework **Flask** com o interpretador de templates **Jinja2**.

**Solução:** Montar uma classe lúdica Flask contendo tratamento de vetores e mapear rotas capturando dados enviados através de requisições POST.

```
from flask import Flask, render_template, request
app = Flask(__name__)
nomes = []

@app.route('/', methods=['GET', 'POST'])
def index():
    if request.method == 'POST':
        nomes.append(request.form['nome']) # Captura o dado do formulário HTML
    return render_template('index.html', nomes=nomes) # Renderiza dinamicamente
```

- **`@app.route('/', methods=['GET', 'POST'])`:** Mapeia a URL raiz do projeto indicando que o método index processa requisições de leitura (GET) e de envio (POST).
- **`request.form['nome']`:** Propriedade que intercepta e captura os dados enviados via formulários HTML lógicos em tela.
- **`render_template('index.html', ...)`:** Aciona o motor Jinja2 para ler a página `index.html` e injetar nela dinamicamente a lista de dados atualizada de nomes lúdicos.

**Resultado:** Um sistema simples e ágil que grava novos nomes e os renderiza na tela de visualização sem códigos desnecessários e configurações pesadas.

**Por que essa solução funciona:** O Flask intercepta os cabeçalhos de rede do protocolo HTTP e delega de forma direta o tratamento das requisições para as rotinas lógicas mapeadas em Python.

**O que preciso aprender com esse exemplo:** O microframework **Flask** é excelente para projetos minimalistas, flexíveis, e APIs rápidas por não impor restrições ou estruturas rígidas.