**Problema:** Uma biblioteca pública precisa digitalizar o gerenciamento de seus livros, usuários e registros de transações de empréstimos. O sistema deve impedir anomalias e incoerências estruturais, como realizar o empréstimo de um livro que não existe no catálogo ou de forma associada a um leitor não cadastrado, além de evitar que livros sejam indevidamente removidos do catálogo se houver devoluções pendentes.

**Conceito utilizado:** Modelo de Banco de Dados Relacional, Chave Primária (PK), Chave Estrangeira (FK) e Integridade Referencial.

**Solução:** Mapear as entidades do sistema, especificar tabelas isoladas para Livros e Usuários, e criar uma tabela transacional intermediária conectando-as por chaves estrangeiras.

```
-- Tabela Livro com Chave Primária
CREATE TABLE Livro (
    id_livro INT PRIMARY KEY AUTO_INCREMENT, -- Garante unicidade e índice físico rápido
    titulo VARCHAR(150) NOT NULL,
    autor VARCHAR(100) NOT NULL,
    ano_publicacao INT,
    num_exemplares INT NOT NULL
);

-- Tabela Usuario com Chave Primária
CREATE TABLE Usuario (
    id_usuario INT PRIMARY KEY AUTO_INCREMENT,
    nome VARCHAR(100) NOT NULL,
    endereco VARCHAR(200),
    telefone VARCHAR(20)
);

-- Tabela de Empréstimos com as restrições de integridade referencial
CREATE TABLE Emprestimo (
    id_emprestimo INT PRIMARY KEY AUTO_INCREMENT,
    id_usuario INT, -- Chave Estrangeira vinculada
    id_livro INT,   -- Chave Estrangeira vinculada
    data_emprestimo DATE NOT NULL,
    data_devolucao_prevista DATE NOT NULL,
    -- Conecta as tabelas de forma segura impedindo orfandade
    FOREIGN KEY (id_usuario) REFERENCES Usuario(id_usuario),
    FOREIGN KEY (id_livro) REFERENCES Livro(id_livro)
);
```

**Resultado:** O sistema gerenciador de banco de dados impede cadastros falsos de empréstimos que apontem para livros ou leitores inexistentes, e bloqueia tentativas acidentais de exclusão física de registros que possuam vínculos ativos em andamento.

**Por que essa solução funciona:** As chaves estrangeiras informam de maneira explícita ao banco de dados que existe uma dependência estrutural entre os registros. O SGBD assume a responsabilidade de auditar e validar todas as ações de inserção, alteração e deleção, assegurando que as conexões lógica se mantenham intactas.

**O que preciso aprender com esse exemplo:**

- A Chave Primária (PK) identifica de maneira única e irrepetível cada linha de uma tabela.
- A Chave Estrangeira (FK) materializa os relacionamentos em nível de banco de dados.
- A integridade referencial assegura consistência e previne a corrupção lógica do banco.