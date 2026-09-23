[[EXEMPLOS-PRÁTICOS DE INTERFACE E USABILIDADE]]
#ASSUNTO

## Visão geral

O estudo de **Interface e Usabilidade** investiga a relação entre o ser humano e os sistemas tecnológicos, com foco na concepção de soluções fáceis de usar, eficientes e agradáveis. Este material reúne fundamentos teóricos de Interação Humano-Computador (IHC), engenharia de requisitos, design de interação, técnicas de prototipagem, métodos de avaliação (inspeção e observação) e práticas de acessibilidade e gamificação. O objetivo principal é estruturar o processo iterativo de **Design Centrado no Usuário (DCU)** para construir soluções digitais que ofereçam uma experiência excelente, reduzindo fricções cognitivas e erros operacionais.

---

## Conceitos principais

- **Interface**: Conjunto de todos os componentes de um sistema interativo com os quais as pessoas entram em contato físico (botões, telas touch), perceptivo (imagens, sons) ou conceitual (mensagens, orientações para ações futuras). Atua como o canal de comunicação entre o usuário e o sistema.
- **Usabilidade**: Um atributo de qualidade que mede a facilidade de uso das interfaces de usuário. Segundo a **ISO 9241-11 (2018)**, é a extensão na qual um sistema, produto ou serviço pode ser usado por usuários específicos para atingir objetivos específicos com **eficácia, eficiência e satisfação** em um contexto específico de uso.
- **Experiência do Usuário (UX - User Experience)**: Engloba todos os processos físicos, cognitivos e emocionais desencadeados no usuário a partir da sua interação com um produto, sistema ou serviço. Diferente da usabilidade (que foca na interação direta), a UX cobre **toda a jornada do usuário**, incluindo expectativas antes do uso e reflexões/memórias após o término da tarefa.
- **Ergonomia e Fatores Humanos**: A ergonomia estuda cientificamente a relação entre as pessoas e seu ambiente de trabalho. O conceito de fatores humanos expande essa visão para analisar as dimensões cognitivas, emocionais e comportamentais de interação, buscando otimizar o design das máquinas de acordo com as capacidades físicas e mentais humanas.
- **Affordance**: Conceito adotado por Donald Norman que define as características e propriedades visuais ou físicas de um objeto que comunicam, de forma intuitiva, como ele deve ser operado ("convite formal ao uso").
- **Design Centrado no Ser Humano (DCH / DCU)**: Abordagem de projeto orientada a compreender ativamente as necessidades, objetivos e contextos das pessoas, aplicando ciclos repetidos de concepção, prototipação, teste e refinamento.

---

## Conteúdo explicado

### 1. Evolução Histórica da IHC e Usabilidade

A relação do homem com suas ferramentas iniciou-se na pré-história com a adaptação de pedras e madeiras para caçar de forma mais eficaz. No entanto, a usabilidade como diferencial competitivo começou a aparecer em anúncios de produtos na década de 1930.

- **Segunda Guerra Mundial**: Foi o grande divisor de águas, exigindo que governos investissem na compreensão de erros humanos cometidos durante a operação de painéis complexos de equipamentos militares.
- **ENIAC (1946)**: Primeiro computador programável eletrônico de uso geral; priorizava reduzir o esforço operacional de conexão física de cabos e válvulas.
- **Década de 1950**: O desenvolvimento de linguagens de programação de alto nível (COBOL, FORTRAN) e cartões perfurados facilitou a interação lógica com o computador.
- **Década de 1960 (Início da GUI)**: O software _Sketchpad_ (1963) permitiu desenhar diretamente na tela, criando o primeiro passo para as interfaces gráficas (GUI). Em 1968, Douglas Engelbart apresentou o primeiro mouse, revolucionando a precisão de seleção em telas.
- **Décadas de 1970 e 1980**: A popularização dos computadores pessoais (PCs) para usuários leigos tornou obrigatória a simplificação das interfaces, estabelecendo a IHC como campo de pesquisa estruturado.
- **Era da Internet (Anos 1990 em diante)**: A web permitiu que os usuários mudassem facilmente de um site para outro caso encontrassem interfaces confusas, consolidando o investimento em UX e usabilidade como fatores de sobrevivência das empresas.

### 2. O Ciclo do Projeto Centrado no Usuário (ISO 9241-210)

O desenvolvimento de qualquer interface interativa requer um processo estruturado em quatro etapas cíclicas e iterativas:

1. **Análise e especificação do contexto de uso**: Identificar quem são as pessoas, quais são seus objetivos, as tarefas que executarão e as características dos ambientes físico, técnico, social, cultural e organizacional em que o sistema será inserido.
2. **Especificação dos requisitos do usuário e da organização**: Consolidar as metas, restrições e objetivos específicos de usabilidade que o projeto deve atingir.
3. **Produção das soluções de projeto (Design)**: Desenvolver soluções preliminares de interface. Começa-se com protótipos de baixa fidelidade e evolui-se de forma incremental com base em refinamentos.
4. **Avaliação do projeto**: Testar sistematicamente as soluções propostas junto aos usuários reais para validar se os requisitos de uso foram cumpridos e identificar problemas pendentes.

### 3. Processos Cognitivos e Ergonomia Cognitiva

Para projetar sistemas fáceis de usar, é preciso compreender como a mente processa informações. O processo cognitivo compreende cinco etapas básicas:

- **Captação**: Sensores humanos (visão, audição, tato, etc.) capturam as pistas ambientais.
- **Seleção (Atenção)**: O cérebro escolhe quais estímulos processar, já que os sensores captam mais dados do que a capacidade de processamento imediato.
- **Filtragem**: Filtros internos (valores, personalidade, repertório, experiências passadas, crenças) determinam o que é relevante.
- **Interpretação**: O cérebro analisa e dá sentido às informações filtradas.
- **Ação**: A resposta resultante, que pode ser cognitiva (pensar, entender um ícone) ou motora (clicar, falar).

Uma boa interface reduz a **carga cognitiva**, garantindo que as informações apresentadas se adéquem aos sensores e filtros dos usuários para acelerar o entendimento e evitar erros operacionais.

### 4. Metodologias Ágeis de Projeto (Design Thinking, Design Sprint e Scrum)

Para responder às necessidades de negócios dinâmicos, o projeto centrado no usuário utiliza metodologias de validação rápida:

#### Design Thinking

Propõe encontrar o equilíbrio entre três dimensões fundamentais: **Desejabilidade** (necessidades do usuário), **Viabilidade** (estratégia de negócio) e **Praticabilidade** (recursos técnicos disponíveis). É dividido em seis fases:

- _Compreensão_: Pesquisa de campo e descoberta focada no que o usuário faz, pensa e sente.
- _Definição_: Organização, análise e síntese dos dados para focar nos problemas reais.
- _Ideação_: Geração colaborativa de grande volume de ideias sem julgamento inicial.
- _Prototipação_: Construção ágil de maquetes e telas para tangibilizar as ideias.
- _Avaliação_: Teste dos protótipos com usuários para colher feedbacks e refinar a solução.
- _Implementação_: Execução final e desenvolvimento técnico da interface validada.

#### Design Sprint (Google Ventures)

Reduz o processo de descoberta e validação de ideias a uma semana de trabalho intensivo com uma equipe multidisciplinar:

- **Segunda-feira**: Compreender o problema, desenhar a jornada de uso e definir o alvo/desafio da semana.
- **Terça-feira**: Explorar soluções existentes e desenhar propostas individuais de telas.
- **Quarta-feira**: Debater as ideias, votar nas soluções mais promissoras e criar o _storyboard_ detalhado.
- **Quinta-feira**: Construir o protótipo funcional baseado no storyboard e alinhar o roteiro dos testes.
- **Sexta-feira**: Testar o protótipo com pelo menos 5 usuários reais do perfil-alvo, colhendo o aprendizado.

#### Scrum integrado à UX

Para garantir usabilidade em metodologias ágeis de desenvolvimento de software, recomenda-se a inserção de um **Sprint 0** focado exclusivamente na pesquisa inicial dos usuários e na definição do backlog de usabilidade. As atividades de descoberta de UX devem ser incorporadas ao backlog e priorizadas em cada ciclo curto (Sprints de 1 a 4 semanas) de desenvolvimento.

### 5. Métodos de Pesquisa e Levantamento de Requisitos

Os requisitos de um sistema interativo não devem ser baseados em suposições da equipe técnica, mas sim em dados coletados junto ao público-alvo. Dividem-se os métodos de pesquisa de campo em:

|Tipo de Método|Nome do Método|Funcionamento e Aplicação Prática|
|:--|:--|:--|
|**Escuta**|**Entrevista Tradicional**|Sessões individuais baseadas em um roteiro semiestruturado. Devem priorizar perguntas abertas ("como", "por que") para extrair sentimentos, objetivos e experiências passadas. Evita-se perguntas hipotéticas.|
|**Escuta**|**Grupo Focal**|Discussão de 5 a 10 participantes de perfil semelhante sob mediação. Facilita a convergência de opiniões e ideias compartilhadas, mas o moderador deve evitar que participantes dominantes influenciem os demais.|
|**Escuta**|**Questionários**|Método ágil e de baixo custo para alcançar grande volume de dados. Prioriza perguntas fechadas e de múltipla escolha para rápida tabulação quantitativa, sem cansar o respondente.|
|**Observação**|**Observação de Campo**|O pesquisador registra comportamentos em ambientes naturais sem intervir ou guiar a ação, visando identificar as dificuldades cotidianas reais.|
|**Observação**|**Análise de Tarefas**|Mapeamento minucioso do passo a passo lógico que o usuário realiza para completar uma tarefa. Revela os modelos mentais e gargalos do processo.|
|**Observação**|**Shadowing**|O pesquisador acompanha o usuário em sua rotina diária como uma "sombra", construindo empatia profunda sobre as pressões e fatores externos que afetam o uso da tecnologia.|
|**Misto**|**Entrevista Contextual**|Realização de uma entrevista semiestruturada no exato ambiente de uso do produto, permitindo alternar entre perguntas e observação direta do comportamento.|
|**Misto**|**Diário de Uso**|Os participantes documentam suas interações em um diário físico ou aplicativo por médio ou longo prazo. Excelente para capturar flutuações contextuais e hábitos ao longo do tempo.|
|**Misto**|**Card Sorting**|Os participantes organizam cartões físicos ou digitais contendo dados da interface em grupos que façam sentido lógico para eles, definindo nomes para os grupos. Essencial para arquitetar menus e fluxos intuitivos de navegação.|

### 6. Artefatos de Especificação de Usuários e Suas Jornadas

Uma vez coletados, os dados densos e complexos das pesquisas precisam ser representados de maneira clara para o time de desenvolvimento:

- **Personas**: Arquétipos fictícios que sintetizam os comportamentos, características demográficas, preferências, dores, ferramentas e objetivos dos grupos reais identificados no público-alvo. Auxiliam a gerar empatia e servem de guia no recrutamento para testes de usabilidade.
- **Mapa de Empatia**: Matriz visual estruturada em quadrantes para rastrear o que o usuário _pensa, sente, ouve, vê, diz e faz_, destacando no rodapé suas _Dores_ (obstáculos, frustrações) e _Ganhos_ (necessidades, sonhos).
- **Cenários de Uso**: Narrativas descritivas ou gráficas (_Storyboards_) que contam um contexto de uso típico, abordando a motivação inicial, a sequência lógica de ações do usuário e o desfecho da interação na interface.
- **Mapa de Jornada do Usuário**: Roteiro visual que mapeia a experiência de uso ponta a ponta. Estrutura-se em três zonas principais:
    - _Zona A (Lentes)_: Determina o escopo da jornada, descrevendo o cenário e a Persona envolvida.
    - _Zona B (Experiência)_: Ilustra as fases da jornada, contendo as ações, pensamentos, pontos de contato diretos e a curva emocional de sentimentos.
    - _Zona C (Insights)_: Consolida as dores, oportunidades de refinamento futuro e os responsáveis técnicos internos de cada fase.
- **Mapa de História do Usuário (User Story Map)**: Técnica ágil que decompõe as metas de uso do software em três níveis organizados horizontalmente e verticalmente:
    - _Atividades_: Ações amplas e gerais que o usuário realiza.
    - _Etapas_: Subtarefas específicas necessárias para concluir cada atividade.
    - _Detalhes_: Pequenas interações técnicas de tela que complementam as etapas.

### 7. Princípios do Design Visual Aplicados a Interfaces

As propriedades de aparência e diagramação de uma tela determinam o sucesso ou falha do entendimento intuitivo do sistema. Cinco princípios fundamentais de design visual devem guiar essa construção:

- **Escala**: Diferenciar o tamanho relativo dos elementos para indicar importância e hierarquia em um fluxo de leitura visual.
- **Hierarquia Visual**: Utilizar tamanho, posição e cor para guiar ativamente a ordem em que o olho varre a tela. No ocidente, a leitura segue o formato de "escanear" da esquerda para a direita, de cima para baixo.
- **Equilíbrio**: Organização de componentes de maneira harmoniosa e proporcional.
- **Contraste**: Distinguir elementos com funções e comportamentos diferentes. Textos colocados sobre fundos de cores semelhantes prejudicam diretamente a legibilidade. Devem-se testar as opções em ambientes reais de uso.
- **Gestalt**: Aplicar as leis de percepção do cérebro, estruturando a interface para que as informações sejam compreendidas como um todo coeso.

#### Diretrizes de Ergonomia Física nos Layouts Móveis

Ao projetar para dispositivos móveis, o tamanho e o posicionamento de itens devem levar em conta medidas físicas.

- **Uso do Polegar**: Pesquisas de Hoober (2013) observando 1.333 usuários demonstraram que **49% das pessoas utilizam o polegar** para operar o telefone celular. Com base nisso, o posicionamento dos botões e menus prioritários e frequentes deve ocupar as regiões inferiores e centrais da tela ("área de alcance fácil"), evitando posições de topo que exigem movimentos forçados ou uso das duas mãos.
- **Tamanho de Botão**: A área física de toque em telas móveis deve respeitar as medidas do dedo dos usuários maiores para evitar toques involuntários e erros de seleção.

### 8. Estilos de Interação e Microinterações

Os **Estilos de Interação** definem as maneiras pelas quais as pessoas inserem e recebem dados do sistema:

- _Linguagem Natural_: Uso de voz, gestos corporais ou digitação de sentenças comuns (chatbots estruturados por NLP).
- _Linguagem de Comando_: Uso de códigos específicos e atalhos de caracteres (terminal de comandos).
- _Seleção por Menus_: Apresentação de opções fixas onde o usuário clica ou toca diretamente, sem a necessidade de memorizar comandos.
- _Preenchimento de Formulários_: Indicado para coletar grande quantidade de dados por campos de texto ou caixas de seleção, estruturado como os formulários físicos do cotidiano.
- _WIMP (Windows, Icons, Menus, Pointers)_: Paradigma visual baseado em janelas de delimitação, ícones analógicos representativos do mundo físico, menus suspensos de escolha e ponteiros de rastreamento do mouse.

#### Microinterações

São alterações sutis e pontuais que ocorrem em elementos específicos ao sofrerem uma ação. Servem para indicar o estado do sistema, fornecer feedback de ações concluídas e prevenir erros acidentais (exemplo: animação do botão de "Adicionar ao carrinho"). Conforme Saffer (2013), dividem-se em quatro elementos mecânicos:

1. **Gatilho (Trigger)**: O disparador da ação (clique do usuário ou gatilho automático por mudança de estado do sistema).
2. **Regras**: Parâmetros que ditam o comportamento lógico do elemento quando acionado.
3. **Feedback**: A indicação perceptiva (visual, sonora, tátil) comunicando o que mudou no elemento.
4. **Loops e Modos**: Definições temporais de repetição, duração do comportamento e retorno do elemento ao seu estado padrão original.

### 9. A Estrutura da Experiência do Usuário (Modelo de Garrett)

Jesse James Garrett (2010) propõe organizar o projeto de qualquer interface em cinco camadas de abstração, lidas em ordem projetual **de baixo para cima** (da mais abstrata para a mais concreta):

```
▲  5. Camada de Superfície: Design Visual e acabamento gráfico (fontes, paleta de cores, ícones).
│  4. Camada de Esqueleto: Design da Interface, da Navegação e da Informação (Wireframe estrutural).
│  3. Camada de Estrutura: Design de Interação e Arquitetura da Informação (fluxos de telas e categorias).
│  2. Camada de Escopo: Especificação Funcional e Requisitos de Conteúdo (o que deve ser construído).
│  1. Camada de Estratégia: Objetivos de Negócio e Necessidades do Usuário (base empírica).
```

### 10. Prototipação: Vantagens e Níveis de Fidelidade

A prototipação permite simular o fluxo de navegação, aparência e funcionamento do sistema para realizar correções rápidas e de baixo custo antes de iniciar o desenvolvimento em código. Classifica-se os protótipos em três níveis de fidelidade:

- **Baixa Fidelidade (_Wireframes_ / _Paper Prototypes_)**: Esboços rápidos feitos à mão ou em ferramentas digitais simples. Focam na organização espacial e na hierarquia de elementos, sem acabamento de cores ou imagens. São baratos e fáceis de modificar.
- **Média Fidelidade**: Utilizam ferramentas digitais para detalhar o fluxo das telas, botões funcionais e a lógica de transição entre seções, permitindo simular a navegação real sem implementar código funcional.
- **Alta Fidelidade**: Apresentam todos os elementos do produto finalizado (identidade visual, cores, ícones refinados, microinterações, textos reais). Utilizados para testes finais de usabilidade antes de o produto ser lançado ao mercado.

_Vantagem Econômica_: Quanto mais cedo os problemas de usabilidade forem detectados e corrigidos nos protótipos, mais barato será o projeto. Alterações feitas após o lançamento final geram retrabalho complexo e perda direta de clientes.

### 11. Avaliação de Interfaces: Técnicas de Inspeção e de Observação

As avaliações servem para identificar potenciais problemas nas telas e certificar que a lógica projetual atende às demandas do usuário. São categorizadas em dois grandes grupos:

```
                    ┌────────────────────────────┐
                    │  AVALIAÇÃO DE INTERFACE    │
                    └─────────────┬──────────────┘
                                  │
         ┌────────────────────────┴────────────────────────┐
         ▼                                                 ▼
┌─────────────────────────────────┐               ┌─────────────────────────────────┐
│     TÉCNICAS DE INSPEÇÃO        │               │     TÉCNICAS DE OBSERVAÇÃO      │
│     (Sem participação de        │               │       (Com participação de      │
│          usuários)              │               │            usuários)            │
└────────┬────────────────────────┘               └────────┬────────────────────────┘
         ├─ Avaliação Heurística                           ├─ Testes de Usabilidade
         ├─ Percurso Cognitivo                             ├─ Card Sorting / Tree Testing
         └─ Inspeção de Normas                             └─ Testes A/B
```

#### A) Técnicas de Inspeção (Sem a presença de usuários)

Realizadas por especialistas em usabilidade baseados em documentos de referência:

- **Avaliação Heurística**: Inspeção sistemática baseada no cumprimento de princípios de usabilidade, como as 10 Heurísticas de Nielsen. É realizada em duas fases: primeiro, cada avaliador varre a interface de forma individual para identificar e mapear desvios; depois, os especialistas se reúnem para discutir os achados e desenhar o relatório final de severidade e propostas de solução.
- **Percurso Cognitivo**: O especialista simula o processo mental e comportamental de um usuário de primeiro uso passo a passo em uma tarefa. A cada passo, o avaliador deve se fazer **quatro perguntas cruciais** baseadas em Cybis (2015):
    1. _O usuário tentará realizar a ação correta para alcançar o objetivo?_
    2. _O usuário verá o objeto de interface associado a esta ação?_
    3. _O usuário reconhecerá o objeto da interface como associado a esta ação?_
    4. _O usuário compreenderá o feedback fornecido pelo sistema como um progresso na tarefa?_
- **Inspeção de Normas**: Verificação das telas frente a determinações legais ou técnicas padronizadas de usabilidade (como as normas ISO/IEC ou ABNT).

#### B) Técnicas de Observação (Com a presença de usuários reais)

- **Teste de Usabilidade**: Observação controlada de usuários reais executando tarefas típicas do sistema.
    - _Presencial_: Conduzido em campo (contexto real sujeito a interrupções) ou em **Laboratório de Usabilidade** (ambiente controlado com parede de espelho falso separando a sala de testes da sala de observadores, equipada com câmeras e gravadores de áudio).
    - _Remoto Síncrono_: Conduzido por videoconferência com compartilhamento de tela, onde o moderador passa as instruções em tempo real e acompanha a interação à distância.
    - _Remoto Assíncrono_: O participante executa as tarefas sozinho guiado por um software específico que grava sua tela e suas reações faciais, enviando o arquivo para análise posterior dos pesquisadores.
- **Teste de Árvore (_Tree Testing_)**: Avaliação específica para validar se a hierarquia de categorias e menus elaborada é intuitiva. Apresenta-se o esqueleto textual do menu e solicita-se ao usuário que aponte onde encontraria um item específico.
- **Testes A/B**: Comparação direta entre duas versões de layout (A e B) enviadas para grupos distintos de usuários para medir qual opção atinge melhores taxas de conversão ou menor tempo de conclusão.

### 12. Acessibilidade Digital e Tecnologias Assistivas

Projetar para a acessibilidade significa eliminar barreiras físicas e digitais e garantir que o acesso ao conteúdo textual, em áudio ou vídeo seja universal. A Lei Brasileira de Inclusão (LBI, 2015) estabelece a acessibilidade como um direito essencial do cidadão.

#### Diretrizes do WCAG (Web Content Accessibility Guidelines)

O World Wide Web Consortium (W3C) organiza as diretrizes de acessibilidade em quatro princípios fundamentais:

1. **Perceptível**: Apresentar as informações em formatos que o usuário possa capturar. Exige oferecer alternativas textuais para imagens, adicionar audiodescrição e legendas a conteúdos sonoros.
2. **Operável**: Permitir que todas as interações e navegações das telas sejam executadas (exemplo: garantir acesso total de todas as funcionalidades pelo teclado, tempo suficiente para leitura e evitar layouts que causem convulsões).
3. **Compreensível**: Fornecer informações legíveis, navegações previsíveis e assistência interativa de entrada de dados para ajudar a evitar erros.
4. **Robusto**: O código do sistema deve ser estruturado de forma limpa para garantir compatibilidade com tecnologias assistivas atuais e futuras.

#### Recursos e Softwares de Tecnologia Assistiva

- _Leitores de Tela_: NVDA (gratuito de código aberto para Windows, integrado ao VLibras), JAWS (comercial e completo para Windows) e Voiceover (nativo em produtos da Apple).
- _Tradutores automáticos de LIBRAS_: VLibras, Hand Talk e Rybená.
- _Simuladores de Daltonismo_: Chromatic Vision Simulator, Color Blind Pal, Vischeck e Color Oracle.
- _Acessibilidade Motora_: Motrix (controle do computador por comandos de voz), Camera Mouse (rastreio de movimentos da cabeça via webcam) e eSSential Accessibility (controle do cursor por voz ou movimentos de cabeça).

### 13. Gamificação e Engajamento

Gamificação é a aplicação de componentes, mecânicas e dinâmicas de jogos em contextos do mundo real para incentivar atitudes específicas e reter a atenção do usuário. O engajamento se dá a partir de recursos como:

- _Sistema de Pontuação_: Recompensa imediata por conclusão de lições ou tarefas.
- _Desafios e Conquistas_: Objetivos claros que fornecem metas e distintivos virtuais (_badges_).
- _Níveis e Progressão_: Indicação visual (barras de progresso) de evolução pessoal dentro da jornada.
- _Competição Saudável_: Rankings públicos ou placares de líderes (_leaderboards_) que promovem a interação comunitária.
- _Autonomia e Personalização_: Permitir que o usuário tome decisões e molde sua jornada.

---

## Conceitos que não posso confundir

```
┌────────────────────────────────────────────────────────────────────────────────────────┐
│                              USABILIDADE vs. UX (EXPERIÊNCIA DO USUÁRIO)               │
├────────────────────────────────────────────────────────────────────────────────────────┤
│ • Usabilidade: Foco na facilidade de uso durante a interação (eficácia e eficiência)   │
│  .                                                                             │
│ • Experiência do Usuário (UX): Cobre toda a jornada (expectativas anteriores, reações  │
│   emocionais e lembranças de longo prazo).                                │
└────────────────────────────────────────────────────────────────────────────────────────┘

┌────────────────────────────────────────────────────────────────────────────────────────┐
│                        DESIGN RESPONSIVO vs. ADAPTATIVO vs. MULTIPLATAFORMA            │
├────────────────────────────────────────────────────────────────────────────────────────┤
│ • Responsivo: Layout fluído que se reorganiza de forma dinâmica e automática a        │
│   qualquer dimensão de tela por meio de grids e media queries.              │
│ • Adaptativo: Desenvolvimento de layouts separados e específicos para cada categoria │
│   de dispositivo (versão mobile separada de desktop).                            │
│ • Multiplataforma: Compartilhamento de código comum que permite executar o aplicativo   │
│   em diferentes sistemas operacionais (iOS, Android, Web).                  │
└────────────────────────────────────────────────────────────────────────────────────────┘

┌────────────────────────────────────────────────────────────────────────────────────────┐
│                               CARD SORTING vs. TREE TESTING                            │
├────────────────────────────────────────────────────────────────────────────────────────┤
│ • Card Sorting: Processo de agrupamento livre ou guiado de cartões para desenhar a     │
│   arquitetura inicial de navegação e menus.                                      │
│ • Tree Testing (Teste de Árvore): Validação de uma estrutura de menu pré-existente     │
│   para verificar se o fluxo lógico proposto realmente funciona.                  │
└────────────────────────────────────────────────────────────────────────────────────────┘

┌────────────────────────────────────────────────────────────────────────────────────────┐
│                         TESTE DE USABILIDADE REMOTO SÍNCRONO vs. ASSÍNCRONO            │
├────────────────────────────────────────────────────────────────────────────────────────┤
│ • Síncrono: Sessão ao vivo com o moderador guiando e tirando dúvidas simultaneamente   │
│  .                                                                          │
│ • Assíncrono: O participante executa os cenários de teste de forma autônoma sem a      │
│   presença do moderador; o sistema grava a tela para análise posterior.     │
└────────────────────────────────────────────────────────────────────────────────────────┘

┌────────────────────────────────────────────────────────────────────────────────────────┐
│                                 MOCKUPS vs. WIREFRAMES                                 │
├────────────────────────────────────────────────────────────────────────────────────────┤
│ • Wireframes: Esboços e representações puramente estruturais de interfaces digitais   │
│   focados no posicionamento básico dos elementos (esqueletos de tela).      │
│ • Mockups: Simulação em imagens digitais que aproximam o protótipo ao produto real    │
│   (como a tela do aplicativo inserida na imagem de um smartphone físico).        │
└────────────────────────────────────────────────────────────────────────────────────────┘
```

---

## Pontos importantes para prova

### 1. Componentes Essenciais da Usabilidade (ISO 9241-11):

- **Eficácia**: Acurácia (precisão de correspondência ao pretendido) e completude (extensão na qual o usuário conclui o objetivo).
- **Eficiência**: Quantidade de recursos (esforço mental, físico e tempo) consumidos para alcançar os resultados.
- **Satisfação**: Respostas cognitivas, físicas e emocionais resultantes da experiência de uso.

### 2. Três Componentes Causa-Efeito de um Problema de Usabilidade:

1. **Elemento de Interface**: Causa do problema (ícone confuso, texto incompreensível, carregamento lento).
2. **Impacto na Tarefa**: Consequência prática (atraso, preenchimento incompleto, desistência do processo).
3. **Impacto no Usuário**: Resposta emocional gerada (confusão, insegurança, frustração, raiva).

### 3. Fatores de Severidade de Problemas de Usabilidade (Nielsen):

- **Frequência**: Se ocorre de forma comum ou rara.
- **Impacto**: Nível de dificuldade para o usuário superar ou contornar o problema.
- **Persistência**: Se os usuários enfrentam o erro de forma sistemática e contínua ou se aprendem a evitá-lo na primeira ocorrência.
- _Graus_: Classificados em **1-Baixo, 2-Médio, 3-Alto**.

### 4. As 10 Heurísticas de Nielsen:

1. _Visibilidade do status do sistema_ (indicar andamento de downloads, carregamentos).
2. _Compatibilidade entre o sistema e o mundo real_ (linguagem familiar, uso de ícones analógicos).
3. _Controle e liberdade do usuário_ (permitir ações de desfazer e refazer, saídas claras).
4. _Consistência e padrões_ (mesma paleta de cores, botões padronizados).
5. _Prevenção de erros_ (mensagens de confirmação prévias a ações críticas).
6. _Reconhecimento no lugar de recordação_ (minimizar a carga da memória mostrando comandos visíveis).
7. _Flexibilidade e eficiência de uso_ (atalhos de teclado para usuários experientes).
8. _Projeto estético e minimalista_ (eliminar elementos visuais raramente necessários).
9. _Reconhecimento, diagnóstico e recuperação de erros_ (mensagens claras indicando a solução sem códigos internos de programação).
10. _Ajuda e documentação_ (disponibilização de manuais estruturados ou tutoriais integrados).

### 5. As 8 Regras de Ouro de Shneiderman:

1. _Esforce-se para assegurar a coerência_.
2. _Busque a usabilidade universal_ (adequar layout a idosos, iniciantes e limitações técnicas).
3. _Forneça feedback_ (respostas para todas as ações).
4. _Projete diálogos que indiquem o término da ação_ (passo a passo com início, meio e conclusão clara).
5. _Previna erros_.
6. _Permita que as ações sejam revertidas facilmente_.
7. _Mantenha os usuários no controle_.
8. _Reduza a carga da memória de curto prazo_ (evitar exigir lembrança de dados de uma tela anterior).

### 6. Leis Mentais da Percepção Visual (Gestalt):

- **Unidade**: Um elemento que se encerra em si mesmo ou serve de componente de um todo.
- **Segregação**: Capacidade de destacar unidades em relação ao todo por meio de alto contraste.
- **Unificação**: Percepção de elementos semelhantes como uma única composição visual coesa.
- **Fechamento**: Tendência do cérebro de fechar vãos e completar formas inacabadas mentalmente.
- **Continuidade**: Alinhamentos ordenados que sugerem uma trajetória linear (reta ou curva) contínua.
- **Proximidade**: Elementos fisicamente próximos são percebidos pelo cérebro como membros de um mesmo grupo.
- **Semelhança**: Elementos semelhantes em cor, tamanho ou forma são agrupados cognitivamente.
- **Pregnância**: Princípio da simplicidade máxima. A mente reduz cenas visuais complexas à sua forma geométrica mais simples e equilibrada.

### 7. Subcaracterísticas da Usabilidade de Software (ISO/IEC 25010):

- _Reconhecimento de adequação_ (entender se o software atende ao seu problema de forma rápida).
- _Aprendizagem_ (facilidade de instruir-se no uso).
- _Operabilidade_ (facilidade de controle e inserção de comandos).
- _Proteção contra erros do usuário_.
- _Estética da interface com o usuário_.
- _Acessibilidade_.

---

## Revisão rápida

### Resumo para Memorização

```
                    ┌─────────────────────────────────────────┐
                    │          INTERFACE & USABILIDADE        │
                    └────────────────────┬────────────────────┘
                                         │
        ┌────────────────────────────────┼────────────────────────────────┐
        ▼                                ▼                                ▼
  INTERAÇÃO (IHC)                    PROCESSO                       AVALIAÇÃO
┌─────────────────────────┐      ┌─────────────────────────┐      ┌─────────────────────────┐
│ • Interface: Canal de   │      │ • DCH/DCU: Iterativo    │      │ • Inspeção (Sem         │
│   comunicação entre o   │      │   e focado no usuário   │      │   usuário): Heurística  │
│   usuário e o sistema   │      │  .             │      │   e Percurso Cognitivo  │
│  .               │      │ • Design Thinking:      │      │  .      │
│ • Usabilidade: Eficácia │      │   Compreensão, Definição│      │ • Observação (Com       │
│   (acurácia/completude) │      │   Ideação, Prototipação,│      │   usuário): Testes de   │
│   Eficiência (recursos/ │      │   Avaliação e Implemen- │      │   usabilidade, Card     │
│   tempo) e Satisfação   │      │   tação.│      │   Sorting.   │
│  .                 │      │ • Design Sprint: Uma    │      │ • Severidade (Nielsen): │
│ • UX: Engloba antes,    │      │   semana para validar   │      │   Frequência, Impacto e │
│   durante e depois da   │      │   soluções.       │      │   Persistência (1 a 3)  │
│   interação.   │      │                         │      │  .                │
└─────────────────────────┘      └─────────────────────────┘      └─────────────────────────┘
```

#### Fórmulas e Guias Rápidos

- **Usabilidade** = Eficácia (Acurácia + Completude) + Eficiência (Recursos + Tempo) + Satisfação.
- **4 Perguntas do Percurso Cognitivo**: Ele tentará realizar a ação? Conseguirá ver o objeto? Conseguirá associar o objeto à ação? Compreenderá o feedback de progresso?
- **Regra de Hoober**: 49% usam o celular com apenas um polegar. Posicione ações cruciais na metade inferior da tela.
- **WCAG (POCO)**: Princípios fundamentais de acessibilidade digital: **P**erceptível, **O**perável, **C**ompreensível, **R**obusto (ou **O**bjetivo).

---
