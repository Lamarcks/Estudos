**Problema:** Encontrar padrões e estruturas ocultas em uma base de dados de clientes para organizá-los em grupos (segmentos) homogêneos que possuem comportamentos de compra, preferências ou características afins. A grande dificuldade é que os dados de entrada não possuem rótulos prévios ou categorias pré-definidas.

**Conceito utilizado:** Aprendizado Não Supervisionado (Segmentação / Clustering).

**Solução:**

1. **Agrupamento por Similaridade:** Alimenta-se a rede neural diretamente com as variáveis brutas comportamentais e cadastrais dos clientes.
2. **Mapeamento de Correlações:** Sem a ajuda de respostas conhecidas (sem supervisão), os algoritmos internos da rede calculam a proximidade matemática dos atributos dos clientes em várias dimensões.
3. **Definição dos Segmentos:** A rede cria partições ou grupos agrupando clientes que têm perfis mais parecidos entre si e separando-os de grupos com comportamentos divergentes.

**Resultado:** Base de clientes organizada em clusters com características semelhantes, permitindo criar campanhas personalizadas de alta conversão para cada público.

**Por que essa solução funciona:** Redes neurais operando de forma não supervisionada conseguem processar dados de alta complexidade e identificar correlações e dependências profundas entre as variáveis, estabelecendo afinidades naturais entre os dados brutos de entrada.

**O que preciso aprender com esse exemplo:** No aprendizado **não supervisionado**, não existem rótulos nem respostas "corretas" prévias. O algoritmo foca em revelar a estrutura e as afinidades naturais internas que residem no próprio conjunto de dados.