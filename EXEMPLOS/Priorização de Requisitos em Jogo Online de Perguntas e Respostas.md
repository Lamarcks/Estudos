**Problema:** Durante o planejamento de escopo de um jogo online de perguntas e respostas voltado ao estudo para concursos, a equipe de TI identificou dezenas de funcionalidades. Com prazo e orçamento apertados, como determinar cientificamente o que deve ser programado na primeira versão e o que pode ser adiado ou descartado?

**Conceito utilizado:**

- **Tríade de Priorização de Requisitos**: _Essencial_, _Importante_ e _Desejável_.

**Solução:** A equipe analisou cada requisito técnico com base na necessidade operacional:

- **Requisitos Essenciais** (Vitam a completude; sem eles, o sistema não roda ou não pode ser implantado):
    - _Exemplo_: "O jogador deverá realizar um cadastro antes de jogar, criando apelido, senha e escolhendo um avatar".
    - _Exemplo_: "O aluno só pode acessar uma disciplina/fase se estiver matriculado nela".
- **Requisitos Importantes** (São muito relevantes, mas não impedem a entrega do software funcional; podem ser implantados em segundo plano):
    - _Exemplo_: "Criptografia de senhas no sistema acadêmico" (O sistema roda sem criptografia inicialmente, mas precisa dela para ter segurança aceitável no mercado).
- **Requisitos Desejáveis** (São opcionais; podem ser facilmente postergados ou descartados caso o cronograma sofra atrasos):
    - _Exemplo_: "Contagem do tempo exato que o aluno/jogador permaneceu logado no semestre".

**Resultado:** O jogo pôde ser lançado no prazo de forma simplificada e segura, com novos recursos importantes (criptografia) e desejáveis (cronômetro) sendo agregados em incrementos de manutenção subsequentes.

**Por que essa solução funciona:** Permite focar 100% da força de trabalho técnica no núcleo de valor do sistema (_Minimum Viable Product_ - MVP), evitando atrasos catastróficos decorrentes de excesso de refinamento em funcionalidades acessórias.

**O que preciso aprender com esse exemplo:** Priorizar requisitos protege a viabilidade econômica do projeto. Lembre-se: **Essencial** é vital para o sistema funcionar; **Importante** é necessário para a qualidade/segurança futura; **Desejável** é opcional e descartável sob estresse de tempo.