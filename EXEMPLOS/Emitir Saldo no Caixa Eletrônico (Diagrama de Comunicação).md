**Problema:** Elaborar um diagrama de interação com foco estrutural que represente o caso de uso **"Emitir Saldo"** em um caixa eletrônico (ATM). O fluxo prevê que o cliente insere o cartão, digita a senha, o sistema valida a conta bancária correspondente e apresenta o saldo na interface.

**Conceito utilizado:** **Diagrama de Comunicação UML** (antigo diagrama de colaboração) com numeração sequencial obrigatória, vínculos físicos e estereótipos.

**Solução:** A estrutura é organizada mapeando os objetos participantes conectados por linhas de vínculos:

1. **Atores e Lifelines**:
    - `Cliente` (Ator).
    - `VisaoEmitirSaldo` (Fronteira - `<<boundary>>`): Interface física da tela.
    - `ControleEmitirSaldo` (Controle - `<<control>>`): Gerenciador da operação de consulta.
    - `comum1 : ContaComum` (Entidade - `<<entity>>`): Repositório físico dos dados bancários.
2. **Numeração de Mensagens Sequenciais (eixo Y lido pela ordem numérica)**:
    - `1: Inserir cartão da conta` \(\rightarrow\) (Do `Cliente` para `VisaoEmitirSaldo`).
    - `1.1: Número da conta informado` \(\rightarrow\) (Da fronteira para o controle).
    - `1.2: consultarConta(long)` \(\rightarrow\) (Do controle para o objeto `ContaComum`).
    - `1.3: verdadeiro: int` \(\rightarrow\) (Mensagem de retorno do banco para o controle, indicando que a conta existe).
    - `1.4: Solicitar senha` \(\rightarrow\) (Mensagem de retorno do controle para a fronteira para pedir a senha ao cliente).
    - `2: Informar senha` \(\rightarrow\) (Do `Cliente` para a fronteira).
    - `2.1: Senha informada` \(\rightarrow\) (Da fronteira para o controle).
    - `2.2: validarSenha(int)` \(\rightarrow\) (Do controle para `ContaComum`).
    - `2.3: verdadeiro: int` \(\rightarrow\) (Mensagem de retorno com a validação positiva).
    - `2.4: emitirSaldo()` \(\rightarrow\) (O controle executa a operação interna no objeto `ContaComum`).
    - `2.5: saldo: double` \(\rightarrow\) (Retorno do valor do saldo para o controle).
    - `2.6: Apresentar saldo` \(\rightarrow\) (Do controle para a fronteira exibir em tela).

**Resultado:** Um diagrama de colaboração estruturado e compacto (conforme a _Figura 7 da Unidade 3, Aula 4_), que usa setas direcionais desenhadas ao lado dos rótulos numéricos das mensagens para indicar o sentido da transmissão de dados.

**Por que essa solução funciona:** Como não há escala de tempo vertical, a **numeração composta obrigatória (ex: 1.1, 1.2)** é a única forma de garantir que o programador compreenda exatamente a ordem lógica que as chamadas de métodos de sistemas devem seguir no código fonte.

**O que preciso aprender com esse exemplo:** O diagrama de comunicação **não suporta quadros de fragmentos compostos (como alt, opt, loop)**. Para representar loops ou retornos no diagrama de comunicação, utilizam-se condições de guarda entre colchetes diretamente nos rótulos de mensagens numeradas.