**Problema:**  
Demonstrar o funcionamento prático de geradores de sequências e de comandos de desvio de execução para otimizar interações em laços.

- **Subproblema A:** Interromper um loop assim que o primeiro número par for identificado em um intervalo numérico.
- **Subproblema B:** Imprimir os números de 1 a 10 pulando apenas um valor específico.

**Conceito utilizado:**  
Sintaxe do gerador `range()`, diretrizes de controle de fluxo `break` (interrupção total) e `continue` (pular ciclo de itração).

**Solução:**

```
# --- Caso A: Uso do Break ---
print("Buscando o primeiro número par:")
for numero in range(1, 11):
    if numero % 2 == 0:
        print("O primeiro número par encontrado é:", numero)
        break  # Interrompe o loop imediatamente

# --- Caso B: Uso do Continue ---
print("\nImprimindo números de 1 a 10 (excluindo o 5):")
for numero in range(1, 11):
    if numero == 5:
        continue  # Abandona a iteração atual e passa para o próximo número
    print(numero)
```

**Resultado:**

- **Caso A:** Imprime apenas "O primeiro número par encontrado é: 2".
- **Caso B:** Imprime a sequência de 1 a 10 omitindo o número 5.

**Por que essa solução funciona:**  
O comando `break` força a saída do escopo interno do bloco de loop imediatamente. O `continue` aborta as linhas de código abaixo dele na iteração corrente, retornando o ponteiro de execução ao início do laço para avaliar o próximo valor.

**O que preciso aprender com esse exemplo:**

- `break` serve para paradas antecipadas quando o objetivo do laço é alcançado (busca concluída).
- `continue` serve para ignorar dados indesejados sem quebrar a execução completa da lista.