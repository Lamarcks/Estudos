**Problema:** No sistema de locação de veículos, mapear a estrutura de herança da classe abstrata **`Pessoa`** e suas duas subclasses especializadas **`PessoaFisica`** e **`PessoaJuridica`** para tabelas relacionais de forma a garantir desempenho nas consultas e normalização dos dados.

**Conceito utilizado:** Estratégias de mapeamento de herança para modelo relacional: **Alternativa 1 (Tabelas Compartilhadas com compartilhamento de ID)**.

**Solução:** Mapeia-se a generalização utilizando três tabelas distintas ligadas por chaves primárias compartilhadas:

1. **Tabela da Superclasse (`Pessoa`)**: Contém os atributos comuns a todos os tipos de pessoas e adiciona um **atributo discriminador** chamado `tipoPessoa` para indicar se o registro é físico ou jurídico:
    - `Pessoa (`\(\underline{\text{pessoaId}}\), nome, logradouro, numeroLogradouro, bairro, cidade, estado, cep, telefone, celular, situacao, enderecoEletronicoLogin, senhaAlfanumerica, **tipoPessoa [PF/PJ]**, demaisFK`)`.
2. **Tabela da Subclasse 1 (`PessoaFisica`)**: Não cria um ID novo autoincrementado. Utiliza o mesmo `pessoaId` (compartilhado da superclasse) como sua Chave Primária e Chave Estrangeira simultaneamente, contendo apenas os atributos exclusivos de pessoa física:
    - `PessoaFisica (`\(\underline{\text{pessoaId}}\), cpf, dataNascimento, sexo, telefoneComercial, pessoaIdJ, demaisFK`)`.
3. **Tabela da Subclasse 2 (`PessoaJuridica`)**: Segue a mesma regra, compartilhando o ID da superclasse:
    - `PessoaJuridica (`\(\underline{\text{pessoaId}}\), cnpj, inscricaoEstadual, razaoSocial, dataAberturaEmpresa, contato, desconto, demaisFK`)`.

**Resultado:** O banco de dados relacional implementa a estrutura de herança de forma altamente normalizada, evitando colunas nulas em branco e desperdício de espaço físico de disco.

**Por que essa solução funciona:** Ao compartilhar a chave primária `pessoaId` entre as tabelas pai e filho, o SGBDR garante que um registro em `PessoaFisica` corresponda exatamente ao seu cadastro de dados básicos na tabela `Pessoa`. Para recuperar as informações completas de um cliente de CPF específico, o sistema realiza uma operação de junção (`INNER JOIN`) simples entre as tabelas.

**O que preciso aprender com esse exemplo:** Existem 3 abordagens de mapeamento de generalização clássicas em provas:

1. **Tabelas Compartilhadas (Alternativa 1)**: Uma tabela para a superclasse e uma para cada subclasse, compartilhando a PK. Vantagem: Normalização máxima. Desvantagem: Exige `JOIN` para consultas.
2. **Tabelas por Subclasse (Alternativa 2)**: Elimina a tabela da superclasse, duplicando todas as colunas comuns em tabelas individuais para as subclasses. Vantagem: Sem `JOIN` para buscar uma pessoa física. Desvantagem: Perda de reuso.
3. **Tabela Única / Mesa Diretora (Alternativa 3)**: Cria uma única tabelona contendo todas as colunas do pai e dos filhos juntas. Vantagem: Velocidade extrema de consulta. Desvantagem: Geração de muitas colunas com valores nulos (_null_) para atributos que não se aplicam ao registro.
