**Problema:**  
Desenvolver um protótipo para um terminal de autoatendimento de cinema que sugira um filme com base na idade inserida pelo cliente e avalie se existem ingressos disponíveis.

**Conceito utilizado:**  
Estrutura condicional hierárquica e múltiplos testes condicionais de variáveis de controle em blocos independentes.

**Solução:**

```
# Solicita a idade do cliente
idade = int(input("Por favor, digite sua idade: "))

# Estrutura 1: Verifica a idade para sugestão de filmes
if idade < 12:
    print("Recomendamos o filme infantil FILME 1.")
elif 12 <= idade < 18:
    print("Recomendamos o filme adolescente FILME 2.")
else:
    print("Recomendamos o emocionante FILME 3.")

# Estrutura 2: Verifica a disponibilidade física de ingressos
quantidade_ingressos = 10  # Quantidade simulada no estoque de vendas

if quantidade_ingressos > 0:
    print("Ingressos estão disponíveis. Divirta-se no cinema!")
else:
    print("Desculpe, todos os ingressos estão esgotados para hoje.")
```

**Resultado:**  
Uma recomendação personalizada impressa em tela seguida do status imediato de possibilidade de venda do bilhete.

**Por que essa solução funciona:**  
O programa executa dois blocos de tomada de decisão separados: o primeiro bloco condicional atua sugerindo o filme mais adequado de acordo com a idade, e o segundo valida apenas a variável quantitativa de estoque de bilhetes.

**O que preciso aprender com esse exemplo:**  
Blocos de decisão sequenciais e isolados podem trabalhar em conjunto para fornecer saídas completas em fluxos de sistemas de vendas.