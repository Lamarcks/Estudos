**Problema:** Uma tabela "Filho" possui atributos que descrevem o aluno, a escola que ele frequenta, a sala de aula e o professor associado. Um professor pode trabalhar em mais de uma escola e ministrar aulas em salas diferentes. As chaves candidatas compostas são concatenadas e compartilham um atributo em comum (`Nome do Filho`):

- Chave Candidata A: `{Nome do Filho, Número da Sala}`.
- Chave Candidata B: `{Nome do Filho, Nome do Professor}`. O `Nome do Professor` depende do `Número da Sala` em uma escola, mas a sala não é uma chave candidata isolada. Isso viola a integridade e gera redundâncias que a 3FN tradicional não consegue identificar.

**Conceito utilizado:** Forma Normal de Boyce-Codd (FNBC).

**Solução:** A tabela "Filho" deve ser decomposta em duas tabelas distintas para garantir que todos os determinantes sejam de fato chaves candidatas:

1. Criar a tabela `Filho` para armazenar as informações intrínsecas ao estudante:
    - `Filho` (#NomeFilho, EndereçoFilho, DataNascimento, &NumeroSala, &NomeEscola).
2. Criar a tabela `Sala` para isolar a estrutura das salas de aula e seus professores associados:
    - `Sala` (#NumeroEscola, #NumeroSala, NomeProfessor).

**Resultado:** As anomalias de chaves compostas sobrepostas são eliminadas, garantindo que qualquer alteração de professor ocorra em uma tabela de controle de salas separada.

**Por que essa solução funciona:** A FNBC é uma versão mais rígida da 3FN. Ao exigir que _todo_ determinante seja uma chave candidata, ela impede que relacionamentos funcionais entre atributos de chaves candidatas compostas diferentes causem inconsistências em nível de linha.

**O que preciso aprender com esse exemplo:** A FNBC se torna necessária apenas quando ocorrem três condições concomitantes: a entidade possui múltiplas chaves candidatas, essas chaves são compostas e elas compartilham pelo menos um atributo em comum.