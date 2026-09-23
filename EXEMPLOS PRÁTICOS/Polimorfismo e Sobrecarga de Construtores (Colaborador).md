**Problema:** Inicializar objetos de uma classe de diferentes maneiras dependendo das informações que a aplicação dispõe no momento da criação, sem a necessidade de criar múltiplas classes para representar a mesma entidade.

**Conceito utilizado:** **Polimorfismo por sobrecarga de métodos (_Overload_)** aplicado ao construtor de uma classe em linguagens orientadas a objetos.

**Solução:** Criar uma única classe `Colaborador` e definir o seu método construtor múltiplas vezes, variando apenas o conjunto de parâmetros recebidos em cada assinatura de método.

```
public class Colaborador {
    public String nomeColaborador;
    public Integer idadeColaborador;
    public String docPessoalColaborador;

    // 1. Construtor sem parâmetros (default)
    public Colaborador () { }

    // 2. Construtor parametrizado apenas com nome
    public Colaborador (String nomeColaborador) {
        this.nomeColaborador = nomeColaborador;
    }

    // 3. Construtor parametrizado com nome e idade
    public Colaborador (String nomeColaborador, Integer idadeColaborador) {
        this.nomeColaborador = nomeColaborador;
        this.idadeColaborador = idadeColaborador;
    }

    // 4. Construtor parametrizado com nome, idade e documento pessoal
    public Colaborador (String nomeColaborador, Integer idadeColaborador, String docPessoalColaborador) {
        this.nomeColaborador = nomeColaborador;
        this.idadeColaborador = idadeColaborador;
        this.docPessoalColaborador = docPessoalColaborador;
    }
}
```

- **Linhas 1 a 4:** Declaração de atributos públicos da classe.
- **Linha 6:** Construtor vazio que cria o objeto sem valores iniciais definidos.
- **Linhas 8 a 10:** Construtor que inicializa apenas o nome. O operador `this` é usado para distinguir o atributo do parâmetro local.
- **Linhas 12 a 15 e 17 a 21:** Construtores alternativos que aceitam combinações progressivas de atributos para instanciar o colaborador com mais detalhes estruturados.

**Resultado:** O desenvolvedor ganha flexibilidade para instanciar o objeto utilizando qualquer uma das 4 assinaturas descritas (ex: `new Colaborador("Ana")` ou `new Colaborador("Carlos", 30, "1234")`), evitando erros em tempo de compilação.

**Por que essa solução funciona:** A Máquina Virtual (JVM) analisa o número e o tipo dos parâmetros passados no ato de instanciação (`new`) e invoca exatamente o construtor cuja assinatura corresponde aos valores fornecidos.

**O que preciso aprender com esse exemplo:** A **Sobrecarga (Overload)** permite que um método (ou construtor) seja redefinido na mesma classe com parâmetros distintos. Ela difere da Sobrescrita (_Override_), que altera o comportamento de um método herdado de uma superclasse.