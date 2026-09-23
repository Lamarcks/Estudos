**Problema:**  
Dada uma lista de linguagens de programação contendo strings em formato misto de caixa alta/baixa, gerar uma nova lista contendo os mesmos termos padronizados totalmente em letras minúsculas.

**Conceito utilizado:**  
Mutabilidade de listas, métodos nativos de strings (`.lower()`) e sintaxe de **List Comprehension**.

**Solução:**

```
# Lista original heterogênea
linguagens = ["Python", "Java", "JavaScript", "C", "C#", "C++", "Swift", "Go", "Kotlin"]
print("Antes da listcomp =", linguagens)

# List Comprehension para conversão e substituição in-place
linguagens = [item.lower() for item in linguagens]

print("Depois da listcomp =", linguagens)
```

**Resultado:**  
Substituição de todos os elementos originais por suas versões padronizadas em caixa baixa.

**Por que essa solução funciona:**  
A list comprehension itera internamente em C sobre cada elemento da lista original, aplicando o método `.lower()` e montando uma nova lista em memória de forma compacta e pythônica.

**O que preciso aprender com esse exemplo:**  
A list comprehension reduz linhas de código em loops simples de mutação ou filtragem de listas de forma otimizada.