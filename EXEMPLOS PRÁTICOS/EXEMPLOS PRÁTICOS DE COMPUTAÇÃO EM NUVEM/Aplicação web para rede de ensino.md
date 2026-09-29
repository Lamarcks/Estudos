## Cloud Bursting

**Descrição da situação-problema**

Uma rede de ensino superior com faculdades em várias cidades deseja criar uma aplicação web na qual os estudantes podem consultar a matriz curricular dos cursos e a oferta de disciplinas obrigatórias e eletivas, bem como realizar a matrícula em disciplinas a cada semestre. Como o número de estudantes nessa rede é muito grande, a escalabilidade da aplicação é um fator relevante. A instituição decidiu utilizar uma infraestrutura em nuvem para hospedar a aplicação. Sua tarefa  é avaliar qual modelo de implantação de ambiente de nuvem deve ser utilizado para o cenário apresentado.

**Resolução da situação-problema**

A solução mais adequada seria a nuvem híbrida. Os dados dos alunos permaneceriam em uma nuvem privada, garantindo maior controle e segurança, enquanto servidores de nuvem pública hospedariam réplicas da interface web durante os períodos de matrícula. Após esses períodos, os recursos públicos seriam liberados para reduzir custos. Esse aumento temporário de capacidade por meio da nuvem pública é denominado **Cloud Bursting**.