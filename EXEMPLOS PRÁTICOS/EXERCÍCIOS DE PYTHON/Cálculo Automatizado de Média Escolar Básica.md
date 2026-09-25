**Problema:**  
Um docente necessita automatizar e processar o cálculo da média final das notas de seus estudantes e exibir imediatamente se o aluno está "Aprovado" ou "Reprovado" com base em uma nota de corte.

**Conceito utilizado:**  
Coerção de tipos (`int()`), operadores aritméticos, variáveis e estruturas condicionais relacionais simples (`if` e `else`).

**Solução:**

```
# Captura as notas e as converte de string para tipo inteiro
Nota_1 = int(input("Digite a Nota 1: "))
Nota_2 = int(input("Digite a Nota 2: "))
Nota_3 = int(input("Digite a Nota 3: "))
Nota_4 = int(input("Digite a Nota 4: "))

# Calcula a média aritmética das quatro notas inseridas
media = (Nota_1 + Nota_2 + Nota_3 + Nota_4) / 4

# Condição para a aprovação do aluno
if media >= 6:
    situacao = "Aprovado"
else:
    situacao = "Reprovado"

# Apresenta a média calculada e a respectiva situação final
print(f"Média: {media}")
print(f"Situação: {situacao}")
```

**Resultado:**  
Cálculo aritmético exato e classificação booleana automática do desempenho discente.

**Por que essa solução funciona:**  
Por padrão, `input()` coleta dados no formato `str` (texto). A função `int()` realiza a coerção explícita de tipos, habilitando cálculos matemáticos legítimos sobre os valores numéricos coletados.

**O que preciso aprender com esse exemplo:**  
Sem a coerção explícita (`int()` ou `float()`), a execução aritmética resultará em falhas de execução ou concatenação incorreta de strings.