**Problema:** Modelar a lógica do processo de **pagamento de mensalidades em atraso** em um clube social. As regras de negócio estipulam que o funcionário busca o sócio, o sistema consulta suas mensalidades devidas e, se houver pendências em atraso, deve calcular automaticamente os juros acumulados para cada parcela antes de exibi-las em tela. O sócio seleciona quais pagar (obrigatoriamente pagando as mais antigas primeiro), o atendente confirma o pagamento no sistema, que quita as parcelas e gera o recibo.

**Conceito utilizado:** **Diagrama de Sequência UML** com fragmentos combinados de **`loop`** e condições de guarda (**`[Em atraso]`**).

**Solução:** O diagrama de sequência define as interações através de duas estruturas de repetição importantes:

1. **Fase de Consulta (Loop 1)**:
    - O atendente passa o número do cartão para o controlador, que chama o método `consSocio()` no objeto `socio1:Socio`.
    - O controlador inicia o fragmento de interação `loop [Para cada mensalidade]`.
    - Dentro do loop, chama o método `consens()` (consultar mensalidade).
    - Caso a mensalidade atenda à condição de guarda **`[Em atraso]`**, o objeto da mensalidade dispara uma **mensagem reflexiva (autochamada)** chamada `calcJuros()` para atualizar o saldo devido com a multa aplicada.
2. **Fase de Pagamento (Loop 2)**:
    - O sócio escolhe as parcelas e o atendente clica em processar.
    - O controlador inicia um segundo fragmento `loop [Para cada mensalidade]`.
    - Chama o método `quitarMens()` diretamente no objeto da mensalidade.
    - Confirmados os pagamentos, o controlador aciona a mensagem de retorno na interface para emitir e imprimir o recibo físico de quitação.

**Resultado:** O fluxo temporal completo da operação bancária do clube social é detalhado com o mapeamento dinâmico correto de laços condicionais repetitivos.

**Por que essa solução funciona:** Os quadros de **fragmento combinado (`loop`)** encapsulam as mensagens envolvidas na iteração, permitindo transpor regras de programação estruturada (como estruturas `for` ou `while`) diretamente para a arquitetura visual da UML de forma limpa.

**O que preciso aprender com esse exemplo:** A **autochamada ou mensagem reflexiva** ocorre quando o objeto invoca um método interno de sua própria classe. Ela é desenhada como uma **seta em formato de U que sai da lifeline do objeto e retorna para o seu próprio foco de controle**.