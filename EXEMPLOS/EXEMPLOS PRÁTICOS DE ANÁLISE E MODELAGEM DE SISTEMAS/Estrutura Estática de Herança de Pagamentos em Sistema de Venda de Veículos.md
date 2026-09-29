**Problema:** Mapear a estrutura estática do modelo de dados para uma revendedora de automóveis. O sistema deve registrar as interações lógicas entre Carros, Clientes, Vendedores e as Vendas realizadas, lidando com o fato de que cada venda pode ser faturada em duas formas de pagamento distintas (à vista ou a prazo) com atributos exclusivos.

**Conceito utilizado:**

- **Diagrama de Classes UML**.
- **Relacionamento de Herança (Generalização/Especialização)**.
- **Multiplicidade de Associações lógicas**.

**Solução:** A equipe desenhou o seguinte esquema estrutural de classes:

1. **Classes e Atributos**:
    - `Carro`: placa (int), ano (int), marca (string), modelo (string), origem (string).
    - `Cliente`: nome (string), telefone (int), endereco (string), cpf (int).
    - `Vendedor`: numero (int), nome (string).
    - `Venda` (Superclasse): numVenda (int), dataVenda (date), valor (float), tipo (int).
    - `A_vista` (Subclasse / Especialização): valorDesconto (float), banco (string), tipo (string).
    - `A_prazo` (Subclasse / Especialização): qtddParcela (int), valorParcela (float).
2. **Relacionamentos e Multiplicidades**:
    - Entre `Carro` e `Venda`: Multiplicidade `1 -> 1` (Cada carro específico está associado a exatamente uma única venda).
    - Entre `Cliente` e `Venda`: Multiplicidade `1 -> 1..*` (Um cliente pode realizar uma ou várias compras de carros ao longo do tempo, mas cada venda pertence a apenas um único cliente).
    - Entre `Vendedor` e `Venda`: Multiplicidade `1..* -> 1..*` (Um vendedor realiza múltiplas vendas, e uma venda pode ter a participação ou supervisão de vendedores).
    - **Herança de Pagamentos**: `A_vista` e `A_prazo` são ligadas à superclasse `Venda` por uma linha com seta de ponta fechada vazada apontando para `Venda`. Elas herdam todos os atributos básicos de `Venda` (como valor e data).

**Resultado:** Um modelo estrutural estático padronizado em UML que dita perfeitamente como o banco de dados orientado a objetos ou relacional deve ser codificado.

**Por que essa solução funciona:** A aplicação de herança na modelagem orientada a objetos poupa a escrita de código redundante e duplicado para os atributos básicos de venda nas classes de pagamento à vista e parcelado, agilizando futuras manutenções.

**O que preciso aprender com esse exemplo:** A generalização/especialização no Diagrama de Classes UML organiza as dependências de dados de forma hierárquica. Lembre-se: use a **seta de ponta fechada vazada** apontando para a superclasse (pai) para representar herança em provas.