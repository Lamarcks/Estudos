**Problema:** Uma universidade precisa organizar o controle de financiamento de pesquisas científicas. No modelo acadêmico estabelecido, Pesquisadores Doutores recebem uma verba fixa de R$ 15.000 por projeto ativo, enquanto Pesquisadores Mestres recebem R$ 10.000 por projeto. O sistema deve herdar as propriedades comuns compartilhadas (como nome, área e quantidade de projetos), mas impedir a criação de um pesquisador genérico e sem classificação ativa.

**Conceito utilizado:** Classes Abstratas (`abstract`), declaração de métodos abstratos e Polimorfismo de Sobrescrita.

**Solução:** Definir a classe conceitual base `Pesquisador` como abstrata para impossibilitar instanciações diretas e forçar as classes concretas filhas (`PesquisadorDoutor` e `PesquisadorMestre`) a implementarem as lógicas orçamentárias específicas.

```
// Modelo base conceitual - Não pode sofrer instanciações diretas
public abstract class Pesquisador {
    protected String nome;
    protected String areaPesquisa;
    protected int numeroProjetos;

    public Pesquisador(String nome, String areaPesquisa, int numeroProjetos) {
        this.nome = nome;
        this.areaPesquisa = areaPesquisa;
        this.numeroProjetos = numeroProjetos;
    }

    // Assinatura abstrata que delega o comportamento de cálculo
    public abstract double calcularFinanciamento();
}

// Subclasse concreta para Doutor
class PesquisadorDoutor extends Pesquisador {
    public PesquisadorDoutor(String nome, String areaPesquisa, int numeroProjetos) {
        super(nome, areaPesquisa, numeroProjetos);
    }
    @Override
    public double calcularFinanciamento() {
        return numeroProjetos * 15000; // Regra de financiamento do Doutorado
    }
}

// Subclasse concreta para Mestre
class PesquisadorMestre extends Pesquisador {
    public PesquisadorMestre(String nome, String areaPesquisa, int numeroProjetos) {
        super(nome, areaPesquisa, numeroProjetos);
    }
    @Override
    public double calcularFinanciamento() {
        return numeroProjetos * 10000; // Regra de financiamento do Mestrado
    }
}
```

**Resultado:** O sistema calcula as dotações financeiras com base nas classes filhas correspondentes e utiliza o polimorfismo para processar diferentes tipos de pesquisadores de forma genérica e padronizada:

```
Pesquisador p1 = new PesquisadorDoutor("Dr. Silva", "Física", 3);
Pesquisador p2 = new PesquisadorMestre("Mestre Santos", "Biologia", 2);

System.out.println(p1.calcularFinanciamento()); // Exibe: 45000.0
System.out.println(p2.calcularFinanciamento()); // Exibe: 20000.0
```

**Por que essa solução funciona:** Como a superclasse `Pesquisador` é marcada com a palavra-chave `abstract`, ela opera estritamente como um esqueleto conceitual e impede chamadas inconsistentes. A responsabilidade pela lógica específica do método abstrato é delegada e cobrada obrigatoriamente das classes derivadas concretas.

**O que preciso aprender com esse exemplo:**

- Classes abstratas compartilham estados e herança comum de atributos e de métodos concretos, mas proíbem a instanciação direta via operador `new`.
- Subclasses não abstratas devem obrigatoriamente sobrescrever e implementar todos os métodos abstratos herdados da classe pai para compilar.