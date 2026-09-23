**Problema:**

- **Problema A:** Converter valores de produtos cotados em Dólar para Reais usando uma taxa fixa.
- **Problema B:** Extrair apenas os valores pares contidos em uma lista numérica de 1 a 10.

**Conceito utilizado:**  
Paradigma funcional em Python, funções `map()`, `filter()`, funções anônimas `lambda` e conversão de geradores para coleções físicas com `list()`.

**Solução:**

```
# --- Caso A: Map para transformação ---
precos_em_dolares =
taxa_de_cambio = 5.25

# Aplica a multiplicação sobre cada elemento da lista
precos_em_reais = list(map(lambda x: x * taxa_de_cambio, precos_em_dolares))
print("Preços convertidos em R$:", precos_em_reais)


# --- Caso B: Filter para seleção lógica ---
numeros =

# Seleciona apenas os elementos que retornam True no teste lógico (paridade)
numeros_pares = list(filter(lambda x: x % 2 == 0, numeros))
print("Apenas números pares filtrados:", numeros_pares)
```

**Resultado:**

- **Caso A:** `[525.0, 262.5, 393.75, 630.0]`.
- **Caso B:** ``.

**Por que essa solução funciona:**

- `map()` varre o iterável aplicando a regra lambda para computar e gerar novas saídas de tamanho idêntico ao original.
- `filter()` atua testando booleanamente cada registro, mantendo no iterável resultante apenas os valores que passaram no teste lógico da função lambda.

**O que preciso aprender com esse exemplo:**  
`map` transforma conteúdos, enquanto `filter` altera o tamanho do conjunto com base em critérios lógicos.