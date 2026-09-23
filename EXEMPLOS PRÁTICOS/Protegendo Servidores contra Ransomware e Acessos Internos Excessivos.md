**Problema:** A equipe de TI de uma empresa descobriu que a maioria dos funcionários internos possui permissões de nível de administrador sem necessidade. Essa configuração expõe a empresa a vazamentos de dados de clientes, remoções acidentais e vulnerabilidade extrema a ataques de ransomware, que poderiam paralisar toda a operação caso o malware infectasse uma única máquina.

**Conceito utilizado:** Princípio de **Mínimos Privilégios (Least Privilege)**, autenticação unificada e proteção a longo prazo.

**Solução:** Implementar um plano de proteção em profundidade baseando-se em 6 pilares de segurança:

1. **Configuração de Mínimos Privilégios**: Restringir permissões para que cada usuário acesse apenas as pastas necessárias ao trabalho.
2. **Controle de Acesso Centralizado**: Integrar todas as contas via Active Directory ou LDAP, forçando senhas complexas e expirações periódicas.
3. **Instalação de Antimalware Corporativo**: Prover varreduras síncronas contra ramsomwares com monitoramento e alertas em tempo real.
4. **Configuração de Backup Protegido**: Realizar backups automáticos diários criptografados e armazenados em servidores isolados fisicamente e fora da rede local.
5. **Atualizações Automáticas**: Configurar o S.O. para instalar correções críticas automaticamente em horários fora do expediente.
6. **Treinamento de Equipe**: Fornecer workshops periódicos para os usuários evitarem ameaças comuns de phishing.

**Resultado:** Isolamento de privilégios de acesso a dados confidenciais, mitigação contra malwares avançados e capacidade de restauração limpa sem riscos de pagamento de resgate a cibercriminosos.

**Por que essa solução funciona:** Se um computador for infectado por um ransomware, o vírus só conseguirá criptografar os arquivos para os quais aquele usuário logado possuía permissões de escrita. Ao retirar privilégios excessivos e usar grupos limitados, o S.O. atua como um escudo contendo o alastramento do malware na rede.

**O que preciso aprender com esse exemplo:** O elo mais fraco da segurança cibernética é o fator humano. Controlar privilégios por meio de contas centralizadas e manter backups isolados fora de rede são as melhores defesas para a sobrevivência de dados organizacionais.