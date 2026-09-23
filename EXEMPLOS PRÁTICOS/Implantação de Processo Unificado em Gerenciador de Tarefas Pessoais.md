**Problema:** Você é o gerente de projetos encarregado de construir um aplicativo para dispositivos móveis voltado ao gerenciamento de tarefas e lembretes pessoais. Sua missão é projetar um plano de ciclo de vida completo utilizando com rigor técnico a estrutura disciplinada e orientada por arquitetura do **Processo Unificado (PU)**.

**Conceito utilizado:**

- **As 4 Fases do Processo Unificado** (_Concepção, Elaboração, Construção, Transição_).
- **Eixos do PU**: Papel (quem), Artefato (o quê), Atividade (como) e Disciplina (quando).

**Solução:** O plano inicial de projeto foi desenhado sob o seguinte cronograma e divisão de tarefas:

1. **Fase de Concepção**:
    - _Atividades_: Definir a visão global, metas de negócio e viabilidade financeira. Levantar os requisitos lógicos centrais (inserir, editar e categorizar tarefas).
    - _Artefatos_: Documento de Visão inicial, lista estruturada de requisitos lógicos e diagramas simples de casos de uso.
2. **Fase de Elaboração**:
    - _Atividades_: Analisar em profundidade os riscos tecnológicos (ex.: concorrência de sincronização local de lembretes e segurança de senhas). **Definir e consolidar a arquitetura base estável** do software.
    - _Artefatos_: Especificação formal de arquitetura lógica, diagramas de classe UML e plano de contingência e mitigação de riscos.
3. **Fase de Construção**:
    - _Atividades_: Desenvolvimento ativo do sistema codificando os casos de uso planejados em ordem progressiva de complexidade (do básico ao avançado). Realização contínua de testes automatizados unitários e de integração.
    - _Artefatos_: Código-fonte codificado e documentado, scripts de testes lógicos automatizados e relatórios analíticos de cobertura de testes.
4. **Fase de Transição**:
    - _Atividades_: Lançamento de versão _beta_ controlada para usuários reais a fim de corrigir bugs em produção. Treinamento, homologação formal do cliente e deploy final nas lojas de aplicativos móveis.
    - _Artefatos_: Aplicativo homologado funcional, manuais do usuário em PDF e cronograma de publicação.

**Resultado:** O aplicativo de tarefas foi construído com arquitetura modular altamente expansível, sem que o projeto estourasse os limites orçamentários definidos.

**Por que essa solução funciona:** O PU foca intensamente na fase de **Elaboração** para extinguir os riscos de arquitetura antes de iniciar o desenvolvimento massivo. Isso evita que falhas estruturais graves (como sincronização paralela ineficiente) sejam descobertas tardiamente na fase de codificação.

**O que preciso aprender com esse exemplo:** No Processo Unificado, a arquitetura e os riscos são tratados de forma prioritária nas fases iniciais (**Concepção e Elaboração**). Isso prepara uma fundação sólida para que a codificação na fase de **Construção** seja previsível e sem retrabalhos estruturais.