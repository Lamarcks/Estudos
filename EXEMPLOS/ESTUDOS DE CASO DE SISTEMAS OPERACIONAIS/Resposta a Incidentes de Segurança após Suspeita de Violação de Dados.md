**Problema:** Uma empresa que lida com registros pessoais e financeiros confidenciais de clientes descobre que a integridade de seu sistema de arquivos compartilhado na rede interna foi violada, ocorrendo um vazamento de dados de relatórios. A diretoria exige medidas de resposta imediata para conter a falha e auditar o sistema.

**Conceito utilizado:** Auditoria, Criptografia e **Controle de Acesso Baseado em Papéis (RBAC - Role-Based Access Control)**.

**Solução:** Agir de acordo com o plano de resposta a incidentes de segurança cibernética:

1. **Auditoria de Acesso**: Analisar os logs e registros detalhados do sistema para rastrear quem visualizou, modificou ou copiou arquivos recentemente.
2. **Controle de Acesso por Papel (RBAC)**: Migrar a concessão de acessos comuns para perfis baseados no cargo/função do colaborador no organograma da empresa, limitando credenciais individuais soltas.
3. **Criptografia em Repouso**: Aplicar criptografia total aos discos que guardam dados de clientes.
4. **Firewalls e Segurança de Rede**: Segmentar a rede interna para bloquear conexões não autorizadas ao servidor compartilhado.

**Resultado:** Identificação do usuário ou brecha que causou o vazamento, bloqueio imediato de novas intrusões e proteção nativa dos arquivos vazados caso o disco físico seja removido da rede corporativa.

**Por que essa solução funciona:** Logs detalhados de auditoria registram cada chamada ao sistema com carimbo de tempo (timestamp) e ID de usuário, servindo como uma trilha forense incontestável. A criptografia de dados em repouso garante que se o invasor extrair os arquivos binários do HD, ele não conseguirá descriptografar os dados sem a chave secreta.

**O que preciso aprender com esse exemplo:** A segurança em sistemas de arquivos deve ser proativa e contínua. Logs de eventos detalhados, isolamento de rede e criptografia de dados são os três elementos básicos necessários para auditar e resistir a incidentes de vazamento.