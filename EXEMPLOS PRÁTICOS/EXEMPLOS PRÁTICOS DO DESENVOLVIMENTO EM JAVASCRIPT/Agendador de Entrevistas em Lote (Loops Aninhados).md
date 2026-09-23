**Problema:** Após selecionar os candidatos adequados, a empresa necessita de uma rotina automática que ordene os nomes alfabeticamente e gere uma planilha de horários para as entrevistas no dia seguinte. Restrições do fluxo:

1. As entrevistas ocorrem das 8:00 às 11:00.
2. Cada bloco de entrevista dura exatamente 20 minutos.
3. Se a hora coincidir com horários de almoço/descanso (das 12h às 13h), o sistema deve ignorar essa iteração no agendador e prosseguir com os horários válidos.

**Conceito utilizado:** Loops aninhados, estrutura de desvio e interrupção rápida de laço (`continue`) e ordenação de vetores em formato alfabético (`sort()`).

**Solução:**

```
var hora = 8;
var minutos = 20;
var total_entrevistas = 0;
const saida = 11;

var entrevistados = [
    "João Mariano", "Adélia de Souza", "Fábio Almeida", "Carla Silva",
    "Paulo Arruda", "Leonardo Rocha", "Tiago de Lima", "Patrícia de Lima",
    "Fernanda Brito", "Maria da Conceição"
];

// 1. Organiza o array original em ordem alfabética crescente
entrevistados.sort();

// 2. Loop principal que controla a passagem das horas
for (let i = hora; i <= saida; i++) {
    // Desvio condicional: se cair na hora de almoço, pula imediatamente
    if (i == 12 || i == 13) {
        continue; // Passa para a próxima iteração do loop i ignorando o código abaixo
    }

    // Loop secundário interno que calcula e exibe os blocos de minutos
    for (let j = 0; j < 60; j = j + minutos) {
        total_entrevistas++;

        // Formata os minutos iniciais para exibir "8:00" em vez de "8:0"
        if (j == 0) {
            console.log(i + ":" + j + "0" + ":" + entrevistados[total_entrevistas - 1]);
        } else {
            console.log(i + ":" + j + ":" + entrevistados[total_entrevistas - 1]);
        }
    }
}
```

**Resultado:** No painel do console do desenvolvedor é impressa a listagem formatada dos entrevistados ordenados de A a Z com o horário associado (Ex: "8:00: Adélia de Souza", "8:20: Carla Silva", "8:40: Fábio Almeida", etc.).

**Por que essa solução funciona:** A chamada `sort()` opera modificando diretamente as referências internas do array. O loop aninhado usa a variável `i` para iterar sobre as horas e `j` sobre frações de minutos agregando de 20 em 20. O termo `continue` aborta imediatamente o ciclo atual da hora, pulando a execução daquele trecho de código específico de forma limpa.

**O que preciso aprender com esse exemplo:** Como usar loops dentro de loops para resolver problemas de matrizes multidimensionais e horários, e usar comandos de interrupção parcial como `continue`.