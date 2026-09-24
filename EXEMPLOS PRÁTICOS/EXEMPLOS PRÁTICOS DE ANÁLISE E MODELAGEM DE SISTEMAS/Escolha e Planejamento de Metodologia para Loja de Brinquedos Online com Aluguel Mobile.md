**Problema:** Uma tradicional loja de brinquedos deseja construir uma plataforma de e-commerce web para compra de produtos e, paralelamente, um aplicativo mobile nativo (Android e iOS) que ofereça de forma exclusiva o serviço de locação e assinatura de brinquedos. A empresa de TI precisa selecionar o modelo de ciclo de vida ideal para gerenciar o projeto, as divisões de equipe de desenvolvimento e o fluxo de entregas.

**Conceito utilizado:**

- **Modelos Prescritivos (Cascata)** vs. **Modelos Incrementais/Iterativos**.
- **Metodologias Ágeis (Scrum / Framework Kanban)**.

**Solução:**

1. **Refutação do Modelo Cascata**: O modelo linear rígido foi rejeitado porque exigiria a especificação completa de todas as particularidades de aluguel mobile de uma única vez. O cliente teria que esperar meses de programação cega antes de receber qualquer produto funcional para teste, gerando alta probabilidade de insatisfação.
2. **Adoção do Scrum (Abordagem Ágil e Incremental)**:
    - A equipe foi subdividida em frentes de trabalho paralelas (Site e-commerce, App Android, App iOS).
    - Os requisitos iniciais de negócio foram convertidos em **Histórias de Usuário** e estruturados em prioridades no **Product Backlog**.
    - O desenvolvimento foi organizado em **Sprints** (ciclos síncronos de tempo fixo), visando entregar incrementos parciais rápidos (exemplo: lançar primeiro o site para viabilizar as vendas enquanto se programa o aluguel mobile).
3. **Visualização e Gestão (Quadro Scrum/Kanban)**: Montagem de um painel visual (ex.: Trello) para controlar o progresso diário das tarefas do site:
    - _Backlog (A Fazer)_: Gerar interfaces do site (wireframes), Definir paleta de cores, Definir estrutura do banco de dados.
    - _Em andamento_: Codificação da API de pagamentos.
    - _Pronto_: Mapeamento conceitual do banco de dados.

**Resultado:** O cliente começou a vender brinquedos pelo site em poucas semanas, enquanto as equipes mobile colhiam feedbacks reais dos primeiros usuários das versões parciais (Sprints mobile), ajustando a lógica de aluguel de forma dinâmica.

**Por que essa solução funciona:** Metodologias ágeis reconhecem que em softwares complexos de mercado é impossível prever com total precisão todos os requisitos no dia zero do projeto. Dividir as entregas em incrementos funcionais parciais reduz o risco geral e viabiliza faturamento rápido ao negócio do cliente.

**O que preciso aprender com esse exemplo:** Softwares modernos com componentes multiplataforma e alto dinamismo devem fugir da linearidade rígida do modelo Cascata. Deve-se adotar **ciclos iterativos rápidos (Sprints de Scrum)** para entregar valor real de forma progressiva.
