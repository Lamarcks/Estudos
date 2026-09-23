**Problema:** Evitar que um estudante recém-matriculado precise redigitar suas informações pessoais e financeiras para departamentos diferentes (como a secretaria acadêmica e o financeiro).

**Conceito utilizado:** Banco de dados centralizado e compartilhamento de base de dados multiaplicação.

**Solução:** Substituir o armazenamento de arquivos isolados por setor por um banco de dados único centralizado, acessado por interfaces e sistemas de aplicação distintos.

- O sistema de controle acadêmico da secretaria realiza o cadastro e insere os dados no banco central.
- O sistema do setor financeiro consulta a mesma tabela de dados pessoais para gerar os boletos de pagamento, sem duplicar o cadastro.

**Resultado:** Consistência e integridade das informações entre departamentos, reduzindo o retrabalho.

**Por que essa solução funciona:** O SGBD centraliza o armazenamento dos arquivos físicos em um único servidor e gerencia as conexões simultâneas das aplicações de forma síncrona.

**O que preciso aprender com esse exemplo:** A principal vantagem de um banco de dados integrado não é apenas guardar dados, mas permitir que múltiplos softwares consumam a mesma fonte de dados de forma consistente e com controles de acesso específicos.