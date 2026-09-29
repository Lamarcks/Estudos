**Problema:**  
Processar repetidamente números digitados pelo usuário, exibindo se cada um é par ou ímpar, encerrando a execução do programa apenas quando o dígito `0` for inserido.

**Conceito utilizado:**  
Laço condicional indeterminado (`while`) controlado por valor de sentinela e operador aritmético módulo (`%`).

**Solução:**

```
numero = int(input("Insira um número (ou 0 para sair): "))

while numero != 0:
    if numero % 2 == 0:
        print(f"O número {numero} é par.")
    else:
        print(f"O número {numero} é ímpar.")

    # Solicita novamente a entrada do usuário para atualizar a variável de controle
    numero = int(input("Insira o próximo número (ou 0 para sair): "))
```

**Resultado:**  
Classificação em lote e em tempo real até que o comando de parada (`0`) finalize a execução.

**Por que essa solução funciona:**  
O comando `while` testa a condição lógica antes de cada ciclo. O valor `0` altera a condição de teste para falsa (`0 != 0` resulta em `False`), finalizando a estrutura iterativa.

**O que preciso aprender com esse exemplo:**  
Em loops baseados em sentinelas de entrada, a variável de controle deve ser reavaliada no fim do bloco interno do loop para evitar loops infinitos.