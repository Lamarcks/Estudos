**Problema:**  
Coletar e validar a opinião de clientes para uma lista de 5 filmes, exigindo que a nota dada por eles esteja estritamente no intervalo de 1 a 5 estrelas e concedendo uma opção de encerramento precoce do sistema a qualquer momento pelo usuário.

**Conceito utilizado:**  
Laço iterativo determinado (`for`) contendo um laço iterativo infinito (`while True`) com condicionais internos de controle.

**Solução:**

```
filmes = ["Filme 1", "Filme 2", "Filme 3", "Filme 4", "Filme 5"]

for filme in filmes:
    while True:
        classificacao = input(f"Nota para '{filme}' de 1 a 5? (ou 0 para parar): ")

        if classificacao == '0':
            print(f"Classificação de '{filme}' interrompida.")
            break  # Encerra o loop interno

        classificacao = int(classificacao)

        if classificacao < 1 or classificacao > 5:
            print("Entrada inválida! Escolha de 1 a 5.")
        else:
            print(f"'{filme}' classificado com {classificacao} estrelas.\n")
            break  # Sai do loop interno do filme atual e passa para o próximo filme
```

**Resultado:**  
Classificação válida, em lote e resiliente a erros de digitação para cada item da lista.

**Por que essa solução funciona:**  
O loop `while True` gera uma validação obrigatória e ininterrupta. O código só progride para o próximo filme da lista externa (`for`) quando um comando de escape `break` válido é acionado no laço interno de teste.

**O que preciso aprender com esse exemplo:**  
Aninhamentos de loops são ideais para gerenciar listas onde cada item individual requer rotinas de validação de dados dinâmicos.