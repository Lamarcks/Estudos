**Problema:** Você atua como cientista de dados em uma empresa de varejo e precisa prever com precisão a quantidade de vendas futuras de um determinado produto. Este é um problema altamente não linear e influenciado por múltiplos fatores simultâneos apresentados em uma tabela histórica:

- **Variáveis de Entrada (Inputs):** Mês (\(x_1\)), Estoque (\(x_2\)), Precipitação (\(x_3\)) e Dias de Promoção (\(x_4\)).
- **Variável de Saída (Output):** Quantidade prevista de produtos vendidos.

_Amostras dos dados históricos presentes nas fontes:_

- Mês: `7`, Estoque: `111`, Precipitação: `21.3961`, Dias de Promoção: `2` \(\rightarrow\) Vendas: `49.0838`
- Mês: `4`, Estoque: `3`, Precipitação: `152.206`, Dias de Promoção: `3` \(\rightarrow\) Vendas: `0.0000`
- Mês: `11`, Estoque: `349`, Precipitação: `108.253`, Dias de Promoção: `9` \(\rightarrow\) Vendas: `115.254`

**Conceito utilizado:** Arquitetura de Rede Neural Totalmente Conectada (com duas camadas ocultas), Soma Ponderada, Função de Ativação ReLU e Aprendizado por Backpropagation e Gradiente Descendente.

**Solução:**

1. **Definição das Entradas:** Os neurônios da camada de entrada recebem os valores brutos de cada registro (Mês, Estoque, Precipitação e Dias de Promoção).
2. **Soma Ponderada nos Neurônios Ocultos:** Cada ligação possui um peso (\(w_i\)). Cada neurônio realiza a combinação linear das entradas multiplicadas pelos respectivos pesos e soma o bias (\(b\)): \[z = w_1x_1 + w_2x_2 + w_3x_3 + w_4x_4 + b\]
3. **Aplicação de Não Linearidade:** Aplica-se uma função de ativação sobre o resultado obtido para passá-lo adiante: \[\text{Saída do Neurônio} = f(z)\]
4. **Uso de ReLU na Saída:** Como o volume de vendas é uma variável contínua que nunca pode ser negativa (o menor valor físico é zero), a função **ReLU** (que retorna zero para valores negativos e mantém o valor original para positivos) é selecionada para a camada de saída.
5. **Ajuste de Parâmetros (Treinamento):** O modelo roda a _Forward Propagation_ para prever. Ele calcula a diferença entre a previsão e a venda real (Erro). Pelo _Backpropagation_, o erro volta calculando o gradiente de cada peso. O _Gradiente Descendente_ atualiza esses pesos na direção que reduz o erro de previsão.

**Resultado:** Uma rede neural treinada que estima com precisão as vendas de um produto de acordo com o cenário comercial (mês, estoque disponível, clima e promoções).

**Por que essa solução funciona:** A combinação de camadas ocultas estruturadas com funções de ativação não lineares (como a ReLU) permite que a rede neural capture padrões extremamente sutis e relações complexas (não lineares) nos dados comerciais, algo impossível de ser ajustado com modelos estatísticos tradicionais retos.

**O que preciso aprender com esse exemplo:** Problemas de regressão que buscam estimar valores contínuos não negativos (como faturamento, quantidades físicas e vendas) devem utilizar a função de ativação **ReLU** na sua camada final para garantir consistência matemática e física ao modelo.