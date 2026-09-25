**Problema:**  
Refatorar o processo de cálculo de notas escolares combinando funções parametrizadas para o cálculo de médias e funções anônimas rápidas para arredondamento das notas calculadas.

**Conceito utilizado:**  
Integração de funções nomeadas (`def`), funções anônimas de única instrução (`lambda`), funções nativas (`sum()`, `len()`, `round()`) e expressões condicionais ternárias.

**Solução:**

```
# Lista de notas dos estudantes
notas = [7.5, 8.0, 6.5, 9.0, 7.0]

# Função regular nomeada para calcular a média
def calcular_media(lista_notas):
    total = sum(lista_notas)
    media = total / len(lista_notas)
    return media

# Expressão Lambda para arredondar o valor resultante para duas casas
arredondar_media = lambda val: round(val, 2)

# Execução do pipeline de dados
media_bruta = calcular_media(notas)
media_final = arredondar_media(media_bruta)

# Atribuição da situação final usando um operador ternário em Python
situacao = "Aprovado" if media_final >= 7 else "Reprovado"

print(f"Notas: {notas}")
print(f"Média Arredondada: {media_final}")
print(f"Situação: {situacao}")
```

**Resultado:**  
Arredondamento preciso e classificação concisa da nota calculada.

**Por que essa solução funciona:**  
O Python combina funções perfeitamente pois trata funções como objetos de primeira classe. A expressão `lambda` cria dinamicamente uma função anônima de escopo reduzido para cálculos pontuais, sem poluir a tabela de símbolos de funções do programa.

**O que preciso aprender com esse exemplo:**  
A combinação de funções nomeadas com lambdas permite construir estruturas concisas, legíveis e altamente eficientes para análise de dados e processamento aritmético simples.