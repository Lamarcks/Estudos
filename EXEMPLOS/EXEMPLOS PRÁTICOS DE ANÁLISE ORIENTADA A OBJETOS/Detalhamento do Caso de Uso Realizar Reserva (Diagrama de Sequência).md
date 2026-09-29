**Problema:** No sistema hoteleiro, detalhar visualmente a **comunicação temporal interna** que ocorre quando um hóspede realiza uma reserva. É necessário mapear que o hóspede interage com uma página web, um controlador valida os dados junto às classes de entidade (`Hospede`, `Empresa`, `TipoApartamento`), instancia uma nova `Reserva` e, opcionalmente, emite um comprovante ao final da operação.

**Conceito utilizado:** **Diagrama de Sequência UML** com uso de estereótipos de classes (`<<boundary>>`, `<<control>>`, `<<entity>>`), mensagens construtoras (`create`) e fragmentos de interação.

**Solução:** O diagrama é estruturado no eixo X com os seguintes objetos e papéis:

1. `Hospede` (Ator): Envia os dados iniciais.
2. `PaginaReserva` (Estereótipo `<<boundary>>`): Interface gráfica que recebe as mensagens do ator.
3. `ControladorReserva` (Estereótipo `<<control>>`): Gerencia a lógica do processo.
4. `reserva : Reserva` (Estereótipo `<<entity>>`): Objeto instanciado de forma dinâmica por meio da mensagem construtora `<<create>>` enviada pelo controlador.
5. `empresa : Empresa`, `hospede : Hospede` e `tipoApartamento : TipoApartamento` (`<<entity>>`): Classes persistentes que fornecem dados de apoio.

**O fluxo de mensagens ordenado no eixo Y (cronológico) é:**

1. O `Hóspede` envia a mensagem síncrona `Informa dados da reserva` para a `PaginaReserva`.
2. A interface repassa os dados chamando o método `carregarPaginaReserva()` no `ControladorReserva`.
3. O controlador dispara a mensagem construtora `create` para instanciar o objeto `reserva:Reserva`.
4. O controlador executa buscas internas de dados: `recuperarEmpresa()` no objeto `empresa`, `recuperarHospede()` no objeto `hospede` e `recuperarTipo()` no objeto `tipoApartamento`.
5. O controlador realiza validações internas condicionais através de autochamadas: `validarDataEntrada()` e `validarDataSaida()`.
6. Após a confirmação, o `Hóspede` clica em confirmar, o controlador executa `cadastrarReserva()`.
7. **Fragmento de Interação (`ref`)**: Na parte inferior do diagrama, um quadro de referência aponta para outro diagrama síncrono chamado `sd Emitir Comprovante de Reserva`.

**Resultado:** O diagrama final (conforme a _Figura 8 da Unidade 3, Aula 1_) mapeia com precisão absoluta a ordem das mensagens e a colaboração de arquitetura de software de três camadas (fronteira, controle e entidade).

**Por que essa solução funciona:** A modelagem de três camadas separa as responsabilidades: se a interface de usuário (`<<boundary>>`) mudar, a lógica de validação (`<<control>>`) e as tabelas de dados (`<<entity>>`) permanecem intactas, reduzindo custos de manutenção de software.

**O que preciso aprender com esse exemplo:** Mensagens de criação de objetos no diagrama de sequência são representadas por **linhas tracejadas com setas abertas apontando diretamente para o retângulo do objeto criado**, que é desenhado um nível abaixo das outras lifelines no eixo vertical.