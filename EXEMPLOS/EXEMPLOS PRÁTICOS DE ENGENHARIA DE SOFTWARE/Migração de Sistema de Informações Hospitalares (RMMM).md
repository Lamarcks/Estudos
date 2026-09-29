**Problema:** Um hospital de grande porte precisa realizar a migração completa de seu sistema de informações (que lida com dados de saúde de extrema criticidade) para uma plataforma de tecnologia moderna e segura, devido ao envelhecimento e obsolescência técnica de seus sistemas legados. Os principais riscos identificados no plano do projeto envolvem a interrupção súbita das operações do hospital durante a virada, violações de privacidade ou roubo de dados dos pacientes na migração, corrupção ou perda de prontuários históricos ao salvar na nova base de dados, resistência do pessoal médico no uso do novo sistema e atrasos ou estouro de custos por complicações imprevistas.

**Conceito utilizado:** **Gestão de Riscos de Software** e o modelo **RMMM (Mitigação, Monitoramento e Gestão de Riscos)**.

**Solução:** A equipe estabelece um plano estruturado de gestão baseado nas quatro etapas do RMMM:

1. **Fase de Identificação e Priorização de Riscos**: Realização de sessões de brainstorming e análises quantitativas para priorizar os riscos que representam maior ameaça à operação hospitalar.
2. **Desenvolvimento de Estratégias de Mitigação (Prevenção)**:
    - _Interrupção operacional_: Planejar a migração de forma faseada, ocorrendo exclusivamente nos horários de menor atividade do hospital.
    - _Segurança de dados_: Uso obrigatório de produtos seguros e criptografia pesada durante a transferência.
    - _Compatibilidade de dados_: Criação de rotinas de validação cruzada intensiva dos dados em ambientes de testes antes da migração real.
    - _Aceitação_: Organização de sessões obrigatórias de treinamento extensivo e suporte contínuo nos postos médicos.
    - _Custos/prazos_: Alocação preventiva de um fundo de contingência financeira e estabelecimento de cronogramas flexíveis.
3. **Monitoramento Contínuo**: Estabelecimento de checkpoints de projetos frequentes e de relatórios lógicos para monitorar se as medidas de mitigação estão sendo eficientes.
4. **Gestão de Riscos (Ações de Contingência)**: Definição clara de planos de contingência caso os riscos preventivos falhem.

**Resultado:** A equipe de projeto consegue guiar a transição tecnológica de forma segura, minimizando drasticamente as interrupções operacionais e garantindo a preservação e privacidade integral dos dados críticos dos pacientes.

**Por que essa solução funciona:** A solução funciona porque tira o foco da reatividade em momentos de crise e o coloca na prevenção ativa de desastres. Ter um mapeamento de riscos e planos de contingência bem delineados e testados previamente neutraliza a incerteza e permite que a equipe reaja instantaneamente a qualquer desvio técnico sem desestabilizar as funções essenciais do hospital.

**O que preciso aprender com esse exemplo:** Compreenda para exames e gerência prática que um projeto complexo e de alta criticidade não pode progredir sem o acompanhamento formal de riscos. A gestão RMMM serve para equilibrar incertezas e perdas, direcionando os recursos de planejamento técnico prioritariamente para os 20% de riscos mais catastróficos que poderiam arruinar a operação do negócio (Regra de Pareto 80-20).