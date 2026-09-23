
**Descrição da situação-problema**

Considere uma rede pública de hospitais que faz uso de um sistema de prontuário eletrônico para atender os pacientes de forma mais ágil e eficiente. A rede conta com profissionais de TI e infraestrutura própria na qual está implantado o sistema há alguns anos. O sistema inclui uma base com grande volume de dados sobre o histórico médico dos pacientes.

A fim de reduzir os gastos com os recursos de TI, a rede hospitalar decidiu migrar o sistema para um provedor de computação em nuvem. No entanto, como analista de TI da rede hospitalar, você sugere a necessidade de especificar um plano de contingência para o caso de ocorrer algum problema, pois os hospitais não podem interromper o atendimento aos pacientes. Dessa forma, um dos diretores do hospital lhe faz o seguinte questionamento: quais são os riscos envolvidos na migração para o ambiente de nuvem?

**Resolução da situação-problema**

Existem diversos riscos, entre os quais podemos destacar:

- **Risco de violação de privacidade dos dados médicos dos pacientes**. Como os dados serão transmitidos pela rede dos dispositivos de acesso para o provedor, existe a possibilidade de que eles sejam interceptados por agentes maliciosos, o que seria um problema crítico. Outra possibilidade ligada à segurança é o eventual compartilhamento de recursos no provedor, por exemplo, se as máquinas virtuais alocadas para a rede hospitalar estiverem no mesmo servidor físico no qual estejam também máquinas virtuais de outros clientes. Caso não haja isolamento e proteção dos dados de forma adequada, os dados médicos podem ser violados.

- **Risco de os dados serem armazenados fora de região permitida**. Em geral, os provedores de computação em nuvem possuem vários centros de dados em diferentes regiões, inclusive em países diferentes. Como se trata de uma rede pública e de dados médicos, pode haver restrições legais sobre os dados armazenados em outras regiões. Por exemplo, existem dados de órgãos públicos federais que não podem ser armazenados em outros países. Mesmo que a rede hospitalar escolha um centro de dados em uma região permitida, é preciso estar atento para que réplicas dos dados não sejam criadas em outras regiões.

- **Risco de indisponibilidade do serviço**: se houver falha no provedor ou nos enlaces de comunicação, o sistema não poderá ser acessado remotamente. O desempenho da rede e a confiabilidade do provedor são críticos para operação do sistema.