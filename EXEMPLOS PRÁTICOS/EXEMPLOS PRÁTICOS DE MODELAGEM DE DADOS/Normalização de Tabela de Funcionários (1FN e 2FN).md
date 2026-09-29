**Problema:** A seguinte tabela "Quadro de Funcionário" não normalizada apresenta problemas de anomalia:

|Nome|Idade|Valor da Hora|Cidade|Departamento|Data de Admissão|
|:--|:--|:--|:--|:--|:--|
|Carlos Augusto|25|R$ 18,54|Curitiba|Contabilidade|15/01/2018|
|Roberto César|19|R$ 16,70|São Paulo|Produção|21/11/2017|
|Marta Maria|22|R$ 20,15|Santo André|RH|03/04/2018|

Dificuldades:

1. Não possui chave primária identificadora clara.
2. O campo `Idade` é volátil (muda anualmente, exigindo atualizações constantes).
3. O campo `Cidade` é texto livre, gerando repetição de strings e possíveis erros de digitação.
4. O campo `Departamento` mistura o tema "funcionário" com "departamento" na mesma tabela.

**Conceito utilizado:** Primeira Forma Normal (1FN) e Segunda Forma Normal (2FN).

**Solução:**

- **Passo 1: Aplicar a 1FN**:
    
    1. Criar um atributo identificador único (`#matriculaFunc`) como chave primária.
    2. Substituir o campo calculado `Idade` pelo campo atômico e imutável `dtNascimento`.
    3. Isolar o atributo não atômico `Cidade` criando a tabela auxiliar `Cidade` (`#idCidade`, `Cidade`).
    4. Relacionar as tabelas inserindo a chave estrangeira `&idCidade` na tabela de funcionários.
- **Passo 2: Aplicar a 2FN**:
    
    1. Identificar que o campo `Departamento` não depende apenas de informações do funcionário e trata de um tema à parte.
    2. Remover `Departamento` da tabela principal e criar a tabela `Departamento` (`#codDepart`, `Departamento`).
    3. Inserir a chave estrangeira `&codDepart` na tabela de funcionários.

**Resultado:** O banco de dados agora é composto por três tabelas limpas e normalizadas em conformidade com a 1FN e 2FN:

- `Cidade` (#idCidade, Cidade).
- `Departamento` (#codDepart, Departamento).
- `Funcionário` (#matriculaFunc, nome, dtNascimento, valordahora, dtadmissao, &codDepart, &idCidade).

**Por que essa solução funciona:** A decomposição elimina anomalias de atualização. Alterar o nome de um departamento ou cidade exige modificação em apenas uma linha da tabela correspondente, propagando-se automaticamente a todos os funcionários relacionados.

**O que preciso aprender com esse exemplo:** Dados mutáveis no tempo (como idade) nunca devem ser armazenados diretamente em tabelas; armazene a origem atômica (data de nascimento). O objetivo da 2FN é garantir que a tabela trate de um único tema.