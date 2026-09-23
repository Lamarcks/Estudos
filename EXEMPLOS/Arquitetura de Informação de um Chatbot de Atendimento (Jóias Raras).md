**Problema:** A joalheria "Jóias Raras" quer implementar um sistema de atendimento automatizado via chatbot para sanar dúvidas básicas dos consumidores de forma ágil. O desafio reside em projetar e organizar o fluxo de menus, opções de busca e navegação do robô para garantir que os clientes encontrem as soluções de forma lógica e rápida.

**Conceito utilizado:** Uso combinado das técnicas de classificação e validação estrutural: _Card Sorting_ e Teste de Árvore (_Tree Testing_).

**Solução:**

1. **Mapeamento de Conteúdo:** Conduzir reuniões de grupo focal com a equipe de atendimento humano e analisar registros antigos para listar as dúvidas reais mais frequentes dos clientes.
2. **Etapa de Card Sorting (Desenho):** Escrever cada dúvida identificada em cartões (físicos ou digitais) e solicitar que os usuários reais agrupem as dúvidas da forma mais lógica para eles, atribuindo títulos a cada agrupamento. Isso define a arquitetura inicial de categorias do menu do chatbot.
3. **Etapa de Teste de Árvore (Validação):** Apresentar a estrutura hierárquica proposta a um novo grupo de usuários reais. Dar tarefas específicas (ex: _"Como você consulta o valor do frete para receber no mesmo dia?"_) e observar se os participantes conseguem encontrar a opção correta navegando de forma lógica pelo esqueleto textual dos menus.

**Resultado:** Um fluxo automatizado de chatbot estruturado exatamente conforme o modelo mental de categorização do cliente final, reduzindo frustrações e otimizando o tempo de atendimento.

**Por que essa solução funciona:** A solução funciona porque evita que o time de engenharia de software crie uma lógica de chatbot baseada na organização interna da empresa. Ao desenhar os menus via _Card Sorting_ e testá-los por _Tree Testing_, garante-se que os caminhos verbais do bot correspondam às expectativas dos usuários.

**O que preciso aprender com esse exemplo:**

- Use **Card Sorting** para **descobrir e projetar** a estrutura ideal de classificação de categorias.
- Use **Tree Testing** para **testar e validar** a navegabilidade de uma estrutura de árvore textual de menu pré-desenhada.