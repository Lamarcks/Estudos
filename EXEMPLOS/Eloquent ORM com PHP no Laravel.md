**Problema:** Persistir e ler dados de produtos em um banco relacional utilizando PHP de forma intuitiva, sem a necessidade de escrever queries manuais em arquivos PHP de controle.

**Conceito utilizado:** **Active Record Pattern** implementado nativamente através do Eloquent ORM do framework Laravel.

**Solução:** Gerar o arquivo de migração do banco de dados e o modelo estendido correspondente via linha de comando, e utilizar chamadas nativas de objetos para manipulação dos dados.

1. Criar o modelo e o arquivo de migração estruturado via terminal CLI:
    
    ```
    php artisan make:model Produto -m
    ```
    
2. Definir a estrutura lógicas de colunas no arquivo de migração gerado:
    
    ```
    $table->string('nome');
    $table->decimal('preco', 8, 2);
    ```
    
3. Persistir e obter dados diretamente via classe modelo:
    
    ```
    // Inserindo dados
    Produto::create(['nome' => 'Cadeira Gamer', 'preco' => 849.90]);
    
    // Buscando todos os dados
    $produtos = Produto::all();
    ```
    

- **`php artisan make:model Produto -m`:** Comando CLI que gera o modelo PHP e, através da flag `-m`, cria o arquivo de migração correspondente.
- **`$table->string` e `$table->decimal`:** Define colunas físicas na tabela do banco relacional via código orientado a objetos.
- **`Produto::create()`:** Método do Eloquent que executa a instrução `INSERT` no banco de dados mapeando os valores do vetor.
- **`Produto::all()`:** Executa um `SELECT *` implícito sob a tabela produtos e mapeia o resultado para uma coleção de objetos Java/PHP.

**Resultado:** O desenvolvedor gerencia registros de banco de dados diretamente através de classes modelo nativas do PHP de forma simplificada e orientada a objetos.

**Por que essa solução funciona:** O Eloquent mapeia as propriedades dinamicamente com base nas convenções lógicas de nomes de tabelas (uma classe `Produto` busca automaticamente a tabela pluralizada `produtos`).

**O que preciso aprender com esse exemplo:** O padrão **Active Record** une o mapeamento aos registros do banco diretamente no modelo de domínio, proporcionando uma manipulação ágil dos dados com métodos encadeados.