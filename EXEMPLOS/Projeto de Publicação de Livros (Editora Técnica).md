**Problema:** Uma editora de livros técnicos necessita de um sistema informatizado para gerenciar seu catálogo e processos de publicação. O designer de sistemas precisa organizar as informações coletadas em entrevistas com vendedores, diagramadores e gerentes de produção em uma estrutura coerente.

**Conceito utilizado:** Modelagem Entidade-Relacionamento (MER), Diagrama Entidade-Relacionamento (DER) utilizando a notação de Peter Chen, restrições de participação (total e parcial) e razões de cardinalidade (1:M, M:N).

**Solução:**

1. **Identificação de Entidades e Atributos**:
    - _Áreas_: Código de área (PK) e descrição.
    - _Formatos_: Código de formato (PK), descrição e dimensões (altura e largura).
    - _Encadernações_: Código de encadernação (PK) e descrição.
    - _Autores_: Código de autor (PK), nome, endereço completo (rua, número, bairro, cidade, estado), CPF, RG, telefones, data de nascimento, gênero, estado civil e local de trabalho.
    - _Livros_: Código ISBN (PK), título, formato, tipo de encadernação, páginas, peso, custos, preço de venda, edição, ano, reimpressão e número de contrato.
2. **Definição de Relacionamentos e Cardinalidades**:
    - _Livro pertence à Área_ (M:1): Um livro pertence a uma única área (participação total de Livros), enquanto uma área pode ter vários ou nenhum livro (participação parcial de Áreas).
    - _Livro possui Formato_ (M:1): Um livro só tem um formato (participação total de Livros), mas um formato pode ser aplicado a vários ou nenhum livro (participação parcial de Formatos).
    - _Livro possui Encadernação_ (M:1): Um livro tem uma encadernação (participação total de Livros), mas uma encadernação serve para vários ou nenhum livro (participação parcial de Encadernações).
    - _Autor escreve Livro_ (M:N): Vários autores escrevem vários livros (participação total de ambos os lados; não há autor sem livro e vice-versa no cadastro).

**Resultado:** O mapeamento resulta em um DER completo que expressa graficamente a estrutura do catálogo da editora.

**Por que essa solução funciona:** A modelagem conceitual unifica as visões dispersas dos funcionários (vendas, produção, diagramação) em um único diagrama abstrato que descreve fielmente as regras de negócio antes de qualquer codificação física.

**O que preciso aprender com esse exemplo:** Para modelar relacionamentos M:1, verifique sempre a obrigatoriedade da participação (se o lado "muitos" exige a existência do lado "um"). Atributos compostos (como endereço) devem ser decompostos graficamente em elipses conectadas a uma elipse principal no modelo conceitual.