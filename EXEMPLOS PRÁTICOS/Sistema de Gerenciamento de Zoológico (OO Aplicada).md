**Problema:** Uma empresa de desenvolvimento de software foi contratada para criar um **sistema de gerenciamento de um zoológico**. O sistema precisa realizar o cadastro e a gestão de animais, tratadores, áreas físicas do zoológico e as rotinas de alimentação. O principal desafio é modelar com precisão que diferentes tipos de animais (como mamíferos, aves e répteis) possuem características distintas e respondem a rotinas de alimentação particulares (por exemplo, mamíferos comem em horários e formas diferentes de répteis).

**Conceito utilizado:** Fundamentos do **Paradigma Orientado a Objetos (OO)**: Abstração, Classes, Objetos, Herança (Generalização) e Polimorfismo.

**Solução:**

1. **Identificação de Classes e Objetos**: Mapear as entidades do mundo real em classes abstratas e instanciar objetos concretos:
    - `Animal`: Atributos comuns (nome, idade). _Objeto de exemplo: um leão chamado "Simba"_.
    - `Tratador`: Atributos (nome, telefone). _Objeto de exemplo: tratador chamado "João"_.
    - `Área`: Atributos (nome da área, clima). _Objeto de exemplo: área "Savana Africana"_.
    - `Rotina`: Atributos (horário, tipo de ração). _Objeto de exemplo: "Rotina de alimentação diária para leões"_.
2. **Aplicação de Herança**: Criar uma classe base genérica chamada `Animal` com atributos e comportamentos comuns. Em seguida, criar subclasses específicas como `Mamífero`, `Ave` e `Répteis`, que herdam de `Animal` e adicionam seus próprios atributos e comportamentos exclusivos.
3. **Aplicação de Polimorfismo**: Definir o método abstrato `realizarAlimentacao()` na superclasse `Animal`. Cada subclasse (`Mamífero`, `Ave`, `Répteis`) sobrescreve (_override_) esse método para implementar sua rotina específica de alimentação.

**Resultado:** O sistema consegue tratar todos os animais de forma genérica como instâncias de `Animal` ao chamar o método `realizarAlimentacao()`, mas cada objeto responde executando o comportamento específico de sua respectiva subclasse (um réptil receberá alimentação no seu tempo lento e um mamífero em seu horário programado).

**Por que essa solução funciona:** A herança evita a duplicação de atributos comuns em várias classes (reuso de código), enquanto o polimorfismo permite que a aplicação interaja com qualquer animal usando a mesma assinatura de método (`realizarAlimentacao()`), delegando o comportamento correto para o tempo de execução.

**O que preciso aprender com esse exemplo:** Para provas, lembre-se de que a **herança cria uma hierarquia "é um"** (ex: _Mamífero é um Animal_), enquanto o **polimorfismo permite tratar diferentes objetos de forma uniforme sob a mesma interface**, executando ações diferentes de acordo com o tipo concreto do objeto instanciado.