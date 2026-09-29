**Problema:** Mapear e classificar as demandas de um sistema informatizado de gerenciamento de biblioteca, distinguindo claramente entre as ações lógicas específicas que o sistema deve executar e as restrições ou qualidades gerais que se aplicam a todo o produto.

**Conceito utilizado:** **Requisitos Funcionais (RF)** (comportamentos e ações de entrada/saída) versus **Requisitos Não Funcionais (RNF)** (propriedades emergentes, restrições e atributos de qualidade global).

**Solução:** Os requisitos levantados para o sistema de biblioteca são analisados individualmente e classificados de acordo com sua finalidade:

1. **Requisitos Funcionais (RF)**:
    - _Pesquisa de livros_: Permitir que os usuários pesquisem livros por título, autor ou código ISBN.
    - _Adição/Remoção de livros_: Permitir que os bibliotecários adicionem, removam ou atualizem informações de livros no banco de dados.
    - _Notificações_: Enviar uma notificação automática por e-mail aos usuários quando um livro reservado estiver disponível.
    - _Registro de movimentação_: Manter um registro histórico de todas as transações de empréstimo e devolução de livros.
    - _Emissão de relatórios_: Gerar relatórios mensais de atividade da biblioteca, incluindo estatísticas de movimentação e reservas.
2. **Requisitos Não Funcionais (RNF)**:
    - _Privacidade e Segurança_: Garantir a privacidade dos dados pessoais dos usuários em conformidade com as normas legais de proteção de dados vigentes.
    - _Tempo de Resposta (Desempenho)_: O tempo de resposta para qualquer pesquisa de livro não deve exceder dois segundos.
    - _Compatibilidade (Portabilidade)_: O sistema deve ser totalmente acessível através dos navegadores web mais populares (Chrome, Firefox, Safari).
    - _Escalabilidade (Capacidade)_: O sistema deve ser capaz de suportar até 1.000 usuários simultâneos sem sofrer degradação de performance.
    - _Usabilidade_: O design da interface do usuário deve ser intuitivo, amigável e acessível para todos os tipos de usuários.

**Resultado:** Obtém-se uma especificação de Requisitos clara e sem ambiguidades, servindo de roteiro estável tanto para a equipe de programadores (que sabe exatamente quais telas e fluxos de banco de dados criar) quanto para a equipe de garantia de qualidade.

**Por que essa solução funciona:** A solução funciona porque estabelece uma separação lógica e quantificável. Classificar o "o que" o sistema faz (funcional) de forma separada de "como" ele deve operar sob restrições físicas (não funcional) evita que propriedades globais e críticas (como desempenho ou usabilidade) sejam tratadas como meros detalhes secundários no final do ciclo de desenvolvimento.

**O que preciso aprender com esse exemplo:** Em exames, lembre-se de que os requisitos funcionais referem-se a ações lógicas diretas, enquanto os requisitos não funcionais especificam características sistêmicas amplas (velocidade, segurança, capacidade, compatibilidade). Falhar em um RNF (como tempo de resposta ou privacidade de dados) costuma ser muito mais prejudicial e catastrófico para a viabilidade do produto do que falhas em funcionalidades individuais.