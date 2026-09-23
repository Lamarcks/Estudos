**Problema:**  
Configurar e subir de forma rápida uma API de back-end em um servidor Flask e compartilhá-lo de forma pública na internet para testes externos a partir de uma máquina isolada do Google Colab.

**Conceito utilizado:**  
Rotas e mapeamento de requisições no microframework **Flask**, e criação dinâmica de túneis públicos de rede por meio da tecnologia **ngrok**.

**Solução:**

```
# Requisitos: Executar primeiro a autenticação de conta ngrok e instalar dependências
# !ngrok authtoken SEU_TOKEN_AQUI
# !pip install flask flask-ngrok

from flask import Flask
from flask_ngrok import run_with_ngrok

# Instancia a aplicação Flask básica
app = Flask(__name__)

# Integra o utilitário do ngrok para tunelamento de rede externa
run_with_ngrok(app)

# Cria o mapeamento de rota da raiz do domínio do back-end
@app.route('/')
def index():
    return 'Olá, esta é a rota principal do back-end!'

if __name__ == '__main__':
    # Inicializa o servidor local e expõe o link público temporário
    app.run()
```

**Resultado:**  
Geração de um link dinâmico público provido pelo ngrok (ex: `http://xxxx.ngrok-free.app`) que encaminha requisições web externas diretamente para o servidor local criado no Colab.

**Por que essa solução funciona:**  
O Flask inicia o servidor na porta local padrão `5000`. A biblioteca `flask-ngrok` atua capturando essa porta local e estabelecendo um túnel reverso seguro com o serviço do ngrok na nuvem, fornecendo uma URL pública que contorna bloqueios de rede corporativos.

**O que preciso aprender com esse exemplo:**  
A arquitetura web do Python permite a prototipagem ágil de back-ends robustos e a rápida validação de APIs integradas de forma simples.