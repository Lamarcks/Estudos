**Problema:** Uma universidade precisa armazenar dados cadastrais de seus professores, alunos e funcionários administrativos. Na modelagem preliminar, as três tabelas possuem campos idênticos repetidos: Nome, Endereço, RG, CPF, Data de Nascimento, Nome da Mãe e Nome do Pai. Isso gera redundância, tabelas excessivamente largas e dificulta buscas unificadas.

**Conceito utilizado:** Generalização e Especialização (Herança no modelo lógico/relacional).

**Solução:**

1. Criar uma superclasse/supertipo genérico chamado `Pessoa` que concentrará todos os atributos compartilhados:
    - `Pessoa` (#CPF, Nome, Endereço, RG, DataNascimento, NomePai, NomeMãe).
2. Criar as subclasses/subtipos especializados que herdam de `Pessoa` e contêm apenas os campos exclusivos de seu papel na instituição:
    - `Professor` (&CPF, Matricula, Salario, ValorHoraAula, QtdHorasAula).
    - `Aluno` (&CPF, DtEntrada, DtFormatura).
    - `Funcionario` (&CPF, Salario, DtAdmissao, DtDemissao).

**Resultado:** Estruturas lógicas limpas e unificadas. A herança elimina a redundância física de colunas idênticas replicadas no banco.

**Por que essa solução funciona:** A modelagem orientada a objetos (aplicada no diagrama de classes UML e traduzida no MER) permite mapear relações de "é um" (ex: um Professor _é uma_ Pessoa), facilitando que as tabelas filhas compartilhem a chave primária da tabela mãe como chave estrangeira.

**O que preciso aprender com esse exemplo:** A presença constante de atributos idênticos repetidos durante o levantamento de requisitos de tabelas distintas é o principal sinalizador de que você deve criar uma relação de generalização e especialização no seu banco de dados.