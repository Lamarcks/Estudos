**Problema:**  
Realizar o pipeline de importação direta de dados macroeconômicos em lote no formato JSON de uma API pública do Banco Central do Brasil, avaliar sua integridade estrutural, eliminar duplicidades e incluir colunas de log para controle e autoria de dados.

**Conceito utilizado:**  
Leitura estruturada JSON (`pd.read_json()`), metadados estruturais do DataFrame (`.info()`), limpeza e exclusão de duplicados (`drop_duplicates()`), gravação na memória local (`inplace=True`) e inserção de colunas em lote.

**Solução:**

```
import pandas as pd
from datetime import date

# Passo 1: Captura dos dados brutos diretamente da API do Banco Central
url_selic = "https://api.bcb.gov.br/dados/serie/bcdata.sgs.11/dados?formato=json"
df_selic = pd.read_json(url_selic)

# Passo 2: Avalia a saúde estrutural dos dados importados
print("--- Informações estruturais brutas ---")
df_selic.info()

# Passo 3: Limpeza de linhas redundantes e duplicadas na tabela
df_selic.drop_duplicates(keep='last', inplace=True)

# Passo 4: Enriquecimento de colunas e dados cadastrais de controle de extração
df_selic['data_extracao'] = date.today()
df_selic['responsavel'] = "Autor"

# Passo 5: Inspeção final das colunas tratadas
print("\n--- Estrutura limpa enriquecida ---")
df_selic.info()
print("\nPrimeiros 5 registros processados:")
print(df_selic.head())
```

**Resultado:**  
Importação de milhares de linhas, com exclusão de duplicatas se houvesse, e gravação unificada da coluna de controle cronológico de data em cada registro.

**Por que essa solução funciona:**

- `drop_duplicates()` compara as células lógicas das linhas, enquanto o parâmetro `inplace=True` autoriza o Pandas a sobrescrever a memória diretamente, evitando cópias.
- Atribuições de chaves inexistentes `df_selic['nova_coluna'] = dado` fazem com que o Pandas replique o valor dinamicamente para todas as linhas.

**O que preciso aprender com esse exemplo:**  
Rotinas completas de tratamento em lote garantem dados limpos e livres de ruídos ou duplicidades para análise.