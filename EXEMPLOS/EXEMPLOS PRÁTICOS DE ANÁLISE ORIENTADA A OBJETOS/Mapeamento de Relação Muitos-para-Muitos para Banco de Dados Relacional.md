**Problema:** No projeto de banco de dados do sistema de locação de veículos, mapear o relacionamento estático de **muitos-para-muitos (N:N)** entre as classes de entidades **`Reserva`** e **`ItemAdicional`** (um cliente pode selecionar vários opcionais como bebê conforto, GPS e cadeirinha em uma reserva, e o mesmo tipo de item adicional pode constar em várias reservas do hotel/locadora).

**Conceito utilizado:** Técnicas de **Mapeamento Objeto-Relacional (MOR)** para associações binárias de multiplicidade muitos-para-muitos.

**Solução:** A partir do recorte do diagrama de classes (conforme a _Figura 5 da Unidade 4, Aula 4_):

1. Mapeia-se a classe `Reserva` em sua própria tabela física:
    - `Reserva (`\(\underline{\text{reservaId}}\), dataReserva, dataRetirada, horaRetirada, dataPrevDevolucao, situacao, observacao, demaisFK`)`.
2. Mapeia-se a classe `ItemAdicional` em sua própria tabela física:
    - `ItemAdicional (`\(\underline{\text{itemAdicionalId}}\), nome, descricao, valor`)`.
3. **Criação da Tabela Intermediária (Tabela de Junção)**: Como a relação é muitos-para-muitos, cria-se uma terceira tabela no banco de dados chamada `ReservaItemAdicional`.
4. A Chave Primária (PK) desta tabela intermediária é composta pelas PKs de ambas as tabelas originais, atuando simultaneamente como Chaves Estrangeiras (FKs):
    - `ReservaItemAdicional (`\(\underline{\text{reservaId}}\), \(\underline{\text{itemAdicionalId}}\)`)`. _(Nota: os campos sublinhados com linha contínua representam a chave primária composta; os mesmos campos atuam como chaves estrangeiras vinculadas às tabelas pai)._

**Resultado:** O esquema de banco de dados relacional gerado suporta a relação N:N de forma limpa, normalizada em 3ª Forma Normal, sem criar redundância de dados.

**Por que essa solução funciona:** O modelo relacional clássico não suporta vetores ou listas de IDs dentro de uma única célula de coluna (violação da primeira forma normal). A terceira tabela resolve o acoplamento, permitindo consultas via joins cruzados eficientes.

**O que preciso aprender com esse exemplo:** Em qualquer associação de multiplicidade muitos-para-muitos (\(_.._\)), **é obrigatório criar uma terceira tabela intermediária contendo as chaves primárias de ambas as tabelas associadas como sua chave primária composta**.