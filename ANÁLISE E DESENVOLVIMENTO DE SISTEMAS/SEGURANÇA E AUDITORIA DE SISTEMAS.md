[[EXEMPLOS-PRÁTICOS DE SEGURANÇA E AUDITORIA DE SISTEMAS]]
#ASSUNTO
## Conceitos principais

- **Segurança da Informação (SI):** É o campo que visa proteger a informação de diversos tipos de ameaça para garantir a continuidade dos negócios, minimizando danos e maximizando o retorno sobre os investimentos e as oportunidades de mercado. Baseia-se no gerenciamento integrado de processos de identificação, proteção, detecção, resposta e recuperação.
- **Auditoria de Sistemas:** Processo sistemático, formal e independente de avaliação e verificação de controles de segurança, políticas e procedimentos em um ambiente de TI. Seu objetivo é checar se os padrões estabelecidos estão sendo seguidos, se os registros estão corretos e se os sistemas operam com eficiência, eficácia e ética.
- **Ativo:** Qualquer elemento físico, lógico, de informação ou humano que tenha valor para uma organização e que, portanto, necessite de proteção.
- **Vulnerabilidade:** Ponto fraco ou falha de segurança presente em pessoas, meios físicos, hardwares, protocolos, sistemas operacionais ou aplicações que pode ser explorado por uma ameaça para gerar um incidente.
- **Ameaça:** Causa potencial de um incidente indesejado que pode resultar em danos a um ativo ou à organização. Ela se caracteriza por qualquer ação, acontecimento ou entidade que age sobre um ponto fraco.
- **Risco:** Probabilidade de um agente de ameaça explorar com sucesso uma vulnerabilidade de um ativo usando determinada técnica de ataque, gerando um incidente de segurança e impactos negativos. É calculado matematicamente como o produto entre a Probabilidade de ocorrência e o Impacto gerado (\(Risco = P \times I\)).
- **Controle de Segurança (Contramedida):** Mecanismo de defesa físico, tecnológico, processual ou regulatório aplicado a um ativo para remover vulnerabilidades, mitigar riscos e conter ataques.

---

## Conteúdo explicado

### 1. Princípios e Pilares Fundamentais da Segurança da Informação

A segurança da informação é regida por uma tríade clássica expandida que norteia todas as políticas e mecanismos de defesa:

1. **Confidencialidade:** Garante que a informação não seja disponibilizada ou revelada a indivíduos, entidades ou processos não autorizados. É protegida principalmente por controle de acesso e criptografia.
2. **Integridade:** Salvaguarda a exatidão, completeza e proteção de ativos contra modificações e alterações não autorizadas.
3. **Disponibilidade:** Assegura que os dados, sistemas e serviços estejam acessíveis e utilizáveis pelos usuários legítimos sempre que necessário.
4. **Autenticidade:** Confirma e garante que determinada pessoa, entidade ou sistema é, de fato, quem afirma ser, impedindo falsificações.
5. **Não-Repúdio (Irretratabilidade):** Impede que um usuário ou sistema negue a autoria de uma transação ou de um conteúdo por ele gerado, fornecendo provas sólidas da atividade.
6. **Legalidade:** Aspecto de conformidade com a legislação aplicável e com as regras regulatórias.

---

### 2. Gestão de Riscos (Baseada na ISO/IEC 27005)

A gestão de riscos é um processo analítico e contínuo que deve orientar toda a estratégia de segurança da empresa:

- **Mapeamento e Identificação:** Catalogar ativos, ameaças, agentes de ameaças, técnicas de ataque e vulnerabilidades existentes.
- **Análise e Avaliação:** Estimar o risco multiplicando a probabilidade de ocorrência (valores de 1 a 3) pelo impacto nos negócios (valores de 1 a 4):
    - _Risco Baixo:_ Valores de 1 a 2 na matriz.
    - _Risco Médio:_ Valores de 3 a 4 na matriz.
    - _Risco Alto:_ Valores de 6 a 9 na matriz.
    - _Risco Extremo:_ Valor máximo de 12 na matriz.
- **Tratamento de Riscos:** Conforme a avaliação, o risco pode receber quatro tipos de tratamento:
    1. _Mitigação (Redução):_ Aplicação de controles de segurança para reduzir a probabilidade ou o impacto.
    2. _Aceitação:_ Decisão consciente de conviver com o risco quando o controle é mais caro que o ativo ou o risco é insignificante (exige monitoramento contínuo).
    3. _Eliminação (Evitação):_ Interrupção da atividade ou inutilização do ativo para afastar completamente a ameaça.
    4. _Transferência:_ Repasse do risco para terceiros por meio de seguros ou contratação de provedores especializados (como datacenters em nuvem).

---

### 3. Sistemas de Gestão de Segurança da Informação (SGSI) e Normas Internacionais

O SGSI é a estrutura metodológica usada para operacionalizar a cultura e a segurança corporativa:

- **Ciclo de Melhoria Contínua (PDCA):** O SGSI deve ser estabelecido e revisado dinamicamente seguindo o fluxo contínuo de planejamento, execução, checagem e correção:
    - _Plan (Planejar):_ Estabelecer o escopo do SGSI, objetivos, políticas e identificação de riscos.
    - _Do (Executar):_ Implementar o SGSI, alocar recursos, treinar colaboradores e operar os controles.
    - _Check (Verificar):_ Monitorar, medir o desempenho, realizar análises críticas e conduzir auditorias internas.
    - _Act (Agir):_ Tratar não-conformidades, implementar ações corretivas e promover a melhoria contínua.
- **Família ISO 27000 e Padrões de Apoio:**
    - _ISO 27001:_ Define os requisitos auditáveis obrigatórios para o estabelecimento, implementação, operação e certificação de um SGSI.
    - _ISO 27002:_ Guia de melhores práticas e diretrizes detalhadas para a escolha e implementação dos controles de segurança que apoiam a ISO 27001.
    - _ISO 27005:_ Concentra-se exclusivamente nas diretrizes para a gestão de riscos de segurança da informação.
    - _ISO 27701:_ Estende a ISO 27001 e a ISO 27002 para gerenciar a privacidade de dados pessoais.
    - _ISO 19011:_ Norma que define as diretrizes gerais para auditar qualquer sistema de gestão (incluindo o SGSI da ISO 27001).

---

### 4. Controle de Acesso, Autenticação e Autorização (Tecnologia AAA)

Os controles de acesso gerenciam as permissões de acesso físico e lógico a recursos computacionais e instalações:

- **A Tríade AAA:**
    1. _Autenticação:_ Verificação de que a identidade do usuário ou do sistema é legítima.
    2. _Autorização:_ Determinação das permissões e ações permitidas ao usuário autenticado.
    3. _Auditoria:_ Monitoramento, registro (logs) e análise histórica de todas as atividades efetuadas no sistema.
- **Mecanismos de Autenticação:** Baseiam-se em múltiplos fatores para mitigar o compartilhamento não autorizado:
    - _Fator de Conhecimento:_ Algo que o usuário sabe (senhas seguras e complexas).
    - _Fator de Posse:_ Algo que o usuário possui (tokens físicos, cartões inteligentes ou aplicativos móveis autenticadores).
    - _Fator de Existência/Biometria:_ Algo que o usuário é (impressão digital, reconhecimento facial, leitura de íris).
    - _Certificados Digitais:_ Emitidos por autoridades certificadoras para autenticação robusta de sistemas ou usuários.
    - _MFA (Autenticação Multifatorial):_ Combinação de dois ou mais fatores diferentes para elevar a segurança.
- **Sistemas IAM (Identity and Access Management):** Centralizam o ciclo de vida das contas, permitindo Single Sign-On (SSO) para acesso único a múltiplos apps, federação de identidades e autoatendimento (self-service) para os funcionários.

---

### 5. Ciclo de Vida e Segurança de Dados

A governança de dados exige cuidados em todas as etapas, desde a coleta até o seu descarte final:

1. **Coleta e Classificação:** Os dados devem ser mapeados e categorizados conforme sua criticidade e sensibilidade (público, de uso interno, confidencial ou altamente confidencial) para determinar as regras de proteção, armazenamento e controle de acesso.
2. **Anonimização:** Processo obrigatório legalmente (segundo a LGPD) no qual se utilizam meios técnicos razoáveis e disponíveis para remover ou mascarar a associação direta ou indireta de um dado a um indivíduo, eliminando sua identificabilidade.
3. **Retenção:** Política que regulamenta por quanto tempo a informação deve ser guardada com base em regras de negócios e requisitos legais vigentes. Reter dados desnecessariamente eleva os riscos de violação de privacidade.
4. **Destruição Segura:** Processo de eliminação física ou lógica e irrecuperável das cópias de dados quando estas expiram, evitando vazamentos acidentais.
5. **Armazenamento em Nuvem (Cloud Computing):** Permite elasticidade, mobilidade e armazenamento escalável. No entanto, introduz riscos devido ao modelo de _multitenancy_ (compartilhamento de uma única instância lógica por múltiplos clientes). Exige políticas robustas de criptografia (em repouso, trânsito e processamento), redundância de dados (failover/backup), monitoramento contínuo e definição clara das responsabilidades de segurança compartilhadas com os provedores.

---

### 6. Segurança de Redes e Aplicações Web

A proteção das infraestruturas de comunicação corporativa exige segurança em múltiplas camadas tecnológicas e no desenvolvimento seguro:

- **Vulnerabilidades de Redes:** Podem ocorrer no hardware (dispositivos de rede com falhas), no software (bugs e brechas em sistemas operacionais), nos protocolos (vulnerabilidades estruturais do TCP/IP) ou nos próprios aplicativos expostos.
- **Ameaças Clássicas à Rede:**
    - _Worms (Vermes):_ Códigos maliciosos que se replicam automaticamente pelas redes explorando vulnerabilidades ativas.
    - _Trojan (Cavalo de Troia):_ Programa aparentemente legítimo que executa funções ocultas prejudiciais em segundo plano.
    - _Ransomware:_ Sequestro de dados corporativos por meio de criptografia forte, com extorsão financeira para liberação.
    - _Spoofing:_ Mascaramento de endereços IPs remetentes para forjar comunicações confiáveis.
    - _Man-in-the-Middle (MitM):_ Interceptação física ou lógica das comunicações entre duas partes legítimas para leitura ou injeção de dados falsificados.
    - _DoS e DDoS:_ Sobrecarga intencional dos recursos de um servidor ou rede por meio de requisições massivas para derrubar a sua disponibilidade.
- **Vulnerabilidades em Aplicações Web:**
    - _SQL Injection (Injeção de SQL):_ Entrada de dados maliciosos contendo comandos SQL em campos de formulários não sanitizados que alteram a instrução e dão acesso direto ao banco de dados.
    - _Cross-Site Scripting (XSS):_ Injeção de scripts maliciosos (normalmente em HTML ou JavaScript) em campos de entrada de páginas web que são executados diretamente nos navegadores de outros usuários, roubando sessões.
    - _Cross-Site Request Forgery (CSRF):_ Indução de um usuário autenticado a executar de forma silenciosa e não intencional ações críticas no servidor web que confia no navegador da vítima.
- **Estratégias de Defesa e Desenvolvimento Seguro:**
    - _Validação e Sanitização de Entradas:_ Garantir que todos os dados fornecidos pelo usuário no cliente e revalidados obrigatoriamente no servidor passem por filtros antes de serem processados.
    - _Uso de Consultas Parametrizadas:_ Separar os comandos lógicos do banco de dados das variáveis de entrada do usuário para anular tentativas de injeção de SQL.
    - _Escapar Caracteres e CSP:_ Converter caracteres especiais de HTML/JS e configurar uma _Content Security Policy_ (CSP) para controlar as fontes de carregamento de scripts.
    - _Zona Desmilitarizada (DMZ):_ Segmentação física de rede na qual servidores acessíveis externamente (web, e-mail) ficam isolados entre a internet pública e a rede interna confidencial, reduzindo a movimentação lateral de invasores.
    - _DLP (Data Loss Prevention):_ Soluções automatizadas em endpoints e rede para monitorar e prevenir o vazamento involuntário de dados sensíveis corporativos em tempo real.

---

### 7. Auditoria de Sistemas e Técnicas de Análise de TI

A auditoria de TI atua como a garantia metodológica para assegurar a conformidade, identificar lacunas e mitigar riscos proativamente:

- **Fases Estruturadas do Processo de Auditoria:**

```
  [PLANEJAMENTO]                 [EXECUÇÃO]                  [RELATÓRIO]
- Definição de objetivos        - Coleta de evidências      - Elaboração do relatório
  e escopo                      - Entrevistas com pessoal-   - Comunicação clara
- Avaliação de riscos             chave e auditorias internas  com alta gestão
- Elaboração do plano de TI     - Testes técnicos de rede   - Follow-up corretivo
  e cronogramas                 - Documentação detalhada    - Melhoria contínua

```

- **Três Grandes Grupos de Técnicas de TI:**
    1. _Interação com Pessoas:_ Entrevistas estruturadas, questionários formais, pesquisas, dinâmicas de grupo e observações diretas de rotina diária.
    2. _Análise Manual:_ Revisão detalhada de políticas documentadas, manuais de procedimentos, análise estática de código de software (SAST), desenho de fluxogramas de processos e simulações de mesa.
    3. _Análise Técnica com Ferramentas:_ Scripts customizados, softwares automatizados de varredura de vulnerabilidades (scanners), testes práticos de penetração (pentest) e auditoria de logs operacionais e de rede.

---

## Conceitos que não posso confundir

Ao estudar para avaliações e certificações de auditoria e segurança, é imprescindível discernir com clareza os pares de conceitos semelhantes abaixo:

|Conceito A|Conceito B|Diferença Crucial|
|:--|:--|:--|
|**Evento de Segurança**|**Incidente de Segurança**|Um **Evento** indica apenas uma ocorrência que pode significar uma possível quebra ou desvio de política de segurança. O **Incidente** é o evento indesejado que se concretizou e que possui probabilidade significativa de de fato comprometer operações e causar danos reais à empresa.|
|**Ameaça**|**Vulnerabilidade**|A **Ameaça** é o elemento externo ativo ou acontecimento que pode agir e explorar os sistemas (ex: um vírus ou um invasor). A **Vulnerabilidade** é a falha, fraqueza de configuração ou de código interna que permite a atuação daquela ameaça (ex: um sistema sem atualizar).|
|**DAC (Controle Discricionário)**|**MAC (Controle Mandatório)**|No **DAC**, o próprio proprietário do recurso de dados determina de forma livre quem tem permissão para acessá-lo. No **MAC**, o controle baseia-se estritamente em políticas e classificações hierárquicas inflexíveis definidas pela administração ou leis (comum na área militar), sem interferência do usuário.|
|**RBAC (Controle Baseado em Funções)**|**ABAC (Controle Baseado em Atributos)**|O **RBAC** concede acesso baseado na função ou papel formal do funcionário na empresa (ex: Analista Financeiro). O **ABAC** é altamente contextual e analisa um conjunto de atributos de momento (identidade do usuário, horário de acesso, tipo de dispositivo e localização geográfica).|
|**Criptografia Simétrica**|**Criptografia Assimétrica**|A **Simétrica** usa a mesma chave secreta tanto para cifrar quanto para decifrar os dados, sendo extremamente rápida e eficiente para grandes volumes de dados. A **Assimétrica (Pública)** usa um par de chaves (uma chave pública para cifrar e outra privada exclusiva para decifrar), permitindo comunicação segura e de alto nível de confiança sem a necessidade de compartilhar uma chave comum prévia.|
|**Jailbreaking (iOS)**|**Rooting (Android)**|Ambos consistem em destravar privilégios de superusuário de sistemas operacionais móveis, contornando travas de segurança dos fabricantes. O **Jailbreaking** é o termo técnico para dispositivos da Apple (iOS) e o **Rooting** é o termo correlato para dispositivos que rodam o sistema operacional Android.|
|**Jailbreaking / Rooting**|**BYOD (Bring Your Own Device)**|**Jailbreaking/Rooting** é uma alteração forçada que anula travas de segurança nativas, abrindo caminhos para malwares perigosos. **BYOD** é um programa corporativo formal de negócios que permite aos funcionários o uso regular de seus próprios dispositivos móveis pessoais para acessar redes e recursos corporativos com segurança controlada.|
|**BYOD**|**COPE (Corporate-Owned Personally-Enabled)**|No **BYOD**, a propriedade física e jurídica do equipamento móvel é do usuário. No **COPE**, o equipamento móvel é de propriedade exclusiva da empresa, que define e padroniza as configurações centrais, mas permite de forma flexível a instalação de apps e uso pessoal controlado do dispositivo.|
|**SAST (Teste de Segurança Estático)**|**DAST (Teste de Segurança Dinâmico)**|O **SAST** analisa o código-fonte de forma manual ou automatizada sem executar a aplicação, identificando falhas de fluxo de dados de desenvolvimento. O **DAST** atua de forma dinâmica, executando o sistema em tempo real a partir de requisições na camada de servidor e APIs de backend para identificar vulnerabilidades sob o ponto de vista operacional.|
|**Pentest Black-box**|**Pentest White-box**|No **Black-box**, o testador não tem nenhum conhecimento prévio sobre a rede ou infraestrutura de software, simulando perfeitamente a perspectiva real de um ataque. No **White-box**, o testador recebe informações completas e detalhadas da infraestrutura, configurações e códigos-fonte do sistema para uma auditoria profunda e otimizada de falhas complexas.|
|**Phishing**|**Engenharia Social**|A **Engenharia Social** é a categoria conceitual ampla de manipulação psicológica humana baseada na arte de enganar para obter dados privados de forma ilegítima. O **Phishing** é uma das táticas técnicas específicas de engenharia social executada por e-mail, redes ou SMS para pescar credenciais de usuários legítimos redirecionando-os a portais falsos.|

---

## Pontos importantes para prova

### 1. Etapas do Planejamento e Execução de Auditoria de TI (Para questões de processo)

- **Fase de Planejamento:**
    1. Estabelecer os objetivos e o escopo da auditoria.
    2. Conduzir a avaliação detalhada de riscos de segurança da informação.
    3. Desenvolver o plano de auditoria integrando cronogramas e recursos técnicos.
- **Fase de Execução:**
    1. Coletar evidências substanciais e confiáveis.
    2. Avaliar a eficácia prática dos controles internos de segurança da informação implementados.
    3. Realizar testes técnicos direcionados (varredura de vulnerabilidades, análises de logs de rede).
    4. Documentar e registrar todas as atividades para rastreabilidade.

### 2. Classificações de Controles de Segurança (Questão recorrente de prova)

- **Físicos:** Barreiras tangíveis de acesso físico (cercas, trancas de portas, cartões RFID, biometria física em datacenters, câmeras).
- **Lógicos/Tecnológicos:** Mecanismos computacionais de software e regras de rede (MFA, firewalls estruturados, criptografia, antivírus, IDSs).
- **Organizacionais/Processuais:** Regras formais administrativas e corporativas (PSI documentada, rotinas de backup, auditorias, políticas de troca periódica de senhas, treinamentos de conscientização).
- **Regulatórios:** Conformidades a leis governamentais específicas (LGPD, GDPR, HIPAA).

### 3. Divisões dos Controles por Tempo de Atuação

- **Controles de Prevenção:** Agem de forma antecipada para inibir a ocorrência de incidentes (ex: Criptografia, Firewall, MFA).
- **Controles de Detecção:** Identificam o ataque ou a atividade suspeita enquanto ela acontece ou imediatamente após (ex: IDS - Intrusion Detection System, ferramentas SIEM de monitoramento contínuo de logs).
- **Controles de Resposta/Recuperação:** Reduzem os prejuízos de incidentes já ocorridos e reestabelecem a integridade original de TI (ex: DRP - Recuperação de Desastres, Backups, Análise Forense, restauração de sistemas comprometidos).

### 4. Particularidades em Segurança Móvel (MDM/EMM)

- **MDM (Mobile Device Management):** Gerencia todos os dispositivos móveis corporativos de forma centralizada (fornecimento de acesso remoto, geolocalização, controle de aplicativos instalados, bloqueio e limpeza de dados de forma remota em caso de roubo ou perda do dispositivo).
- **EMM (Enterprise Mobility Management):** Consiste em um ecossistema mais amplo de serviços que auxiliam na gestão de mobilidade organizacional, regulando políticas de uso.

### 5. Auditoria em Ambientes de IoT (Internet das Coisas)

- Exige uma abordagem holística devido à diversidade de protocolos de rede e à natureza distribuída dos endpoints.
- _Focos cruciais no checklist de auditoria de IoT:_ Avaliação de protocolos de comunicação criptografados de redes sem fio, verificação de atualizações automáticas de firmware, auditoria de privacidade e proteção de dados coletados por sensores em conformidade com as regulações de privacidade, e implementação de padrões centralizados de logs para SIEM.

---

## Revisão rápida

### Tríade da Segurança da Informação (CID)

- **C**onfidencialidade (segredo do dado).
- **I**ntegridade (exatidão do dado).
- **D**isponibilidade (tempo de acesso).

### Auditoria de TI: Pilares Centrais

- É **Independente** e **Imparcial** (não deve estar envolvida na operação regular da organização).
- Principais Fases: **Planejamento -> Execução -> Relatório**.

### Auditoria Contínua

- É proativa, avalia sistemas de dados em **tempo real** por monitoramento constante de logs e ferramentas automatizadas, em oposição às auditorias periódicas e pontuais tradicionais.

### Guia Rápido de Ataques de Engenharia Social

- Foca no **fator humano** (medo, cobiça, boa vontade) e não em falhas técnicas de máquinas.
- Contramedidas ideais: **Treinamento contínuo de conscientização** de colaboradores, adoção obrigatória de **MFA** para os sistemas críticos e implementação de **protocolos rígidos de verificação** de identidade.

