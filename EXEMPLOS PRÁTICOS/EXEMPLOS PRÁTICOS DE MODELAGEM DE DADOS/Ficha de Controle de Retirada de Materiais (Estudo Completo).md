**Problema:** Uma loja de materiais de construção gerencia a retirada de mercadorias por clientes confiáveis de forma manual, usando a ficha física descrita abaixo:

```
+--------------------------------------------------------------+
|             FICHA DE CONTROLE DE RETIRADA DE MATERIAIS       |
| Controle ficha nº: 1045                    Data: 31/08/2026  |
| Cliente: João da Silva                     RG: 12.345.678-9  |
| CPF: 111.222.333-44                                          |
| Endereço: Av. das Flores, 120, Apto 3                        |
| Cidade: Blumenau                           UF: SC            |
|                                                              |
| Produtos                                                     |
| Código   Descrição            Quantidade   Preço Unit.  Total|
| 501      Cimento Campeão 50kg 10           R$ 35,00  R$350,00|
| 302      Areia Fina (m³)       2           R$ 90,00  R$180,00|
|                                                              |
|                                     Valor total a pagar: 530 |
+--------------------------------------------------------------+
```

Você precisa normalizar as tabelas desse documento físico até a 4FN e desenhar o DER correspondente.

**Conceito utilizado:** Processo de Normalização Completo (1FN à 4FN).

**Solução:**

1. **Levantamento de Atributos brutos do documento**:
    
    - `Nº Ficha`, `Data`, `Nome Cliente`, `RG`, `CPF`, `Endereço`, `Cidade`, `UF`, `Código Produto`, `Descrição`, `Quantidade`, `Preço Unitário`, `Preço Total Item`, `Valor Total Ficha`.
2. **Aplicação da 1FN (Chaves e Atomicidade)**:
    
    - Identificar o CPF como chave primária do cliente, o Código do Produto como chave primária do produto e o Nº da Ficha como chave primária da transação.
    - Substituir o campo calculado `Idade` (se houvesse) ou garantir que os atributos de texto não tenham múltiplos valores por célula.
3. **Aplicação da 2FN (Isolamento de Temas)**:
    
    - Isolar os temas geográficos criando tabelas próprias de `Cidade` e `Estado` para evitar repetições redundantes de strings nos cadastros:
        - `Cidade` (#idCidade, Cidade).
        - `Estado` (#siglaEstado, Estado).
    - Adicionar as chaves estrangeiras relacionais correspondentes na tabela de Ficha.
4. **Aplicação da 3FN (Remoção de Campos Calculados e Transitividades)**:
    
    - Na tabela de Itens de Produto, o campo `Preço Total Item` (Quantidade * Preço Unitário) é um campo puramente calculado.
    - Na tabela de Ficha, o campo `Valor Total Ficha` também é calculado (soma dos totais de itens).
    - **Regra de 3FN**: Esses campos devem ser fisicamente eliminados do banco de dados, pois podem ser consultados dinamicamente via consultas lógicas SQL operacionais.
5. **Aplicação da 4FN (Decomposição de Atributos Compostos)**:
    
    - O campo `Endereço` é composto. Para atingir a conformidade total 4FN, decompõe-se o campo em uma tabela própria de endereçamento com atributos atômicos:
        - `Endereço` (#cdEndereco, Rua, Número, Complemento, &cdCidade).
        - Vincular o endereço ao Cliente por chave estrangeira `&cdEndereco`.

**Resultado:** O banco de dados estruturado resulta em 6 tabelas altamente normalizadas conectadas sem redundâncias:

- `Estado` (#siglaUF, Estado).
- `Cidade` (#cdCidade, Cidade, &siglaUF).
- `Endereço` (#cdEndereco, Rua, Numero, Complemento, &cdCidade).
- `Cliente` (#CPF, Nome, RG, &cdEndereco).
- `Ficha` (#nrFicha, Data, &cdCliente).
- `Item-Produto` (#idItemProdFicha, &nrFicha, &cdProduto, Quantidade, PreçoUnitário).
- `Produto` (#cdProduto, Descrição).

**Por que essa solução funciona:** Elimina 100% das redundâncias e anomalias de atualização. Se o preço unitário de um produto mudar no cadastro, isso não altera os preços das notas fiscais antigas de retirada, pois o preço cobrado no dia histórico do evento ficou registrado de forma segura na tabela associativa `Item-Produto`.

**O que preciso aprender com esse exemplo:** Campos que são resultado de operações matemáticas básicas entre colunas (como totais ou subtotais) são redundantes e devem ser eliminados na 3FN, pois o SGBD realiza esses cálculos sob demanda nas consultas lógicas operacionais.