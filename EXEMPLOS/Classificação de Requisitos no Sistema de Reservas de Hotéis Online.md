**Problema:** Dado um projeto fictício de um "Sistema de reservas de hotéis on-line", o analista precisa classificar corretamente as necessidades do negócio e do usuário entre **Requisitos Funcionais** (ações lógicas) e **Requisitos Não Funcionais / Estruturais** (características gerais de qualidade, segurança e plataforma), compreendendo a importância de cada classificação para o sucesso do projeto.

**Conceito utilizado:**

- **Requisitos Funcionais (RF)** (o que o sistema deve fazer).
- **Requisitos Não Funcionais (RNF)** ou Estruturais (critérios de qualidade e restrições sobre as funcionalidades).

**Solução:** A equipe realizou a separação detalhada de cada especificação técnica, classificando-as da seguinte forma:

- **Requisitos Funcionais**:
    1. O sistema deve permitir que os usuários criem uma conta usando seu endereço de e-mail (funcionalidade de cadastro).
    2. O sistema deve permitir que os usuários filtrem hotéis por localização, preço e disponibilidade (funcionalidade de busca complexa).
    3. O sistema deve enviar um e-mail de confirmação após a conclusão de uma reserva (comportamento de notificação).
    4. O sistema deve manter um registro de todas as reservas feitas, acessível pelos administradores do hotel (persistência de dados lógicos).
    5. O sistema deve permitir que os administradores do hotel gerenciem as informações de seus hotéis (funcionalidade administrativa).
- **Requisitos Estruturais (Não Funcionais)**:
    1. O sistema deve criptografar as senhas dos usuários antes de armazená-las no banco de dados (restrição de segurança/privacidade).
    2. O tempo de resposta para buscas de hotéis não deve exceder 2 segundos (critério mensurável de desempenho).
    3. O sistema deve ser acessível em dispositivos móveis e desktops (restrição de compatibilidade/portabilidade).
    4. O sistema deve garantir uma disponibilidade de 99,9% (critério de robustez e operação).
    5. O sistema deve oferecer suporte a múltiplos idiomas (critério de usabilidade e internacionalização).

**Resultado:** Uma documentação de escopo clara que permite aos programadores saberem quais funcionalidades precisam codificar diretamente na lógica de negócios e aos arquitetos saberem quais restrições de desempenho, segurança e infraestrutura de hardware devem ser implementadas no ecossistema de software.

**Por que essa solução funciona:** Ao mapear separadamente os requisitos de desempenho e segurança como não funcionais, a arquitetura do sistema é desenhada para suportar criptografia e alta disponibilidade em nível de servidor e banco de dados, enquanto os programadores se concentram em codificar as telas e filtros sem misturar regras de infraestrutura.

**O que preciso aprender com esse exemplo:** Os **requisitos funcionais** definem o comportamento e as ações diretas do software; já os **requisitos estruturais (não funcionais)** definem os limites de qualidade, restrições e padrões arquiteturais cruciais para que o software funcione com segurança, rapidez e escalabilidade.