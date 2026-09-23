**Problema:** A associação de moradores de um bairro gerencia uma horta comunitária em um terreno cedido pela prefeitura. Os lotes possuem tamanhos diferentes de acordo com o tamanho das famílias. É necessário controlar os moradores responsáveis, as hortaliças cultivadas em cada lote, as datas de plantio/colheita para estatísticas e evitar o uso de pesticidas.

**Conceito utilizado:** Criação de DER físico utilizando ferramentas CASE (Lucidchart), chaves primárias (PK), chaves estrangeiras (FK) e tabelas associativas para relacionamentos N:M.

**Solução:** A estrutura proposta divide as informações em 5 tabelas interligadas para evitar anomalias:

1. `Morador` (#IdMorador, Nome, Endereço, CPF, DtNasc, &CodProfissao).
2. `Profissão` (#CodProfissao, Profissão, Observação).
3. `Lote` (#IdLote, Tamanho, Localização, &IdMorador).
4. `Planta` (#CodPlanta, Nome Comum, Nome Científico).
5. `Item Plantado` (#IdItemPlantado, &IdLote, &CodPlanta, DtPlantio, DtColheita, Quantidade, Observação).

**Resultado:** Um esquema de banco de dados robusto que rastreia qual morador cuida de qual lote (relação 1:M), qual a sua profissão (relação 1:M) e o histórico de plantio no lote por meio da tabela associativa `Item Plantado` (relação M:N entre Lote e Planta).

**Por que essa solução funciona:** Ao transformar o plantio em uma entidade associativa (`Item Plantado`), o sistema consegue registrar infinitos eventos de plantio e colheita para o mesmo lote e para a mesma planta ao longo do tempo, sem duplicar dados estruturais de moradores ou plantas.

**O que preciso aprender com esse exemplo:** Ações ou eventos que ocorrem ao longo do tempo (como plantar e colher) entre duas entidades fortes (Lote e Planta) sempre geram uma tabela associativa contendo chaves estrangeiras de ambas e atributos adicionais sobre o evento (datas e quantidades).