**Problema:** Um ginásio poliesportivo chamado **"Ginásio DTC"** possui duas quadras esportivas de tamanhos idênticos disponíveis para locação. Diferentes clientes realizam reservas nessas quadras, com variações de valores cobrados por hora de uso. O analista de sistemas precisa desenhar um diagrama que mostre um retrato real dessas instâncias em tempo de execução para validar os requisitos do sistema de reservas.

**Conceito utilizado:** **Diagrama de Objetos UML**, com foco em vínculos (_links_) sem multiplicidade e valores reais de atributos.

**Solução:** A solução instancia os objetos conforme as especificações de dados reais:

1. **Objeto do Ginásio**: `objGinasio:1 : Ginasio` \(\rightarrow\) Atributo: `nome = "Ginásio DTC"`.
2. **Objetos das Quadras**:
    - `objQuadra:1 : Quadra` \(\rightarrow\) Atributos: `Comprimento = 30`, `Largura = 10`.
    - `objQuadra:2 : Quadra` \(\rightarrow\) Atributos: `Comprimento = 30`, `Largura = 10`.
    - Ambas as quadras possuem **vínculos** lógicos com o objeto `objGinasio:1`.
3. **Objetos de Locação (Reservas)**:
    - `objLocacao:1 : Locações` \(\rightarrow\) Atributo: `valor/hora = 15` (vinculada à quadra 2).
    - `objLocacao:2 : Locações` \(\rightarrow\) Atributo: `valor/hora = 15` (vinculada à quadra 2).
    - `objLocacao:3 : Locações` \(\rightarrow\) Atributo: `valor/hora = 10` (vinculada à quadra 1).
    - `objLocacao:4 : Locações` \(\rightarrow\) Atributo: `valor/hora = 15` (vinculada à quadra 1).
4. **Objetos de Clientes**:
    - `objCliente:2 : Cliente` \(\rightarrow\) Atributos: `Nome = "Jubileu"`, `CPF = 12345678` (vinculado à `objLocacao:1`).
    - `objCliente:2 : Cliente` \(\rightarrow\) Atributos: `Nome = "nakamura"`, `CPF = 741852963` (vinculado à `objLocacao:2`).
    - `objCliente:1 : Cliente` \(\rightarrow\) Atributos: `Nome = "Mario"`, `CPF = 987654321` (vinculado à `objLocacao:3`).
    - `objCliente:2 : Cliente` \(\rightarrow\) Atributos: `Nome = "faustão"`, `CPF = 963852741` (vinculado à `objLocacao:4`).

**Resultado:** O diagrama gerado (conforme a _Figura 6 da Unidade 3, Aula 3_) representa uma "fotografia" estática que comprova que o cliente "nakamura" e o cliente "Jubileu" reservaram a quadra 2, enquanto "Mario" e "faustão" reservaram a quadra 1 em horários distintos.

**Por que essa solução funciona:** Ao mapear valores de dados reais de instâncias de classes, o diagrama de objetos ajuda os desenvolvedores a testar regras de consistência da multiplicidade lógica (se um cliente pode ter múltiplas reservas ao mesmo tempo) de forma visual antes de iniciar a programação.

**O que preciso aprender com esse exemplo:** Diferente do diagrama de classes, o diagrama de objetos **nunca apresenta multiplicidade (como 1..*) em suas conexões**. As linhas de conexão são chamadas de **vínculos (links)** e sempre ligam exatamente um único objeto específico a outro. Além disso, **todos os dados do cabeçalho do objeto devem vir obrigatoriamente sublinhados** (ex: \(\underline{objeto : Classe}\)).