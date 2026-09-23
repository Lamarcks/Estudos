[[EXEMPLOS-PRÁTICOS DE PROJETO DE SOFTWARE]]
#ASSUNTO

# Engenharia e Gestão de Projetos de Software

A gestão de projetos de software engloba o planejamento, a liderança e a execução de atividades para desenvolver soluções tecnológicas eficazes dentro do prazo, custo e qualidade estabelecidos. Ela evoluiu de modelos lineares e preditivos tradicionais para abordagens altamente adaptáveis, ágeis e inovadoras, focadas na entrega de valor e no alinhamento estratégico com o negócio. O sucesso de um projeto moderno depende de um equilíbrio rigoroso entre governança corporativa, práticas consolidadas de engenharia de software (como arquitetura robusta e controle de configuração) e a eficiência das equipes de desenvolvimento.

---

## Conceitos principais

Para garantir a precisão no estudo, os conceitos estruturais da matéria são definidos a seguir:

- **Projeto:** Planejamento temporário estruturado com o propósito de criar um produto, serviço ou resultado único e útil.
- **Gerenciamento de Projetos:** Disciplina que aplica competências, ferramentas e técnicas para dimensionar recursos, liderar equipes, mitigar riscos e assegurar a entrega e aceitação do software.
- **Ciclo de Vida do Projeto:** Sequência de fases (da concepção à entrega final) que define a estrutura de controle, tomada de decisões e governança do projeto.
- **Métrica da Qualidade:** Medida quantitativa do grau em que um sistema, componente ou processo possui um determinado atributo de qualidade.
- **Arquitetura de Software:** Estrutura organizacional do sistema, definindo seus componentes, conectores, restrições de integração e como as partes cooperam entre si.
- **Gerenciamento de Configuração de Software (SCM):** Processo formal que controla e rastreia mudanças nos itens de configuração de software (SCIs) ao longo de todo o ciclo de desenvolvimento.
- **Governança de TI e ESG:** Alinhamento estratégico dos recursos de TI com conformidades regulatórias e princípios ambientais, sociais e éticos corporativos.

---

## Conteúdo explicado

### 1. Fundamentos e Fatores Humanos na Gestão de Projetos

A gestão de projetos de software é guiada por competências técnicas e comportamentais. Segundo o **Project Management Institute (PMI)**, o gerente de projetos ideal deve equilibrar três talentos cruciais, representados pelo **Triângulo de Talentos do PMI**:

1. **Técnicas em Gestão de Projetos:** Práticas e experiências em conduzir cronogramas, custos e escopos.
2. **Liderança:** Comportamento interpessoal que incentiva a cooperação, resolve conflitos e engaja o time.
3. **Gestão Estratégica e Negócios:** Alinhamento técnico do projeto para gerar retorno financeiro e atender às constantes mudanças do mercado.

#### Gestão de Stakeholders e Responsabilidades

As interações de stakeholders são equilibradas por três fatores estruturais essenciais:

- **Autoridade:** Posição ocupada na hierarquia e poder formal na delegação de atividades.
- **Comunicação:** Recursos disponibilizados para o fluxo contínuo de dados e o nível de formalidade adotado.
- **Atividade:** Divisão física e sequencial do trabalho através de instrumentos de delegação.

#### Resolução de Conflitos

Para tratar desavenças interpessoais ou técnicas que ameaçam o andamento do projeto, adota-se um **caminho básico de resolução**: \[\text{Identificar o Problema} \rightarrow \text{Identificar Origem/Causa} \rightarrow \text{Encontrar Alternativas} \rightarrow \text{Aplicar a Solução}\] Se problemas pequenos não forem negociados ou facilitados, podem crescer até forçar a suspensão ou cancelamento do projeto.

---

### 2. Ciclo de Vida e Processos do Projeto

O ciclo de vida clássico de um projeto divide-se em quatro fases sequenciais fundamentais:

1. **Iniciação:** Alinhamento dos objetivos com o negócio, definição preliminar do escopo e obtenção da autorização formal de abertura.
2. **Planejamento:** Detalhamento de como monitorar e controlar as atividades, premissas, restrições e recursos.
3. **Execução:** Fase de maior esforço e produção física, onde ocorre o desenvolvimento, design, codificação e testes.
4. **Finalização:** Obtenção do aceite formal de entrega, arquivamento de documentos e registro de lições aprendidas.

#### Termo de Abertura do Projeto (TAP)

O TAP é o documento formal que autoriza o início do projeto. Seus componentes obrigatórios são:

- **Gestor do Projeto:** Definição do profissional encarregado, usualmente nomeado pelos patrocinadores (_sponsors_).
- **Principais Pontos:** Definição de como e por quem as atividades serão entregues.
- **Justificativa:** Indicação estratégica de prioridade do projeto frente a outros investimentos.
- **Restrições e Premissas:** Limitações financeiras, profissionais e de prazos.
- **Escopo:** Requisitos detalhados solicitados pelos stakeholders.

#### Diferenças entre Ciclos de Vida

Os modelos variam conforme o nível de incerteza técnica e volatilidade de requisitos:

|Ciclo de Vida|Grau de Mudanças|Frequência de Entrega|Características Principais|
|:--|:--|:--|:--|
|**Preditivo** _(Waterfall)_|Baixo|Baixa (entrega única ao final)|Todo o plano é traçado no início; focado em linearidade e sem replanejamento.|
|**Incremental**|Baixo|Alta (em blocos sucessivos)|O projeto é decomposto em partes funcionais que são disponibilizadas sequencialmente.|
|**Iterativo**|Alto|Baixa|Prototipação intensa e empirismo técnico com os usuários para detalhar regras de alta complexidade.|
|**Adaptativo** _(Ágil)_|Alto|Alta (curto prazo)|Conjunção de entregas rápidas e evolução constante com forte interação diária dos stakeholders.|

---

### 3. Metodologias Ágeis e Framework Scrum

O **Manifesto Ágil** (2001) estabeleceu quatro valores centrais focados na flexibilidade e no fator humano:

1. **Indivíduos e interações** mais que processos e ferramentas.
2. **Produto em funcionamento** mais que documentação abrangente.
3. **Colaboração com o cliente** mais que negociação de contratos.
4. **Responder a mudanças** mais que seguir um plano.

#### O Framework Scrum

Trata-se de um modelo ágil e empírico estruturado em papéis, artefatos e reuniões com limite de tempo (_timeboxing_).

```
[Product Backlog]
       │
       ▼ (Sprint Planning)
[Sprint Backlog] ────► [Sprint (2-4 semanas)] ◄─── (Daily Scrum)
                               │
                               ▼
                        [Incremento Pronto] ──► (Sprint Review) & (Sprint Retrospective)
```

##### Artefatos do Scrum

- **Product Backlog:** Lista dinâmica e ordenada de todos os requisitos conhecidos necessários no produto.
- **Sprint Backlog:** Conjunto de itens selecionados do Product Backlog para serem implementados durante a Sprint atual, detalhados em tarefas.
- **Incremento:** Software utilizável, testado e com status de "concluído" produzido ao final da Sprint.

##### Responsabilidades (Papéis)

- **Product Owner (PO):** Representante dos negócios, responsável único por gerenciar, priorizar e dar clareza ao Product Backlog para otimizar o valor do trabalho.
- **Scrum Master (SM):** Líder servidor que apoia a auto-organização do time, remove impedimentos de progresso e garante a aplicação da metodologia.
- **Time de Desenvolvimento:** Profissionais auto-organizados responsáveis por entregar incrementos de software "prontos" a cada ciclo.

##### Eventos do Scrum (Timebox)

- **Sprint:** Ciclo de desenvolvimento fixo de 2 a 4 semanas no qual o incremento é produzido.
- **Planejamento da Sprint (_Sprint Planning_):** Definição colaborativa do objetivo da Sprint (duração de 4 a 8 horas).
- **Reunião Diária (_Daily Scrum_):** Sincronização diária rápida (máximo 15 minutos) realizada pelo time para apontar progressos e gargalos.
- **Revisão da Sprint (_Sprint Review_):** Reunião de validação do incremento funcional junto aos stakeholders (2 a 4 horas).
- **Retrospectiva da Sprint:** Reunião focada na melhoria contínua de processos, ferramentas e relações do time.

---

### 4. Abordagens Inovadoras na Gestão

A união de novos conceitos busca aumentar a eficiência técnica e reduzir desperdícios no fluxo:

- **Design Thinking:** Processo disruptivo fundamentado em três princípios: **Empatia** (compreender os desejos das pessoas), **Colaboração** (co-criação multidisciplinar) e **Experimentação** (testar falhas rapidamente em laboratório - _fail fast_).
- **MVP (Mínimo Produto Viável):** Entrega funcional que visa validar hipóteses de negócios no menor tempo e com o menor esforço possível. Não se trata apenas do software mais simples, mas daquele que efetivamente gera resultados esperados.
- **Lean:** Filosofia voltada à eliminação sistemática de desperdícios (incluindo o retrabalho na correção de códigos), redução de custos e aumento do valor gerado para o cliente.
- **Six Sigma (6s):** Processo estruturado de melhoria contínua focado no controle estatístico de defeitos. Utiliza a medição de **DPO** (_Defeitos por Oportunidade_) e **DPMO** (_Defeitos por Milhão de Oportunidades_): \[\text{DPO} = \frac{\text{Defeitos Identificados}}{\text{Itens de Software} \times \text{Oportunidades de Defeitos}} \quad \text{e} \quad \text{DPMO} = \text{DPO} \times 1.000.000\]

---

### 5. Qualidade do Processo e Métricas (IEEE)

A gestão da qualidade do software exige regularidade e disciplina para sustentar indicadores quantitativos.

#### Métricas de Qualidade (Definições IEEE)

Segundo os padrões IEEE, a avaliação de atributos é dividida em quatro níveis lógicos de medição:

1. **Atributo:** Propriedade física ou abstrata mensurável de uma entidade (Ex: histórias de usuário desenvolvidas).
2. **Métrica:** Medida quantitativa do grau em que o processo ou componente possui o atributo (Ex: correlação de histórias entregues).
3. **Medição:** Ato ou processo operacional de atribuição de um número ou categoria.
4. **Medida:** Valor ou número final resultante do processo de medição (Ex: horas gastas por Sprint).

#### Níveis de Maturidade de Processos (CMMI)

O modelo CMMI classifica a maturidade operacional das organizações em 5 níveis lógicos:

1. **Executada:** As atividades ocorrem de modo empírico para entregar o produto.
2. **Controlada:** Implantação de processos formais de gerenciamento.
3. **Padronizada:** Processos são estruturados institucionalmente (gerenciamento de riscos, soluções).
4. **Medido:** Processos operam sob controle estatístico e métricas quantitativas.
5. **Em Otimização:** Foco total na melhoria contínua e inovação dos processos.

---

### 6. Ferramentas Visuais e Documentação de Projetos

A comunicação eficiente com stakeholders exige o uso de ferramentas informativas e enxutas, evitando-se o desperdício de documentações extensas e inacessíveis.

- **Gráfico de Gantt:** Cronograma linear clássico ideal para mapear durações, dependências automáticas e estágios de módulos (aplicável também em modelos ágeis).
- **Kanban:** Quadro de atividades simples exposto em colunas (Tipicamente: _Prontas para iniciar_, _Em execução_ e _Concluídas_) que facilita a identificação visual de impedimentos pelo Scrum Master.
- **WBS / EAP (Work Breakdown Structure):** Decomposição hierárquica e estruturada do processo de desenvolvimento ou do produto de software em pacotes de trabalho.
- **Gráfico Burndown:** Gráfico de progresso que rastreia a quantidade de Story Points concluídos versus o esforço planejado ao longo das Sprints.

---

### 7. Arquitetura de Software

A arquitetura de software reduz riscos de construção e facilita a manutenção estrutural do sistema em sua fase de evolução.

#### Estilos vs. Padrões Arquitetônicos

- **Estilo Arquitetônico:** Classificação ampla de categorias de sistemas. Define um conjunto de componentes integrados por conectores, restrições estruturais e modelos semânticos de análise (Ex: centralizados em dados, orientados a objetos, em camadas).
- **Padrão Arquitetônico:** Uma regra que impõe transformações e trata de comportamentos específicos da infraestrutura (Ex: controle de concorrência ou sincronização em tempo real).

#### Diretrizes para Decisões Arquitetônicas (Pressman)

Projetistas seniores devem equilibrar cinco pilares conceituais na tomada de decisão:

- **Economia:** Abstração de elementos para evitar complexidade e consumo de recursos desnecessários.
- **Visibilidade:** Clareza técnica e comunicação eficaz das decisões de design para o time.
- **Espaçamento:** Grau adequado de separação de interesses, impedindo fragmentação excessiva.
- **Simetria:** Balanceamento estrutural e comportamental que facilita o aprendizado do código.
- **Emersão:** Flexibilidade para que o controle e a expansibilidade do software surjam de forma auto-organizada.

---

### 8. Gestão Avançada de Software (SCM, CI/CD, Observabilidade e UX)

#### Gerenciamento de Configuração (SCM) e Baseline

O SCM é composto por quatro elementos centrais:

1. **Elementos de componente:** Sistema de banco de dados ou arquivos para gerenciar os itens de configuração (SCIs).
2. **Elementos de processo:** Tarefas formais para autorizar e aplicar alterações.
3. **Elementos de construção:** Ferramentas automáticas que montam componentes validados.
4. **Elementos humanos:** A disciplina e as características adotadas pelo time na execução.

> ⚠️ **Conceito de Baseline (Referência):** É um marco no desenvolvimento caracterizado por um ou mais itens de configuração (SCIs) formalmente revisados, testados e aprovados técnica e gerencialmente, que passa a servir de base inalterável para futuras evoluções. Mudanças em uma baseline exigem procedimentos rígidos de controle.

#### Integração Contínua e Implantação Contínua (CI/CD)

Prática originada em metodologias como XP e DevOps. Consiste na fusão diária de componentes com o incremento de software em evolução.

- **Pilares do CI/CD:** Minimizar variantes de código, testar e integrar com alta frequência e automatizar processos.
- **Vantagens:** Feedback imediato aos desenvolvedores, redução do tempo de integração final e geração de relatórios de métricas mais precisos.

#### Observabilidade e Detecção de Anomalias

Consiste no monitoramento digital avançado dos processos em tempo real para tomada de decisões estratégicas de negócios.

- **Detecção de Anomalias:** Identificação de padrões comportamentais de sistemas operacionais que desviam radicalmente do esperado (anomalias e _outliers_).
- **Práticas-Chave:** Coleta sistemática de logs e métricas de desempenho; definição de limites de comportamento normal; uso de algoritmos analíticos automáticos; e mentalidade ativa das equipes para investigar falhas.

#### Prototipação e UX Design

O processo lógico de **User Experience (UX)** estruturado em cinco etapas de iteração contínua é mapeado abaixo:

```
[Rascunhar a Interface (Rabiscos/Esboço)]
                 │
                 ▼
     [Criar o Protótipo Virtual]
                 │
                 ▼
  [Adicionar Código de Entrada/Saída]
                 │
                 ▼
     [Testar o Protótipo com Usuários]
                 │
                 ▼
    [Atualizar o Protótipo com Feedbacks]
```

O principal elemento no projeto de interação é a **modelagem de personas**, que sintetiza as características, sentimentos e limitações do público-alvo.

---

### 9. Governança e Paradigmas Estratégicos (ITIL, COBIT e ESG)

A maturidade organizacional requer o uso coordenado de frameworks estratégicos de governança e sustentabilidade corporativa:

- **ITIL:** Biblioteca de gerenciamento aplicável à infraestrutura de TI que fornece suporte prático e flexível para a transformação digital de ativos físicos, digitais e humanos.
- **COBIT (ISACA):** Manual internacional focado em auditoria corporativa e controle de sistemas de informação.
- **ESG (Environmental, Social, Governance):** Paradigma que equilibra objetivos financeiros de curto prazo com impactos éticos de longo prazo. É dividido em três pilares:
    1. _Environmental (Ambiental):_ Mitigação de emissões de carbono, eficiência energética e gestão de resíduos.
    2. _Social (Social):_ Relações humanas, bem-estar mental e físico, diversidade e inclusão dos colaboradores.
    3. _Governance (Governança):_ Transparência ética, políticas de remuneração de altos cargos, segurança de dados e conformidade regulatória.

---

## Conceitos que não posso confundir

```
  ┌─────────────────────────────────────────────────────────────────┐
  │                           ESCOPO                                │
  │                                                                 │
  │  ┌─────────────────────────────┐   ┌─────────────────────────┐  │
  │  │      ESCOPO DO PRODUTO      │   │    ESCOPO DO PROJETO    │  │
  │  │                             │   │                         │  │
  │  │ Define o que o cliente quer │   │ Define todo o trabalho  │  │
  │  │ de requisitos funcionais e  │   │ e os processos de TI    │  │
  │  │ não funcionais.             │   │ para realizar a entrega │  │
  │  └─────────────────────────────┘   └─────────────────────────┘  │
  └─────────────────────────────────────────────────────────────────┘
```

- **Escopo do Produto vs. Escopo do Projeto:**
    - _Escopo do Produto:_ Descreve as propriedades, características físicas e funcionalidades requeridas para que o software atenda às necessidades operacionais do cliente.
    - _Escopo do Projeto:_ Compreende todo o trabalho, atividades, processos técnicos, sequência de tarefas e prazos estritamente necessários para construir e entregar o produto.
- **Gerente de Projeto vs. Scrum Master:**
    - _Gerente de Projeto:_ Exerce autoridade baseada em comando e controle (modelo preditivo); ele planeja e "empurra" a demanda direcionando o "o que" e o "como fazer" para a equipe.
    - _Scrum Master:_ Atua como um líder servidor e facilitador; ele não dá ordens diretas, mas remove impedimentos e apoia a equipe auto-organizada que "puxa" as tarefas para decidir "como fazer" em colaboração.
- **Atributo vs. Métrica vs. Medição vs. Medida:**
    - _Atributo:_ O aspecto físico/abstrato sob contagem (Ex: as falhas em um sistema).
    - _Métrica:_ O método/fórmula quantitativa para analisar o atributo (Ex: quantidade de falhas detectadas na Sprint).
    - _Medição:_ O processo operacional de coleta (Ex: realizar testes de produto de software e catalogar os erros).
    - _Medida:_ O dado numérico de saída (Ex: foram identificadas exatamente 8 falhas).
- **Estilo Arquitetônico vs. Padrão Arquitetônico:**
    - _Estilo:_ Define a divisão macroestrutural e as regras de conectores de um sistema (Ex: separar o processamento em camadas lógicas).
    - _Padrão:_ Trata de uma questão tática, comportamental e de infraestrutura dentro de um estilo (Ex: definir sincronização paralela de dados na rede).
- **ITIL vs. COBIT:**
    - _ITIL:_ Fornece processos práticos de suporte ao ciclo de serviços e transformação digital dos ativos.
    - _COBIT:_ Foca no alinhamento estratégico de controle corporativo, compliance e auditoria sob a tutela da ISACA.

---

## Pontos importantes para prova

### Definições Críticas

- **Baseline (Referência):** Um marco formalmente revisado e acordado que serve de base estável para desenvolvimentos futuros, alterada somente via controle formal.
- **MVP:** Validação de modelo de negócio com esforço mínimo, assegurando entrega funcional de sucesso.
- **Burndown:** Rastreia o esforço que resta para concluir o planejado a cada período.

### Classificações Cruciais

- **Níveis do CMMI:** 1. Executada \(\rightarrow\) 2. Controlada \(\rightarrow\) 3. Padronizada \(\rightarrow\) 4. Medido \(\rightarrow\) 5. Em otimização.
- **Pilares do ESG:** Environmental (Ambiental), Social (Pessoas) e Governance (Ética de Gestão).
- **Triângulo do PMI:** Técnicas em Gestão \(\leftrightarrow\) Liderança \(\leftrightarrow\) Gestão de Negócios.

### Etapas e Passos de Processo

- **Construção de UX (Pressman):** Rascunhar interface \(\rightarrow\) Protótipo digital \(\rightarrow\) Adicionar código de E/S \(\rightarrow\) Testar \(\rightarrow\) Atualizar.
- **Ciclo de Vida do Projeto:** Iniciação \(\rightarrow\) Planejamento \(\rightarrow\) Execução \(\rightarrow\) Finalização.
- **Tratamento de Anomalias (Observabilidade):** Coleta de dados \(\rightarrow\) Definição de padrões normais \(\rightarrow\) Execução de algoritmos \(\rightarrow\) Mindset investigativo.

### Regras e Exceções

- **Regra da Sprint:** Uma Sprint do Scrum é estritamente de período fixo (_timeboxing_ de 2 a 4 semanas) e não pode sofrer extensões.
- **Exceção de Cancelamento de Sprint:** Apenas o Product Owner (PO) detém o poder formal para cancelar uma Sprint (ou o projeto inteiro) antes do prazo se o retorno esperado deixar de existir.

---

## Revisão rápida

- **O que é o Triângulo de Talentos do PMI?** Técnicas de Gestão de Projetos, Liderança e Gestão Estratégica de Negócios.
- **Quais os 4 valores Ágeis?** Indivíduos/Interações > Processos/Ferramentas; Software Funcional > Documentação Extensa; Colaboração > Contratos; Responder a Mudanças > Seguir Plano.
- **Quais os 5 eventos do Scrum?** Sprint, Planejamento da Sprint, Daily Scrum, Revisão da Sprint e Retrospectiva da Sprint.
- **Quais os 3 pilares do Design Thinking?** Empatia, Colaboração e Experimentação.
- **Qual a diferença estrutural entre Gantt e Kanban?** Gantt mapeia dependências de tarefas em linha de tempo; Kanban foca no fluxo visual das tarefas em colunas (_To Do, Doing, Done_).
- **Quais os elementos de medição da qualidade do IEEE?** Atributo, Métrica, Medição e Medida.
- **O que é a Baseline no SCM?** Um item de configuração de software (SCI) formalmente aprovado em revisão técnica que serve de marco para novas alterações.
- **O que significa DPO e DPMO no Six Sigma?** DPO calcula os defeitos por oportunidade identificados em itens de software; DPMO escala essa proporção para um milhão de oportunidades a fim de obter o índice estatístico de qualidade.

---
