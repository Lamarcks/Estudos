**Problema:** A cadeia de hotéis deseja modernizar suas operações diárias criando um **sistema de gerenciamento de reservas**. O projeto precisa ser planejado e executado conforme o **Processo Unificado (UP)**, integrando diagramas UML a cada fase correspondente do projeto.

**Conceito utilizado:** Ciclo de vida do **Processo Unificado (UP)**: fases de Concepção (Iniciação), Elaboração, Construção e Transição, utilizando a UML como modelagem suporte.

**Solução:** A equipe estruturou o projeto executando os seguintes passos em cada fase:

1. **Fase de Iniciação (Concepção)**: Identificação dos atores (Hóspede e Funcionário da recepção) e casos de uso essenciais (`Realizar Reserva`, `Cancelar Reserva`, `Check-in` e `Check-out`). Definição da arquitetura lógica inicial.
2. **Fase de Elaboração**: Modelagem estrutural detalhada com o **Diagrama de Classes** (representando as entidades `Cliente`, `Reserva`, `Quarto` e `Serviço`). Criação do **Diagrama de Sequência** para descrever passo a passo a interação temporal na realização de uma reserva (cliente solicita, o sistema verifica a disponibilidade de quartos no banco de dados e registra).
3. **Fase de Construção**: Desenvolvimento de código iterativo mapeando as classes e métodos da UML em classes de programação orientada a objetos. Realização de testes de integração.
4. **Fase de Transição**: Implantação física no hotel, treinamento de funcionários, correção de bugs identificados na fase beta e entrega de documentação.

**Resultado:** O hotel obteve um sistema funcional e documentado, com baixíssimo nível de retrabalho ou falhas arquiteturais graves.

**Por que essa solução funciona:** O UP mitiga os riscos de forma iterativa. Os diagramas UML atuam como pontes de comunicação: na iniciação, os casos de uso alinham as expectativas com os diretores do hotel; na elaboração, os diagramas de classes e sequência guiam diretamente o trabalho da equipe de programação.

**O que preciso aprender com esse exemplo:** Não se cria diagrama de classes detalhado na fase de iniciação. **A UML evolui com o UP**: casos de uso dominam a Concepção; diagramas de classes e sequência dominam a Elaboração e Construção; diagramas de implantação/instalação dominam a Construção e Transição.