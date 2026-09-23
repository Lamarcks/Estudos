**Problema:** Uma pequena empresa possui uma infraestrutura de rede antiga cabeada totalmente obsoleta que gera lentidão constante e quedas de conexões. O administrador de redes da empresa foi encarregado de projetar uma nova rede local corporativa que atenda simultaneamente a quatro requisitos estratégicos cruciais:

1. **Melhor mobilidade**: Os funcionários precisam se movimentar livremente no ambiente de trabalho sem perder a conectividade.
2. **Confiança e redundância**: A rede não pode parar totalmente caso ocorra uma falha física pontual em um computador ou em uma única fiação.
3. **Facilidade de gerenciamento**: A infraestrutura de manutenção lógica deve ser simplificada devido ao tamanho reduzido da equipe interna de TI.
4. **Baixo custo**: Manter os custos de cabeamento e hardware de suporte controlados.

**Conceito utilizado:** Projeto de rede baseado na **Topologia Estrela (Star Topology)** e tecnologias **Wi-Fi (IEEE 802.11)**.

**Solução:** Plano estruturado em 8 etapas consecutivas para a reestruturação física e de TI:

1. **Passo 1 (Planejamento)**: Mapeamento de planta baixa para determinar o posicionamento do switch/roteador central e calcular o alcance físico ideal dos pontos de acesso Wi-Fi necessários.
2. **Passo 2 (Seleção)**: Adquirir um switch gerenciável de alto desempenho de borda para atuar como o concentrador central da estrela, pontos de acesso Wi-Fi empresariais adicionais e cabeamento de par trançado estruturado.
3. **Passo 3 (Configuração Central)**: Configurar portas de trunking no switch central, criar VLANs lógicas de isolamento para os departamentos da empresa (TI, Financeiro e RH) e estabelecer políticas de priorização de Qualidade de Serviço (QoS). Garantir que o nó central esteja protegido por uma fonte de alimentação redundante e ininterrupta (Nobreak).
4. **Passo 4 (Instalação Wi-Fi)**: Fixar fisicamente os pontos de acesso (APs) sem fio em áreas limpas e elevadas no escritório. Configurar segurança forte, estabelecendo senhas complexas e ativando criptografia empresarial robusta.
5. **Passo 5 (Teste e Monitoramento)**: Realizar testes de estresse de sinal simulando conexões móveis contínuas de funcionários caminhando pelas salas e mapear a velocidade de banda em tempo real.
6. **Passo 6 (Treinamento)**: Orientar os funcionários sobre as melhores práticas corporativas de segurança virtual de acesso e relatórios de incidentes.
7. **Passo 7 (Medidas de Segurança)**: Ativar firewalls na borda da internet, implementar sistemas preventivos de detecção de intrusão e exigir autenticação forte dos dispositivos móveis corporativos.
8. **Passo 8 (Manutenção Contínua)**: Definir rotinas programadas para atualizações de software de firmware dos switches e dos pontos de acesso sem fio.

**Resultado:** Uma rede moderna estável de altíssima confiabilidade. A adoção da topologia estrela garante que o rompimento físico de um cabo individual em um escritório afete exclusivamente aquela fiação específica, mantendo toda a rede da empresa e demais funcionários operando normalmente e sem interrupções de conexão.

**Por que essa solução funciona:** Diferente da topologia em anel ou barramento tradicional, na topologia estrela os caminhos físicos dos hosts de dados não são compartilhados linearmente. Cada dispositivo possui seu cabo dedicado com o nó concentrador centralizado (switch), isolando problemas elétricos individuais de fiação de forma física e automática no switch.

**O que preciso aprender com esse exemplo:** A topologia estrela resolve os problemas de redundância e escalabilidade para dispositivos de ponta, porém introduz um **Ponto Único de Falha (Single Point of Failure)**: se o switch centralizado falhar eletricamente, toda a comunicação da rede da organização é interrompida. É essencial que esse nó central tenha proteções redundantes contra falhas físicas.
