**Problema:** Desenvolver um sistema de locação de mídias que gerencie múltiplos itens específicos (como `BlueRay` e `Ebook`) de forma unificada, evitando a duplicação manual de lógica comum (como campos de título ou métodos para consulta de estoque).

**Conceito utilizado:** **Herança** em programação orientada a objetos (reuso estrutural).

**Solução:** Criar uma classe base (superclasse) abstrata contendo as propriedades e comportamentos comuns a todas as mídias, e fazer com que as mídias específicas herdem (derivem) dessa classe base.

```
// Classe Base (Superclasse)
public class AlugaItem {
    string _titulo;
    public string Titulo {
        get { return _titulo; }
        set { _titulo = value; }
    }
    public Boolean PesquisaEstoque(string titulo) {
        // Lógica para verificar se o item está em estoque
        return true;
    }
}

// Classes Derivadas (Subclasses) que herdam de AlugaItem
public class BlueRay : AlugaItem {
    // Herda automaticamente o campo _titulo, propriedade Titulo e o método PesquisaEstoque
}

public class Ebook : AlugaItem {
    // Herda as mesmas propriedades e pode adicionar campos específicos como ISBN
}
```

- **Linhas 1 a 14:** Definição da superclasse `AlugaItem` com atributo privado encapsulado por getters/setters em C# e o método de domínio `PesquisaEstoque`.
- **Linha 15:** O operador `:` indica herança estrutural em C# (equivalente a `extends` em Java). A classe `BlueRay` se torna herdeira de `AlugaItem`.
- **Linha 18:** A classe `Ebook` também é declarada como derivada de `AlugaItem`, herdando toda a sua estrutura base de forma automática.

**Resultado:** As subclasses `BlueRay` e `Ebook` agora herdam os atributos e comportamentos da classe principal, podendo ser manipuladas através de referências genéricas à superclasse, além de poderem estender seus próprios comportamentos.

**Por que essa solução funciona:** A herança estabelece uma relação lógica de "é um" (ex: "um Ebook é um AlugaItem"). Isso permite que todas as propriedades públicas e protegidas da classe pai fiquem disponíveis para as classes filhas sem a necessidade de reescrever uma linha de código sequer nelas.

**O que preciso aprender com esse exemplo:** A herança promove o princípio **DRY (Don't Repeat Yourself)**. Classes derivadas herdam implicitamente tudo que é definido na classe base e podem adicionar ou sobrescrever seus próprios comportamentos se houver necessidade.