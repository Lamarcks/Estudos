**Problema:**  
Dada uma lista de convidados oficial e uma lista dinâmica de pessoas que já confirmaram presença, identificar com precisão quais pessoas ainda não confirmaram presença para que o organizador possa enviar lembretes direcionados.

**Conceito utilizado:**  
Combinação de estruturas de dados ordenadas (tuplas imutáveis e listas mutáveis) e filtragem por pertencimento lógica via list comprehension.

**Solução:**

```
# Tupla imutável com a listagem oficial estática de convidados
convidados = ("Alice", "Bob", "Carol", "David", "Eve")

# Lista mutável de presenças confirmadas pelo canal de atendimento
confirmados = ["Bob", "David"]

# Identifica quem está na lista oficial mas NÃO confirmou
nao_confirmados = [pessoa for pessoa in convidados if pessoa not in confirmados]

# Exibição dos resultados
print("Convidados pendentes de confirmação:")
for pessoa in nao_confirmados:
    print(pessoa)
```

**Resultado:**  
Apenas os nomes "Alice", "Carol" e "Eve" são impressos em tela como pendentes de contato.

**Por que essa solução funciona:**  
O operador `not in` realiza testes rápidos de associação lógica entre coleções. A list comprehension compila essa checagem sequencialmente sobre a tupla de convidados, montando a lista dos faltantes em apenas uma linha.

**O que preciso aprender com esse exemplo:**  
Tuplas são recomendadas para listas estáticas de dados fixos (ex: lista oficial inalterável), enquanto listas e compreensões auxiliam em lógicas dinâmicas de comparação.