
**Problema:**  
Criar um sistema dinâmico para uma academia de esportes onde o aluno informa o peso e a altura em um formulário HTML, e o JavaScript calcula o valor do IMC e exibe a classificação de saúde (Magreza, Normal, Sobrepeso ou Obesidade) diretamente na tela sem recarregar a página.

**Conceito utilizado:**  
Manipulação da árvore DOM (`getElementById`, `innerText`), escuta de eventos (`addEventListener`), funções com retorno e estruturas condicionais encadeadas (`if / else if`).

**Solução:**

1. Crie uma função pura para calcular a fórmula do IMC: \[\text{IMC} = \frac{\text{peso}}{\text{altura}^2}\].
2. Crie uma função condicional para retornar a classificação do IMC com base na tabela de referência.
3. Associe um escutador de evento de clique ao botão de cálculo para capturar os dados dos campos `<input>`, executar os cálculos e injetar o resultado nas tags de texto HTML.

```
// Captura o elemento do botão no DOM
const botaoCalcular = document.getElementById('calcular');

// 1. Função para calcular a fórmula matemática do IMC
function calcularIMC(peso, altura) {
    let valorIMC = peso / (altura * altura);
    return valorIMC.toFixed(2); // Retorna o valor arredondado para 2 casas decimais
}

// 2. Função para validar o status conforme a tabela de referência
function validarStatusIMC(valorIMC) {
    let status = '';
    if (valorIMC < 18.5) {
        status = 'Magreza';
    } else if (valorIMC >= 18.5 && valorIMC <= 24.9) {
        status = 'Normal';
    } else if (valorIMC >= 25.0 && valorIMC <= 29.9) {
        status = 'Sobrepeso';
    } else if (valorIMC >= 30.0 && valorIMC <= 39.9) {
        status = 'Obesidade';
    } else {
        status = 'Obesidade Grave';
    }
    return status;
}

// 3. Evento de clique do botão
botaoCalcular.addEventListener('click', function() {
    // Lê os valores digitados nos inputs
    let peso = document.getElementById('peso').value;
    let altura = document.getElementById('altura').value;

    // Executa as funções lógicas
    let resultadoIMC = calcularIMC(peso, altura);
    let resultadoStatus = validarStatusIMC(resultadoIMC);

    // Injeta os resultados de volta no HTML
    document.getElementById('resultado_valor_imc').innerText = resultadoIMC;
    document.getElementById('resultado_status_imc').innerText = resultadoStatus;
});
```

**Resultado:**  
Ao digitar `100` para peso e `1.89` para altura e clicar em "Calcular", o sistema exibe instantaneamente o valor `27.99` no campo de IMC e `Sobrepeso` no campo de status.

**Por que essa solução funciona:**  
A propriedade `.value` lê o conteúdo atualizado dos campos de entrada de texto no momento em que o evento de clique ocorre. O método `.innerText` altera com segurança apenas o nó de texto visível na árvore do DOM correspondente àquele `id` específico, re-renderizando a tela.

**O que preciso aprender com esse exemplo:**

- `document.getElementById('id').value` recupera a entrada do usuário em formulários.
- `document.getElementById('id').innerText` altera o texto exibido dentro de uma tag HTML.
- A separação de responsabilidades em funções menores (`calcularIMC` e `validarStatusIMC`) deixa o código mais limpo e reutilizável.
