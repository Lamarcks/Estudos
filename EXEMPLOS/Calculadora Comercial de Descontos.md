**Problema:**  
Desenvolver um programa comercial para ajudar os vendedores de uma loja a computarem o valor final de uma venda, validando se o percentual de desconto inserido está estritamente no intervalo aceitável de 0% a 100%.

**Conceito utilizado:**  
Estrutura de decisão lógica baseada em testes booleanos com coerção para ponto flutuante (`float`).

**Solução:**

```
# Captura o valor bruto do produto e o percentual de desconto concedido
valor_produto = float(input("Digite o valor do produto: R$ "))
percentual_desconto = float(input("Digite o percentual de desconto (0-100): "))

# Valida se os limites do desconto são aceitáveis
if percentual_desconto < 0 or percentual_desconto > 100:
    print("Erro: O percentual de desconto deve estar contido entre 0% e 100%!")
else:
    # Realiza as operações matemáticas lógicas
    desconto = valor_produto * (percentual_desconto / 100)
    valor_final = valor_produto - desconto

    print(f"Valor com desconto: R$ {valor_final:.2f}")
```

**Resultado:**  
Cálculo confiável do valor comercial final ou tratamento de erro caso as regras sejam violadas.

**Por que essa solução funciona:**  
O operador condicional composto `or` valida se qualquer um dos extremos inválidos foi alcançado. Se ambas as sentenças inválidas forem falsas, a execução avança para o bloco lógico seguro do `else`.

**O que preciso aprender com esse exemplo:**  
Verificações rigorosas de dados de entrada (`input`) garantem a estabilidade das aplicações em ambientes corporativos reais.