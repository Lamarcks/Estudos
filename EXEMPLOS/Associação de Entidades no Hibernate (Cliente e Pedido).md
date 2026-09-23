**Problema:** Mapear um relacionamento de "um para muitos" (onde um cliente pode realizar vários pedidos) do código para um banco de dados relacional sem criar scripts SQL manuais de criação de tabelas (`CREATE TABLE`) e restrições de chaves estrangeiras (`FOREIGN KEY`).

**Conceito utilizado:** **Mapeamento Objeto-Relacional (ORM)** declarativo via anotações da especificação JPA/Hibernate.

**Solução:** Anotar as classes de domínio `Cliente` e `Pedido` com metadados estruturados que instruem o framework sobre como criar e interligar as tabelas físicas no banco.

```
@Entity
public class Cliente {
    @Id
    @GeneratedValue
    private Long id;

    private String nome;

    @OneToMany(mappedBy = "cliente") // Um cliente para muitos pedidos
    private List<Pedido> pedidos;
}

@Entity
public class Pedido {
    @Id
    @GeneratedValue
    private Long id;

    private String descricao;

    @ManyToOne // Muitos pedidos para um único cliente
    @JoinColumn(name = "cliente_id") // Coluna que armazena a chave estrangeira
    private Cliente cliente;
}
```

- **`@Entity`:** Identifica as classes Java (`Cliente` e `Pedido`) como entidades monitoradas que correspondem a tabelas relacionais no banco de dados.
- **`@Id` e `@GeneratedValue`:** Configura as chaves primárias numéricas das tabelas com incremento automático gerenciado pelo banco.
- **`@OneToMany(mappedBy = "cliente")`:** Configura uma relação bidirecional, indicando que o mapeamento físico do vínculo é resolvido pelo atributo `cliente` dentro da classe `Pedido`.
- **`@ManyToOne` e `@JoinColumn(name = "cliente_id")`:** Define a chave estrangeira `cliente_id` na tabela física de pedidos que faz referência ao ID do respectivo cliente.

**Resultado:** Ao iniciar a aplicação com a propriedade `hibernate.hbm2ddl.auto` definida como `create` ou `update`, o Hibernate executa as instruções SQL nativas no banco, criando as tabelas estruturadas e o relacionamento físico de chave estrangeira automaticamente.

**Por que essa solução funciona:** O motor do Hibernate mapeia reflexivamente as classes anotadas e utiliza as instruções de anotação para traduzir entidades lógicas em objetos relacionais de tabelas físicas.

**O que preciso aprender com esse exemplo:** As anotações `@OneToMany` e `@ManyToOne` estabelecem a integridade referencial da aplicação. O parâmetro `mappedBy` define o lado inverso do relacionamento e evita a criação de tabelas associativas intermediárias redundantes.