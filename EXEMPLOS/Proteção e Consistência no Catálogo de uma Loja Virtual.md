**Problema:** Impedir inconsistências financeiras graves em um catálogo, tais como registrar ou atualizar o preço de um produto com valores negativos ou zerados, e evitar que a quantidade do estoque seja corrompida com números negativos.

**Conceito utilizado:** Encapsulamento estrito (atributos privados com métodos modificadores controlados) e inicialização via construtor.

**Solução:** Definir variáveis de instância como privadas (`private`) para restringir manipulações livres e introduzir filtros lógicos de verificação de limites condicionais dentro dos métodos _setters_.

```
public class Produto {
    // Atributos protegidos de acesso direto externo
    private String nome;
    private double preco;
    private int quantidade;

    // Construtor obriga a especificação de estado inicial completo na instanciação
    public Produto(String nome, double preco, int quantidade) {
        this.nome = nome;
        this.preco = preco;
        this.quantidade = quantidade;
    }

    public String getNome() { return nome; }
    public double getPreco() { return preco; }
    public int getQuantidade() { return quantidade; }

    // Validação de segurança obrigatória para o preço
    public void setPreco(double preco) {
        if (preco > 0) {
            this.preco = preco;
        }
    }

    // Validação de segurança obrigatória para o estoque
    public void setQuantidade(int quantidade) {
        if (quantidade >= 0) {
            this.quantidade = quantidade;
        }
    }

    public void exibirDetalhes() {
        System.out.println("Produto: " + nome + " | Preço: R$ " + preco + " | Estoque: " + quantidade);
    }
}
```

**Resultado:** Se tentarmos passar valores inadequados através do comando `produto.setPreco(-50.0)`, o estado interno do objeto permanece inalterado e protegido.

**Por que essa solução funciona:** A restrição de visibilidade bloqueia qualquer manipulação por atribuição direta, como `produto.preco = -10.0`. O objeto só pode sofrer alterações de dados através de seus métodos acessores públicos, que aplicam validações rígidas antes de autorizar a gravação do valor na memória física.

**O que preciso aprender com esse exemplo:**

- Validações em métodos modificadores (_setters_) e construtores garantem a consistência e a integridade de dados e objetos.