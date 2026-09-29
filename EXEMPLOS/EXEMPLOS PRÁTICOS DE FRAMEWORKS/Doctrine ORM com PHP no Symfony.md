**Problema:** Garantir total desacoplamento e isolamento entre as regras e modelos de negócio da aplicação e as regras físicas de infraestrutura de persistência em bancos de dados relacionais.

**Conceito utilizado:** **Data Mapper Pattern** implementado fisicamente pelo framework de persistência Doctrine ORM do Symfony.

**Solução:** Separar a entidade de negócio pura (`Produto`) da classe responsável por orquestrar e monitorar seu ciclo de persistência ativa (`EntityManager`).

1. Gerar a estrutura básica de classes de entidade:
    
    ```
    php bin/console make:entity Produto
    ```
    
2. Persistir e ler dados de forma estruturada:
    
    ```
    // Instancia uma classe pura (sem acoplamento direto de banco)
    $produto = new Produto();
    $produto->setNome('Monitor 4K');
    $produto->setPreco(1299.00);
    
    // Delega a persistência ao EntityManager gerenciador
    $entityManager->persist($produto); // Agenda a operação na memória
    $entityManager->flush();           // Executa a transação no banco físico
    
    // Consultando os registros
    $repo = $entityManager->getRepository(Produto::class);
    $produtos = $repo->findAll();
    ```
    

- **`php bin/console make:entity`:** Comando Symfony para inicializar a modelagem da entidade.
- **`$produto = new Produto()`:** Instancia um objeto simples que não interage de forma direta ou ativa com o banco.
- **`$entityManager->persist()`:** Registra o estado da instância na sessão do Doctrine.
- **`$entityManager->flush()`:** Consolida fisicamente no banco de dados todas as alterações lógicas de forma atômica e agrupada.
- **`getRepository()` e `findAll()`:** Acessa uma classe repositório isolada específica da entidade para realizar queries orientadas.

**Resultado:** Evita acoplamento direto dos objetos de domínio à persistência física. O modelo mantém-se testável e flexível a alterações arquiteturais.

**Por que essa solução funciona:** Diferente do Eloquent, as classes lógicas geradas não herdam rotinas ou conexões de persistência direta, delegando toda a comunicação e sincronização ao componente centralizado do framework (`EntityManager`).

**O que preciso aprender com esse exemplo:** O **Data Mapper** mantém entidades totalmente isoladas de implementações de persistência. Sua utilização garante conformidade com regras estritas de segurança em sistemas corporativos.