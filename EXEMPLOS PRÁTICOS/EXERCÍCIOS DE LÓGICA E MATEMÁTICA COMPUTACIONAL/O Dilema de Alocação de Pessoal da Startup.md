**Problema:** Uma startup possui 6 funcionários (\(A, B, C, D, E, F\)) e deve alocar exatamente 2 funcionários para cada um de seus 3 novos projetos de desenvolvimento (\(Projeto X\), \(Projeto Y\) e \(Projeto Z\)). Sabendo que cada funcionário só pode ser designado para um único projeto e que a ordem de alocação das duas pessoas dentro do time de cada projeto não importa, quantas maneiras diferentes existem de realizar essa distribuição?

**Conceito utilizado:** Análise combinatória sequencial, arranjos sem repetição e princípio multiplicativo de eventos independentes.

**Solução:** Como os projetos são distintos, a distribuição deve ser calculada de forma sequencial para cada time:

1. **Passo 1 (Projeto X):** Escolher 2 funcionários dos 6 disponíveis (\(n=6, r=2\)). \[A(6, 2) = \frac{6!}{(6-2)!} = \frac{6!}{4!} = \frac{720}{24} = 30 \text{ maneiras}\]
2. **Passo 2 (Projeto Y):** Como 2 funcionários já foram alocados ao Projeto X, restam apenas 4 disponíveis. Devemos selecionar 2 deles (\(n=4, r=2\)): \[A(4, 2) = \frac{4!}{(4-2)!} = \frac{4!}{2!} = \frac{24}{2} = 12 \text{ maneiras}\]
3. **Passo 3 (Projeto Z):** Com 4 colaboradores já alocados, restam apenas 2 funcionários para os 2 lugares do Projeto Z (\(n=2, r=2\)): \[A(2, 2) = \frac{2!}{(2-2)!} = \frac{2!}{0!} = \frac{2}{1} = 2 \text{ maneiras}\]
4. **Passo 4 (Total de Alocações):** Como as escolhas das equipes dos projetos são sucessivas e independentes, multiplicamos os resultados parciais obtidos: \[\text{Maneiras Totais} = 30 \text{ (Proj X)} \times 12 \text{ (Proj Y)} \times 2 \text{ (Proj Z)} = 720\]

**Resultado:** Existem **720** maneiras totalmente diferentes de organizar as equipes da startup entre os projetos de desenvolvimento.

**Por que essa solução funciona:** A modelagem probabilística reduz o espaço amostral de seleção a cada passo porque os funcionários não podem ser duplicados (seleção sem reposição). Multiplicar as combinações parciais calcula todo o espaço de ramificações possíveis de decisão.

**O que preciso aprender com esse exemplo:** Diferente de escolher apenas um grupo isolado, problemas de partição de um conjunto maior em várias equipes menores e exclusivas exigem o cálculo de combinações sucessivas multiplicadas em cadeia.