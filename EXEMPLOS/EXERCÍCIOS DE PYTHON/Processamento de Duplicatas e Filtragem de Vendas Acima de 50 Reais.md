**Problema:**  
Devido a uma falha no sistema de checkout de uma loja de varejo, as tabelas de vendas registraram linhas duplicadas e omitiram o valor unitário de cada produto. É preciso realizar o tratamento de exclusão de duplicidades, computar o preço de cada item (receita total / quantidade) e filtrar apenas os itens de alto ticket (com valores acima de R$50,00) para subsidiar uma campanha de marketing.

**Conceito utilizado:**  
Lógica de eliminação física de duplicidades, operações matemáticas estruturadas em colunas inteiras de DataFrames e testes booleanos de mascaramento lógico.

**Solução:**

```
import pandas as pd

# Dados de vendas com inconsistências (redundâncias e falta de preço unitário)
data = {
    'nome': ['Produto A', 'Produto B', 'Produto C', 'Produto A', 'Produto E'],
    'quantidade de itens comprados':,
    'tipo de item': ['Eletrônico', 'Vestuário', 'Alimento', 'Eletrônico', 'Alimento'],
    'receita total':
}
df = pd.DataFrame(data)

# Passo 1: Elimina as linhas duplicadas mantendo apenas o último registro registrado
df.drop_duplicates(keep='last', inplace=True)

# Passo 2: Computa em lote o preço individual do item de forma vetorizada
df['preço do item'] = df['receita total'] / df['quantidade de itens comprados']

# Passo 3: Mascaramento lógico (teste booleano) para isolar registros com preço superior a 50 reais
itens_acima_de_50 = df[df['preço do item'] > 50]

print("Tabela filtrada final:")
print(itens_acima_de_50)
```

**Resultado:**  
Exclusão automática de redundâncias estruturais, computação das notas fiscais e retorno exclusivo do "Produto B" com preço computado de R$80,00.

**Por que essa solução funciona:**  
O Pandas realiza a divisão vetorizada das colunas, alinhando de forma posicional o cálculo matemático linha a linha. O comando de filtro `df[df['coluna'] > valor]` avalia um vetor booleano temporário interno (`True`/`False`) mantendo visível apenas as linhas com valor verdadeiro correspondentes ao critério estipulado.

**O que preciso aprender com esse exemplo:**  
A manipulação lógica e operações de limpeza integradas reduzem códigos complexos de manipulação de dados corporativos em lote.