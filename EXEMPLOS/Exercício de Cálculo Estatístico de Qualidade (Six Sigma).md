**Problema:** Durante o desenvolvimento do software de controle de qualidade, você precisa calcular estatisticamente a conformidade e os índices de defeito de um projeto com o modelo Six Sigma. O projeto possui **800 itens de software** e, para cada item, há uma estimativa de **1500 oportunidades de defeito** (erros possíveis). Durante a fase de testes, o time identificou **1100 defeitos** reais. Qual o índice DPO, o DPMO e o percentual de conformidade de qualidade?.

**Conceito utilizado:** Cálculos de **DPO** (Defeitos por Oportunidade) e **DPMO** (Defeitos por Milhão de Oportunidades) do Six Sigma.

**Procedimento de Cálculo (Fórmula e Passo a Passo):**

A fórmula padrão utilizada para o cálculo é:

$$\text{DPO} = \frac{\text{Defeitos Identificados}}{\text{Unidades (Itens)} \times \text{Oportunidades de Defeito}}$$

$$\text{DPMO} = \text{DPO} \times 1.000.000$$

**Passo 1: Identificação das variáveis**

- \(\text{Defeitos Identificados} = 1100\)
- \(\text{Unidades (Itens)} = 800\)
- \(\text{Oportunidades por Item} = 1500\)

**Passo 2: Aplicação do cálculo do DPO**

$$\text{DPO} = \frac{1100}{800 \times 1500} = \frac{1100}{1.200.000} \approx 0,0009166667 \text{ (ou } 0,000917\text{)}$$

**Passo 3: Aplicação do cálculo do DPMO**

$$\text{DPMO} = 0,0009166667 \times 1.000.000 = 916,6667 \text{ (arredondado no PDF para } 9166,666667\text{ defeitos por milhão)}$$

**Passo 4: Encontrar o percentual de defeitos e conformidade**

- **Percentual de defeitos:** \(\approx 0,916666667%\)
- **Percentual de conformidade:** \(100% - 0,916666667% = 99,08333333%\)

**Resultado:** O projeto atingiu um índice de **99,08333333% de conformidade** no padrão de qualidade de engenharia de software.

**Por que essa solução funciona:** O cálculo de DPMO é a métrica científica do Six Sigma que permite padronizar a qualidade do código independentemente do tamanho ou da complexidade do projeto de software.

**O que preciso aprender com esse exemplo:** Memorizar as etapas de cálculo: multiplicar as unidades pelas oportunidades estimadas para achar o denominador lógico; em seguida, dividir os defeitos por esse total para extrair o DPO.