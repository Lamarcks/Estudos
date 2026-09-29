**Problema:** Uma rede de postos de coleta de exames laboratoriais no Sul do país utiliza há 15 anos o mesmo software baseado em arquitetura **desktop sem acesso à internet**. A alta gestão deseja expandir o negócio por meio de novas filiais integradas. O analista de sistemas precisa avaliar se é financeiramente e operacionalmente viável atualizar o sistema legado antigo ou projetar um software totalmente novo, sugerindo as tecnologias modernas adequadas e as competências necessárias para a equipe de desenvolvimento.

**Conceito utilizado:**

- **Análise de Viabilidade Técnica e Econômica**.
- **Modernização de Sistemas Legados**.
- **Arquitetura Baseada em Nuvem (_Cloud Computing_)** e **Sistemas Web/Mobile**.

**Solução:**

1. **Estudo de Viabilidade**: Determinou-se que atualizar o sistema antigo (desktop isolado) é inviável, pois ele não foi projetado para os recursos de rede e comunicação em tempo real necessários para interligar filiais geograficamente dispersas. A decisão técnica correta é construir um novo sistema.
2. **Investigação de Campo**: Visitar uma unidade física do laboratório para acompanhar de perto o fluxo real de trabalho, como o cadastramento da coleta de um paciente, o tempo operacional gasto e o modelo de entrega dos laudos.
3. **Proposta Tecnológica**:
    - Armazenamento do banco de dados unificado em **nuvem** (AWS, Google Cloud ou Microsoft Azure) para centralização e integração das filiais.
    - Desenvolvimento de **site e aplicativo móvel** integrado para agendamento de exames, acompanhamento do processamento das amostras laboratoriais e emissão/impressão de laudos em formato PDF diretamente pelo paciente.
    - Adoção da linguagem **JAVA** pela portabilidade e redução de custos operacionais do cliente.
    - Posterior introdução de suporte a **códigos de barras** e **QR-Code** para identificação de amostras e tubos de ensaio com total rastreabilidade.

**Resultado:** Um parecer técnico e projeto estratégico aprovado para desenvolvimento de um sistema web/mobile integrado e robusto, assegurando que o laboratório possa centralizar seus dados e expandir suas filiais com eficiência.

**Por que essa solução funciona:** A centralização das informações em um banco de dados em nuvem elimina a barreira do "silo tecnológico" que o software desktop isolado criava. O aplicativo e o site descentralizam o processo de agendamento e a entrega de laudos, reduzindo filas nas recepções físicas.

**O que preciso aprender com esse exemplo:** Sistemas legados desktop que não suportam conexão com a internet inviabilizam a expansão de franquias. O papel do analista de sistemas é identificar esse limite técnico e propor uma **rearquitetura baseada em nuvem e APIs móveis/web** para integrar processos ponta a ponta.