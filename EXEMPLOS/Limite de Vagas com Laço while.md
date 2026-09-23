**Problema:** A empresa do processo seletivo deseja limitar e controlar a entrada de dados do sistema para, no máximo, 10 inserções de candidatos na aplicação. Quando chegar a essa marca de 10 rodadas, o sistema deve registrar as notas, notificar o usuário que o limite foi atingido e parar de forma definitiva.

**Conceito utilizado:** Estruturas de laço de repetição baseadas em condições de parada prévias (`while`), variáveis acumuladoras e conversão para dados de ponto flutuante (`parseFloat`).

**Solução:**

```
let nota, conceito;
let count = 1; // Variável de controle do contador iniciada em 1

// Executa o bloco de código repetidamente até que o contador passe de 10
while (count <= 10) {
    nota = parseFloat(prompt("Informe a nota do estudante: "));
    if (nota) {
        if ((nota <= 10) && (nota >= 8)) {
            console.log('Conceito A');
        }
        if ((nota < 8) && (nota >= 5)) {
            console.log('Conceito B');
        }
    } else {
        console.log('Você precisa se dedicar um pouco mais');
    }

    count++; // Incrementa a variável para avançar o estado do laço
}
```

**Resultado:** O navegador abre uma caixa de entrada pedindo a nota do candidato consecutivamente. Ao processar exatamente 10 registros, a aplicação cessa seu processamento espontaneamente.

**Por que essa solução funciona:** O comando `while` testa a validade lógica de `count <= 10` antes do início de cada ciclo. O incremento do contador (`count++`) garante que a expressão eventualmente se torne falsa, terminando o loop e evitando um travamento por loop infinito.

**O que preciso aprender com esse exemplo:** Como usar variáveis contadoras para criar ciclos finitos de repetição condicional e validar dados digitados dinamicamente via `prompt`.