**Problema:**  
Demonstrar a interação inicial com o usuário por meio do console de forma legível e eficiente, capturando o nome de um estudante e gerando saudações formatadas.

**Conceito utilizado:**  
Funções de Entrada/Saída (`print` e `input`), formatadores de caracteres e interpolação literal de strings (**f-strings** reguladas pelo PEP 498).

**Solução:**

```
# Realiza a leitura do valor inserido pelo usuário
nome = input("Digite um nome: ")

# Exibição com formatador de caracteres clássico (estilo C)
print("Olá, %s, bem-vindo à disciplina de programação. Parabéns pelo seu primeiro hello world" % (nome))

# Exibição otimizada com f-string (padrão recomendado PEP 498)
print(f"{nome}, bem-vindo à disciplina de programação. Parabéns pelo seu primeiro hello world")
```

No console, se o usuário digitar "Estudante Querido", o script gerará a saída formatada de ambas as formas.

**Resultado:**  
Exibição correta da string inserida pelo usuário integrada à mensagem de boas-vindas.

**Por que essa solução funciona:**  
O comando `input()` suspende a execução até que uma string seja inserida. A _f-string_ funciona em tempo de execução avaliando expressões diretamente dentro de chaves `{}` de forma veloz.

**O que preciso aprender com esse exemplo:**  
A f-string é a abordagem mais legível, limpa e eficiente para concatenação de variáveis de texto em Python.