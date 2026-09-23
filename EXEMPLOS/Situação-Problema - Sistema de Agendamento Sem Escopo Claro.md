**Problema:** Uma equipe de desenvolvimento de software iniciou o projeto de um sistema de agendamento para clínicas médicas sem que os limites e requisitos estivessem definidos com clareza. O cliente esperava funcionalidades avançadas, como confirmação automática via WhatsApp e relatórios gerenciais de comparecimento, mas a equipe entregou apenas uma agenda digital interna básica. A situação agravou-se quando a escolha de uma linguagem de programação pouco compatível com a infraestrutura existente inviabilizou integrações de rede essenciais.

**Conceito utilizado:**

- Definição de Escopo de Sistema.
- Envolvimento precoce dos Stakeholders.
- Escolha Estratégica de Tecnologia/Linguagem de Programação.

**Solução:** A solução metodológica para este problema exige:

1. **Definição formal de escopo**: Mapear detalhadamente o que entra e, principalmente, o que fica de fora do projeto para alinhar as expectativas do cliente.
2. **Envolvimento colaborativo**: Conectar desenvolvedores, designers, QAs (testadores) e clientes clínicos desde o início para validar histórias de uso.
3. **Análise de compatibilidade técnica**: Avaliar a infraestrutura legada e as tecnologias de mercado antes de codificar (como APIs existentes para disparo de mensagens), escolhendo linguagens adequadas.

**Resultado:** O projeto sofreu atrasos severos, frustração extrema do cliente e necessidade de refazer partes expressivas da arquitetura de software (retrabalho dispendioso).

**Por que essa solução falhou:** A falta de um escopo formalizado remove os critérios de aceitação e os limites do plano de teste. Escolher tecnologias por preferência pessoal, e não por arquitetura, isola a aplicação do restante do ecossistema tecnológico da empresa.

**O que preciso aprender com esse exemplo:** O escopo é a pedra angular da qualidade de software; ele dita diretamente a elaboração dos planos de teste. Decisões de tecnologia isoladas e sem validação prévia de compatibilidade comprometem a viabilidade e a sustentabilidade de todo o ciclo de vida do programa.