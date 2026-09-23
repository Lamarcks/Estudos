**Problema:** Criar uma barra de progresso horizontal para simular o carregamento dinâmico de itens na página, atualizando as dimensões de renderização do Canvas a cada 10 milissegundos e interrompendo o ciclo de atualizações automaticamente ao preencher o limite físico horizontal da tela (1280px) para evitar vazamento de memória e processamento.

**Conceito utilizado:** Loop de atualizações por temporizador assíncrono (`setInterval`), interrupção de ciclo ativo (`clearInterval`), preenchimento em tela de pixels cumulativos e variáveis de acréscimo de fator de velocidade.

**Solução:** _HTML de estrutura básica:_

```
<canvas id="progress" height="10" width="1280"></canvas>
<script src="exercicio4.js"></script>
```

_CSS de layout:_

```
#progress {
    position: fixed;
    background-color: #c4c1c1; /* Cor cinza que serve de trilha de fundo */
}
```

_JavaScript de lógica (`exercicio4.js`):_

```
var canvas = document.getElementById('progress');
var ctx = canvas.getContext('2d');

// Configurações Geométricas e Dinâmicas da Animação
var x = 0;
var y = 0;
var altura = 10;
var largura = 0;
var fator = 60; // Quantidade de pixels incrementados a cada rodada
var resolucao = 1280; // Largura do Canvas

ctx.fillStyle = "#4169E1"; // Cor Azul Royal da barra ativa definida pela equipe

function animacao() {
    // Redesenha o retângulo incrementalmente somando o fator à largura
    ctx.fillRect(x, y, largura = largura + fator, altura);

    // Condição de parada: se cobrir toda a largura, encerra o ciclo de animação
    if (largura > resolucao) {
        clearInterval(atualiza); // Destrói o processo de repetição em segundo plano
    }
}

// Inicia e executa a função de animação a cada 10 milissegundos
var atualiza = setInterval(animacao, 10);
```

**Resultado:** Uma faixa de cor azul royal preenche de forma ágil e fluida a linha cinza do topo da tela da esquerda para a direita, parando o processamento imediatamente ao tocar o limite de 1280px da largura do navegador.

**Por que essa solução funciona:** A chamada `setInterval` dispara de forma recorrente a rotina `animacao` respeitando a fração de milissegundos determinada. Ao atingir o tamanho limite parametrizado, a rotina de controle usa o método `clearInterval` para anular a referência ativa do temporizador, fechando o fluxo assíncrono.

**O que preciso aprender com esse exemplo:** Como trabalhar com temporizadores assíncronos dinâmicos e desenhar em tempo de execução para gerar animações limpas de alta performance na interface de usuário.